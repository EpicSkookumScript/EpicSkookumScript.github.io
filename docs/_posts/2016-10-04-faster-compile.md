---
layout: post
title: "Upcoming SkookumIDE will compile waaaaay faster"
sidebar-page: none
categories: Unreal

---

The mad computer scientists of SkookumScript are feverishly at work on the next version of the SkookumIDE (Integrated Development Environment)—and we are unabashedly giddy to reveal that we have just reconfigured the compilation process to make SkookumScript compile 10-25 times faster!

We mad-scientifically verified this result by going back to the code for <a href="/about/#sleeping-dogs"><em>Sleeping Dogs</em></a>—a massive open-world game with 8000 complex SkookumScript commands—and found that its compile time has leaped from an already awe-inspiring 3 seconds on the current SkookumIDE to an amazing 0.3 seconds on the upcoming SkookumIDE. That’s 10 times faster, folks. And on our SkookumDemo project, which contains 5000 Unreal Engine 4 calls, compile speed jumped from 3 seconds to a blink-and-you’ll-miss-it 0.12 seconds. That’s 25 times faster—fast enough to be accurately described as “insanely fast”. <em>Muahahaha!</em>

What sorcery is this?! We accomplished this phenomenal feat by moving all SkookumScript files into memory, making it unnecessary for the IDE to access the hard drive during the compiling process. Oh yeah. We went there. And we did that.

Stay tuned for the new-and-improved SkookumIDE, coming later this fall from the SkookumScript team!

![](/images/blog/2016-10-04_skookumdemo.jpg){:.pic-full}

It's great that this demo now compiles 25 times faster, but what I really want is for this robot to stop crashing into me and exploding.
{:.caption}



