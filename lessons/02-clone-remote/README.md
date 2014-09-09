# Downloading a Remote Repository

## Overview of Git at the Command Line

Open up the command line, and check to see which version of Git
you have installed. Look at Git's short help, list of all
commands, and a single command. Recommend Stack Overflow /
Google in additional to the command line help.

### Lesson Objectives

By the end of this lesson, you will be able to retrieve help for git's
commands from the command line.

### Self-Check

You are able to check which version of git is installed from the command
line.

### Summary

The commands we used in this lesson allowed us to read the manual
pages for git from the command line.

- `git`
- `git help` (same as running git without a parameter)
- `git help clone`

For additional information on the specifics of using any one
command, do a Google search. You'll probably end up at Stack
Overflow. I've also put together a [comprehensive list of resources
for learning git](http://gitforteams.com/resources/offsite.html).

## Cloning your GitLab repository

With your fork of a projec setup, it's now time to download the
project so that you can work on it locally. There isn't actually a
fork command in git! When you create a fork of a project, you are
merely cloning, or copying, the repository to a new location. Once
you have a local clone of your repository, you will have essentially
setup a chain between the three repositories. The original
repository (my copy) is the "upstream project". It might receive
contributions from any number of people, but they will always need
to be approved by me. The next repository in your chain, is the
repository which you forked from my project. This one you have
write access to. Perhaps other people will be interested in the
adaptations you've been making to your copy, and will be interested
in helping you with yours (this is where the concept of "fork" comes
in, as the two repositories may diverge over time, just like the
tines on a fork). The third, and final repository in the chain, is
your local repository. From this repository you have one connection
to the remote repository you cloned from. You could add others as
well. In subsequent lessons we'll talk about why you might want to
do this.

Cloning a project is very straight forward. You will need to:

1. Navigate to the project page for the repository you want to clone.
2. Locate the instructions on how to clone, copy the instructions.
3. At the command line, navigate to the directory where you want to
   download the repository to.
4. Paste the command line instructions.

Generally these instructions will be in the format of:

`git clone http://urltoproject/repository-name.git`

optionally, you may include a new directory name (by default the
name of the project is used as the directory name).

`git clone http://urltoproject/repository-name.git new-directory-name`

### Lesson Objectives

By the end of this lesson, you will be able to clone a repository
from a code hosting system, such as GitLab.

### Self-Check

Do you have a copy of the project on your hard drive? Navigate into
the directory and make sure there are files present. There will also
be a hidden folder, `.git`.

### Summary

The commands we used in this lesson allowed us to create a local
copy of our GitLab project.

`git clone http://urltoproject/repository-name.git new-directory-name`

We can repeat this command as many times as you like, to download
the repository multiple times (this can be helpful if you want to
throw away your local copy and start again from scratch).

## Reviewing History with git log

We'll be working a lot more with Git's log command in the lesson on
finding and fixing bugs. For now, let's use it to get a real quick
overview of the repository we've just downloaded. We can use Git in
two or three different ways, depending on what's compiled into our
system. We'll look at the full commit messages, a short log, and (if
you have it installed) Git's graphical browser. We'll also take a
quick look at how this compares to how GitLab displays the
information.

### Lesson Objectives

By the end of this lesson, you will be able to review the history
for a local repository using the log command.

### Self-Check

Are you able to find the two most recent commit messages for the
downloaded repository? What was a quick summary of the changes made?
Who were they made by?

### Summary

In order to review the history of our repository, we need to use the
log command. There are a number of parameters we can use to show
slightly different information.

- `git log`
- `git log --oneline`

Finally, the last little tool I find helpful, is some kind of
graph generator for my repository's history. This tool gives me
the context of where a change came "from" (are you a branch? is
it ahead of another branch in terms of commits?). GUIs for git
will give you a much more elegant view of your repository than
these tools, but they work just fine for me.

I can either draw the graph at the command line:

`git log --oneline --graph`

An example of this output would be as follows:

```
* edcd486 Updated deps.
* 05af892 No need for layout anymore.
*   eb85b12 Merge pull request #11 from stevector/master--implements-spelling
|\
| * 086b01e Spelling fix in 2013-02-04-highlight.md
* |   c5f46bd Merge pull request #10 from stevector/master--fixing-typo-in-readme
|\ \
| * | 58e67f4 Spelling fix in README
|/ /
* |   eebb37d Merge pull request #8 from kenjis/fix_url
```

The dots represent a commit. Anything to the right of the first
is (or was) a branch. The branch names are not listed in this
output.

Or, I can open up the git browser, gitk, and click around a bit. The
git browser is a special add-on which might not be enabled in
your version of git. For example: this functionality is *not*
available in the OSX-installed version of git, but it is
available in the brew-installed version. To open the browser,
use the following command:

`gitk`
