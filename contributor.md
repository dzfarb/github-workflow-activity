# Contributors' Guide

__Note:__ In the instructions below __ALL_CAPS__ is a placeholder that you must replace with a real value.

## Overview

### Prepare to work on a project

1. [Fork the project](#fork-the-project)
2. [Clone your fork](#clone-your-fork)
3. [Add upstream remote](#add-upstream-remote)


### Prepare to work on an issue

1. [Claim an issue](#claim-an-issue)
2. [Update master](#update-master)
3. [Create a feature branch](#create-a-feature-branch)
4. [Create a pull-request](#create-a-pull-request)


### Work on an issue

1. [Create and test a change](#create-and-test-a-change)
2. [Commit the change](#commit-the-change)
3. [Push changes in feature branch to your fork](#push-changes-in-feature-branch-to-your-fork)


### Update and resolve conflicts on a pull-request

1. [Update master](#update-master)
2. [Merge master into feature branch](#merge-master-into-feature-branch)
3. [Push changes to your fork](#push-changes-to-your-fork)
4. [Request a review](#request-a-review)


### Clean up

1. [Update master](#update-master)
2. [Delete the feature branch](#delete-the-feature-branch)
3. [Push changes in master to your fork](#push-changes-in-master-to-your-fork)


## Details

### Fork the project

1. Log into GitHub.
2. On GitHub, navigate to the project on which you want to work.
3. Click __Fork__ in the upper-right corner.
4. If you are a member of one or more organizations, select your personal account to receive the fork.
4. You should now be looking at your fork of the project on GitHub.


### Clone your fork

1. Log into GitHub.
2. On GitHub, navigate to ___your fork___ of the project.
3. Follow GitHub's instructions for [Cloning a repository](https://help.github.com/articles/cloning-a-repository/).


### Add upstream remote

1. Follow GitHub's instructions for [Configuring a remote for a fork](https://help.github.com/articles/configuring-a-remote-for-a-fork/).


### Claim an issue

1. Log into GitHub.
2. On GitHub, navigate to the project on which you are working.
3. Click the __issues__ tab.
4. Search for an open issue that interests you. Alternatively, if you have an idea but don't see an issue for it, create an issue.
5. Make sure the issue is not assigned to anyone, and no-one else has claimed it (check comments).
6. Claim the issue by leaving a comment that you are working on it.




### Update master

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Pull changes from upstream into the master branch.

    ```
    git checkout master
    git pull upstream master
    ```

3. Push the now updated master in your local repository to your fork.

    ```
    git push origin master
    ```


### Create a feature branch

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```


2. Create a feature branch off of the master branch. Name your branch something related to what you are working on: e.g., `login_fix` or `preview_feature`.

    ```
    git checkout master
    git branch FEATURE_BRANCH
    ```

### Create a pull-request

Before you can create a pull-request, you need at least one commit. In these instructions you will create an empty commit. You could just as easily make a small change and commit that instead.

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Create the empty commit on your feature branch

    ```
    git checkout FEATURE_BRANCH
    git commit --allow-empty -m "Start work on FEATURE"
    ```

3. Push changes in the feature branch to your fork, create a remote branch in your fork by the same name, and tell git to track that remote branch with your local branch. (This is a powerful little command.)

    ```
    git push -u origin FEATURE_BRANCH
    ```

4. Follow GitHub's instructions for [Creating a pull request from a fork](https://help.github.com/articles/creating-a-pull-request-from-a-fork/).

5. In a comment on the pull-request, link to the issue number(s) that the pull-request is attempting to address. This is done by putting the issue number after a pound-sign: e.g., `#32`. For more details see GitHub's article [Autolink references and URLs](https://help.github.com/articles/autolinked-references-and-urls/). This cross-links the issue with the pull-request.


### Create and test a change

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Checkout your feature branch

    ```
    git checkout FEATURE_BRANCH
    ```

3. Make a small change using your standard development environment (e.g., Atom.io, Notepad++, Eclipse, etc.).

4. Test the change to make sure it works.

### Commit the change

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Checkout your feature branch

    ```
    git checkout FEATURE_BRANCH
    ```

3. Stage your changes.

    ```
    git add .
    ```

4. Confirm that only files that should be committed are staged.

    ```
    git status
    ```

5. If there are files staged that shouldn't be (e.g., anything that can be generated from source, personal/private configurations or data, etc.) see [Unstaging changes](#unstaging-changes).

6. Commit changes and provide a good commit messages.

    ```
    git commit -v
    ```


### Unstaging changes

Depending on which changes you want to unstage, do one of the following.

* Unstage all changes

    ```
    git reset HEAD
    ```

* Unstage all changes in a directory

    ```
    git reset HEAD -- PATH/TO/DIRECTORY
    ```

* Unstage individual files

    ```
    git reset HEAD -- FILE1 FILE2 ...
    ```

To avoid this problem in the future, do one of the following.

* Stage files individually from now on

    ```
    git add FILE1 FILE2
    git add FILE3
    ```

* Or edit `.gitignore` to forever ignore these files and stage again. See Atlassian's article on [.gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore).

    ```
    vim .gitignore      # use your favorite editor
    git add .
    ```


### Push changes in feature branch to your fork

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Push you changes in FEATURE_BRANCH to your fork.

    ```
    git push origin FEATURE_BRANCH
    ```

Notes:

- Any pull-requests associated with a branch are automatically updated when you push your changes to that branch.


### Merge master into feature branch

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Merge changes from master into your feature branch.

    ```
    git checkout FEATURE_BRANCH
    git merge master
    ```

3. If there were conflicts, follow GitHub's instructions for [Resolving a merge conflict using the command-line](https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/). Be sure to test your changes before committing them.

4. If there were no conflicts, just test the merged copy. If there are any problems, continue working on your feature until they are resolved.


### Request a review

When you think your pull-request is ready to be merged into the project's master, request a review from the maintainer by using an `@username` in a comment on the pull-request (see [Mention @somebody. They're Notified](https://blog.github.com/2011-03-23-mention-somebody-they-re-notified/)).

You might also want to review some of the spirit of communication on GitHub by reading [15 rules for communicating at GitHub](https://ben.balter.com/2014/11/06/rules-of-communicating-at-github/).


### Delete the feature branch

Don't do this until your pull-request has been merged, or you give up.

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Delete the feature branch from your local repository.

    ```
    git checkout master
    git branch -d FEATURE_BRANCH
    ```
    
    Note: if the last statement complains that the branch has not been merged, you may be trying to delete the wrong branch or the maintainer may have used a "merge" strategy that was not a merge at all. So first, check that you have the correct branch and that your pull-request for that branch has actually been merged. If so, and you are really, really, REALLY sure, then force the delete with a capital "D": `git branch -D FEATURE_BRANCH`.

3. Delete the feature branch from your fork.

    ```
    git push -d origin FEATURE_BRANCH
    ```


### Push changes in master to your fork

1. From the command-line, change into your clone's root directory.

    ```
    cd CLONES_ROOT
    ```

2. Push you changes in master to your fork.

    ```
    git push origin master
    ```


## Copyright and Licensing

Copyright 2018 Darci Burdge and Stoney Jackson SOME RIGHTS RESERVED

This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/ .