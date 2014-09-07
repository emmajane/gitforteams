# Working with Branches

**Overview of Branching Strategies**
Scheduled release vs. Continuous development.

**Listing All Branches**
List all branches in the repository. Compare between the local branches, and the remote branches.

**Using a Different Branch**
Checkout a different branch. Open a finder window at the same time and see how files (dis)appear when different branches are checked out.

**Using Best Practices for Changes**
Always start by creating a written description of what you're about to do. Yes, this will often feel like overhead, but it is a really good habit to get into, especially when you're working in larger teams.

**Creating an Issue in GitLab**
In your private repository, create a new issue ticket which outlines the changes you're about to make.

**Creating a Branch**
Using the branching convention, start on MASTER, and then, create a new branch using the convention: ticket number-issue, create a new branch in your local respository. Checkout the new branch as well

**Creating a Tracked Branch**
Repeat the previous lesson, but this time add tracking when the branch is created. Start by checkout of master, and branching from there.

**Adding Changes to your Local Repository**
Use the command `git add filename` to add the file to the index. Then commit your changes to save the change to your local repository. I usually do a commit at the command line, and then commit --amend to write a longer commit message which relates to the issue.

**Uploading Your Changes with git push**
Upload the change to the remote repository with `git push origin master`. In newer versions of git, you should be able to just use `git push`.

**Adding Tracking to a Previously Created Branch**
Checkout the branch which doesn't have tracking added. Try (and fail) to push the branch. Make necessary adjustments to be able to upload the branch to the remote repository.

**Confirming Your Branch was Uploaded**
Log into GitLab to ensure the branch has been uploaded to the remote repository.

