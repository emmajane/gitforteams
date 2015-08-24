# Whispering Piles Release Cycle Documentation

## Sprints and Release Cycle

You'll notice that we have no time-based milestones in the ticket tracker. We are no longer doing sprints that last for two weeks, with a big release every third week. We do a new release on the site every Wednesday with whatever work is ready to go at that time. We now have three sites for our process; dev, QA, and live. Here's how it works:

Throughout the week, we do peer review of resolved tickets prior to the work getting merged into the dev branch.
On Monday morning we take whatever is in the dev branch at that time and merge that into the QA branch. Dev work continues in the dev branch/site, while the QA site is updated with the latest code for release.
We create the weekly QA checklist in hackpad by copy/pasting the QA user story from the tickets that were merged in the last week. (Every new ticket needs to have a QA user story as the first line of the ticket.)
Everyone on the team QAs the tickets we've closed, as well as doing a general spot check of the site to look for bugs and regressions. We also have a suite of tests that get run, and a list of standard manual QA we must do every week. Any QA fails or regression bugs that are found are opened in the ticket tracker and put in the QA Fixes bucket so they can be addressed (fixed or reverted) prior to release.
Wednesday morning we merge the qa branch into the master branch, tag it, and pull it onto the live site.
Every Thursday we do a blog post sharing what we've accomplished during the last week.
This system means that we are constantly making improvements to the site. We can also respond more quickly to member support issues that involve bugs or features on the site, which gives us a big customer support win. The other nice thing, in terms of morale and momentum, is that if you happen to miss getting your ticket into a release you don't have to wait three weeks to see it finally get on the site. It can simply go in the following week. Doing this in weekly bites also means that the QA list is relatively short and manageable.

Some may wonder at the PM overhead for weekly tickets and QA. As far as QA overhead, since we now require the QA test as part of the ticket itself, it's pretty easy to just get a list of the tickets that were merged within the last week, do a little copy/paste and you have your test list. Since it is only a week's worth of work we often only have about 20 tickets to test plus the 14 manual standard tests. We have at least four or five people doing QA, so an hour or two for each person covers our QA needs, and doesn't concentrate it all on one person.

## Branch Management

This is our branch management policy. We are basically following the Git workflow outlined in this blog post: http://nvie.com/posts/a-successful-git-branching-model.

### Workflow Branches

- **dev** this is the main development line, code created in a feature branch that has been reviewed by a peer should be merged to this branch. Regular feature/bug branches should be made from this branch.
- **qa** code in this branch is in QA for the next scheduled release.
- **master** this is the production ready, deployed to the live server code. Hotfixes should be made from this branch.

### Branch Types and Names

These are the conventions for the kinds of branches we use and naming them. NOTE: you should never use the master branch.

- **Ticket branches** (e.g. 1545-add-queue-button). Each ticket should have its own branch normally and these should be named as _ticket#-some-descriptive-name_.
- **Feature branches** (e.g. add-guides) If you have substantial work on a set of tickets that go together feel free to make a new feature branch for it. You can name that branch with some sort of descriptive title, without a ticket number.
- **Hot fix branches** (e.g. hotfix-614-quickfind). These should be used for all hot fix tickets, one branch per ticket. They should be named as hotfix-_ticket#-description_. Hotfix branches should always be branched from the latest tagged release.

## Ticket Assignment

For the other side of the PM work, sprint loading and ticket assignment, we've removed that almost entirely by implementing self-assigned tickets. There is no PM work to go through the backlog and load a sprint anymore. This obviously requires a lot of trust, and for the whole team to be on the same page about where our priorities lie. We're a small team, all focused on the same goals. The roadmap makes it clear what our priorities are, and we trust each other to make sure the work gets done.

People can work on any ticket in the ticket tracker, but the buckets are listed in order of priority, and we assign each ticket a relative priority level as well, so we know where we need to focus at least part of our effort every week. This lets people work on things that are personally interesting or bugging the hell out of them, while trusting they will also work on stuff that isn't fun, but we all know needs to get done. If there is a particular deadline for something, then that is communicated to the team by email and/or scrum call (we have scrum twice a week, on Monday and Wednesday), and is often set to a higher priority so it floats to the top of our ticket lists.

The main PM responsibility on this side is making sure new tickets are reviewed, put in the right bucket, and assigned a priority. Instead of PM, we call this person the gatekeeper. As the product owner I am the gatekeeper, though I'll ask someone else to step in when I'm out of the office. When someone creates a new ticket, they don't put it in a bucket or assign priority, but they do state in the ticket if they feel that the ticket should be a high priority or a hot fix and if so, why. I review all new tickets daily (which is often only a max of two or three, if any) and decide the final priority. It's a very lightweight process and normally only takes me a few minutes a day.

This new process has made our site-building efforts much more flexible, which is really important for us. We all have multiple areas of responsibility, and being able to balance your available time for the site with other tasks is huge. If you end up not actually having time for tickets due to other responsibilities (remember, creating content and taking care of our members are our main responsibilities—not site development), you just don't assign any to yourself for that week, instead of feeling bad because you couldn't complete the ones assigned to you by someone else. On the other hand if you are blowing through tickets, then you can simply grab something from the pile and keep going without waiting on someone to give you work.

We work with a peer review system. Please note that if you do not have everything in place for a review, your ticket is likely going to be kicked back to you to resolve the issues first, especially if it isn't clear how to test/review the ticket. More about the peer review process can be found at [Peer Review](http://gitforteams.com/resources/review-process.html).

### Working on Tickets

1. Ensure a ticket is open in the ticket tracker, that it's for the current sprint, and is assigned to you.
2. Work in a new branch that contains the ticket number that you're working on. (Please do not work directly in dev, or merge your code to the dev branch without review.) Note, that if you have multiple tickets that are very intertwined, you can create a feature branch to cover that group of tickets. You still need to use ticket ids in your commit messages. (@see step #3)
3. On all commits for your ticket before pushing your branch, ensure that you have the ticket number in your commit message. This will automatically tie your branch to the ticket and make reviewing easier and faster. If you need to, use commit --amend to include the ticket #.
Add ticket numbers with a "#" before them so the ticket tracker will associate the commit with the ticket; however, do not start your commit message with a # sign. The following are acceptable formats for commit messages:
  - "[#66]
  - "References #666"
  - "Resolves #666" - will also mark the ticket as resolved. (@see step #4)
4. In the ticket tracker, mark your ticket as "Resolved".
When marking a ticket as resolved include any manual steps necessary in a comment.
5. Unassign the ticket from yourself. A ticket that is "unclaimed" is ready for anyone to review.
