## On an index card...

Write down your answer to the following questions:

- REQUIRED: What do you need to learn about Git today?
- OPTIONAL: How does Emma **get in touch** with you after the workshop to make sure your question(s) were answered?

Note: during the break I'm going to review the index cards to make sure we're on track.


## My Goal for this Workshop

By the end of this session you should be able to:

- Choose a **governance strategy** for your project.
- Choose a **branching strategy** for your project.
- Create project-specific **documentation** which outlines how your team members interact with your code.


## Warning!

This session is not about all the commands you can run in Git, and it doesn't start by telling you to `init` something.

### If you want that kind of stuff:

[gitforteams.com/resources/offsite.html](http://gitforteams.com/resources/offsite.html)


## Workshop Outcome:<br />Personalized Documentation

![Example of the Star Wars Sprintflow](../../resources/workflow-sample-diagram.png)

Note: this is where we want to end up by the end of today. You know where each
branch lives. You know how / where a branch is closed.


## Yes, the slides are uploaded.

[gitforteams.com/workshops/devwinter](http://gitforteams.com/workshops/devwinter)

==========
# Warm-up<br/> Exercise

## People and Process<br /> Before Commands and Code


## Basic Questions...

- Who has commit access?
- Why do you know your code isn't broken?
- Does your team use test-driven development?
- Do you have an independent quality assurance team?
- Can you deploy "broken" code?

Note: we'll start with the easy questions you MUST be able to answer. Your current answers may help you to uncover problems witn your current setup.


## Activity: Identify Current R&R

1. Write down a list of all of the people/**roles** on your code team.
2. Write a list of the tasks these people/roles are **responsible** for code-wise.

Note: R&R = roles and responsibilities


## Activity: Sketch the Assembly Line

Sketch a time line of how code is incorporated into your project.

- Where do people grab the code from?
- How do people share their work? (branch? patch? fork?)
- Is there a review process?
- Are there barriers to code commits (test suite, QA team)?

Note: right now, there are no wrong answers. It's just a sketch. A rough approximation is fine.



## Example: Single Branch

![Centralized: Everyone works in master branch](../../resources/workflow-single-branch.png)

Everyone pushes their work to the same branch on a central repository. There's no peer review or testing.


## Example: Pre-Merge QA Team

![Automated gatekeeper](../../resources/workflow-gatekeeper-human.png)

A quality assurance team, and optional test suite, decide if your work is acceptable.

Note: or this could be just an automated testbot.


## Example: CI or Post-Merge Test Suite

![Automated gatekeeper](../../resources/workflow-gatekeeper-automated.png)

A testbot notifies you if your work is not acceptable (possibly after adding it to the main branch).

Note: CI assumes everything is good, but notifies you if it's not.

==========
# Part 1

## Commit Access <br>and Code Governance

When you first create a Git project, you will need to decide who can commit their code to the repository.

Note: Step 1: Identify and describe the governance for your code.


## Overview

- **Dispersed Repositories** - Trust Few; Propose *a Solution*
- **Collocated Repositories** - Trust Few; Talk About *Your Progress*
- **Shared Repository** - Trust Everyone to use the Process


## Dispersed: Trust Few;<br>Propose a Solution

Everyone has read access. Very few have write access. Suggested
changes are presented as whole ideas in a single patch file for
review.


![Dispersed Repositories: Untrusted coders; typical for open source projects](../../resources/strategy-permissions-patching.png)


## Contributors with Dispersed Repositories

<table>
<tr><th width="50%">Pro</th><th>Con</th></tr>
<tr><td>
<li> Forces a review process.
<li> Works well with git tools (bisect, gitk).
</td>
<td>
<li> Sharing work is more complicated than branching.
<li> Contributors (potentially) need to setup their own code
  hosting platform.
</td>
</tr>
</table>

Note: This is what git was optimized for. It's archaic and
doesn't work well with web-based code hosting and ticketing
platforms such as GitHub.


## Examples of<br >Projects with Dispersed Contributor Repositories

<ul class="fragment">
<li>Linux
<li>Drupal
<li>FOSS projects still using a centralized code hosting model OR mailing-list code sharing model
</ul>

Note: Linux, Drupal


## Collocated: Trust Few;<br>Talk About *Your Progress*

Project forks give full permissions to developers so they can
do work in any commit granularity they choose. New work is
added to the main project through a request to the upstream
project via a proposed **branch of commits**.


![Collocated: Untrusted coders; typical for open source projects](../../resources/strategy-permissions-forking.png)


## Contributors with Collocated Contribution Repositories

<table>
<tr><th width="50%">Pro</th><th>Con</th></tr>
<tr><td>
<li> Forces a review process.
</td>
<td>
<li> Commit granularity may prevent effective debugging. 
<li> Private repos must be duplicated per team member.
<li> More steps to incorporate new work.
</td>
</tr>
</table>

Note: This is the default strategy for public code repositories
with open access for viewing the project. Wrote a resource on
why this may be bad at
http://developerworkflow.com/resources/evolution-social-coding.html


## Examples of<br>Collocated Contributor Repositories

<ul class="fragment">
<li>Django
<li>Ruby on Rails
<li>CakePHP
<li>FOSS projects hosted on GitHub
</ul>

Note: Django, Rails, CakePHP


## Shared Repository<br>(Joint Custody)<br>Trust Everyone to Use the Process

Developers work in a branch of the centralized code repository. Only the politics of the project prevent them from committing their work to the main body of work.


![Shared Repository: Trusted coders branch](../../resources/strategy-permissions-branching.png)


## Shared Repository 

<table>
<tr><th width="50%">Pro</th><th>Con</th></tr>
<tr><td>
<li> Encourages clean/working master.
</td>
<td>
<li> Encourages, but does not *require* code review.
<li> Must give explicit write permission to all team members.
</td>
</tr>
</table>

Note: This is the default strategy for private code repositories with named team members. For BIG projects, it can be time consuming to assign permissions to all devs.


## Examples of<br>Projects with Shared Repositories

<div class="fragment">
<p>Internal projects with trusted developers
</div>

Note: Internal projects using a centralized system (e.g. Git, Hg, bzr) **OR** centralized systems with liberal branching.


## Review

- **Contributors with Dispersed Repositories** <br>Trust Few; Propose *a Solution*
- **Contributors with Collocated Repositories** <br>Trust Few; Talk About *Your Progress*
- **Contributors Publishing to a Shared Repository** <br>Trust Everyone to use the Process


## So What?

- If you choose **Shared Repository**, you need to setup a private repository for your code, and grant permission to all team members to push their changes to the server.
- If you choose **Collocated Repositories**, you need to setup public or private repository for your code, and ensure all team members to can create their own clone of the project on the same system, and submit merge requests from their copy to the main project.

==========
# Part 2

## Cataloguing Code<br />with Branching Strategies

Identify and describe how your code is managed <br>within a single repository.


## Branching Strategies

- Scheduled Release: [Gitflow](http://nvie.com/posts/a-successful-git-branching-model/) 
  or [Simplified Gitflow](http://drewfradette.ca/a-simpler-successful-git-branching-model/)
- Constant Integration: [Branch Per Feature](https://www.acquia.com/blog/pragmatic-guide-branch-feature-git-branching-strategy)
  or [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)


## Scheduled Release

- Optimized for the collation of many smaller changes into a single release.
- Typically used for a download-able product; or web site with a scheduled release cycle (e.g. "Wednesdays").
- Incorporates human-reviews, and possibly automated tests.

![scheduled release: gitflow](../../resources/strategy-branching-gitflow.png)

Note: if you have the concept of stable releases, hotfixes, point releases, security releases, multiple supported versions, etc, then you need this granularity for your branches. There is always a period of time where you do not trust your code/developers and want to have a separate QA period. Thinking like a download-able product: version 4 vs. version 5 of The Software (a piece of software)


## Constant Integration 

- Code is deployed faster than scheduled releases; assumes all check-ins are deployable.
- Requires (trusted) test coverage.
- Typically uses a mechanical gatekeeper to check in code to the master branch.
- Often has flippers/flags for fine grained access to in-progress features.
- Fewer branches to maintain / keep updated.

![continuous delivery: feature branches](../../resources/strategy-branching-cd.png)

Note: if you don't need the granularity of multiple supported versions, you can probably get away with something closer to this branching strategy. Can you get away with just tags? Do you intend to go back and work on a previous version? As soon as you have the concept of a separate security hotfix, you need to introduce a separate branch. In CD: everything is urgent, so there's not a separation of a really urgent security fix. CI, CD vs CD: http://puppetlabs.com/blog/continuous-delivery-vs-continuous-deployment-whats-diff


## Activity

Which best describes your current setup?

- Scheduled Release: [Gitflow](http://nvie.com/posts/a-successful-git-branching-model/) 
  or [Simplified Gitflow](http://drewfradette.ca/a-simpler-successful-git-branching-model/)
- Constant Integration: [Branch Per Feature](https://www.acquia.com/blog/pragmatic-guide-branch-feature-git-branching-strategy)
  or [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
  
Note: On the sketch diagram you created previously, add a CIRCLE (or a triangle, or a pony) around the collation points for code. These represent new branches. Where possible, REDUCE the number of collation points because merging out-of-date branches is a potential pain point.


## So What?

- If you choose **scheduled release**, streamline how your code is collated for release.
- If you choose **constant integration**, codify how trust is deployed in your code.

==========
# Part 3

## Commit Granularity

The Great Rebase Debate


## super nerdy rant alert!

[Evolution of Social Coding](http://developerworkflow.com/resources/evolution-social-coding.html)


## What is a Commit

A record of the changes to the repository.

![scheduled release: gitflow](../../resources/strategy-branching-gitflow.png)

Note: let's start with the very, very basics. A commit is a record of change.


## How can we use Commits

- log
- gitk
- blame
- bisect

Note: We use commits when we look at our project's history. We also use commits to debug our code with "advanced" tools, such as bisect.


## Sharing Work: A brief history lesson

The patch workflow and `git am`.

<blockquote>The commit message is formed by the title taken from the "Subject: ", a blank line and the body of the message up to where the patch begins.</blockquote>

**In other words: a commit is a whole idea.**

Note: the Linux kernel developers chose to use a patching workflow and created command line tools to support this branching strategy.


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


## /rant

[Evolution of Social Coding](http://developerworkflow.com/resources/evolution-social-coding.html)


## So What?

Discuss with your team how they want to find bugs,<br>and therefore **HOW your commits should be recorded**.

Note: are you social coding? Or are you using git as it was designed to work with the command line tools it ships with?

==========
# Part 4

## Putting it all Together

Note: these are both in the resources for the repository


## Some Notes on Naming

- Use terms which resonate with your team (MVP -> LBB).
- Giving a descriptive name to projects and processes allows you to change the meaning by changing the name.
- There are a lot of Ewoks.
- There are more My Little Ponies.


## Whispering Pines Workflow

![Example of the Whispering Pines Sprintflow](../../resources/workflow-whisperingpines.png)

Note: Aiming for stability first, speed second. Some test coverage. Changes are collated weekly onto a QA server, and deployed from there.


## Whispering Pines Workflow<br />Documentation

github.com/emmajane/gitforteams

- [Whispering Pines Weekly Workflow](http://github.com/emmajane/gitforteams/blob/master/resources/workflow-sample-whisperingpines-code.md)
- [Release philosophy](http://github.com/emmajane/gitforteams/blob/master/resources/workflow-sample-whisperingpines-releasecycle.md)
- [Deployment](http://github.com/emmajane/gitforteams/blob/master/resources/workflow-sample-whisperingpines-deployment.md)


## Activity: Sketch Your Workflow

- Restructure your previous diagrams to show where code is collated for release.
- Add arrows to represent the direction of travel between repositories for code.
- To the arrows, add the git commands which you'd use.
- Create a written narrative which describes the EXACT commands people should use to move code through the process. (See previous slide for examples.)


## Last Thing

<table>
<tr>
<th width="50%">Index Card</th>
<th>Feedback</th>
</tr>
<tr>
<td>
<li>What did you learn?
<li>What is (still) confusing?
<li>What will you change for your project?
</td>
<td>
Please fill out the feedback forms! We can't make this better without your help.
</td>
</tr>
</table>

==========
# Resources

- Articles: [gitforteams.com](http://gitforteams.com/)
- Videos: [Collaborating with Git](http://shop.oreilly.com/product/0636920034872.do?cmp=il-prog-books-videos-product_promo_bwidget644_0636920034872_external)
- Book: [Git for Teams](http://shop.oreilly.com/product/0636920034520.do)
- Slides: [gitforteams.com/workshops/devwinter/](http://gitforteams.com/workshops/devwinter/)


Interested in being an Early Ready for *Git for Teams*?
<br>Leave me your email address, and I'll send you a PDF / .epub!
