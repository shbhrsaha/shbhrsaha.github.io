---
layout: post
title: "Life after Codecademy: setting up your<br /> development environment"
---

![](/static/development-environment/angrylaptop.png)

### Introduction

So, you've finished a tutorial on Codecademy. Now what?

It's time to set up your development environment. This process is one of the most overlooked and oftentimes frustrating part of learning to program, but it's easier with the right preparation.

In this article, I'll begin by explaining what a development environment is and why it's sometimes hard to set up. I'll then offer some advice to keep in mind as you actually set up your development environment. Finally, I'll conclude by recommending some tutorials that will instruct you how to set up a development environment in the language/platform of your choice.

### What is a Development Environment

Codecademy is an amazing tool. It's great for getting "the feel" for programming and the syntax of a particular language with clear guidance each step of the way. But at some point, you'll want to start writing programs of your own. To do so, you must first set up a development environment on your computer.

A development environment is a set of software that enables you to write programs for a particular language or platform. This software oftentimes includes a text editor, shell, and a compiler/interpreter.

A text editor is simply a program in which you'll type your code. Examples include [Sublime Text](http://www.sublimetext.com/), [Notepad++](http://notepad-plus-plus.org/), and [Eclipse](http://www.eclipse.org/). You're probably familiar with the Codecademy text editor:

{% include image.html url="/static/development-environment/codecademy.png" caption="Codecademy's text editor and development environment" %}

A text editor on your computer is similar, but offers a number of extras like file saving, autocomplete, and debugging tools.

The shell is the second component of a development environment. Simply put, the shell is a program in which you give commands to the computer, and the computer returns its response. Though bewildering at first, the shell will very quickly become an indispensable part of your software development toolkit.

{% include image.html url="/static/development-environment/shell.png" caption="What a shell looks like" %}

On Windows, the default shell is called Command Prompt. On OS X, the shell is called Terminal. I highly recommend that beginners with Windows computers use a program called [Cygwin](http://www.cygwin.com/) instead of Command Prompt. This is because Cygwin lets you use a shell environment called "bash"--which is the same environment in OS X Terminal and most Linux systems. In addition, most shell commands you encounter on the web will probably be for the bash environment, so it's best that you set up your development environment accordingly. More details can be found in the Windows-related tutorials at the links below.

Finally, a key part of your development environment is a compiler or interpreter. The details here are not too important to worry about, at the moment. In essence, the compiler/interpreter is software that will take the code you write and convert it into a form that the computer can understand.

### Why Setting Up a Development Environment Can Be Hard

Development environment setup is oftentimes overlooked because developers don't _really_ want to think about it. In truth, setting up a development environment can be a frustrating process because everyone's computer is slightly different. As a result, the same setup tutorial may work for one developer and not another.

From a beginner's standpoint, the challenges of setting up a development environment flies in the face of the mainstream belief that programming is "easy". It's at this stage that many beginners are suddenly forced to think in a programmer's mindset. Creativity, logical reasoning, and adaptability are all important skills to kick in at this stage.

### How to Set Up a Development Environment

I don't want to explain the exact links and clicks required to set up a development environment. There's plenty of good tutorials for that, which I'll recommend at the end. Instead, I want to offer some general advice for setting up a development environment that will ultimately guide you through the process.

First, you should decide for what language/platform you want to write software. Decide whether you want to make Python programs, Android apps, HTML web sites, or something else.

Once you've decided on a language/platform, find a good tutorial to guide you through the process. You can ask an experienced friend for a recommendation or search on Google. An experienced friend can discern for you whether a tutorial is clear, up-to-date, and worth your time. On the other hand, searching on Google is not too difficult--as the best tutorials usually rise to the top.

An absolutely crucial skill you need to learn is the ability to google effectively. Consider the following query for finding a Python development environment: "how to set up python development environment on windows."

Including a phrase like "how to" or "getting started" will help to locate tutorials. Then, you should include the language/platform you want and the words "development environment". Finally, it's important to mention the operating system (Windows, in this example) you use because the instructions for setting up the development environment will vary.

From there, you should pick a tutorial that you like and follow the instructions!

What if you get stuck? That's perfectly fine. In programming, few things ever go as planned the first time. Perhaps some command you type throws an error or an installation doesn't go as planned.

Once again, you should turn to Google as your primary source for help. It's even more critical here to use good search techniques. I suggest that you copy-paste as succinct and representative excerpt of the error as possible. The more succinct the better, and by "representative" I mean you should google excerpts that are unique to the situation.

For example, perhaps the error you encounter is "TypeError: unsupported operand type(s) for +: 'int' and 'str'". If you google only "TypeError", you will receive too broad a set of search results because there are many instances in which a TypeError will be thrown. Including the entire line excerpted above will be more effective because it is unique to your particular situation. Be careful, though, you don't want to include information that is unique to you and only _you_. For example, you should exclude parts of the error that include your computer login name and directories specific to your personal project. You need to use your judgment and have some sense of the underlying problem. It's not obvious initially, but you will quickly develop intuition.

### Conclusion

As frustrating as it may sometimes be, setting up a development environment is perfectly doable! If you get stuck, troubleshooting help is abundant on the web. Most experienced developers are also happy to help.

Having your development environment also just feels great. You'll feel like a carpenter geared up with a hammer and nail. You'll have everything you need to build the software you want.

In closing, I'd like to recommend a few tools and tutorials that might help you get started.

- Python
    - Windows: [How to Set Up a Python Development Environment on Windows](http://www.davidbaumgold.com/tutorials/set-up-python-windows/)
    - OS X: Macs already have Python installed. Just run `python` from Terminal.
- Java
    - Windows & OS X: [UC Irvine](http://www.ics.uci.edu/~thornton/ics22/LabManual/SettingUpJava.html)
- HTML/CSS/Javascript
    - Windows & OS X: You just need a web browser and text editor! (See below for recommendations.)
- Android
    - Windows & OS X: [Android SDK](http://developer.android.com/sdk/index.html)
- iOS
    - OS X: [First XCode Project](http://codewithchris.com/first-xcode-project/)

If you're doing Java development, I recommend [Eclipse](http://www.eclipse.org/) or [NetBeans](https://netbeans.org/) for project management. For general-purpose text editing and programming in most other languages, I recommend [Sublime Text](http://www.sublimetext.com/).

[ May 2014 ]