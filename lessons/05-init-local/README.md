# Getting Started as a Team of One

In the previous lesson we took a look at a repository which already
existed. For many people this will be a typical first experience
with version control: working with something that someone else
started. Eventually though, you will have a need to setup your own
repository. In these next few lessons, we'll cover a few of these
scenarios. 

- Initializing an emptry project
- Converting an existing set of untracked files to git

## Initializing an Empty Project

Use the command `git init` to start a new project locally. This
creates an empty directory that you can now put stuff into.

### Lesson Objectives

By the end of this lesson, you will be able to begin a new project
which will be tracked by Git.

### Self-Check

By the end of this lesson, you will be able to create a new git
repository.

### Summary

- `git init`
- `ls -al` (or on Windows `dir`)

## Converting an Existing Project to Git

In the previous lesson you started an empty repository. Once you've
created the repository it's time to get to work and add files to the
repository.

You can start with any folder of files and create a git repository
from it, using the `git init` command. This time instead of starting
with an empty directory, start with an existing directory of files
and “convert” your non-versioned project into a git repository. 

Once the repository has been created, there are two basic operations
you need to run to add files to the repository:

- `git add`
- `git commit`

When you `add` the files to the repository, you're actually added
them to a temporary staging index. This temporary stage allows you
to orchestrate, or direct, the specific scene you want to commit to
the repository. This means you can work on bigger problems, and then
segment your thinking into individual commits. When you first start
working with Git, this can seem like an unnecssary step, but as you
become more comfortable with the advanced functions in git, you see
the advantage of being able to craft commit messages. (We'll talk
about this in later lessons.)

### Lesson Objectives

By the end of this lesson, you will be able to add files to a
repository.

### Self-Check

Make sure your files were added to the repository by ensuring there
are no untracked files in the directory, and you have a log message.
Use the commands `git status` and `git log` to confirm your work.

### Summary

- `git init`
- (add files to the directory you've just initialized)
- `git status`
- `git add`
- `git status`
- `git commit`
- `git status`

