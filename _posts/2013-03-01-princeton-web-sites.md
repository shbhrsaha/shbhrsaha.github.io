---
layout: post
title: Who at Princeton has a web site?
category:
    - Other
---

> I was curious how many students at Princeton had posted a web site and, if so, what those sites were about. Check out the [Princeton Undergraduate Personal Web Site Surfer](/static/princeton-web-sites/explorer.html) to stumble upon some cool pages.

![](/static/princeton-web-sites/graph1.png)

### Student Web Sites Are Interesting
Every student at Princeton University has the opportunity to set up a static web site at the www.princeton.edu/~netid/, where "netid" is their student computer username. In fact, the page you're reading is hosted on one such site (my netid is saha).

A few weeks ago in February 2013, I found myself with a file containing College Facebook data for every undergraduate currently attending the university. With this large list of NetIDs, I was curious how many students at Princeton had posted a web site and, if so, what those sites were about. Visiting student web sites are a cool way to learn about myriad student activities and interests across academic departments.

### The Scripts
I wrote a few Python scripts to ping every netid-based url at princeton.edu, record the HTTP response status, and for those returning a response code of 200, ensure that the content was more than just the default directory listing.

### The Fun Stuff
The final list contained 383 netids whose web sites seemed to contain interesting information. I then wrote [Princeton Undergraduate Personal Web Site Surfer](/static/princeton-web-sites/explorer.html) to randomly present only those webpages that were detected to contain interesting content as of March 2013.

I wondered about the breakdown of web sites posted by class:

![](/static/princeton-web-sites/graph3.png)

And here's the number of web sites by major:

![](/static/princeton-web-sites/graph2.png)

It's expected that Computer Science is near the top of the list, but I was surprised to see Politics, History, and English close behind. In the coming years I bet we'll see more students setting up web sites.

### GitHub
The main scripts are available in a [GitHub repository](https://github.com/shbhrsaha/websites).

### Notes

Thanks to everyone who wrote in:

1. Margaret Fortney '13 and Peter Johnsen '15 add that COS 109 -- "Computers in Our World" -- would explain the prevalence of web sites among non-COS students. The course is commonly taken to fulfill the quantitative reasoning distribution requirement and features a project where students build personal web sites.
2. Margaret recommends [this article](http://helpdesk.princeton.edu/kb/display.plx?ID=9847) for students looking to set up their own ~netid web site.
