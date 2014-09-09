# Configuring Git

Over time, you will find little shortcuts that help you use Git at
the command line. Personally I've found those who are the most
frustrated with it, are the ones with the least amount of
customization. You don't *need* do to any of the things I've setup
in this lesson, but you might find them a little helpful. As this
setup will be hugely dependent on how you are working at the command
line, I'm not going to spend a lot of time in the *video* showing
you how to get this setup. There are some resources in the
repository that you've already downloaded (look for the "sample"
files in the directory `resources`).

There are two types of configuration settings you'll be making when
working with Git: global settings which apply to all repositories
that you work on, and local settings which only apply to the current
repository. An example of a global setting might be your name;
whereas your email might be customized based on personal projects
and work projects.

Global settings are stored in in the file `~/.gitconfig`, local
settings are stored in the file `.git/config` for the specific
repository you are working in. You will always be able to go back
and edit your settings if you want to.

## Identifying Yourself

In order to get credit for your work, you'll need to tell Git who
you are. We'll store this setting globally. As it's a global
setting, you don't need to be in a specific repository to make the
change.

### Lesson Objectives

By the end of this lesson, you will be able to add your name and
email to Git for proper attribution in commit messages.

### Self-Check

When you run the following command, is your name displayed?

`git config --get user.name`

### Summary

`git config --global user.name 'Your Name'`
`git config --global user.email 'me@example.com'`

If you want to make these changes only to the current repository,
replace the parameter `--global` with `--local`.

## Changing the Commit Message Editor

By default, you'll be using Vim. I really like Vim, so that's what
you'll be seeing in the videos. It's a bit hardcore though, so you
might want to change your editor to something else. Note: the commit
will only finish when you QUIT the editor, so you'll want to use
something fairly lightweight.

### Lesson Objectives

By the end of this lesson, you will be able to change the default
text editor for commit messages.

### Self-Check

When you run the following command, is the name of your text editor
displayed?

`git config --get core.editor`


### Summary

To change the text editor for your commit messages, use one of the
following commands as is appropriate for your editor of choice:

`git config --global core.editor mate -w`
`git config --global core.editor subl -n -w`


## Adding Color

Reading huge walls of text can be difficult. We'll add some color
helpers to our command line to make it easier to see what git is
doing.

### Lesson Objectives

By the end of this lesson, you will be able to enable the color
hinting to show branch colors, and diffs by color.

### Self-Check

Within the repository you downloaded for the previous lesson, when
you view the log, are the commit hashes a different color than the
author, date, and commit messages?

`git log`

### Summary

`git config --global color.ui true`

### Lesson Bonus: Customize Your Command Prompt

If you're working from the command line, you get ZERO clues
about what's going on with your files, until you explicitly ask
Git about them. This is tedious to keep having to ask. It's
like when you were 8 and sat in the back of the car whining at
the driver saying, "are we almost there yet?"

Instead of having to explicitly ask, I've modified my command line 
prompt to tell me which branch I currently have checked out and 
whether or not I've made changes to any of the files in my 
repository. This is a fairly common hack, but every developer
will have their own little quirks on how they implement it.
Searching the web for `bash prompt git status` will yield lots
of results. My own prompt is fairly simple, but others have
added a lot more details to their prompt. For example: [Show your git status and branch (in color) at the command prompt](https://coderwall.com/p/pn8f0g) or [local
file status](https://github.com/magicmonty/bash-git-prompt). As
with all things technical: the more you add initially, the more
you'll need to debug if it doesn't work right away.

I found the fancy prompts to actually be quite fussy to set up,
and ended up giving up on the really detailed ones. I recommend
you too start with something really simple and then add to it if
you *really* need more information. The simple change in
colour, along with the name of the branch, actually suits me
just fine and is less distracting without all the extra
information.

This as a self-study piece.
