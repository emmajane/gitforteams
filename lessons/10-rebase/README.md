# Rewiring History with Rebase

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

