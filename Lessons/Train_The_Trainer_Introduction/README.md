# Introduction to "Train the Trainer"

Hello, and welcome one and all to this train the trainer workshop.

(First: A personal introduction. Who am I, and why am qualified to be in front of everyone?)

# ResOS

During this workshop we are going to be mentioning "ResOS" quite a lot. Just so that we are all on the same
page, ResOS stands for "Researcher Operating System".
 
In short, this training is designed to teach researchers how to use a  new kind of operating system - an operating 
system built in the cloud and designed for doing research at a  University or Research Institution like CSIRO, 
Nasa or CERN.

Hopefully, all of you know what an "operating system" is, be that an operating system for your laptop such as:

* Window Vista, Window 8 or Windows 10
* Perhaps you are an Apple user
* Perhaps you mostly use the operating system on your Android Phone (usually named after some kind of candy) or your
  iPhone operating system
* And some of you might be proper geeks and even use linux - (oooooh!)

Coincidentally, CSIRO, NASA and CERN all use the "cloud operating system" we are going to teach you about.
 
The engine which runs ResOS is called OpenStack.

NB "ResOS" is a conceit: it's a pretend operating system, however we have made up this metaphor to make it easy for 
you to communicate to your community how a cloud operating system works the same way that operating systems on your 
laptops and mobile phones work.

Ok, let's get you started. 

First off, I want you to break up into groups of 3-4 people.

The first exercise that I want you to do as a group is to develop a persona for your group.

"What's a persona?" I think I hear you ask.

A persona is the representation of the goals and behaviour of a group of hypothetical users.

The theory is that by understanding the needs and abilities of that persona, you can better satisfy the needs and 
abilities of the larger group.

A good persona should represent a skill set and a behaviour pattern - not a job description. 

By example, here's a persona that I developed:

## An Astronomer at a University

**Name:**     Associate Professor Glenn Bording
**Job title:**     Senior researcher and lecturer, Radio Astronomy group

**Demographics:**

* 40 years old
* Programming experience in C and Fortran
* Basic HPC experience
* Prefers to work with physical hardware

**Background:**

* While preparing a new course for undergraduates, developed a computing challenge to support research using real data
* Realised the BYOD for most students were not powerful enough
* Labs not suitable for task
* Teaching parallel programming and getting accounts for students would be difficult
* Heard about the research cloud

**Goal:** 

* Now keen to learn about ResOS to see if it solves this problem.

Once you, as a group, have agreed on your persona, hold up a green sticky note. But you'd better be quick, because
I'm giving you only 5 minutes!

Ok: for our purposes today, the persona's that you have developed represent the people that you will be explaining 
our ResOS training course to.

So as we go through today I want each group to ask themselves just what it would take to communicate the concepts or 
activities we are covering to this persona. 

If you find you can't do it, then stop me, and we will all discuss it and see if we can come up with a better approach.
*Ask for one or two persona's to be read out*
*Objectives for the day.*
And I'll occasionally be asking you for a demonstration of how you would do this...

What we will be working with is a [software carpentry](https://software-carpentry.org/) style course that consists of a 
number of segments, each addressing a different aspect of ResOS.

It's all kept in an online repository, so you can revisit it at any time, use it as a stand alone course if you want to,
and even, hopefully, contributes changes and extensions back!

So as you can see, its a fairly formal course intended to be delivered by a person standing in front of a class.

But because this is a "Train the trainers" event, I am not going to give you this course. 
Instead, we are going to do a higher level walk through. Of course, if you want to give this course yourself, feel free!

The repository can be found at: https://github.com/resbaz/nectar-cloud-lessons

As we work through this, I want you all to note any errors or changes that need to be done to the course material.
 
By raising issues!

At the end of the day you are going to get a chance to make changes by editing the files directly in the GitHub
repository.

So, without further ado, on to the first lesson. Find it in your browsers!

If you can't find it, hold up a Red sticky note, otherwise, a Green one to let me know you're ready to continue.

For more on personas, there is the [wikipedia entry](http://en.wikipedia.org/wiki/Persona_%28user_experience%29) and of
course, the book [The Inmates are Running the Asylum](http://www.amazon.com/The-Inmates-Are-Running-Asylum/dp/0672326140).
Also, the blog posting [Perfecting Your Persona's](http://www.cooper.com/journal/2001/08/perfecting_your_personas)