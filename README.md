# Git and Git Flow Cheat Sheet

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Git cheat sheet saves you from learning all the commands by heart.

Be free to contribute, update the grammar mistakes. You are also free to add
your language file.

## Git Cheat Sheet English

### Index

* [Set Up](#setup)
* [Configuration Files](#configuration-files)
* [Create](#create)
* [Local Changes](#local-changes)
* [Search](#search)
* [Commit History](#commit-history)
* [Move / Rename](#move--rename)
* [Branches & Tags](#branches--tags)
* [Update & Publish](#update--publish)
* [Merge & Rebase](#merge--rebase)
* [Undo](#undo)
* [Git Flow](#git-flow)

-------------------------------------------------------------------------------

## Setup

### Show current configuration

```console
git config --list
```

### Show repository configuration

```console
git config --local --list
```

### Show global configuration

```console
git config --global --list
```

### Show system configuration

```console
git config --system --list
```

### Set a name that is identifiable for credit when review version history

```console
git config --global user.name "[firstname lastname]"
```

### Set an email address that will be associated with each history marker

```console
git config --global user.email "[valid-email]"
```

### Set automatic command line coloring for Git for easy reviewing

```console
git config --global color.ui auto
```

### Set global editor for commit

```console
git config --global core.editor vi
```

-------------------------------------------------------------------------------

## Configuration Files

### Repository specific configuration file [--local]

```console
<repo>/.git/config
```

### User-specific configuration file [--global]

```console
~/.gitconfig
```

### System-wide configuration file [--system]

```console
/etc/gitconfig
```

-------------------------------------------------------------------------------

## Create

### Clone an existing repository

There are two ways

Via SSH

```console
git clone ssh://user@domain.com/repo.git
```

Via HTTP

```console
git clone http://domain.com/user/repo.git
```

### Create a new local repository in the current directory

```console
git init
```

### Create a new local repository in a specific directory

```console
git init <directory>
```

-------------------------------------------------------------------------------

## Local Changes

### Changes in working directory

```console
git status
```

### Changes to tracked files

```console
git diff
```

### See changes/difference of a specific file

```console
git diff <file>
```

### Add all current changes to the next commit

```console
git add .
```

### Add some changes in &lt;file&gt; to the next commit

```console
git add -p <file>
```

### Add only the mentioned files to the next commit

```console
git add <filename1> <filename2>
```

### Commit all local changes in tracked files

```console
git commit -a
```

### Commit previously staged changes

```console
git commit
```

### Commit with message

```console
git commit -m 'message here'
```

### Commit skipping the staging area and adding message

```console
git commit -am 'message here'
```

### Commit to some previous date

```console
git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

### Change last commit

*Don't amend published commits!*

```console
git commit -a --amend
```

### Amend with last commit but use the previous commit log message

*Don't amend published commits!*

```console
git commit --amend --no-edit
```

### Change committer date of last commit

```console
GIT_COMMITTER_DATE="date" git commit --amend
```

### Change Author date of last commit

```console
git commit --amend --date="date"
```

### Move uncommitted changes from current branch to some other branch

```console
git stash
git checkout branch2
git stash pop
```

### Restore stashed changes back to current branch

```console
git stash apply
```

### Restore particular stash back to current branch

* *{stash_number}* can be obtained from `git stash list`

```console
git stash apply stash@{stash_number}
```

### Remove the last set of stashed changes

```console
git stash drop
```

-------------------------------------------------------------------------------

## Search

### A text search on all files in the directory

```console
git grep "Hello"
```

### In any version of a text search

```console
git grep "Hello" v2.5
```

### Show commits that introduced a specific keyword

```console
git log -S 'keyword'
```

### Show commits that introduced a specific keyword (using a regular expression)

```console
git log -S 'keyword' --pickaxe-regex
```

-------------------------------------------------------------------------------

## Commit History

### Show all commits, starting with newest (it'll show the hash, author information, date of commit and title of the commit)

```console
git log
```

### Show all the commits(it'll show just the commit hash and the commit message)

```console
git log --oneline
```

### Show all commits of a specific user

```console
git log --author="username"
```

### Show changes over time for a specific file

```console
git log -p <file>
```

### Display commits that are present only in remote/branch in right side

```console
git log --oneline <origin/master>..<remote/master> --left-right
```

### Who changed, what and when in &lt;file&gt;

```console
git blame <file>
```

### Show Reference log

```console
git reflog show
```

### Delete Reference log

```console
git reflog delete
```

-------------------------------------------------------------------------------

## Move / Rename

### Rename a file

Rename Index.txt to Index.html

```console
git mv Index.txt Index.html
```

-------------------------------------------------------------------------------

## Branches & Tags

### List all local branches

```console
git branch
```

#### List local/remote branches

```console
git branch -a
```

### List all remote branches

```console
git branch -r
```

### Switch HEAD branch

```console
git checkout <branch>
```

### Checkout single file from different branch

```console
git checkout <branch> -- <filename>
```

### Create and switch new branch

```console
git checkout -b <branch>
```

### Switch to the previous branch, without saying the name explicitly

```console
git checkout -
```

### Create a new branch from an exiting branch and switch to new branch

```console
git checkout -b <new_branch> <existing_branch>
```

#### Checkout and create a new branch from existing commit

```console
git checkout <commit-hash> -b <new_branch_name>
```

### Create a new branch based on your current HEAD

```console
git branch <new-branch>
```

### Create a new tracking branch based on a remote branch

```console
git branch --track <new-branch> <remote-branch>
```

### Delete a local branch

```console
git branch -d <branch>
```

### Rename current branch to new branch name

```console
git branch -m <new_branch_name>
```

### Force delete a local branch

*You will lose unmerged changes!*

```console
git branch -D <branch>
```

### Mark `HEAD` with a tag

```console
git tag <tag-name>
```

### Mark `HEAD` with a tag and open the editor to include a message

```console
git tag -a <tag-name>
```

### Mark `HEAD` with a tag that includes a message

```console
git tag <tag-name> -am 'message here'
```

### List all tags

```console
git tag
```

### List all tags with their messages (tag message or commit message if tag has no message)

```console
git tag -n
```

-------------------------------------------------------------------------------

## Update & Publish

### List all current configured remotes

```console
git remote -v
```

### Show information about a remote

```console
git remote show <remote>
```

### Add new remote repository, named &lt;remote&gt;

```console
git remote add <remote> <url>
```

### Rename a remote repository, from &lt;remote&gt; to &lt;new_remote&gt;

```console
git remote rename <remote> <new_remote>
```

### Remove a remote

```console
git remote rm <remote>
```

*Note: git remote rm does not delete the remote repository from the server. It
simply removes the remote and its references from your local repository.*

### Download all changes from &lt;remote&gt;, but don't integrate into HEAD

```console
git fetch <remote>
```

### Download changes and directly merge/integrate into HEAD

```console
git remote pull <remote> <url>
```

### Get all changes from HEAD to local repository

```console
git pull origin master
```

### Get all changes from HEAD to local repository without a merge

```console
git pull --rebase <remote> <branch>
```

### Publish local changes on a remote

```console
git push <remote> <branch>
```

### Delete a branch on the remote

```console
git push <remote> :<branch> (since Git v1.5.0)
```

OR

```console
git push <remote> --delete <branch> (since Git v1.7.0)
```

### Publish your tags

```console
git push --tags
```

-------------------------------------------------------------------------------

### Configure the merge tool globally to meld (editor)

```consolebash
git config --global merge.tool meld
```

### Use your configured merge tool to solve conflicts

```console
git mergetool
```

## Merge & Rebase

### Merge branch into your current HEAD

```console
git merge <branch>
```

### List merged branches

```console
git branch --merged
```

### Rebase your current HEAD onto `<branch>`

*Don't rebase published commit!*

```console
git rebase <branch>
```

### Abort a rebase

```console
git rebase --abort
```

### Continue a rebase after resolving conflicts

```console
git rebase --continue
```

### Use your editor to manually solve conflicts and (after resolving) mark file as resolved

```console
git add <resolved-file>
```

```console
git rm <resolved-file>
```

### Squashing commits

```console
git rebase -i <commit-just-before-first>
```

Now replace this,

```console
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

to this,

```console
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

-------------------------------------------------------------------------------

## Undo

### Discard all local changes in your working directory

```console
git reset --hard HEAD
```

### Get all the files out of the staging area(i.e. undo the last `git add`)

```console
git reset HEAD
```

### Discard local changes in a specific file

```console
git checkout HEAD <file>
```

### Revert a commit (by producing a new commit with contrary changes)

```console
git revert <commit>
```

### Reset your HEAD pointer to a previous commit and discard all changes since then

```console
git reset --hard <commit>
```

### Reset your HEAD pointer to a remote branch current state

```console
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

### Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes

```console
git reset <commit>
```

### Reset your HEAD pointer to a previous commit and preserve uncommitted local changes

```console
git reset --keep <commit>
```

### Remove files that were accidentally committed before they were added to .gitignore

```console
git rm -r --cached .
git add .
git commit -m "remove xyz file"
```

-------------------------------------------------------------------------------
