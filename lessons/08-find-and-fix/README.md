# Finding and Fixing Bugs

There are two ways to look for bugs: determining where the problem code is; and determining when (and by whom) the problem code was introduced. Generally I debug from within the current code, but in more complicated code bases it can be useful to compare “working” and “non-working” states (we'll use git bisect for this).

## Finding Relative History with Git Log

Tips and tricks for getting the most useful git log messages – match
this with diagrams of what the command is actually showing.

### Lesson Objectives

By the end of this lesson, you will be able to choose very specific
ranges of history to look at.

### Self-Check

Draw the graphs for what each of these combinations represent. Check
your work using gitk to verify your diagrams.

### Summary

- `git log HEAD^` // not including the latest
- `git log HEAD~3` // not including the last three
- `git log <branch>..<branch>` // difference between two
- `git log <commit>..<commit>`
- `git log <branch>..` // what's here, but not there
- `git log ..<remote/branch>` // what's there, but not here
- run all of these again but with `git diff`, not `git log`

## Finding the Last Working State with Bisect

Often it can be difficult to figure out exactly how a bug was
introduced in your code. You know something went wrong, but you just
can't figure out where that extra 2px margin came from. Introducing
git bisect!

First you'll need to define the problem you're trying to isolate,
and then you can use git bisect to find the commit where the problem
was introduced. 

If you need an emergency “out” of the bisect you can simply use
checkout to return to a different branch. This is much like
recovering from a detached head state.

### Lesson Objectives

By the end of this lesson, you will be able to use git bisect to
find a specific state in your code.

### Self-Check

Were you able to find the bug?

### Summary

- `git log <since_last_merge_to>..<what's_been_added_here> --oneline`
- `git bisect start`
- `git bisect good <commit_id>`
- `git bisect bad <commit_id>`
- `git bisect reset`
- `git checkout <branch>`

### Gotchas

- You need to be in the top-level directory to run bisect.
- It is assumed that the current work is "bad". So, you can't go
  back and find when something is fixed, you need to go back and
  find where something broke. (Git gets very confused if you try to
  find where a **fix** was introduced.)

## Finding the History of a File with Blame

Quick command to get a history of who has changed a specific file.
Can be helpful when you're working in teams to find the person who
might know more about the specific changes that were made to that
part of the code base.

### Lesson Objectives

By the end of this lesson, you will be able to look at the history
for a specific file.

### Self-Check

### Summary

- `git blame <filename>`
- `git log <commit> -p`

## Using Stash to Work on an Emergency Bug Fix

You need to do something “real quick” for a client, but you're in
the middle of a complicated set of tasks in your current branch. Put
all of this work on hold with the “stash” command instead of writing
a useless commit that you have to unpack later.

I once heard someone joking about how he could "git stash his
morality" when watching horror movies. In other words: he could put
his values aside while he watched the movie. ... maybe you needed to
be there.

### Lesson Objectives

By the end of this lesson, you will be able to put your work on hold
temporarily with git stash.

### Self-Check

### Summary

- `git stash`
- `git stash list`
- `git stash apply`
- `git stash drop`
