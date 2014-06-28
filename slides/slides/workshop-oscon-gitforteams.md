## Warning!

This is not a talk about all the commands you can run in Git.

### Resources for Commands:

- [Mega Resources List o' Links](http://developerworkflow.com/resources/offsite.html)
- [Git Documentation](http://git-scm.com/doc)
- [Pro Git](http://git-scm.com/book)


## My Goal for this Workshop

By the end of this session you should be able to:

- Determine a permission strategy for your project.
- Determine a branching strategy for your project.
- Create documentation which outlines how your team members will use version control.


## Workshop Outcome:<br />Personalized Documentation

![Example of the Star Wars Sprintflow](../../resources/workflow-sample-diagram.png)

Note: this is where we want to end up by the end of today. You know where each
branch lives. You know how / where a branch is closed.


## github.com/emmajane/gitforteams

You'll want a copy of the slides for reference as we go through the activities. Please open this page now.

==========
# Warm-up<br/> Exercise

## People and Process<br /> Before Commands and Code


## Sample (Rhetorical?) Questions

- Who has commit access?
- Why do you know your code isn't broken?
- Does your team use test-driven development?
- Do you have an independent quality assurance team?
- Can you deploy "broken" code?


## Activity: Identify Current R&R

1. Write down a list of all of the people/roles on your code team.
2. Write a list of the tasks these people/roles are responsible for code-wise.

Note: R&R = roles and responsibilities


## Activity: Sketch the Assembly Line

Sketch a timeline of how you'd like new code to be incorporated into your project. Is there a review processs? A test suite? Minimal barriers to code commits?

(You will to refine this sketch during the workshop. There are no wrong answers right now.)


## Sample Activity Answer:<br/>Centralized

Everyone works in the same centralized repository. There's no peer review or testing.

![Centralized: Everyone works in master](../../resources/workflow-centralized.png)


## Sample Activity Answer:<br/>Pre-Merge QA Team

A quality assurance team, and optional test suite, decide if your work is acceptable.

![Automated gatekeeper](../../resources/workflow-gatekeeper-human.png)

Note: or this could be just an automated testbot.


## Sample Activity Answer:<br/>CI or Post-Merge Test Suite

A testbot notifies you if your work is not acceptable (possibly after adding it to the main branch).

![Automated gatekeeper](../../resources/workflow-gatekeeper-automated.png)

Note: CI assumes everything is good, but notifies you if it's not.

==========
# Part 1

## Project Hosting

When you first create a Git project, you will need to decide who can commit their code to the repository.

Note: Step 1: Identify and describe the governance for your code.


## Centralized: Trust Everyone

Everyone has read-write access to the same repository on a centralized disk (e.g. subversion). This is also how you work *locally* with Git.

![Centralized: Everyone works in master](../../resources/strategy-permissions-centralized.png)

- Pro: Author has to deal with their own merge conflicts.
- Con: No guarantee the code works.


## Forked: Trust No One

Project forks give full permissions to developers so they can do work.
New work is added to the main project through a request to the upstream project.

![Forking: Untrusted coders; typical for open source projects](../../resources/strategy-permissions-forking.png)

- Pro: Forces a review process.
- Pro: Encourages experimentation.
- Con: Private repos must be duplicated per team member.
- Con: More steps to incorporate new work.

Note: This is the default strategy for public code repositories with open access for viewing the project.


## Branched: Trust the Process

Developers work in a branch of the centralized code repository. Only the politics of the project prevent them from committing their work to the main body of work.

![Branching: Trusted coders branch](../../resources/strategy-permissions-branching.png)

- Pro: Encourages clean/working master.
- Con: Must give explicit write permission to all team members.
- Pro/Con: Encourages, but does not **require** code review.

Note: This is the default strategy for private code repositories with named team members.


## Your Home Work

- If you choose **BRANCHED**, you need to setup a PRIVATE repository for your code, and grant permission to all team members to push their changes to the server.
- If you choose **FORKED**, you need to setup PUBLIC or PRIVATE repository for your code, and ensure all team members to can create their own PUBLIC or PRIVATE copy of the project, AND submit merge requests to the main project.

==========
# Part 2

## Separating Collated Code <br />with Branching Strategies

Identify and describe how your code is collated within your repository.


## Branching Strategies

- Scheduled Release: [Gitflow](http://nvie.com/posts/a-successful-git-branching-model/) 
  or [Simplified Gitflow](http://drewfradette.ca/a-simpler-successful-git-branching-model/)
- Continuous Deployment: [Branch Per Feature](https://www.acquia.com/blog/pragmatic-guide-branch-feature-git-branching-strategy)
  or [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)


## Scheduled Release

- Optimized for the collation of many smaller changes into a single release.
- Typically used for a downloadable product; or web site with a scheduled release cycle (e.g. "Wednesdays").
- Incorporates human-reviews, and possibly automated tests.

![scheduled release: gitflow](../../resources/strategy-branching-gitflow.png)

Note: if you have the concept of stable releases, hotfixes, point releases, security releases, multiple supported versions, etc, then you need this granularity for your branches. There is always a period of time where you do not trust your code/developers and want to have a separate QA period. Thinking like a downloadable product: version 4 vs. version 5 of The Software (a piece of software)


## Continuous Deployment

- Code is deployed faster than scheduled releases.
- Requires (trusted) test coverage.
- Typically uses a mechanical gatekeeper to check in code to the master branch.
- Often has flippers/flags for fine grained access to in-progress features.
- Fewer branches to maintain / keep updated.

![continuous delivery: feature branches](../../resources/strategy-branching-cd.png)

Note: if you don't need the granularity of mulitple supported versions, you can probably get away with something closer to this branching strategy. Can you get away with just tags? Do you intend to go back and work on a previous version? As soon as you have the concept of a separate security hotfix, you need to introduce a separate branch. In CD: everything is urgent, so there's not a separation of a really urgent security fix. (a deployed system)


## Activity

Which best describes your current setup?

- Scheduled Release: [Gitflow](http://nvie.com/posts/a-successful-git-branching-model/) 
  or [Simplified Gitflow](http://drewfradette.ca/a-simpler-successful-git-branching-model/)
- Continuous Deployment: [Branch Per Feature](https://www.acquia.com/blog/pragmatic-guide-branch-feature-git-branching-strategy)
  or [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
  
<br />On the sketch diagram you created previously, add a CIRCLE (or a triangle, or a pony) around the collation points for code. These represent new branches. Where possible, REDUCE the number of collation points because merging out-of-date branches is a potential pain point.


## Your Home Work

- If you choose **SCHEDULED RELEASE**, determine the points where code needs to be collated for release.
- If you choose **CONTINUOUS DEPLOYMENT**, codify how trust is deployed in your code.

==========
# Part 3

## Commit Granularity

The Great Rebase Debate


## What is a Commit

<blockquote>Record changes to the repository</blockquote>


## How can we use Commits

- log
- gitk
- blame
- bisect


## Sharing Work: A brief history lesson

The patch workflow and `git am`.

<blockquote>The commit message is formed by the title taken from the "Subject: ", a blank line and the body of the message up to where the patch begins.</blockquote>

In other words: a commit is a whole idea.


## Sharing Work: Today

`git push`

Shares an entire branch, with all your micro commits.

![branches collapsed by default](../../resources/git-log-graphical.png)


## Compare: bzr

![branches collapsed by default](../../resources/bzr-log-graphical.png)

Note: branches are collapsed by default; there is a sane commit message when the branch is merged into master (unlike git which gives you a default "merged!" message)


## Problem!

Git tools are COMMIT-aware, not BRANCH-aware.

- gitk
- bisect


## Solution!

`git rebase`

<blockquote>Forward-port local commits to the updated upstream head</blockquote>

In English: re-draw the graph for the commit history as if the rebased commits were already in the history when you did your work.


## Solution!

`git rebase -i`

<blockquote>Make a list of the commits which are about to be rebased. Let the user edit that list before rebasing. This mode can also be used to split commits (see SPLITTING COMMITS below).</blockquote>

In English: combine, or separate, any commits previously made.


## Yes, Re-write History

Because the tools used to interpret history are crude, the recommended approach is simply to fix history.

*TWITCH*

But this is how Git works. So there you go.


## Activity

???

- Do a rebase together.
- Discuss team dynamics and which tools you'll want to use (bisect, gitk, blame, etc)

==========
# Part 4

## Putting it all Together

- These examples are pulled from Drupalize.Me when I was working as their PM and sometimes front end dev.
- This is a product with no external stakeholders.
- YMMV, YOLO, etc.

Note: these are both in the resources for the repository


## Project Highlights

- Drupal 6 -> Drupal 7 upgrade
- Aiming for speed of work, not stability.
- Changes were **not** being deployed to the live server.
- No weekly demos (which you might have for client work).
- Total time: 18 months.
- [Star Wars Sprintflow](../../resources/workflow-sample-starwars.md)


## Some Notes on Naming

- Use terms which resonate with your team (MVP -> LBB).
- Giving a descriptive name to projects and processes allows you to change the meaning by changing the name.
- There are a lot of Ewoks.
- There are more My Little Ponies.


## The Star Wars Workflow

![Example of the Star Wars Sprintflow](../../resources/workflow-starwars.png)

Note: pre-launch: peer review with branched permission strategy; separate QA server where work is available for review, but typically devs just look at their local version of the current dev branch.


## Whispering Pines Workflow

![Example of the Star Wars Sprintflow](../../resources/workflow-whisperingpines.png)

- Aiming for stability first, speed second.
- Some test coverage.
- Changes are collated weekly onto a QA server, and deployed from there.

Documentation: 
- [Whispering Pines Weekly Workflow](../../resources/workflow-sample-whisperingpines-code.md)
- [Release philosophy](../../resources/workflow-sample-whisperingpines-releasecycle.md)
- [Deployment](../../resources/workflow-sample-whisperingpines-deployment.md)


## Final Activity: Sketch Your Workflow

- Restructure your previous diagrams to include the infrasture where code is collated.
- Add arrows to represent the direction code travels.
- To the arrows, add the git commands which you'd use.
- Create a written narrative which describes the EXACT commands people should use to move code through the process. (See previous slide for examples.)

==========
# Resources

- [Developer Workflow](http://www.developerworkflow.com/)
- Scheduled Release: [Gitflow](http://nvie.com/posts/a-successful-git-branching-model/)
  ([Cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/))
  or [Simplified Gitflow](http://drewfradette.ca/a-simpler-successful-git-branching-model/)
- Continuous Deployment: [Branch Per Feature](https://www.acquia.com/blog/pragmatic-guide-branch-feature-git-branching-strategy)
  or [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
