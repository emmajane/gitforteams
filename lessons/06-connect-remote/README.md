# Overview of Connecting to Remote Repositories

You've been working locally, and suddenly you realize you could
share your work with the upstream project. Depending on how you
started your project, you will need to connect your local work in
slightly different ways.

In a centralized version control system, like subversion, there is
one master copy of the repository and all work is written into that
copy. When you commit, the information is immediately uploaded to
that central repository and available to others. In a decentralized
version control system, like Git, there is no single repository that
everyone works with. It is merely a convention which declares one
copy of the repository to be priviledged (and considered to be the
official source for the code).

In this next set of lessons, we'll explore what it means to connect
to a remote repository, and how do make a connection under a few 
different scenarios.

## Copying a Repository

Previously you learned how to clone a project, this hooks up the
remote server as a connection to your repository. You can also start
with any folder which has a .git directory in it. For example: you
could share your git repository with someone via a zipped email
(AVOID doing this with a tool that does synchronization, such as
Dropbox, as it will corrupt your git repository!!).

Making a copy of the repository in this way will make an exact
duplicate of everything, including the history of where this
repository started from.

### Lesson Objectives

By the end of this lesson, you will be able to make copies of your
git repository, and describe the limitations of using this system.

### Self-Check

After making a copy of your repository, can you add a new file to
it? Confirm this by reading the log messages for your repository
after adding the new file.

### Summary

You can easily make a copy of any respository in its current state
by simply making a copy of the directory. When I was first learning
git, I often took advantage of this feature to throw out all of my
uncommitted work and start again from the last commit in the
repository. (By the end of this series you'll have already outgrown
this trick!)

The disadvantage to this system is that the copy still has YOUR
remote(s) defined, and what you really want when you're sharing with
someone else, is to have a third "code hosting" remote repository
set up. You can check to see which remote(s) are defined by your
repository with:

- `git remote`
- `git remote -v` will give you a bit more information
- `git remote show [name_of_remote]` will give additional details
  about the remote (remotes are typically somewhere else, you will
  need an internet connection when using `remote show`)

## Cloning a Local Repository

You want to play with remotes, but you're entirely offline (for
example: watching these videos behind a firewall and you can't get
access to GitLab, GitHub, etc). Use a local directory as your
“remote” repository. Remote actually just means any directory that's
not THIS directory.

### Lesson Objectives

By the end of this lesson, you will be able to clone a repository to
the same file system.

### Self-Check

There is a new copy of your repository, and when you view the
remotes for the new repository, it lists a location in your file
system as the remote. For example:

```
origin  /Users/emmajane/Git/workshop-git-for-teams (fetch)
origin  /Users/emmajane/Git/workshop-git-for-teams (push)
```

### Summary

- `git clone [/full_path/to/repository] [new_project_folder_name]`
- `git clone /Users/emmajane/Workshops/git-for-teams local-clone`

Note: the folder `.git` is in the root of the folder
`git-for-teams`.

## Converting a Set of Files to a Repository

Initially you didn't think you would be doing much with a project,
so you downloaded a zip folder with all the project files instead of
cloning the project.  (in the previous example you DID have the
folder `.git` included in set of files).  You now want to submit a
contribution to the project, but you have absolutely no local
history from the upstream project to connect with.

As we did previously, the first thing you'll need to is fork the
project. This will give you a writable copy of the repository so
that you can upload your changes, and then submit a pull or merge
request back to the project (you'll learn about pull requests
later).

Once your fork is setup, clone the repository to your local
computer. Copy your editing files into the repository. Add the files
to the changing area, and make a commit. If you want to be really
fancy, you can do a bit of extra homework and lookup "interactive
commits". This will let you, by file and by hunk, decide what should
be included in a commit (the default is to work at the file level).

Note: this should ONLY be done if you have one or two minor changes.
If you've been working on your changes for a long time, it's quite
possible your zip copy is out of date. Copying all the files into
the repository WILL introduce regressions and undo any work that has
been made on the project since you last downloaded it. So be
careful, eh?

### Lesson Objectives

By the end of this lesson, you will be able to combine a set of
previously untracked files with a repository.

### Self-Check

Use the command `git log` to ensure the changed files were added to
your repository.

### Summary

- `git clone`
- copy the changed files into the repository
- you can use `diff`, or a difftool (I like Kaleidoscope) to show you
  the difference between the two sets of files
- `git add .`
- `git commit -m "Detailed message about the work you've done."`

## Adding Another Remote Connection

You initially cloned a repository that uses a forking repo. Now you
want to publish your results, while still maintaining a connection
to the the upstream project. To accomplish this, you will need to
add a second remote to your project.

I do this all the time when I'm working with open source projects. I
think that I'm never going to want to make a contribution to the
project, and then I find a little bug which I need to fix for
myself, and decide I want to contribute back to the project. I've
also added additional remotes when I want to have a backup, or if
the code hosting has changed for some reason (e.g. I don't have
access to a client's code hosting system yet, so I upload to a
private repo on my code hosting).

In the next set of lessons we'll talk about branching, and keeping
these remotes up-to-date.

### Lesson Objectives

By the end of this lesson, you will be able to add additional
remotes to your repository.

### Self-Check

When you run the following command, you should see two lines (one
remote):

- `git remote -v`

results in something like this:

```
origin  git@github.com:emmajane/vagrant-solo-dev.git (fetch)
origin  git@github.com:emmajane/vagrant-solo-dev.git (push)
```

After adding a second remote, the output of `git remote -v` should
list another two lines (fetch and pull).

```
dme git@github.com:DrupalizeMe/vagrant-intro-series.git (fetch)
dme git@github.com:DrupalizeMe/vagrant-intro-series.git (push)
origin  git@github.com:emmajane/vagrant-solo-dev.git (fetch)
origin  git@github.com:emmajane/vagrant-solo-dev.git (push)
```

### Summary

- `git remote add [name] [url]`
- `git remote show `
- `git remote -v`
