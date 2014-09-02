# Working with Tags

**Overview of Tagging Strategies**
Tags are used to pin-point specific commits. They don't follow a series of commits, like a branch does. They are a single point in time along the history of your work. You can add additional information (like a commit message) to the tag. See git help tag for extra options.

**Listing All Tags**
Use the command `git tag` to see a list of existing tag.

**Investigating a Specific Tag**
Use the command `git show <tagname>` to get the commit message and the author details.

**Checking Out Tags**
You can also checkout this tag. You'll go into a DETACHED HEAD STATE!  But you'll be fine.

**Recovering from a Detached HEAD State**
Checkout the branch you were on previously to return to your regular work.

