# Rewiring History with Rebase

Rebasing is often described as the ultimate Git experience. I have
no problems using it, but I have to admit that it makes me a bit
uncomfortable. Rebasing isn't about changing the results of your
work (although you can if you want to), rebasing is all about
changing the interpretation of how history happened, without
changing the actual outcome you see in your working directory.

History revisionist complaints aside, there are a number of reasons
why you would actually want to use rebase.

1. Bring a feature branch up-to-date based on changes which have
   happened in its ancestor branch. Using rebase in this context
   allows you to keep a nice clean history, and can help you avoid
   merge conflicts when you've finished your work and you're ready
   to merge it into the main line for your project.
2. Clean up granular commits and improve the commit message. This is
   especially useful if you've been using reset or revert and you
   have some odd messages in your commit history. This is also
   useful if you have a number of commits that, due to a peer review
   or sober second thought, you've decided were not the correct
   approach. Remember when we did the git bisect? cleaning up your
   history so there are only good, intentional commits will make it
   easier to use bisect.

## Bringing Your Work Up-to-Date with Rebase

This is likely one of the first times you'll be “forced” to use
rebase when working with Git. In this use case, you're using rebase
to bring your local branch up-to-date by replaying previous commits
which happened upstream as if they were already in place before you
started your work.

### Lesson Objectives

By the end of this lesson, you will be able to update a branch using
rebase to add commits which have happened in the ancestor branch.

### Self-Check

When you compare the two branches, ensure there are no changes in
the mainline branch which aren't in your own. You can use `git log
..master` to show you commits which have been added to master. If
there are none, your branch is up-to-date.

### Summary

Make sure rerere is enabled!

- `git config --global rerere.enabled true`

Look to see if there are outstanding commits in the other branch,
then run the rebase (it will feel similar to merging).

- `git log ..master`
- `git rebase master`
- if there are merge conflicts: resolve the conflict and follow the
  onscreen instructions to proceed

## Using Rebase to Combine Several Commits

The next most common use for rebase is to take several little
commits you've made and squash them into a single commit. This
allows you to hide some of your messy work, and show only a lovely
final solution to your team. This can also be used to simplify a
simplifying a merge / pull request before incorporating it into the
main branch for your project (the "trunk").

### Lesson Objectives

By the end of this lesson, you will be able to use pick, squash,
edit, and reword when rebasing your work.

### Self-Check

Make a temporary branch and shuffle the last five commits around.
Then verify your work by looking the history with the commands log,
diff, and show.

### Summary

- `git log --oneline`
- (choose a commit for the message you do want to keep)
- `git rebase -i <commit_id>`
- pick: leave as-is
- squash: keep the commit, but merge it into the previous commit (2
  for 1 deal)

## Using Rebase to Truncate a Branch Before Merging

This example is the same as the previous one, but this time we'll be
adding the commands to merge a truncated feature branch into the
master branch.

### Lesson Objectives

By the end of this lesson, you will be able to incorporate
interactive rebasing with merging to add a truncated set of commits
to a master branch.

### Self-Check

Then verify your work by looking the history with the commands log,
diff, and show.

### Summary

- Make a temporary branch and add three commits. 
- Create an integration branch off of master. 
- Merge the temporary branch. 
- Rebase the commits added so there is only one new commit on the
  branch using `git rebase -i HEAD~3`
- Checkout master. Merge the integration branch onto master.

Alt commands:

- `git log --oneline`
- (choose a commit for the message you do want to keep)
- `git rebase -i <commit_id>`
- (set the message you want to collapse to "squash")
- (update the commit message to remove the references to the
  revert/reset commit)

## Combining Your Changes Into Another Branch

When you merge two branches, you preserve the history that there was
once a different branch. You can maintain a single line of work in
your log by merging two branches, or by using rebase. If you have a
specific graph you want to maintain, you need to choose the right
method for how you'll combine two sets of work.

- rebase: graph looks like it's always had the commits in place.
- merge: graph looks like the merge were part of a separate branch.

### Lesson Objectives

By the end of this lesson, you will be able to identify when you
should use rebase, and when you should use merge.

### Self-Check

You can identify from a graph if merge was used, if merge --no-ff
was used, or if rebase was used.

### Summary

Bringing a branch up-to-date: use rebase, or pull.

- `git rebase <branch>` // will always look like a fast forward even
  if there is a true merge
- `git pull` (fetch + merge with fast forwards)

Incorporating new work: use merge.

- `git merge --no-ff <branch>`

Don't really care how your graphed history looks:

- `git merge <branch>` // might look like rebase if it can fast
  forward, but won't if there's a true merge

## Changing Previous Commits with Interactive Rebase

Let's say you tucked two files into a commit a little while ago
which should have actually been two separate commits. Use
interactive rebasing to go back to that point and fix what went
where (note: you can also do interactive commits if you want to
chunk changes in a single file into two commits).

### Lesson Objectives

By the end of this lesson, you will be able to squash a reset or
revert commit into the previous commit.

### Self-Check

You can "remove" the reference to a commit without changing the
contents of the files in the latest commit on a branch.

### Summary

- `git log --oneline`
- (choose a commit for the message you do want to keep)
- `git rebase -i`
- pick: leave as-is
- edit: change the files in the commit
- reword: change only the commit message
- squash: keep the commit, but merge it into the previous commit (2
  for 1 deal)
- fixup: like squash, but throw-away the commit message 
