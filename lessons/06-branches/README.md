# Working with Branches

In version control, branches are a way of separating different
ideas. They are used in a lot of different ways. You may use
branches to denote different versions of software (for example,
Drupal a branch for version 5, 6, 7, 8, 9 and each of these branches
contains significantly different code). You might use very short
term branches to work on a new bug fix. You might use a branch to
test out a new idea.

If you're not sure if you should be working on a different branch,
it may help to ask yourself a few questions:

1. Is it possible I will want to completely abandon this idea if
   things don't work out?
2. Am I creating something which is a significant deviation from
   the current published version of the software?
3. Does my work need to undergo a review before it's published, or
   accepted into the published version of the software?

If you answered "yes" to any of these questions, you should consider
creating a new branch for your work.

Within a branch, you may have one or more commits. You were already
introduced to the concept of a commit when you added new files to
your repository in the previous lessons.

A commit is a unit of intention which you may want to reverse, or
build from at a later date. When you first start working with
distributed version control, chances are good you'll work in commits
which are actually too granular for advanced tools (you'll learn
more about this in the lessons on rebasing). This is because we're
coming from a different mindset when it comes to "saving our work"
and being able to "undo mistakes". When we use this mindset, we
think of clicking the save button, or using undo to remove the last
few things we typed. When the commits are this small, the commit
messages tend to be nearly useless ("stopped for lunch"; "tried
something"; "didn't work"; "ooops"; "testing"). If we wanted to
rollback history, how the heck would we use those commit messages to
find the spot where the code was working the way we intended!

It took me quite a while to get OUT of the habit of thinking of Git
as a place where I "saved my work" and instead as a place where I
"recorded my results". As you develop your sense of what makes a
useful commit, simply separate your work into different branches. As
you confirm the work is done, you can merge this completed branch
back into the main development line.

In these lessons you'll learn about the strategies software
development teams typically use to separate branches; you'll learn
how to work with branches; and we'll walk through a typical example
of how to work with a branch on a remote repository. Unlike many git
tutorials, I'm going to focus on how we use branches when
*collaborating with others*, and not just working on our own project
(much like I am with this repository of lesson notes).

## Listing All Branches

Branches allow us to work on independent thoughts at a time. Your repository will
have its own branches. Remote repositories have their own branches. Just because
you can see a branch, doesn’t mean you have the latest content.

### Lesson Objectives

By the end of this lesson, you will be able to list local branches, and remote
branches for your repository.

### Self-Check

Using a cloned copy of the the lesson repository, you should be able to list the
local branches, and the remote branches.

### Summary

- `git branch`
- `git branch --list`
- `git branch -a`
- `git branch -r`
- `git fetch`
- `git remote show <remote_name>`

## Using a Different Branch

When you checkout a branch, you are updating the visible files on your system
("the working tree") to match the version stored in repository.

When you switch between branches, it can sometimes be helpful to have a Finder
window open so you can see what files are changing (appearing and disappearing)
when the different branches are checked out.

### Lesson Objectives

By the end of this lesson, you will be able to check out a local branch.

### Self-Check

When you changed to a different branch, the git log showed a different commit 
for the most recent work than the branch you were on previously. (You can check
this with `git log --oneline`.) Technically two branches don't NEED to have
different commits though, so self-check isn't perfect.

### Summary

- `git checkout <branch_name>`
- `git checkout --track <remote>/<branch_name>`

## Establishing Your Branching Strategy

As you build up your work, you'll add more parallel branches to your work flow.
Any work which happens in a branch is completely isolated from other branches in
your repository. Can you have completely different files for completely different
versions of your software. The branches should all have a relationship to one
another though, they shouldn't contain completely different projects!

You can invent your own branching strategies. For example, in the repository for
these lessons, I have one main branch that I use for workshops. Nearly all of my
work is done directly in this branch and it is immediately visible when people
visit the project page.

I also have a few branches for ideas that are still in progress, and not ready for
immediate consumption (they're still available, you just need to know to look for
them). For example: while I was working on the video lessons, I created a new
branch. When the lessons are recorded, I'll merge this branch back into the master
branch so that the content is immediately visible to everyone. I also have a
branch with random files which I have no intention of merging back into the master
branch. This branch, sandbox, is meant to help you learn about branching. It's
sort of a fun Easter egg for people who aren't taking the lessons, and don't
bother looking into the branch.

What I'm doing with this repository is quite specialized and unique to my project.
You can invent your own branching strategies for your own projects, but when it
comes to software development, there are a number of "best practices" out there
which you may want to consider following. By using a convention, you make it a lot
easier for other people to collaborate on your project, AND do things correctly.

Let's take a look at these branching strategies now.

There are effectively two ways that teams can work on software: either they
collate the work, saving it up for a major release; or they are continuously
deploying very tiny changes to production. (I sometimes joke that the original
continuous deployment was live editing on the server.  Some people think I'm being
serious when I say this though ... so be careful if you try to make the same
joke.)

**Scheduled Release**

- Most popular example: GitFlow.
- Optimized for the collation of many smaller changes into a single release.
- Typically used for a download-able product; or web site with a scheduled 
  release cycle (e.g. "Wednesdays").
- Incorporates human-reviews, and possibly automated tests.

![scheduled release: gitflow](../resources/strategy-branching-gitflow.png)

If you have the concept of stable releases, hotfixes, point releases, security
releases, multiple supported versions, etc, then you need this granularity for
your branches. There is always a period of time where you do not trust your
code/developers and want to have a separate QA period. Thinking like a
download-able product: version 4 vs. version 5 of The Software (a piece of
software).

**Continuous Deployment**

- Code is deployed faster than scheduled releases; assumes all check-ins are deployable.
- Requires (trusted) test coverage.
- Typically uses a mechanical gatekeeper (CI) to check in code to the master branch.
- Often has flippers/flags for fine grained access to in-progress features.
- Fewer branches to maintain / keep updated.

![continuous delivery: feature branches](../resources/strategy-branching-cd.png)

If you don't need the granularity of multiple supported versions, you can
probably get away with something closer to this branching strategy. Can you
get away with just tags? Do you intend to go back and work on a previous
version? As soon as you have the concept of a separate security hotfix, you
need to introduce a separate branch. In CD: everything is urgent, so
there's not a separation of a really urgent security fix. CI, CD vs CD:
http://puppetlabs.com/blog/continuous-delivery-vs-continuous-deployment-whats-diff

A great way to familiarize yourself with different branching strategies, is to
check out what projects are doing. Here are a few to check out:

- `git clone http://git.drupal.org/project/drupal.git`
- `git clone https://github.com/git/git`
- `git clone https://github.com/twbs/bootstrap`

### Lesson Objectives

By the end of this lesson, you will be able to identify two common
branching strategies, and explain under what circumstances they are
appropriate development strategies for teams.

### Self-Check

Using the diagram you created for the warm-up exercise, can you plot
onto this diagram where the potential branches might be? Does your
current setup look more like a scheduled release (GitFlow), or
continuous deployment branching pattern?

### Summary

These days continuous deployment is the new hot. Everyone wants to be able to do
this. And for very tiny projects, I definitely just work in master and putter
along with each commit acting as a resolution to a problem; however; the bigger
the team gets, the more it will benefit from having some structure in how the
people collaborate on the work.

New teams are unlikely to have the infrastructure needed for continuous
deployment. They are less likely to be writing reliable tests, and they are more
likely working on longer sprint cycles (with deployments happening once every
couple of weeks, not several times a day). For this reason, this video series is
going to focus on how to work with your team in setting up a scheduled release
branching strategy.

## Creating a Topic Branch

It's very easy to create a new branch in Git. Almost too easy...as Git doesn't
provide any guidance on what you're supposed to do in that branch. Assuming you're
working on a software project, the best way to decide what goes into a branch, it
start with the Issue Tracker. 

by creating a written description of what you're about to do, you will have a
clear sense of when to start AND finish with your branch. Yes, this will often
feel like overhead, but it is a really good habit to get into, especially when
you're working in larger teams.

In GitFlow, all new ideas use “Feature” branches. (There's nothing special about
them technically, it's just a naming convention to make it easier to think about
what kind of work happens in the branch.) Feature branches can incorporate one, or
many tickets if the idea is really big. Be careful though, if you have a lot of
people working on really different ideas, and their branches diverge
significantly, you risk creating mini projects instead each repository, making it
difficult to incorporate the work into the common branch at release time.

If it's a new project, you may only have feature branches, and ane integration
branch. By the GitFlow convention, your integration branch would be named
`develop`, and the master branch wouldn't be updated until you had an official
release. Do whatever works for you, but make sure you document whatever you do!

In your private repository on GitLab, create a new issue ticket which outlines the
changes you're about to make. Next, create a corresponding branch in your
repository.  Do your work. Finally, save the changes to your local branch by
adding the changed file, and then committing it.

### Lesson Objectives

By the end of this lesson, you will be able to create a new branch using best
practices, to solve a specific issue identified in your code hosting system. 

### Self-Check

You have a new branch created using the naming convention
`issue_number-terse_description`.

### Summary

1. Create a new issue; note the number on the issue

The new ticket I created was as follows:

```
Problem: The repository is too serious.

Rationale for change: having more jokes in the repository will allow people to
take a break from learning git and have a bit of a laugh.

QA: After this ticket has been resolved, I will be able to read more bad jokes.
```

2. Create a new branch using `git checkout -b <issue-description> sandbox`
3. Add a new joke to the file `badjokes.md`. You now have a "dirty" repository
   with one modified file.
4. Add the joke file to the staging index with `git add <file>`.
5. Commit your joke file to the repository with `git commit`.

I usually do a commit at the command line, and then commit --amend to write a
longer commit message which relates to the issue.

## Uploading Your Changes with git push

To upload your changes to the remote repository, we'll use the command `push`. A
few things need to be in place for this to happen though.

1. You need to have write permission to the repository. Assuming you setup your
   SSH keys correctly, this shouldn't be an issue.
2. The branch you are uploading needs to have a connection to a specific remote
   repository. i.e. you need a "destination"

I generally take the lazy approach to pushing up my branches, and always start
with the shortest sequence, adding parameters as needed.

### Lesson Objectives

By the end of this lesson, you will be able to upload your branches to remote
repositories by using the Git command push.

### Self-Check

Log into GitLab to ensure the branch has been uploaded to the remote repository.

### Summary

`git push`
`git push <remote_name> <branch_name>`

## Accepting and Merging New Work

Once the code review process has been completed, it's time to accept
the new work into the main branch for your project. There are a few
different ways you can combine branches in git. The first maintains
the branch identity, showing that at one time these commits lived in
their own branch. The second does not maintain branch identity.
Instead, it fast-forwards through the commits you're adding to the
main branch. In the history, the fast-forward merge (which is the
default) will make your historical graphs look as though the commits
have always been in place. Those who use a rebasing workflow will
often choose to merge branches with `--no-ff` to maintain the
illusion of the branch, while always updating their master branch
with a rebase to keep a perfect set of "swim lanes". If you prefer a 
history with fewer lines to follow, use the default.

### Lesson Objectives

By the end of this lesson, you will be able to update a update a
local branch using git pull, and merge a local development branch
using the fast-forward and true merge strategies.

### Self-Check

Are you able to incorporate the sandbox branch, or the joke branch
into your work?

### Summary

- `git checkout master`
- `git fetch`
- `git merge <remote>/master`
- `git pull` // a more aggresstive shortcut to fetch + merge
- (assuming master is now up-to-date)
- `git merge <ticket_branch>` // attempts fast forward merge
- `git merge --no-ff <ticket_branch>` // forces a new commit,
  maintains the illusion of a branch
- `git push` // upload the revised copy of the master branch

Example of fast forwarding vs. a true merge:

- `git checkout -b integration_ff`
- `git merge 1-bad_jokes`
- `git log --oneline --graph`
- `git checkout -b integration_no-ff master`
- `git merge --no-ff 1-bad_jokes`
- `git log --oneline --graph`

## Dealing with Merge Conflicts

If two developers have changed the same part of a file and you try
to merge those changes, Git will be unable to know which one should
be kept and will stop the merge process. You will need to check the
files by hand and determine which copy to keep. You may want to use
a mergetool for particularly complicated merges as it will give you
a nicer reference to make decisions from. I personally use
Kaleidoscope, but there are other free tools for each of the
different operating systems.

Once you've solved a merge conflict once, you'll never want to have
to solve it again. You can use `rerere` to save your resolutions.

### Lesson Objectives

By the end of this lesson, you will be able to resolve a merge
conflict.

By the end of this lesson, you will be able to enable to "RE-use a
REcorded Resolution" while rebasing. 

### Self-Check

Edit two files at the same place in two different branches and then
try to merge them. Decide ahead of time which of the two branches
you want to keep the changes from.

Add the same error (which generates a merge conflict) to two
different branches, and bring them both up-to-date with rebasing.
You should only have to resolve the first merge conflict.

### Summary

- `git config --global rerere.enabled true`

- `git checkout -b one`
- (edit the readme title)
- `git checkout master`
- `git checkout -b more`
- (edit the readme title)
- `git merge one`
- (edit the file with the conflict)
- `git add .`
- `git commit`
