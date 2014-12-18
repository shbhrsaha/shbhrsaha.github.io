---
layout: post
title: Reverse-engineering the Kayak app with mitmproxy 
---
<br />
![](/static/kayak-mitmproxy/kayakapp.png)

### Introduction

[Kayak](http://www.kayak.com/)-- the popular fare comparison web site-- recently [discontinued](https://www.kayak.com/labs/api/search/) their API service. Fare comparison APIs frequently [come and go](http://stackoverflow.com/questions/10680408/is-there-any-api-for-getting-flight-fare) to the disappointment of travel hackers. But that doesn't mean we can't hack together our own API.

The most common solution is web scraping, but that approach is vulnerable to small changes in the UI. On the other hand, _mobile_ is an area where UI changes are often independent of the supporting server API. It's for this reason that reverse-engineering mobile applications is a good way to expose APIs that we can exploit.

In this post, I'll explain how I used [mitmproxy](http://mitmproxy.org/)-- a popular network analysis tool-- to reverse-engineer the Kayak mobile app. The result is an understanding of important server endpoints that can be programmatically accessed for personal use.

### Setup

My tool of choice is mitmproxy because it presents network activity in a clean, hackable interface. I used Wireshark for a long time, but I actually couldn't get the TLS decryption working and the X-Window interface was a little clunky. mitmproxy, on the other hand, offers a beautiful experience.

Getting started is straightforward:

    pip install mitmproxy

Run `mitmproxy` to generate certificate files in `~/.mitmproxy`. From that folder, get the `mitmproxy-ca-cert.pem` file onto your mobile device by emailing it to yourself, for example. Then just follow certificate installation steps for [iOS](http://mitmproxy.org/doc/certinstall/ios.html) or [Android](http://mitmproxy.org/doc/certinstall/android.html). By installing the certificate on the mobile devices, we're enabling mitmproxy to decrypt the mobile device's TLS traffic. Because I used the Kayak iPhone app, I'll continue this tutorial with iOS.

We need to configure the mobile device to use our computer's IP address as the proxy. On a Mac, we can find the IP address my opening up System Preferences > Network:

![](/static/kayak-mitmproxy/ipaddress.png)

I configured my iPhone to use my Mac as the proxy by tapping Settings > Wi-Fi > [Network Name], and set HTTP PROXY to 'Manual'. Then I set the computer's IP address as the server and 8080 as the port. We're good to go!

### Recording Kayak network activity

We're now able to observe and save all of the iPhone's network activity, including those occuring over HTTPS. Let's record activity for the Kayak iPhone app by running `mitmdump -w kayak_flows.out` and tapping through the Kayak app as usual. In particular, I navigate to Flights > From > Current location > Find Flights. After getting to the search results page, I close the Kayak app and exit mitmdump by pressing `q`. I know that, during this usage, the Kayak app must have communicated with the server to learn airports and prices. Our next goal is to understand exactly which endpoints offer this interesting data.

### Browsing saved network activity

Having recorded the network activity to a file, I can browse the results in a beautiful curses interface with `mitmproxy -r kayak_flows.out`.

![](/static/kayak-mitmproxy/mitmproxybasic.png)

As I flip through the requests with the arrow keys, the first to jump out is

    GET https://www.kayak.com/k/authajax/?action=registermobile&uuid=[UNIQUE IDENTIFIER]&hash=[A HASH]&model=iPhone4,1&appid=kayakfree&os=8.1.1&msgApiVersion=1&as=0&appdist=adhoc&prefix=`

I hit <Enter> then <Tab> to view the server response. We discover fields for `status`, `uid`, `token`, `sid`, and `bogus`.

Great! I make a note of the `uid`, `token`, and `sid` fields because they might be used in later requests. Back in the request list, I continue to look for interesting URLs. Here's one: 

    GET https://www.kayak.com/api/search/V8/flight/start?cabin=e&travelers=1&origin1=BDL&nearbyO1=false&destination1=LAX&nearbyD1=false&depart_date1=12/18/2014&depart_time1=a&depart_date_flex1=exact&_sid_=[SID VALUE]

![](/static/kayak-mitmproxy/mitmproxyresponse.png)

This request generates a `searchid` that will probably be used soon to uniquely identify my choice of airports, dates, and other preferences.

Indeed, that's the case! Our attention is drawn to:

    GET https://www.kayak.com/api/search/V8/flight/poll?currency=USD&searchid=[SEARCH ID]&c=2000&providerData=true&nc=40&includeopaques=true&showAirlineLogos=true&_sid_=[SID VALUE]

This request includes our `searchid` and `sid` from earlier, and the response is a large JSON object that includes airline names, prices, contact, booking URLs, and more. This is exactly the information we're looking for.

![](/static/kayak-mitmproxy/mitmproxyprices.png)

### Putting it all together

Let's put these observations together to discern a basic API:

- Think of the `uuid=[UNIQUE IDENTIFIER]&hash=[A HASH]` fields to be like an API key and secret generated by running the app with mitmproxy.
- Generate a session id (`sid`) at: `https://www.kayak.com/k/authajax/?action=registermobile&uuid=[UNIQUE IDENTIFIER]&hash=[A HASH]&model=iPhone4,1&appid=kayakfree&os=8.1.1&msgApiVersion=1&as=0&appdist=adhoc&prefix=`
- Generate a `searchid` for a query at: `https://www.kayak.com/api/search/V8/flight/start?cabin=e&travelers=1&origin1=[ORIGIN AIRPORT CODE]&nearbyO1=false&destination1=[DESTINATION AIRPORT CODE]&nearbyD1=false&depart_date1=[DEPARTURE DATE]&depart_time1=a&depart_date_flex1=exact&_sid_=[SID VALUE]`
- Retrieve prices at: `https://www.kayak.com/api/search/V8/flight/poll?currency=USD&searchid=[SEARCH ID]&c=2000&providerData=true&nc=40&includeopaques=true&showAirlineLogos=true&_sid_=[SID VALUE]`

The results presented here are far from a complete API, but I hope this tutorial demonstrates the power of reverse-engineering mobile apps. Tools like mitmproxy helps us obtain a level of understanding previously prohibited by the locked-down nature of mobile operating systems. Given how young the mobile space is, there's never been a better time to do some exploring.

If you liked this article, check out [Extracting My Data from the Microsoft Band](http://jeffhuang.com/extracting_my_data_from_the_microsoft_band.html), [Yik Hak](http://silverskylabs.github.io/yakhak/), and [What They Know Mobile](http://blogs.wsj.com/wtk-mobile/). All of these projects use proxies to reverse-engineer mobile applications in some way.
