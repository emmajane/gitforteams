# Working with Tags

Tags are used to pin-point specific commits. They don't follow a
series of commits, like a branch does. They are a single point in
time along the history of your work. You can think of them like a
bookmark on your work. I don't use tags nearly as much as I should.
As a result, I rely on my commit messages to find specific points in
the repository. You may find working with tags is a good habit to
get into as they'll allow you to easily reference points in your
time line.

## Listing, Adding, and Deleting Tags

### Lesson Objectives

By the end of this lesson, you will be able to view a list of tags,
and add a new tag.

### Self-Check

When you start this lesson, there are no tags on the repository. You'll need to add some tags before you can view them.

### Summary

- `git tag`
- `git log --oneline`
- `git tag -a <tag_name> <commit_id>`
- `git tag -a -m "Reason for tagging" <tag_name> <commit_id>`


## Checking Out Tags

Once a tag is made, you can investigate just the commit where the
tag was added.

You can also checkout this tag. You'll go into a DETACHED HEAD
STATE! But you'll be fine.

### Lesson Objectives

By the end of this lesson, you will be able to investigate a single
commit which has been tagged.

By the end of this lesson, you will be able to locate and checkout a
specific commit hash by using a tag as the reference point.

### Self-Check

You should be able to view the tag message, commit message, and the
diff for that commit.

When you checkout a tag, you'll get a warning message about being in
a DETACHED HEAD state.

### Summary

- `git show <tag_name>`
- `git checkout <tag_name>`

## Recovering from a Detached HEAD State

Checkout the branch you were on previously to return to your regular work.

Here's an example of the message from a checkout I did:

```
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 255a271... Lessons were renumbered to match O'Reilly conventions.
```

### Lesson Objectives

By the end of this lesson, you will be able to describe what a
detached HEAD state is, and be able to recover from it.

### Self-Check

You can get rid of the error messages about being in DETACHED HEAD.

### Summary

- `git checkout <tag_name>`
- `git checkout <branch_name>`
- `git checkout <tag_name>`
- (make changes)
- `git checkout -- <filename>`
- `git status`
- (make changes)
- `git checkout -b <new_branch_to_save_work>`

## Sharing Tags

Tags are only available on your local repository unless you
explicitly share them with others.

### Lesson Objectives

By the end of this lesson, you will be able to add and remove tags
from your remote repository.

### Self-Check

Are you able to find your tags on the remote repository?

### Summary

- `git push --tags <remote_name>` (add the --tags parameter when
  pushing branches)
- `git push origin :<tag_name>`
