# Introduction

## Welcome and Set-up

I've been teaching version control for almost as long as I've
been using it. Over the years I've refined how I've taught this
topic, and have learned a lot about what doesn't work in the
traditional ways we currently teach version control. In this
learning series, I'm going to be doing things a little bit
differently. Instead of focusing on the commands you'll be
running, I'm going to try and start with WHY you'd want to do
something, and then show you HOW you'd go about implementing
the solution.

As a developer, I've learned a lot of little hacks to help me
be more efficiently. I'm still not fantastic at the command
line. I haven't replaced myself with a tiny shell script, but I
am very comfortable working from the command line. I enjoy the
elegance of not having to click eleventy buttons on eight
screens, and instead just issuing a few commands. I've also
found it's a lot easier to write cheat sheets for the command
line than for a GUI. And there seem to be a lot more answers on
Stack Overflow, but that could just be Google optimizing the
answers for the types of things I'm normally looking for.

As this learning series is a "watch over my shoulder" type of
series, we're going to work in my usual fashion: from the
command line. Unlike watching over my actual shoulder, you'll
be able to pause the video, and loop back over anything I've
said if you missed it the first time.

Throughout this learning series I'm going to assume you have a
number of things setup and ready to go. I'll be working from
the command line. If you prefer to use a GUI, you'll need to
figure out how these commands map onto your software
application. I encourage you to try the command line with me.

One of the reasons why people like having a GUI is that it
helps them to create a visual map of what they're working on.
Instead of relying on software to provide this map, I'll be
using diagrams. I encourage you to grab a drawing tool (paper
and pen work great!) and sketch along with me. Creating your
own diagrams will help the learning process as the movement
helps to build yet another neural pathway to the information.

### Lesson Objectives

By the end of this lesson, you will be prepared for learning Git.

### Self-Check

I have assembled the following:

- Drawing tools for diagrams (pencil/pen and paper is fine!).
- Git is installed at the command line.

### Lesson Summary

Working at the command line is universal. It may require some additional
configuration for Windows, but it allows us to share commands across
operating systems without having to worry about the discrepancy between
GUIs.

When learning new topics, creating a drawing to represent information will
help you to create the neural pathways which make it easier to recall the
information later on. 

## Warm-up Exercise

Being able to describe in words, or with pictures, how
something works, converts it from the abstract, into something
which can be programmed. Any time we are able to use words in a
linear fashion (i.e. talking through a problem), we are able to
find the corresponding commands that we'll need to issue to
make our process work. If you are not able to diagram, or
describe your problem, it will be near impossible to find the
matching commands you need to run.

Sketch the assembly line for your code as it exists currently, or as 
you think you would like it to work. Examples: centralized, peer 
review, automated gate keeper.

### Lesson Objectives

By the end of this lesson, you should be able to sketch the
relationship between the people on your team, and the tasks they 
perform.

### Self-Check

Does your diagram summarize how your team currently works
together (or how you'd like them to work together)?

### Summary

There are three fairly common workflows for teams:

- centralized: code checked into a single, central server
- peer review: a person checks the code before merging it to
  a main development branch
- automated gate keeper: a test suite checks the code before
  merging it into a main development branch

These examples aren't exhaustive, and they aren't mutually
exclusive. Your workflow may incorporate bits and pieces of
these, or use something different. We'll work on refining your
understanding of how these diagrams relate to git commands
throughout the rest of this learning series.
