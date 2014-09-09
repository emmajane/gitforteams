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

## Overview of Branching Strategies

There are effectively two ways that teams can work on software: either 
they collate the work, saving it up for a major release; or they are
continuously deploying very tiny changes to production. (I sometimes joke 
that the original continuous deployment was live editing on the server. 
Some people think I'm being serious when I say this though ... so be careful if you try to make the same joke.)

**Scheduled Release**

- Most popular example: GitFlow.
- Optimized for the collation of many smaller changes into a single release.
- Typically used for a download-able product; or web site with a scheduled release cycle (e.g. "Wednesdays").
- Incorporates human-reviews, and possibly automated tests.

![scheduled release: gitflow](../resources/strategy-branching-gitflow.png)

If you have the concept of stable releases, hotfixes, point releases, security releases, multiple supported versions, etc, then you need this granularity for your branches. There is always a period of time where you do not trust your code/developers and want to have a separate QA period. Thinking like a download-able product: version 4 vs. version 5 of The Software (a piece of software).

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

These days continuous deployment is the new hot. Everyone wants to
be able to do this. And for very tiny projects, I definitely just
work in master and putter along with each commit acting as a
resolution to a problem; however; the bigger the team gets,
the more it will benefit from having some structure in how the
people collaborate on the work.

New teams are unlikely to have the infrastructure needed for
continuous deployment. They are less likely to be writing reliable
tests, and they are more likely working on longer sprint cycles
(with deployments happening once every couple of weeks, not several
times a day). For this reason, this video series is going to focus
on how to work with your team in setting up a scheduled release
branching strategy.

## Listing All Branches

List all branches in the repository. Compare between the local branches, and the remote branches.

## Using a Different Branch

Checkout a different branch. Open a finder window at the same time and see how files (dis)appear when different branches are checked out.

## Using Best Practices for Changes

Always start by creating a written description of what you're about to do. Yes, this will often feel like overhead, but it is a really good habit to get into, especially when you're working in larger teams.

## Creating an Issue in GitLab

In your private repository, create a new issue ticket which outlines the changes you're about to make.

## Creating a Branch

Using the branching convention, start on MASTER, and then, create a new branch using the convention: ticket number-issue, create a new branch in your local respository. Checkout the new branch as well

## Creating a Tracked Branch

Repeat the previous lesson, but this time add tracking when the
branch is created. Start by checkout of master, and branching from
there.

## Adding Changes to your Local Repository

Use the command `git add filename` to add the file to the index. Then commit your changes to save the change to your local repository. I usually do a commit at the command line, and then commit --amend to write a longer commit message which relates to the issue.

## Uploading Your Changes with git push

Upload the change to the remote repository with `git push origin
master`. In newer versions of git, you should be able to just use
`git push`.


## Adding Tracking to a Previously Created Branch

Checkout the branch which doesn't have tracking added. Try (and fail) to push the branch. Make necessary adjustments to be able to upload the branch to the remote repository.

## Confirming Your Branch was Uploaded

Log into GitLab to ensure the branch has been uploaded to the remote repository.
