# Finding and Fixing Bugs

**Overview of Isolating Problems**
There are two ways to look for bugs: determining where the problem code is; and determining when (and by whom) the problem code was introduced. Generally I debug from within the current code, but in more complicated code bases it can be useful to compare “working” and “non-working” states (we'll use git bisect for this).

**Using Advanced Options for Git Log**
Tips and tricks for getting the most useful git log messages – match this with diagrams of what the command is actually showing.

**Finding the Last Working State with Bisect**
Define the problem you're trying to isolate, and then use git bisect to find the commit where the problem was introduced. Talk about the problem of web caching. Explain how to get “out” of the bisect once you've identified the problematic commit (by using checkout to return to a different branch).

**Finding the Author History of a File with Blame**
Quick command to get a history of who has changed a specific file. Can be helpful when you're working in teams to find the person who might know more about the specific changes that were made to that part of the code base.

**Using Stash to Work on an Emergency Bug Fix**
You need to do something “real quick” for a client, but you're in the middle of a complicated set of tasks in your current branch. Put all of this work on hold with the “stash” command instead of writing a useless commit that you have to unpack later.
