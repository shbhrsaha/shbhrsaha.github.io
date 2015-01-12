---
layout: post
title: Tale of a $1000 Facebook Bug Bounty
---

For some time a few months ago, I became obsessed with [wireless sniffing](http://en.wikipedia.org/wiki/Packet_analyzer). I didn't want to sniff others' wireless traffic so much as be able to detect smartphones by their wireless probes. There is incredible potential in this area-- a startup called [Euclid Analytics](http://euclidanalytics.com/) is tracking smartphone probes inside stores to provide retail customer analytics.

In my reading, I was surprised to find that until 2010, many major web sites sent sensitive user data over HTTP. That's when a clever Firefox plugin called [Firesheep](http://en.wikipedia.org/wiki/Firesheep) popularized the risks associated with transferring sensitive data over unencrypted connections.

On a whim, I opened my iPhone to check whether the mobile versions of today's major web sites used HTTPS to transmit sensitive data. Sure enough, the subtle lock symbol over sensitive pages assured me of HTTPS on Google's sign-in page.

![Google mobile sign-in page](/static/facebook-bug-bounty/google.png)

What caught my eye was that on the Facebook Mobile landing page, the page loaded over HTTP. Notice the lack of a lock.

![Facebook mobile sign-in page](/static/facebook-bug-bounty/facebook.png)

Usually, this is not a problem even for an authentication page, as long as the endpoint receiving the sensitive data (in this case: username and password) is on HTTPS. Many services do this to cut down on the load time of the authentication page. After poking around, I noticed that the password reset page also lacked an SSL certificate on page load.

I wondered: are the endpoints receiving this authentication data secured with an SSL certificate?

As it turned out, the password reset data did not communicate with a secure endpoint. This is troubling because, though rare, anyone with a packet-sniffing program would be able to sniff my new password if I'm resetting the account from a mobile device on an unsecured network. Using a packet-sniffing tool called [Wireshark](http://www.wireshark.org/), I pinpointed the exact HTTP request that exposed my new password.

![Wireshark displays the password in plaintext](/static/facebook-bug-bounty/wireshark.png)

I reported the vulnerability to [Facebook's Bug Bounty](https://www.facebook.com/whitehat) program in late May 2013. Facebook confirmed the bug two weeks later and pushed a patch shortly afterwards. All in all, learning about network security has made this discovery worthwhile, and the $1000 bounty makes it all the nicer. I hardly feel like a security researcher, but I suppose curiosity and dumb luck can be worth something.

[ July 2013 ]

[Hacker News](https://news.ycombinator.com/item?id=6084312)
