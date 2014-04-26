# Deployment for Whispering Pines Sprints

Deployments are created weekly on two servers: QA and live.

# QA Server

The QA site is currently running off the **origin/qa** branch.

Located at http://example.com

Add code to origin/qa
------------------
The first thing you will need to do is update the QA branch in the repository with the code that is going up. Merge the dev branch into QA. For a hotfix, you may need to cherry-pick the commits since you do not want everything in dev currently.

Make sure you have the latest dev code.

    git checkout dev
    git pull --rebase origin dev

Merge dev into qa.

    git checkout qa
    git pull --rebase origin qa
    git merge --no-ff dev

To select individual hot fix commits:

    git cherry-pick _commit-id_

Update the repo.

  git push origin qa

Update the Server
--------------------

Deployment is currently done via Jenkins though you will have to trigger the job manually.

https://ci.example.com/job/qa.example.com_data_sync/

After updating the site make sure you check the deployment checklist to see if there are any manual steps documented for this deployment: https://example.hackpad.com/Deploymet-Checklist


# Deployment - Live Site

The live site is currently running off tags, which are made from master.

[NAME] is the release manager so normally only she should commit/push to master and create tags.

Add code to master
------------------
The first thing you will need to do is update the master branch in the repo with the code that is going up. For a normal release, you can just merge the QA branch. For a hotfix, you may need to cherry-pick the commits since you do not want everything in QA currently.

    git checkout master
    git pull --rebase origin master

### Merge code into master
For merging in the entire QA branch:

    git merge --no-ff qa

To select individual hot fix commits:

    git cherry-pick _commit-id_

### Add a tag
1. Make sure you have the latest list of tags:

    git fetch --tags

1. View the list of current tags:

    git tag

1. Add a new tag, according to the tag conventions, below:

    git tag -a _tag#_

1. This will prompt you for a commit message, in the message for tags please list things that are being deployed in this version. For regular releases, hit the high points, for hot fixes, list the ticket number and brief description.

1. Update the remote repo.

    git push --tags origin master

1. Switch back to your dev branch

    git checkout <branchname>

### Tag naming
Tags should be named according to the main version number, the sprint they belong to and whether or not this is a sprint release or a hotfix release (point releases) with the pattern _version.sprint.point_ . The current main version number is [NUMBER].

Examples:

- Sprint 6: Ripple, main release: 2.6.0
- First hotfix after the Ripple release: 2.6.1

Update the Live site
--------------------

Deployment is currently done via Jenkins. Though you will need to edit the existing Jenkins job to tell it what TAG to use.

Deployment job: https://ci.example.com/view/example.com/job/d7.example.com_git_sync/configure

Edit the Execute Shell step in this job and change it to your new TAG.

Save the job. Then click the "Build Now" button in the left column.

In the event of an error, the deployment script takes a snapshot of the DB just before doing the update. Those snapshots can be found in `/var/lib/jenkins/drush-backups/pulls/example.com`

After updating the site make sure you check the deployment checklist to see if there are any manual steps documented for this deployment: https://example.hackpad.com/example.com-Deploymet-Checklist
