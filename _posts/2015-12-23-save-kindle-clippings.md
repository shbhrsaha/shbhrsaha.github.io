---
layout: post
title: Save Kindle clippings with Dickens
categories:
    - Productivity
published: true
---

{% include image.html url="/static/saving-kindle-clippings/screenshot.png" caption="Dickens displaying clippings from a recently read article" %}

I'm a big fan of the Amazon Kindle. Not only is it great for reading books and articles, but also it has a clever highlighting/commenting feature. I can drag my finger across the text to highlight it, optionally add a comment, then revisit it later on the device.

Where the Kindle falls short is in providing an easy way to transfer those clippings to a computer. To the best of my knowledge, every Kindle maintains a file called `documents/My Clippings.txt` that stores all clippings across the device's publications. The format is verbose, however, and it's annoying to search for the exact passage in a particular publication. Amazon created a dashboard at [kindle.amazon.com](https://kindle.amazon.com/), but clippings are limited to those from publications purchased through the Kindle store.

I created [Dickens](https://github.com/shbhrsaha/dickens) to simplify viewing Amazon Kindle clippings on the computer. The application is more convenient than reading 'My Clippings.txt' myself or uploading it to a web service. Unlike the Amazon Kindle web application, Dickens loads clippings from content not purchased on the Amazon Store as well.

This was my first time building an app in [Electron](http://electron.atom.io/), and I loved it. While the packaged applications it creates are large, Electron is delightfully elegant and has a small learning curve.

[Download for Mac OS X](https://github.com/shbhrsaha/dickens/releases/download/v0.1/Dickens.zip) &sdot; [GitHub](https://github.com/shbhrsaha/dickens)
