# Finding and Fixing Bugs

**Overview of Isolating Problems**
There are two ways to look for bugs: determining where the problem code is; and determining when (and by whom) the problem code was introduced. Generally I debug from within the current code, but in more complicated code bases it can be useful to compare “working” and “non-working” states (we'll use git bisect for this).

**Using Advanced Options for Git Log**
Tips and tricks for getting the most useful git log messages – match this with diagrams of what the command is actually showing.

**Finding the Last Working State with Bisect**
Define the problem you're trying to isolate, and then use git bisect to find the commit where the problem was introduced. Talk about the problem of web caching. Explain how to get “out” of the bisect once you've identified the problematic commit (by using checkout to return to a different branch).

**Finding the Author History of a File with Blame**
Quick command to get a history of who has changed a specific file. Can be helpful when you're working in teams to find the person who might know more about the specific changes that were made to that part of the code base.

**Using Stash to Work on an Emergency Bug Fix**
You need to do something “real quick” for a client, but you're in the middle of a complicated set of tasks in your current branch. Put all of this work on hold with the “stash” command instead of writing a useless commit that you have to unpack later.

## Rollbacks, Resets, and Undoing Your Work

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

## Rewiring History with Rebase

**Overview of Rebase**
Unlike the previous examples, rebase is about changing the commit history for the sake of a cleaner history. Its primary function is to help you rework how you got to a given solution, rather than change the final solution itself.

**Bringing Your Work Up-to-Date with Rebase**
This is likely one of the first times you'll be “forced” to use rebase when working with Git. In this use case, you're using rebase to bring your local branch up-to-date by replaying previous commits which happened upstream as if they were already in place before you started your work.

**Saving and Sharing Your Resolutions with Rerere**
Once you've solved a rebase once, you'll never want to have to deal with the merge conflicts that mayhave come up during the process again. Use `rerere` to save and share your resolutions.

**Using Squash to Combine Several Commits**
The next most common use for rebase is to take several little commits you've made and squash them into a single commit. This allows you to hide some of your messy work, and show only a lovely final solution to your team.

**Using Squash to Truncate a Branch Before Merging**
This example is the same as the previous, except this time you are simplifying a merge / pull request before incorporating it into the trunk.

**Combining Your Changes Into Another Branch with Rebase**
When you merge two branches, you preserve the history that there was once a different branch. You can maintain a single line of work in your log by “merging” two branches with rebase.

**Changing Previous Commits with Interactive Rebase**
Let's say you tucked two files into a commit a little while ago which should have actually been two separate commits. Use interactive rebasing to go back to that point and fix what went where (note: you can also do interactive commits if you want to chunk changes in a single file into two commits).

## Collaborating on GitHub

**Overview of GitHub**
Introduction to who/what GitHub is. Special notes: this is a private company, it is not based on open source software. It is a platform which improves your experience with Git, but has several of its own GitHub “isms” which can make it difficult to know when you're working with Git, and when you're working with GitHub terms.

**Creating an Account**
Signup for a GitHub account.

**Forking a Repository**
Start by making a copy of the repository that I created. This is now your own playground to do whatever you want in. (Review of the GitLab procedure, except for GitHub.)

**Making Changes to Your Fork**
If you want to make changes to your fork, you need to clone the work locally, and the push the revisions back up to the server.

**Making Quicker Changes with the Web UI**
You can avoid making a local copy by using the Web UI to make simple changes to your repository. Generally it's harder to maintain good commit message quality through this method. (Linus refuses to accept commits submitted this way because of the poor formatting on messages.)

**Tracking Your Changes with Issues**
A review of how to create a ticket with an issue.

**Importing a New Repository**
Import the repository you created on GitLab (or download and upload the one that I created which you initially cloned from).

**Accepting a Pull Request**
Overview of how to deal with an incoming pull request. (might need to break this into smaller segments)

**Extending GitHub with Hub**
There is an additional set of command line tools available through the project Hub. I've used it to convert issues into Pull Requests (although I think that feature is now deprecated). Others have used it to create Pull Request builders (create a new EC2 instance for specific pull requests). If you use GitHub a lot, and are comfortable at the command line, you may find this project useful.

## Collaborating on BitBucket

**Overview of BitBucket**
Introduction to who/what BitBucket is. Special notes: this is a private company, it is not based on open source software. It is a platform which improves your experience with Git, but has several of its own “isms” which can make it difficult to know when you're working with Git, and when you're working with their terms.

**Creating an Account**
Signup for a BitBucket account.

**Importing a Repository**
Import the repository you created on GitLab (or download and upload the one that I created which you initially cloned from).

**Making Changes to Your Fork**
If you want to make changes to your fork, you need to clone the work locally, and the push the revisions back up to the server.

**Tracking Your Changes with Issues**
A review of how to create a ticket with an issue. Check to see if you can still convert an issue into a pull request.

**Accepting a Merge Request**
Overview of how to deal with an incoming pull request. (might need to break this into smaller segments)
