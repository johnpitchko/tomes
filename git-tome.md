# Tome of Git

## Update .gitignore

Easy enough; just edit the `.gitignore` file and make any relevant changes to add/remove file from tracking. 

However, if you add a file/directory that already exists and is being tracked (i.e. was previously committed), you will need to remove it from tracking. For a single file:

```
$ git rm — cached filename
```

To remove a directory (and the contents within the directory):

```
$ git rm -r —cached directory
```

To flush the whole cache:

```
$ git rm -r —cached .
```

You must then add and commit these changes:

```
$ git add .; git commit -m “.gitignore flushed”
```

## Update/checkout from remote repo

1. Fetch all the references from remote repo ` $ git fetch`
2. Checkout the file/directory from the remote repo `$ git checkout origin/master path/to/file`

## GIT BRANCH

### Deleting branches

To delete a local branch:
```
git branch -d <branch name>
```

To delete a remote branch:

```
git push -d <remote_name> <branch_name>
```

## GIT STASH

Temporarily save/stash altered, unstaged files so they will not be lost when switching branches. Stash *will not* save untracked files.

### Stash altered files

```
$ git stash
```

Equivalent of `git stash push`

## GIT DIFF

Compare two files and highlight differences.

### Compare files between two branches.

```
$ git diff <branch> <other branch> -- <filename>
``` 

### Squashing commits

1. Determine how many commits to squash. Run this command to generate a pretty graph of your commit history:

```
git log --graph --decorate --pretty=oneline --abbrev-commit
```

You will want to find the SHA for the _commit before the one you want to squash to_. This will usually be the most recent merge/branch, or HEAD.

2. Run an interactive rebase command specifying the SHA of the commit identified in the above step.

```
$ git rebase -i <SHA>
```

Running the command will open your default text editor listing the commit hashes and messages for the commits you will be squashing. Review to ensure you will squash all the commits that you intend to.

3. Change the word `pick` to `squash` for all the commits that need to get squashed. The `squash` command informs git to combine that commit with the one above. _The first commit should retain the `pick` command._ Save and close your editor. The editor will open again showing all the commit messages.

4. Input the message for the squashed commit.

### Rebase vs Merge

* Both integrate changes from one branch to another.
* Merging is non-destructive; existing branches are unchanged.
* Consequences for the future - impacts future commits because of extraneous merge commit - can be a challenge if there is *lots* of activity in `master`; history can look goofy
* Rebase moves entire feature branch to tip of `master`, creating a cleaner project history.
* Golden rule of rebase: **DO NOT USE ON PUBLIC BRANCHES!!**

# Undoing History (git revert, git reset)

### Revert vs Reset

`git revert` calculates what portions of files need to be changed in order to *revert* them to the previous version.

`git reset` wipes out changed files completely and restores the previous version.

### Undoing a pushed commit

```
git reset --hard HEAD~1
git push -f <remote> <branch>
```
