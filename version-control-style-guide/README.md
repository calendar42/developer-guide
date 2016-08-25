# Version control style guide

## Branching

The remote `master` is **immutable**. This means that commits in `master` can not, under any circumstance, be rewritten.

## Commits


## Rebasing

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

Each line represents a single commit and consists of three parts: an operation, the commit hash and the commit message.

The operation (by default `pick`) instructs git what it should do during rebasing. If you remove a line, the commit is not included in the rebased feature branch. You can alternatively specify `drop` instead of `pick` to remove commits.








A drawback of rebasing (versus merging) is that it is not immediately clear which commits are related to each other. This challenge can be solved by prefixing each commit message with an identifier, such are the JIRA issue to which it is related.

## Useful software to install

- `tig`, a command-line client to view the version control history.
