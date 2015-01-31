---
layout: post
title: Distraction-free writing on the Amazon Kindle
---

<br />
![](/static/writing-amazon-kindle/photo.jpg)
<br /><br />

I love the Amazon Kindle's E-Ink screen.

It's gentle on the eyes, reads easily in sunlight, and creates a distraction-free environment for reading. I wondered, then: how can I use the E-Ink screen for _writing_?

There are some existing solutions. [E-Ink monitors](http://blog.the-ebook-reader.com/2015/01/15/paperlike-13-3-e-ink-monitor-by-dasung-tech-videos/) are for sale, but they're expensive. Alternatively, Max Ogden has a [great tutorial](http://maxogden.com/kindleberry-wireless.html) on how to jailbreak the Kindle to SSH into the Raspberry Pi. His hack provides a portable setup for focused coding and writing.

Jailbreaking felt tedious, though, because of sparse and outdated documentation. I wondered if I could instead use the Javascript-enabled Kindle web browser to display what's typed on another machine in real-time (a la [Collabedit](http://collabedit.com/)).

The result was [_Typewriter_](https://github.com/shbhrsaha/typewriter), a Meteor app that brings distraction-free writing to the Kindle. After firing it up, I point the Kindle's web browser to the Meteor app's IP address and port. Because Meteor synchronizes data across clients, what I type into the computer's browser instantly appears on the Kindle. It actually feels a little magical. The screen is surprisingly responsive to keystrokes, considering network and E-Ink refresh latencies.

<br />
<video width="600" autoplay="autoplay" loop muted>
  <source src="/static/writing-amazon-kindle/clip.mp4" type="video/mp4" />
  Your browser does not support the video tag.
</video>
<br /><br />

Typewriter periodically saves drafts in a backup folder in case I accidentally delete my work. I couldn't figure out a clever way to display the cursor position, but Typewriter generally works well for writing first drafts. In the future it would be nice to run Typewriter on a Raspberry Pi so I won't have to keep a Macbook running on the side.

At a broader level, this hack illustrates the power of Kindle's Javascript engine. The browser can be a foundation for presenting applications in E-Ink, stretching what's possible in an otherwise locked-down operating system.

[ January 2015 ]

[GitHub](https://github.com/shbhrsaha/typewriter)

_Thanks to [Charlie Marsh](http://www.crmarsh.com/) for reading an earlier draft of this post._
