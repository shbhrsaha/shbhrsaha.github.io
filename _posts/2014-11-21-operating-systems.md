---
layout: post
title: How a course in operating systems changed me
---
<br />
![](/static/operating-systems/low-level.png)
<br /><br />
There are few classes at Princeton that changed me like COS 318 (Operating Systems). It was challenging, time-munching, and exhausting, but looking back: I'm glad I took the course.

I had hesitation going into the class because of common wisdom surrounding Operating Systems courses:

> "OS sounds really hard" <br />
> "OS is only for people interested in low-level stuff" <br />
> "OS is a waste of time... when are you going to use that material?"

It's a difficult class, for sure, but consider momentarily suspending anything you've previously heard about the course. Not taking OS isn't going to ruin your software engineering career, but taking it could change you in astounding ways. As a student admittedly lousy at low-level programming, I had my fears going into the course. Now on the other side, I feel that taking OS was the best course selection decision I ever made. Here are some of the ways I changed as a student, software engineer, and problem-solver.

My experience is based on Princeton's COS 318 in Fall 2013, but the impact is generalizable to many other undergraduate OS courses.

(1) OS made me better at debugging
---
There is no doubt that writing an operating system requires a *lot* of debugging. If you thought debugging in your algorithms course was hard, try debugging a program where running it two different times yields two completely different results.

When programs become as intricate as they do in OS, you're forced to learn about the right tools (debuggers are you friend) and develop a disciplined approach to debugging.

<br />
![](/static/operating-systems/rubber-chicken.png)

Before taking the class, debugging was a wandering process in which I frantically tried to brainstorm things I could have messed up. It's a hopeless and exhausting process that I call "rubber chicken debugging". After OS, debugging suddenly turned from an art into a science. I recognized that, in most cases, there is an optimal set of things I can log to locate the problem and quickly discern what solution needs to be implemented.

This approach has proved valuable in other courses and beyond. For example, during my internship at Facebook, I fully embraced the engineering culture of "getting your hands dirty" in the code. If something doesn't work, start logging... immediately. Keep logging until reality disagrees with your expectation. That's the way of thinking that an intensive programming course like OS requires.

(2) OS made my code more efficient
---
OS suddenly made me more conscious of my code's performance. If a program took a long time to run, I would pause to think: what is the limiting factor? CPU? Memory? Disk I/O? Understanding the fundamentals helped me to make my higher-level code faster and leaner.

This fact flies in the face of common wisdom that knowing about operating systems is useful only if you enter a career in low-level programming. Nothing could be further from the truth. It's only by writing OS code in C and Assembly that I appreciated the building blocks of higher level programming languages.

(3) OS made me a better collaborator
---
<br />
![](/static/operating-systems/pair.png)

Our OS class had a few partner projects, in which groups of two students pair-program the assignment. I was incredibly fortunate to be with two of my best friends through the projects. The shared experience of daunting challenges made partners better friends and the whole class a more bonded group.

As collaborators, we became better at pair programming. At first, the temptation with pair programming is for one person to type the code and the other to sit back and watch. In OS, we strived to check each other's code as we went and split up the implementation when it made sense to do so. Collaboration required that we get smarter about version control, so it was also a great opportunity to get better at Git.

(4) OS made me a more disciplined problem solver
---
This is biggest change of all. As a young programmer, I usually turned to the [Feynman Algorithm](http://c2.com/cgi/wiki?FeynmanAlgorithm) when faced with any problem:

1. Write down the problem
2. Think really hard
3. Write down the solution

Adopting this approach made the first few projects in OS absolutely miserable. The class demanded that I develop a more disciplined approach to problem-solving. I ended up creating a method for doing programming assignments that I began applied to other CS classes as well. It involves three sheets of paper for tracking:

(1) __Tasks__: What needs to get done to finish this assignment? I'm [very task-oriented](/2013/09/01/organize-projects/) in project management, so having a list of small tasks comforted me by organizing my work. Start by writing down the big tasks and breaking things down from there. As an analogy, consider the project of baking a cake:

- Procure ingredients
    - Buy eggs
    - Buy milk
    - Buy flour
- Prepare kitchen
    - Wash bowl
    - Wash pan
    - Wash scooper
    - Pre-heat oven
    - Grease pan
- Execute assembly
    - Mix eggs, milk, and flour to make batter
    - Spread batter across pan
    - Insert pan into oven

There are more steps than that, but a list like this sets you up for a feeling of accomplishment after finishing each task. The key is to make these tasks really small so that you're always making progress.

(2) __Bugs__: What bugs do I know about in the code? On this sheet I track open bugs and things I've tried to fix them. In earlier projects I wasted time repeating possible solutions and running into the same bug multiple times. Diligently tracking my bugs and their fixes in later assignments saved me a great deal of time.

(3) __Questions__: What questions do I have? Here I  jot down literally any question I have as soon as I get it. As I learn the answers over time by reading documentation and asking classmates, the knowledge is recorded here.

<br />
![](/static/operating-systems/motion-progress.png)

Having these sheets of paper largely gave me confidence that progress was being made. Without it, I was putting in long hours in the computer lab-- making motion-- but not actually accomplishing much by the end of the day.

Closing Thoughts
---
OS is certainly a challenging course, but consider giving it a shot. It's the class that improved me most as a software engineer. And even if you don't ever remember what a hypervisor is, I think you'll truly appreciate all of the other skills you gain.

Some other perspectives on these topics if you want to read more:

- [John Regehr: Why Take an Operating Systems Course?](http://blog.regehr.org/archives/164)
- [Sean Cassidy: Sherlock Holmes Debugging](http://blog.seancassidy.me/sherlock-holmes-debugging.html)

Thanks to [Dan Kang](http://dskang.com/) for reviewing this post.

[ November 2014 ]

[Hacker News](http://www.reddit.com/r/programming/comments/2n0nw5/how_a_course_in_operating_systems_changed_me/)
&sdot;
[Reddit](http://www.reddit.com/r/programming/comments/2n0nw5/how_a_course_in_operating_systems_changed_me/)
