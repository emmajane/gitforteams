# Rollbacks, Resets, and Undoing Your Work

There are a lot of ways to undo work in Git, and each method is
exactly right sometimes. Unfortunately the commands can be a little
confusing to use as they're so closely named. You might want to make
a cheat sheet for yourself. In fact, I highly recommend creating
little sketches for yourself as you learn these commands. Creating
your own drawings will help reinforce the learning, and it will give
you a mental reference point, which is often easier to remember than
a manual page.

Instead of explaining each command git offers, I'm going to give you
a few different scenarios when you might want to undo your work.

- Doing experimental work in new branches.
- Deleting unsaved changes in the working directory.
- Rewinding time by removing changes (and the commit message).
- Time travelling, by going back to an old commit.

In addition to these methods, rebasing allows you to unhook previous
commits from a chain of events, and create a new chain in the
history (without actually deleting anything). We'll be covering
rebasing in the next lesson.

If you've committed something into the repository, it will always be
there. It's virtually impossible to actually delete work in Git. It
is possible, however, to lose work and not be able to find it again.
If you think you've *lost* history, you'll want to use reflog to
find your lost time.

## Using Branches for Experimental Work

Previously we've created, and deleted branches, using the ticket as
a starting point. But what if you were working on a ticket, and you
weren't sure which of two approaches you should take. In this case
it would be absolutely acceptable to create a branch off of your
ticket branch, noodle around some bit, and then bring those changes
back into your ticket branch.

### Lesson Objectives

By the end of this lesson, you will be able to create, use, and
delete a new branch.

### Self-Check

You can checkout your new branch, and remove it from the list of
branches when you are finished working on your ideas.

### Summary

- `git checkout -b experimental_idea`
- (do work)
- `git add .`
- `git commit`
- `git branch -d experimental_idea`
- `git push <remote> :<branch_name>`

If you want to rollback to a previous commit temporarily:

- `git checkout -b backup_branch`
- `git checkout <branch_to_rollback>`
- `git log --oneline`
- `git checkout <commit_id>`

## Amending a Commit

In a previous lesson we amended a commit so that our branch would be
correctly attached to a ticket we were working on. So long as you
haven't pushed your branch yet, you can also use commit to add
additinal work to the commit.

If you have already pushed the work it's considered bad form to go
back and "fix" shared history. Make sure you're only changing your
own history, or ticket branches which only you are working on.

### Lesson Objectives

By the end of this lesson, you will be able to amend a commit to add
new work.

### Self-Check

You can make additional changes to your repository without a new
commit point being added to your Git timeline.

### Summary

- `git add .`
- `git commit --amend`

## Removing Changes to the Working Directory

You're working along and you just deleted the wrong file. You
actually wanted to keep the the file. Or perhaps you edited a file
that shouldn't have been edited. Before the changes are locked into
place (or "committed") you can "checkout" the files. This will
restore the contents of the file to what was stored in the
last known commit for the branch you're on.

### Lesson Objectives

By the end of this lesson, you will be able to restore a file to the
state it was in in the most recent commit.

### Self-Check

You can restore a deleted file in the working directory.

### Summary

- `rm README.md`
- `git checkout -- README.md`

If you've already staged the file, you'll need to unstage it before
you can restore it.

- `rm README.md`
- `git add .`
- (git checkout -- <file> won't work)
- `git reset HEAD <file>`
- `git checkout -- <file>`

If you want to restore all of the files to the previous commit, you
don't need to make the changes one at a time, you can do it in bulk
with:

- `git reset --hard HEAD`

## Removing Commits with Reset

Use this to throw away commits you didn't want to keep. When you
reset your work, git throws away the commit message, but returns
your working directory to the state it was in the moment before the
commit was stored. So if you didn't really mean to delete a file in
a previous commit, you can reset your working directory.

(It's actually a tricky one to explain, but relatively straight
forward to see it in action.)

Note: this is going to alter history as it removes references to
commits. This means it's best to do this only in your own history,
but not in a shared history.

### Lesson Objectives

By the end of this lesson, you will be able to restore your working
directory to a previously committed state using git reset.

### Self-Check

You can restore a file that was deleted, and remove the reference to
it being deleted.

### Summary

- `rm README.md`
- `git add .`
- `git commit -m "Removing a file that shouldn't be removed"`
- `git log --oneline`
- (copy the commit ID for the commit BEFORE the one you want to
  reset)
- `git reset <commit_id>`
- `git status`
- `git checkout -- <file>`

If you want to undo your undo, you can do that too.

- `git reflog`
- (look for the line above "reset: moving to"; it will be something
  like "checkout: moving from master to <commit_id>).
- `git show <commit_id>`
- (confirm it's the right ID to restore)
- `git checkout <commit_id>`
- `git checkout -b restored_branch`
- `git checkout master`
- `git rebase restored_branch`
- `git branch -d restored_branch`


## Promoting a Previous Commit with Revert

If there was a commit in the past which was incorrect, you can
reverse that single commit. Unlike reset, revert does nothing to the
commits in between. It simply puts back the changes you made in the
commit you're reverting. Unlike reset, revert applies the changes so
you are left with a clean working directory. Resets need to be
paired with a commit as you are "resetting the working directory".

### Lesson Objectives

By the end of this lesson, you will be able to undo previously made
changes by adding them back in a new commit.

### Self-Check

You can reapply the changes that were made previously.

### Summary

- `git log --oneline`
- `git show <commit_id>`
- (confirm this is the change you want to reverse)
- `git revert <commit_id>`

Repeat for each commit that you want to undo. (There's no way to
re-apply changes in bulk while maintaining a record.)
