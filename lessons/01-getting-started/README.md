# Getting Started with Hosted Git Repositories

Most of the people I've worked with are starting out with a project 
they need to collaborate with. They aren't starting with an empty 
folder, but rather with an existing project. I personally find it 
easier to tinker with something rather than stare at a blank screen. 
So the first thing we're going to do is set you up with a practice 
repository that I've created. You won't be able to edit *my* copy of 
the project, but you will be able to make edits to your own copy. 


## Overview of permission strategies

Let's start with a review of permission strategies and the way a 
project can be setup with Git.

Overview of permission strategies:

- *Centralized*. Commonly seen for centralized systems, such as
  Subversion. In this system, everyone is committing into the
  same repository on a single machine. When you're working with
  a distributed version control system, such as Git, you're
  actually using a centralized model. This model often has
  finer grained access on who can make a commit, and where they
  can commit to.
- *Patched*. The first step away from a centralized system, is
  to work in patch files. In this case, there is still a
  central, canonical place where code is stored, like in the
  centralized system. But in this case, very few people are
  allowed to commit to the central repository. Instead, code
  changes are shared as patch files. This permission strategy
  is lesson common today, but it's still used by the Linux
  kernel team, and by Drupal.
- *Forked*. Most open source projects will use a forking
  permission strategy. In this case, we are finally seeing the
  difference (and power) of a distributed version control
  system. In a forking workflow, there are multiple copies
  of the repository. I have my copy; you have your copy. And
  through a social convention, we decide which copy is the
  canonical (or primary) source. This permission strategy is
  used to limit who is allowed to make commits back into the
  canonical source for a project. In other words: it is a
  limiting strategy.
- *Branched*. Whereas a forking strategy gives very limited
  access to a small number of people, a branching strategy is a
  permissive strategy. The branching strategy is typically used
  by internal teams (and the teams responsible for the
  canonical repository of a bigger project). In this strategy
  it is only by convention that people choose which branches
  they want to save their commits to. There are no restrictions
  once you have access.

Permission strategies and branching strategies are often
conflated in articles about version control. This can make it
confusing. When examining a diagram, take a look at the symbols
used. If there are dots representing individual commits, you
are probably looking at a *branching strategy* diagram. We'll
get to those a bit later in the series.

### Lesson Objectives

By the end of this lesson, you will be able to identify four
different permission strategies used for version control, and
explain in each strategy, who may make commits to a repository.

### Self-Check

Identify the reasons why the identified strategies was selected:

- Large open source project may use a forking workflow.
- An internal team project uses a branching workflow.

### Lesson Summary

There are four main permission strategies used with distributed version
control systems:

- Centralized is how you work at your own work station. Changes are saved
  into your local repoitory, unlike in a centralized *system* where the
  changes were saved into a remote repository.
- Patching strategy is where each person has a local repository, and shares
  their work with others by sending patch files, which identify how to
  "patch up" a repository with a common ancestor so it looks like the work
  the developer as done in their own copy of the repository.
- Forked strategy is where each person creates a copy of the canonical
  repository, and maintains a connection to it. Proposed changes are made by
  submitting a "pull request" or "merge request" to the upstream project.
- Branching strategy is where every person on the team has write-access to
  the project. Instead of waiting for a pull request (or merge request) to
  be accepted, they are able to save their changes directly to the
  repository, without additional permission from another person.

## Creating a GitLab Account

GitLab is a free code hosting platform which allows you to create private,
and public repositories. It's also an open source product you can install
behind your own firewall if you're working with a large team. It's not the
most popular system out there, but I believe it offers the most flexibility
to the widest range of people watching these videos. We'll get started with
GitLab, and later in the lessons, I'll show you how to migrate your project
to GitHub, which is currently one of the most popular code hosting platforms
for open source projects. Git is distributed because work can be easily
shared across multiple hosting systems.  Create a GitLab account to store
your first remote repository.

### Lesson Objectives

By the end of this lesson, you will be able to create an account on GitLab.

### Self-Check

Ensure you have a GitLab account before proceding to the next lesson.

### Summary

1. Navigate to www.gitlab.com.
2. At the bottom of the screen locate the link to [create an
   account](https://gitlab.com/users/sign_up).
3. Complete the on-screen instructions to create your account.

### Gotchas

GitLab releases new software every month. If the interface is significantly
different, check the instructions on GitForTeams.com. I have made a backup
of GitLab which uses same interface as these video lessons.

## Adding Your SSH Keys

SSH keys are a way to identify trusted computers, without using 
passwords. When you are using code hosting systems, these SSH
keys will allow you to effectively "log in" to the system, and
either retrieve, or save, code as if you had logged into to your 
account.

### Lesson Objectives

By the end of this lesson, you will be able to locate, and add
your SSH keys to GitLab. If do not have SSH keys already, you
will also be able to create a new SSH key pair.

### Self-Check

Your SSH public key has been uploaded to GitLab.

### Summary

Locate, or Generate SSH Keys:

1. At the command line, run: `cat ~/.ssh/id_rsa.pub`. If there is a blob of
   text printed to the screen beginning with `ssh-rsa` or `ssh-dsa`, skip
   the next step.
2. To generate new keys, run: `ssh-keygen -t rsa -C "$your_email"` 
   (replace with your actual email)
3. To display your new public key, run: `cat ~/.ssh/id_rsa.pub`.
4. Copy the text for your public key.

Add Your Public Key to GitLab:

1. Log in to GitLab.
2. Navigate to your account (top right).
3. Locate and click on the tab for [SSH keys](https://gitlab.com/profile/keys).
4. Click "Add SSH Keys".
5. In the form, paste your SSH public key. (The title is optional.)
6. Click save.

## Forking Your First Project

We are forking so that you can upload your changes to your own
repository. If you cloned from this project directly to your computer
you wouldn't be able to upload your changes to the project (only
“privileged” users can do that).

### Lesson Objectives

By the end of this lesson, you will be able to create a fork of a
remote repository.

### Self-Check

In your GitLab account, you should now have a new project with its
upstream set to `gitforteams/workshop`.

### Summary

Fork the GitLab sample project:

1. Navigate to the project page:
   https://gitlab.com/gitforteams/workshop
2. Locate and click on the
   button labeled "fork".
   https://gitlab.com/gitforteams/workshop/fork

Tada.

## Privatizing Your Repository

Adjust the visibility of your forked repository to PRIVATE.
Although this is completely optional, a lot of people feel more
comfortable making mistakes when they know no one will see
them.

Private repositories are also useful if you want to use GitLab for
private projects, such as client work, and don't want others to be able
to see the code you are creating.

### Lesson Objectives

By the end of this lesson, you will be able to alter the permission
settings of your repository so that no one else can view its contents.

### Self-Check

When you log out of GitLab, are you still able to navigate to your
project page and see your work?

### Summary

Adjust the settings of your forked repository so that the project is
private.

1. Navigate to your account page (click the avatar, top right).
2. From the right sidebar, select the project you've just forked.
3. Click the "settings" tab.
4. Scroll down and change the visibility settings to "Private".
5. Scroll to the bottom of the page and click "save change".
