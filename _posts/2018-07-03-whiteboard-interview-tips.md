---
layout: post
title: Whiteboard interview tips
categories:
    - Software
published: true
links:
    - Reddit: https://www.reddit.com/r/programming/comments/8vv03q/whiteboard_interview_tips/
---

I'm going through interview training at my employer right now. Watching whiteboard interviews reminds me of mistakes I used to make when coding on a whiteboard:

### Poorly naming variables

Naming variables well makes it easier to manage the solution. Some patterns I like: if the solution involves a single hash table, I name it `lookup`. If there are two similar variables being compared in a function, I name them `first` and `second`.

### Not outlining a solution

This isn't required, especially if you're confident you can immediately code the solution. But, I find outlining a solution in bullet points or pseudocode before implementing it makes the process easier. It's easy to chat about a solution and rearrange components when it's still in outline form. Translating an outline into code should then feel trivial.

### Implementing details first

It's tempting to implement *everything* from the start of a solution to its end. However, it's often better to assume some utility functions and classes exist, then go back to implement them later, if necessary. For example, if the problem involves checking if a username/password is valid, assume an `isCorrectLogin` function at first, then go back later to implement it. Focus on the interesting parts. Doing so prioritizes on the "backbone" of the solution, which gives your interviewer the strongest signal of your coding ability.

### Standing too close to the whiteboard

This mistake took me a while to realize. It's easy to miss the "bigger picture" when standing too close to a whiteboard. Only after I started taking a step back every few minutes did logical errors stand out as obvious. Imagine if your day-to-day coding had to be done with the monitor 2" from your face. It's far nicer to move back a bit.

This is not at all a comprehensive list. There's a lot more others have to say about whiteboard interviews. But these are certainly some things that, in my experience, people don't talk enough about.
