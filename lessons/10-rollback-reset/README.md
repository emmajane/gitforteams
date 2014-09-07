# Rollbacks, Resets, and Undoing Your Work

**Overview of Undoing Previous Work**
Show a sketch of the working directory; index; and remote repository. You can undo work in three different places. Work can be undone by deleting commits, or by moving a previous commit to the front of the tip of your work. Rebasing allows you to also unhook previous commits from a chain of events, and create a new chain in the history (without actually deleting anything). Reflog always has your history...if you can remember the commit hash.

**Using Branches for Experimental Work**
Review of how to create / delete branches locally.

**Amending a Commit**
Previously we've used commit amend to change the  message for a commit, but you can also add/remove files from the commit.

**Removing Changes to the Working Directory**
Use checkout and the file name to undo uncommitted work. To undo changes in bulk, you can checkout the remote again, but things might get squirrelly if there are new commits (it might try to merge commits you've made), so when you're just getting started, stick to using this method when you have Uncommitted work you want to undo.

**Removing Commits with Reset**
Use this to throw away commits you didn't want to keep because they were somehow very wrong and shouldn't exist.

**Promoting a Previous Commit with Revert**
Use this to rollback to a previous commit, while still showing that the previous work did exist at some point.
