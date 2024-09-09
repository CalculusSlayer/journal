# Git Notes

Main documentation: https://git-scm.com/

This is a brief reference for git commands I found useful.
I will try to keep the most relevant commands near the top.


## Useful commands

### git restore

i use this to restore a particular file to a different version in a previous
(or sometimes in a future commit).

Examples of usage:

`git restore --source=HEAD main.py`

This command will change the file `main.py` in your working directory and update it
so it is same as the version capture by HEAD or in other words the commit pointer.
Also --source=HEAD is optional if you want to update with HEAD. It is more common
to use --source parameter when you want to change to something that is not head.

Ex:

`git restore --source=HEAD~2 apple.py` 

This updates apple.py in your working
directory so it matches apple.py from 2 commits
before the commit at HEAD.

`git restore --source={commit hash} {file name}`

Here is a more general form. Note you can type in the
full commit hash instead of doing HEAD~x. Also commit hashes
not in your git log but in git reflog are all fair game.

https://git-scm.com/docs/git-restore

### git reflog

`git reflog`

This command lets you see ALL commits you have made on your local repository,
even if they were written from git history from a git hard reset for example.

VERY POWERFUL command.

### 