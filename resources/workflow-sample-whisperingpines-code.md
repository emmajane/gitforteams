# Whispering Pines Workflow (code)

This page includes copy-paste-able git commands for:

1. Working on tickets.
2. Conducting a peer review.

It does not include ["philosophy"-style documentation](releasecycle.md).

# Working on Tickets

The commands we use to work on tickets.

Creating and maintaining branches
-----------------
NOTE: you must keep your branch up with dev. **At least daily you should update dev and rebase your working branch(es).** If you don't, we can end up with PITA conflicts at review time. Any tickets that have merge conflicts will be reopened and kicked back to you to fix before review.

**To start:**

    git clone git@coderepository.example:project/d7me.git

**To make a branch:**

Please ensure you are following our branch naming conventions. They are documented in the [Release Cycle document](release-cycle-sample-1.md). Generally branches will be in the format of ticketID-description.

    git checkout dev
    git pull origin dev
    git checkout -b NNNN-branchname
    git push -u origin NNNN-branchname

Do your work and push from here.

**To keep your branch current with dev:**

    git checkout dev
    git pull origin dev
    git checkout NNNN-branchname
    git rebase dev

If you have conflicts you need to resolve them in your branch prior to doing more work.

**To create a hotfix branch:**

    git tag
    git checkout -b <branchname> <tagname>
    git push -u origin <branchname>

We run `git tag` to see a list of all tag names. It's important to branch from the latest tagged release for hotfixes. The branch name should be in the format hotfix-NNNN-branch-name.

# Peer Review

In addition to the peer review process outlined here, we also have a pre-launch Weekly QA. This process is outlined in a perpetual hackpad (https://lullabot.hackpad.com/Weekly-QA-78mvrBruNm5).

Ready For Review Checklist
----------------------

Developers: Before asking for a peer review, please ensure you have completed everything on this checklist.

- Did I include the ticket # in my final commit message? (if not, use `commit --amend` to include it to re-write your final commit message and include the ticket #).
- Have I documented any additional steps needed to start the review process? e.g. db schema update, or manual configuration
- Have I included a screen shot of what the finished output looks like? (if relevant)
- Have I merged in the dev branch so that my branch is up-to-date with the work other developers have completed?
- Have I un-assigned myself from the ticket, and marked it as resolved in the ticket tracker?

Conducting a Peer Review
-----------------
We are currently using a peer-review process. Code reviews help both the reviewer and the reviewee improve their Drupal skills. As part of our weekly tasks, everyone will be responsible for some ticket review. You may self-assign yourself to review a ticket, or be assigned a ticket to review (either by the person who was working on it, or by a PM). Before you begin your review, please ensure the ticket has been assigned to you in the ticket tracker.

Read through the ticket and associated comments. It should include all of the items from the "Review for Review Checklist" (above). If it does not, ask the developer/designer to update the ticket using the checklist. Reassign the ticket to them so they know the ball is in their court.

Once the ticket really is ready for a code review, proceed with the following steps:

1. Assign yourself to the ticket so that others know it is currently being worked on by someone, and that it is not available for review.

2. Checkout a local copy of the branch relating to the ticket. From the command line this is done with:
        git branch -a # show a list of all available branches
        git fetch # downloads the branches
        git checkout --track -b NNNN-branch-name origin/NNNN-branch-name # NNNN should be the ticket number
        (short version of above = git checkout --track origin NNNN-branch-name)

3. Complete any steps outlined in the ticket to confirm the branch works "as advertised" in the ticket. If there are any errors, or things are missing, attempt to verify if the problem is on your end (e.g. did you clear cache?). If you cannot replicate what you should be seeing, contact the developer/designer and ask them for help to get your local environment looking like what it should in the ticket.
4. Once you've confirmed the branch is correct and complete it can be merged into the dev branch. Ensure your branch is up-to-date:
        git checkout dev
        git pull
        git checkout NNNN-branch-name
        git rebase dev

5. Confirm the branch is still working "as advertised" (see step 3).
6. Merge the branch you've reviewed into dev and push it back up.
        git checkout dev
        git merge --no-ff NNNN-branch-name
        git push

7. Confirm your new branch has been successfully integrated into the development site. It will take about five minutes for d7dev.drupalize.me to be updated with the revised branch. Complete any additional steps required to sync the database with the new code (e.g. enable new modules). Proceed only once the new code is working on d7dev.drupalize.me.
8. Close the ticket in the ticket tracker. At this time there should not be any additional notes required; however, review the ticket carefully before closing it. If there are "part 2" bits (e.g. the site building part is finished, but now the ticket needs theming work), update the ticket as follows:
 * unassign the ticket
 * move the ticket to the MVP backlog
 * update the component, if relevant (e.g. move it from Site Building to Theming)<br><br>
8. Delete the ticket branch as follows:
        git branch -d NNNN-branch-name # delete the local branch
        git push origin --delete NNNN-branch-name # delete the remote branch
9. Note that you can do `git fetch -p origin`. The -p option tells fetch to delete any tracking branches that no longer exist in the corresponding remotes; by default they are kept around.
