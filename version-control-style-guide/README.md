p
# Version control style guide


## Overview

This document describes a method of versioning source code using `git`.


## Branching

There are *remote* and *local* branches. Remote branches are in the remote repository (i.e. GitHub), local branches only exist on your local machine.

The remote `master` is **append only**. This means that commits in `master` can not, under any circumstance, be rewritten. Doing so will bring others in trouble when they rebase their feature branches on top of `master`.


### Keeping your branches up-to-date

It is important to keep your local branches up-to-date. Ofcourse, it is possible to update your local branch when you have finished completing a task. However, this will increase the number of commits that need to be diff'ed, and also potentially more merge conflicts. To make life easier it is a good practice to update your feature branch every day, and when someone notifies you that master has been updated.

To update your branch with the latest version of the remote master you can issue the following command:

`git remote update && git rebase origin/master`


## Merge conflicts

It is natural that a merge conflict might occur when rebasing a feature branch on top of master. A merge conflict means that `git` was not able to automatically apply a commit.

When this happens, `git` will stop rebasing and you will have to manually correct the conflict. Issue a `git diff` command to find out in which files there are conflicts. This will show you the files where merge conflicts have occurred. If you keep your commits atomic and as small as possible, it shouldn't be a lot of work to resolve. Below is an example of a merge conflict:

```
<<<<<<< HEAD:mergetest
This is my third line
=======
This is a fourth line I am adding
>>>>>>> 4e2b407f501b68f8588aa645acafffa0224b9b78:mergetest
```

The upper part (separated by `======`) represents the **last** commit that was succesfully applied. The lower part is the commit that could not be applied automatically.

After you have resolved the merge conflict, add the file using ``git add -u`` and check for more conflicts using ``git diff`. Continue the rebase with ``git rebase --continue``.

> `git add -u` stages all updated files for commit. The above example assumes that you have
> **only** edited files that contained merge conflicts.


## Commits

### Commit messages

-	To keep an overview of which commits belong to a single feature, prefix the commit
	message with the issue identifier in lowercase because it saves you typing (discuss).




## Rebasing

A drawback of rebasing (versus merging) is that it is not immediately clear which commits are related to each other. This challenge can be solved by prefixing each commit message with an identifier, such are the JIRA issue to which it is related (discuss).

### What happens when you rebase

It should under normal circumstances not be necessary to rebase on any other branch than `origin/master`.


### How to rebase

To rebase your feature branch on master, issue the following command:

`git remote update && git rebase -i origin/master`

This will open your favorite editor, showing a list of all commits that are in the feature branch but not in master:

> You can configure the editor that git uses by setting the `EDITOR` environment variable (e.g. `export EDITOR=vi`). To make
> this preference permanent, you can add the `export` in your bash profile (`~/.bash_profile` for OSX users). The bash
> profile is executed every time a terminal is launched.

```
pick ef9e602 Add Makefile
pick ff44885 Add script to run nosetests with Django env
pick 54ef499 Add LatLon module as a dependency
pick a672439 Add utils module
pick 1a650bb Add mock TravelMatrix client
pick 93f0c5b Comment out the test server test cases
pick b114d75 Use mock client instead of live one.
pick 88a2ee5 Use assertGreater() in test_generator_arrive()
pick 50e0454 Use assertGreater() in test_generator_depart()
```

Each line represents a single commit and consists of three parts: an operation, the commit hash and the commit message. Note that this is an **ordered** list. Git will apply the commits in the order defined here.

The operation (by default `pick`) instructs git what it should do during rebasing. If you remove a line, the commit is not included in the rebased feature branch. You can alternatively specify `drop` instead of `pick` to remove commits.

### Rewriting commits





## Useful software to install

- `tig`, a command-line client to view the version control history.
