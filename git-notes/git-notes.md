# Git Notes

Main documentation: https://git-scm.com/

This is a brief reference for git commands I found useful.
I will try to keep the most relevant commands near the top.

## Useful commands

### [git reflog](https://git-scm.com/docs/git-reflog)

This command lets you see ALL commits you have made on your local repository,
even if they were written from git history from a git hard reset
or git restore for example.

`git reflog`

***VERY POWERFUL command.***

***

### [git restore](https://git-scm.com/docs/git-restore)

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

***

### [git mv](https://git-scm.com/docs/git-mv)

This is a powerful command that allows you to
rename a file or folder without lose git history
associated with it*.

* \*Git difftool may start acting up once you run this
(git diff works no problem). So instead after this you
might have to rely on the git lens vscode extension
or try:   `git difftool --find-renames`. This command
forces git to find the renames and correctly map
the same files.

`git mv {previous name} {new name}`

After running this command, the file/directory will be staged and
ready to be committed for the next commit.

***

### [git rm](https://git-scm.com/docs/git-rm)


`git rm {file name}`

This is a command used to remove file/directory
from both your remote repository and working directory

In order to remove from the remote directory but not
from your working directory, do:

`git rm --cached {file name}`

The above effectively allowed you to remove something you
accidentally pushed to remote. After running this,
the deleted file will be staged and ready to be committed.

***

### [git reset](https://git-scm.com/docs/git-reset)

**TODO:** Add more documentation here regarding the specific commands and examples.

There are 3 different types or reset you can do:
1) soft: leaves working directory untouched, leaves index untouched, moves commit pointer to whatever specified
2) mixed: leaves working directory untouched, clears index, moves commit pointer to whatever specified
3) hard: changes working directory, clears the index, moves commit pointer to whatever specified

***

### [git difftool](https://git-scm.com/docs/git-difftool)
**TODO**: 
- Add example commands
- Add instructions on how to set up

This commands opens up a visual tool so you can compare
different commits. It is basically the GUI version
of `git diff`.

You may have to do some setup prior to using this.

***

### [git mergetool](https://git-scm.com/docs/git-mergetool)
**TODO**: 
- Add example commands
- Add instructions on how to set up

This command opens up a visual tool so you can safely
merge different branches and hopefull solve your
merge conflict. It is basically the GUI version
of `git merge`.

You may have to do some setup prior to using this.

***

### [git checkout](https://git-scm.com/docs/git-checkout)

Git checkout is for creating/switching to different branches in your repository.

Ex: `git checkout -b feature_branch`

This commands creates a new branch called "feature_branch" and switches over to it.

`git checkout feature_branch2`

This command on the other hand switches to the branch called "feature_branch2" only
if it exists. If it does not exist, an error will be thrown.

`git checkout --detached {commit hash}`

This command switches to a new branch in a "detached state". Basically changes and commits
will not be saved once you exit this branch. It is used for quickly checking something out.

***

### [git stash](https://git-scm.com/docs/git-stash)

The `git stash` command is used to temporary throw away dirty code temporarily and
later recover if needed.

`git stash push -- {name of file} -m {commit message}`

This version of the command for example stashes just one file and has a specific commit message.

`git stash pop "{stash id}"`

This command applies version of the file/files onto your working directory and
pops from stack.

`git stash apply "{stash id}"`

This command also applies version of the file/files onto your working directory
but does not pop from the stack.

`git stash list`

This command is used to see all your stashes in your local repository.

***

## Notes

### 3 similar commands: git-revert, git-restore, git-reset

`git revert` is about making a new commit that reverts the changes made by other commits.

`git restore` is about restoring files in the working tree from either the index
or another commit

`git reset` is about updating your branch, moving the commit pointer in to add or remove
commits from the branch. This operation changes the commit history.

https://stackoverflow.com/questions/58003030/what-is-git-restore-and-how-is-it-different-from-git-reset

## Resources

Official git book: https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository