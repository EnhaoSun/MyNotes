## Git Command

## git stash

git-stash - Stash the changes in a dirty working directory away

**SYNOPSIS**

```shell
git stash list [<options>]
git stash show [<options>] [<stash>]
git stash drop [-q|--quiet] [<stash>]
git stash ( pop | apply ) [--index] [-q|--quiet] [<stash>]
git stash branch <branchname> [<stash>]
git stash [push [-p|--patch] [-k|--[no-]keep-index] [-q|--quiet]
	     [-u|--include-untracked] [-a|--all] [-m|--message <message>]
	     [--] [<pathspec>…]]
git stash clear
git stash create [<message>]
git stash store [-m|--message <message>] [-q|--quiet] <commit>
```

`git stash pop` applies the top stashed element and removes it from the stack.

`git stash apply` does the same, but leaves it in the stash stack.

### rename a stash

Let's assume your stash list looks like this:

```
$ git stash list
stash@{0}: WIP on master: Add some very important feature 
stash@{1}: WIP on master: Fix some silly bug
```

First, you must remove stash entry which you want to rename:

```
$ git stash drop stash@{1}
Dropped stash@{1} (af8fdeee49a03d1b4609f294635e7f0d622e03db)
```

Now just add it again with new message using sha of commit returned after dropping:

```
$ git stash store -m "Very descriptive message" af8fdeee49a03d1b4609f294635e7f0d622e03db
```

And that's it:

```
$ git stash list
stash@{0}: Very descriptive message
stash@{1}: WIP on master: Add some very important feature
```



## git branch

If you want to rename a branch while pointed to any branch, do:

```
git branch -m <oldname> <newname>
```

If you want to rename the current branch, you can do:

```
git branch -m <newname>
```

Change the remote a branch is tracking

```
git branch branch_name --set-upstream-to(or -u) your_new_remote/branch_name
```

Check out remote branch

```shell
git checkout -b local_branch <name of remote>/test
```

Delete local branch

```bash
git branch -d <branch-name>
git branch -D <branch-name>		// Delete branch forcely
```

Delete remote branches

```bash
git push origin --delete <branch-name>
```



### remote





## git commit

Removing file from committed area requires 3 commands to be run, they are as follows-

```shell
git reset --soft HEAD~1
```

Above will undo the latest commit. if you do `git status` you will see files in the staging area. Now, we can easily remove it from staging area, as mentioned from previous point.

```shell
git rm --cached <file-name>
```

or remove files which has been added

```shell
git reset <file>
```

reset to a branch

```shell
git reset --hard origin/master
```

