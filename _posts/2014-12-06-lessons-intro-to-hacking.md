---
layout: post
title: Lessons from teaching a hack class
---

> As a class independent of the university curriculum, _Introduction to Hacking_ taught subjects not traditionally listed in the course catalog.

### Introduction

As a college student, I spend most of my (sleep-deprived) days attending class. Rarely do I get the opportunity I had last Spring: to actually _teach_ a class with one of my best friends, Charlie Marsh.

Before you get any ideas about my joining the faculty, I should provide some context. The class, titled [_Introduction to Hacking_](http://introtohacking.github.io/), was one of several student-run "hack classes" offered by the [Princeton Entrepreneurship Club](http://www.princetoneclub.com/). We taught how to solve practical problems with programming. Topics covered included data analysis with Python, web scraping, machine learning, and more. As a class independent of the university curriculum, _Introduction to Hacking_ taught subjects not traditionally listed in the course catalog. The weekly lectures attracted 20-30 students each-- a miracle in an otherwise uneventful campus.

In this post, I share some of the lessons we learned along the way. I hope this information helps future hack class instructors-- and teachers anywhere-- make the most of their classes.

### 1. Hack classes work

I'm enthusiastic about hack classes because they _share interesting knowledge_ in a _flexible format_ with _genuinely passionate students_. 

Each hack class is motivated by an interesting topic-- one that the university does not address, is difficult to learn alone, or both. When Stanford University began to offer an [iOS programming class](http://cs193p.stanford.edu/), the iOS hack class brought the same content to a physical classroom at Princeton. _Introduction to Hacking_ taught topics we felt students were excited about because of technical buzz ("machine learning!") and usefulness over the course of many careers. In both cases, the hack class shared interesting knowledge that was not available in the university curriculum.

Flexibility is a key benefit to hack classes. As an instructor, I can create a class or adjust the syllabus without the bureacracy of a registrar. Students benefit from the freedom to attend whatever lectures they wish. Historically, student retention was a problem in hack classes where material was cumulative from week-to-week because students were afraid of not being able to keep up in lecture. To reverse this trend, we designed the lectures in _Introduction to Hacking_ to be modular-- each session stood by itself and did not require students to attend previous lectures. This proved to be a great idea because it affords students the flexibility to just attend whatever sessions they find interesting.

By their "optional" nature, hack classes attract only genuinely passionate students. This is an amazing benefit because a lecture hall of passionate students leads to rich discussions, which leads to better learning for everyone. Here, too, instructors experience a benefit: to actually be _good instructors_. If Charlie and I were not interesting, people would've simply stopped coming. When things are going poorly, this realization can be disheartening. But when things are going well, it's enriching and motivating for students and instructors alike.

Hack classes aren't perfect, but I believe they effectively fill a gap in the university curriculum. They're flexible initiatives that invite students to teach interesting material to other passionate students. And they work.

### 2. Students take hack classes for different reasons

Charlie and I ask the _why?_ question often. Before even deciding to teach _Introduction to Hacking_, we thought about why exactly we were going to do it. (More on this at the end.)

We realized that students too-- often subconsciously-- think about why they should participate in a hack class. Reasons vary from "I want to learn the material" to "the instructors are my friends". As instructors, we tried to tease out these reasons early with a short survey.

To our surprise, we received over 50 responses! Either students were passionate about communicating their motivations or they loved taking surveys. Responses varied widely, but the two key takeaways were that students had diverse levels of experience, and some students wanted to learn just one or two of the topics on the syllabus. We structured the course with these two considerations in mind.

Because of the diverse levels of experience, we emphasized "survey over deep dive". We used lecture to introduce "what's out there", and concluded with three slides listing next steps for novice, intermediate, and advanced programmers, respectively. Conveniently, the nature of the topics in _Introduction to Hacking_ made the class's survey nature easy to implement. Many advanced programmers just hadn't gotten around to checking out some of the topics like web scraping, and novices didn't require special knowledge to understand how the tools and libraries were used. By explicitly communicating the survey nature of the course, we maintained focus while accomodating the students' diverse levels of experience.

It's perfectly fine for some students to attend one or two sessions. As I mentioned, we designed each lecture to stand on its own. In addition, we distributed lecture slides and example code in advance of the session day as often as possible. This enabled students to attend the lectures that mattered most to them. It also gave us feedback on which topics sounded interesting to students. "Git, Bash Tricks" was our least-attended, "Computer Security: Passwords, Web, Wireshark" our most-attended.

Understanding students' motivations helped us to structure the class most effectively.

### 3. Teaching is hard

Coming out of the class, Charlie and I have a greater appreciation for our teachers. The practice is challenging for a number of reasons.

Teaching requires significant empathy for students. While we were comfortable with the content, we had to take a step back to identify _How would a beginner understand this?_ Adequate preparation was key to answering this question effectively. One instance of this was in the security lecture, where I wanted to introduce packet sniffing tools to students who'd never heard of a network "packet". I had to clear my mind of anything I knew about networks to realize all that mattered was an awareness for "hosts", "routers", and "packets" flowing between them. The result was a [single slide](https://www.dropbox.com/s/9rqa913ewc6luek/7_Computer_Security.pdf) demonstrating their relationship. Striving for simplicity over complexity, I realized that what _not_ to include was just as important as what to include.

Teaching requires significant preparation time. Each week, Charlie and I spent 3-5 hours writing the lecture slides. We then met for an hour to provide each other feedback and divvy up the task of writing the live demo, which usually required another 1-2 hours.

As much as teaching demands empathy and time, it is also incredibly rewarding. A well-prepared lecture feels like it just "falls into place", and the joy of students' understanding makes it worthwhile.

### 4. Communication is crucial

The quality of communication can make or break a hack class. Communication spans messaging, questions, and feedback.

Messaging promotes awareness for the class and maintains student interest from week-to-week. To our amazement, _Introduction to Hacking_ attracted over 200 students to its signup list. I think some of this success can be attributed to "grassroots" methods-- we started adding individual friends who expressed interest to the list months in advance of the course. During the class, we emailed the "what" and "why" of each lecture a few days in advance. We also broadcast-emailed listservs about the individual lecture topics. That way, students who hadn't signed up for the course attended the security lecture just because they were interested in the topic.

In the lectures themselves, we promoted communication by constantly encouraging questions. A trick I learned is to ask "What questions do you have?" instead of "Do you have any questions?". Doing this communicates that questions are _expected_ and are not a barrier to the class's progress. For after class, we tried a "Hack Hour" with an online form submission for questions, but this method quickly fell apart. We realized that informal, one-on-one Q&A that naturally arises after lecture was more effective. The majority of the help provided during that time was for development environment setup.

Charlie and I were eager to hear feedback. Students preferred writing their feedback to saying it in-person. To facilitate that communication, we created an anonymous online form for anyone to send feedback just by clicking a link on the web site. While we received around five responses from that form over that the semester, the majority of feedback came by email from friends.

### Closing Thoughts

A few months after _Introduction to Hacking_ ran, I was chatting with a friend who had taken the course. A politics major, he was actually now studying for a software engineering interview. I was surprised. He explained that, over the past year, he realized software engineering was actually his true calling, and _Introduction to Hacking_ was an influential reason for that change.

Across our projects, Charlie and I are most motivated by the potential for _impact_. It's our answer to the _why?_ question I mentioned earlier: we want our work to matter. My politics friend is just one instance of how hack classes are an incredible vehicle for impact. I believe that, in many cases, students learn more effectively when they're taught by other students. And I'm grateful for the opportunity to have been a part of that.

[ December 2014 ]

