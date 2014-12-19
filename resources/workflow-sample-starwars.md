Star Wars Sprint Workflow
-------------------------

{NAME} is the product manager.

Dev site (http://d7.example.com) updates on **dev** branch automatically when commits are added to the **dev** branch.

For the Drupalize.Me upgrade we're working with a peer review system. Please note that if you do not have everything in place for a review, your ticket is likely going to be kicked back to you to resolve the issues first, especially if it isn't clear how to test/review the ticket.

**Working on Tickets**

1. Ensure a ticket is open in the ticket tracker, that it's for the current sprint, and is assigned to you.
2. Work in a new branch that contains the ticket number that you're working on. (Please do not work directly in dev, or merge your code to the dev branch without review.) Note, that if you have multiple tickets that are very intertwined, you can create a feature branch to cover that group of tickets. You still need to use ticket ids in your commit messages. (@see step #3)
3. On all commits for your ticket before pushing your branch, ensure that you have the ticket number in your commit message. This will automatically tie your branch to the ticket and make reviewing easier and faster. If you need to, use commit --amend to include the ticket #.
Add ticket numbers with a "#" before them so the ticket tracker will associate the commit with the ticket; however, do not start your commit message with a # sign. The following are acceptable formats for commit messages:
  - "[#66]
  - "References #666"
  - "Resolves #666" - will also mark the ticket as resolved. (@see step #4)
4. In the ticket tracker, mark your ticket as "Resolved".
When marking a ticket as resolved include any manual steps necessary in a comment.
5. Find a buddy to review and merge your code into the dev branch. See notes below on the review process we use.

Branch Types and Names
----------------------
These are the conventions for the kinds of branches we use and naming them. NOTE: you should never use the master branch.

- **Ticket branches** (e.g. 1545-add-queue-button). Each ticket should have its own branch normally and these should be named as _ticket#-some-descriptive-name_.
- **Feature branches** (e.g. add-guides) If you have substantial work on a set of tickets that go together feel free to make a new feature branch for it. You can name that branch with some sort of descriptive title, without a ticket number.
- **Hot fix branches** (e.g. hotfix-614-quickfind). These should be used for all hot fix tickets, one branch per ticket. They should be named as hotfix-_ticket#-description_.

Creating and maintaining branches
-----------------
NOTE: you must keep your branch up with dev. **At least daily you should update and merge the dev branch into your working branch(es).** If you don't, we can end up with PITA conflicts when moving back into master and live. Any tickets that have merge conflicts will be reopened and kicked back to you to fix before review.

**To start:**

D7
    `git clone git@githost.example.com/d7me.git`

**To make a branch:**

 -  `git checkout dev`
 -  `git pull origin dev`
 -  `git branch <branchname>`
 -  `git checkout <branchname>`
 -  `git push origin <branchname>`

Do your work and push from here.

**To keep your branch current with dev:**

    git checkout dev
    git pull origin dev
    git checkout <branchname>
    git rebase dev

If you have conflicts you need to resolve them in your branch prior to doing more work.

Ready For Review Checklist
----------------------
- Did I include the ticket # in my final commit message? (if not, use commit --amend to include it to re-write your final commit message and include the ticket #).
- Have I documented any additional steps needed to start the review process? e.g. db schema update, or manual configuration
- Have I included a screen shot of what the finished output looks like? (if relevant)
- Have I merged in the dev branch so that my branch is up-to-date with the work other developers have completed?

Conducting a Peer Review
-----------------
We are currently using a peer-review process. Code reviews help both the reviewer and the reviewee improve their Drupal skills. If you are asked to conduct a review, please use the following steps.

1. Review the ticket that has been assigned to you. It should include all of the items from the "Review for Review Checklist" (above). If it does not, ask the developer/designer to update the ticket using the checklist.

2. Checkout a local copy of the branch relating to the ticket. From the command line this is done with:

3. 

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

7. Confirm your new branch has been successfully integrated into the development site. It will take about five minutes for d7.example.com to be updated with the revised branch. Complete any additional steps required to sync the database with the new code (e.g. enable new modules). Proceed only once the new code is working on d7.example.com

8. Close the ticket in the ticket tracker. At this time there should not be any additional notes required; however, review the ticket carefully before closing it. If there are "part 2" bits (e.g. the site building part is finished, but now the ticket needs theming work), update the ticket as follows:
  - unassign the ticket
  - move the ticket to the MVP backlog
  - update the component, if relevant (e.g. move it from Site Building to Theming)
