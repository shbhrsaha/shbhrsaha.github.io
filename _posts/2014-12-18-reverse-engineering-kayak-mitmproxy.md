---
layout: post
title: Reverse-engineering the Kayak app with mitmproxy
categories:
    - Software
links:
    - Hacker News: https://news.ycombinator.com/item?id=8778003
    - Reddit: https://www.reddit.com/r/programming/comments/2px1mv/reverseengineering_the_kayak_app_with_mitmproxy/
    - Hackaday: http://hackaday.com/2015/01/03/reverse-engineering-the-kayak-mobile-api/
popular: True
---
![](/static/kayak-mitmproxy/kayakapp.png)

### Introduction

[Kayak](http://www.kayak.com/)-- the popular fare comparison web site-- recently [discontinued](https://www.kayak.com/labs/api/search/) their API service. To the dismay of travel hackers, fare comparison APIs frequently [come and go](http://stackoverflow.com/questions/10680408/is-there-any-api-for-getting-flight-fare). But that doesn't mean we can't hack together our own Kayak API.

Web scraping is the most common way to imitiate an API, but it's vulnerable to small changes in the UI. On the other hand, _mobile_ is an area where UI changes are often independent of the supporting server API. Developers often change the "look and feel" of the mobile app, but seldom swap out the server _endpoints_ from which data are obtained. For this reason, reverse-engineering mobile applications is a good way to expose APIs that we can exploit.

In this post, I'll explain how I used [mitmproxy](http://mitmproxy.org/)-- a popular network analysis tool-- to reverse-engineer the Kayak mobile app. The result is an understanding of important server endpoints that can be accessed programmatically for personal use.

### Setup

My tool of choice for reverse-engineering mobile apps is mitmproxy because it presents network activity in a clean, hackable interface. I used Wireshark for a long time, but I actually couldn't get the TLS decryption working and the X-Window interface was a little clunky. Mitmproxy functions as a proxy between the mobile device and the rest of the Internet. Any traffic targeting the phone must travel through mitmproxy, allowing us to analyze it.

Getting started with mitmproxy is straightforward:

    pip install mitmproxy

Run `mitmproxy` to generate certificate files in `~/.mitmproxy`. From that folder, get the `mitmproxy-ca-cert.pem` file onto your mobile device by emailing it to yourself, for example. Then follow certificate installation steps for [iOS](http://mitmproxy.org/doc/certinstall/ios.html) or [Android](http://mitmproxy.org/doc/certinstall/android.html). Because I used the Kayak iPhone app, I'll continue this tutorial with iOS.

Mobile apps often encrypt traffic to protect data integrity and confidentiality. Transport Layer Security (TLS) is a popular protocol for implementing this encryption. By installing the certificate on a mobile device, we’re enabling mitmproxy to decrypt its TLS traffic, which includes HTTPS requests and responses.

We need to configure the mobile device to use our computer's IP address as the proxy. On a Mac, we can find the IP address my opening up System Preferences > Network:

![](/static/kayak-mitmproxy/ipaddress.png)

I configured my iPhone to use my Mac as the proxy by tapping Settings > Wi-Fi > [Network Name], and set HTTP PROXY to 'Manual'. Then I set the computer's IP address as the server and 8080 as the port.

### Recording Kayak network activity

We're now able to observe and save all of the iPhone's network activity, including those occuring over HTTPS. Let's record activity for the Kayak iPhone app by running `mitmdump -w kayak_flows.out` and tapping through the Kayak app as usual. In particular, navigate to Flights > From > Current location > Find Flights. After getting to the search results page, close the Kayak app and exit mitmdump by pressing `ctrl+c`. We know that, during this usage, the Kayak app must have communicated with the server to learn airports and prices.

### Browsing saved network activity

Having saved the network activity to a file, we can browse the results in a beautiful [curses](http://en.wikipedia.org/wiki/Curses_%28programming_library%29) interface with `mitmproxy -r kayak_flows.out`.

![](/static/kayak-mitmproxy/mitmproxybasic.png)

As we flip through the requests with the arrow keys, the first to jump out is:

    GET https://www.kayak.com/k/authajax/?action=registermobile&uuid=[UNIQUE IDENTIFIER]&hash=[A HASH]&model=iPhone4,1&appid=kayakfree&os=8.1.1&msgApiVersion=1&as=0&appdist=adhoc&prefix=`

I hit &lt;Enter&gt; then &lt;Tab&gt; to view the server response. We discover fields for `status`, `uid`, `token`, `sid`, and `bogus`.

Great! Let's make a note of the `uid`, `token`, and `sid` fields because they might be used in later requests. Back in the request list, we continue to look for interesting URLs. Here's one:

    GET https://www.kayak.com/api/search/V8/flight/start?cabin=e&travelers=1&origin1=BDL&nearbyO1=false&destination1=LAX&nearbyD1=false&depart_date1=12/18/2014&depart_time1=a&depart_date_flex1=exact&_sid_=[SID VALUE]

![](/static/kayak-mitmproxy/mitmproxyresponse.png)

This request generates a `searchid` that will probably be used shortly to uniquely identify our choice of airports, dates, and other preferences.

Indeed, that's the case! Our attention is drawn to:

    GET https://www.kayak.com/api/search/V8/flight/poll?currency=USD&searchid=[SEARCH ID]&c=2000&providerData=true&nc=40&includeopaques=true&showAirlineLogos=true&_sid_=[SID VALUE]

This request includes our `searchid` and `sid` from earlier, and the response is a large JSON object that includes airline names, prices, contact, booking URLs, and more. This is exactly the data we're looking for.

![](/static/kayak-mitmproxy/mitmproxyprices.png)

### Putting it all together

Let's put these observations together to discern a basic API:

- Think of the `uuid=[UNIQUE IDENTIFIER]&hash=[A HASH]` fields to be like an API key and secret generated when running the mobile app.
- Generate an `sid` at: `https://www.kayak.com/k/authajax/`
- Generate a `searchid` at: `https://www.kayak.com/api/search/V8/flight/start`
- Retrieve prices at: `https://www.kayak.com/api/search/V8/flight/poll`

You can check out a complete basic client on [GitHub](https://github.com/shbhrsaha/kayak-mobile-client).

The results presented here are far from a complete API, but I hope this tutorial demonstrates the power of reverse-engineering mobile apps. Tools like mitmproxy helps us obtain a level of understanding previously prohibited by the locked-down nature of mobile operating systems. Given how young the mobile space is, there's never been a better time to do some exploring.

To read more about researching mobile apps with proxies, check out [Extracting My Data from the Microsoft Band](http://jeffhuang.com/extracting_my_data_from_the_microsoft_band.html), [Yik Hak](http://silverskylabs.github.io/yakhak/), and [What They Know Mobile](http://blogs.wsj.com/wtk-mobile/).
