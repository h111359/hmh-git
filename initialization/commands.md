# Git

## Contents

- [Git](#git)
  - [Contents](#contents)
  - [Concepts](#concepts)
  - [Setup](#setup)
  - [Initialization](#initialization)
    - [Create a simple file in a folder](#create-a-simple-file-in-a-folder)
    - [Create a new repository on the command line](#create-a-new-repository-on-the-command-line)
  - [Differences](#differences)
  - [Branching](#branching)
    - [List branches](#list-branches)
    - [Create branch](#create-branch)
    - [Merge branches](#merge-branches)
    - [Renaming a local branch](#renaming-a-local-branch)
    - [Remove branch](#remove-branch)
      - [Remove local branch](#remove-local-branch)
      - [Remove the remote branch](#remove-the-remote-branch)
  - [Remote repo](#remote-repo)
      - [Add remote repo to your local repo](#add-remote-repo-to-your-local-repo)
      - [Pushing changes](#pushing-changes)
    - [Renaming files](#renaming-files)
    - [Remove file](#remove-file)
  - [Restore previous versions](#restore-previous-versions)
    - [Restore file in the Working directory](#restore-file-in-the-working-directory)
    - [Unstage files](#unstage-files)
    - [Change the title of the last commit](#change-the-title-of-the-last-commit)
    - [Restore from a previous commit](#restore-from-a-previous-commit)
      - [A specific file](#a-specific-file)
      - [The whole commit](#the-whole-commit)


## Concepts

Git maintains 3 file trees:

- Working - whatever is in the folder currently
- Staging - prepared to be staged
- Repository - the repo itself

## Setup

Get help

    git help
    git help log

System level

    git config --system

User level

    git config --global

Local/project level

    git config

List the configurations:

    git config --system --list
    git config --global --list
    git config --list
    git config user.name
    git config user.email


## Initialization

### Create a simple file in a folder

    echo "# bookmarks" >> README.md

### Create a new repository on the command line

    git init
    git add *
    git commit -m "first commit"


If you want directly to commit, skipping the staging phase:

    git commit -a -m "message"
    git commit -am "message"

See the commits

    git log

See more condensed list of the commits (more useful):

    git log --oneline

Limit the output

    gir log -n 5
    git log --since=2024-01-25
    git log --until=2024-01-25
    git log --author="Hr"
    git log --grep="Init"


Check what's the current state:

    git status

## Differences

Changes in the working tree not yet staged for the next commit.

    git diff

Changes between the index and your last commit; what you would be committing if you run git commit without -a option.

    git diff --staged
    git diff --cached   

Changes in the working tree since your last commit; what you would be committing if you run git commit -a

    git diff HEAD 


To see the exact words changed:

    git diff --color-words


See what's the content of a specific commit:

    git show <xxxxx - the begining of the SHA>


To see the exact words changed:

    git diff --color-words

## Branching

### List branches

To list local branches:

    git branch

To list all local and remote branches:

    git branch -a

### Create branch

    git switch -c new-branch

### Merge branches

If we want to merge another branch in the current branch:

    git merge another-branch

### Renaming a local branch

  1. Rename the local branch

    git branch -m old_branch new_branch

   2. (If needed) Forcefully rename the current branch to "new_branch". If "new_branch" branch exists, it will be overwritten.

    git branch -M new_branch

  3. After renaming locally, the branch should be renamed on the origin. To do that, first delete the old named branch on the origin and then push the new one:

    git push origin --delete old_branch

  4. Push the new branch and at the same time set the upstream reference to the remote branch 

    git push origin -u new_branch


### Remove branch

#### Remove local branch

    git branch -D gh-pages

#### Remove the remote branch

    git push origin -d gh-pages

## Remote repo

#### Add remote repo to your local repo

---

    git remote add origin https://github.com/h111359/bookmarks.git

---

The command git remote add origin <https://github.com/xxxx/yyyy.git> is used in Git to add a new remote repository to your local Git repository. Here's a breakdown of each part of the command:

- git remote add: This is the Git command used to add a new remote reference to your local repository. A "remote" in Git is essentially a version of your repository that is hosted on the internet or network somewhere, which allows you to push to (upload) and pull from (download).

- origin: This is the conventional name given to the default remote server in Git. It's essentially an alias that allows you to refer to the remote server's URL more conveniently. "Origin" is not mandatory; it's just a widely adopted convention. However, you could name it anything you prefer (e.g., "upstream", "central", etc.), but "origin" is standard when you're talking about the primary remote repository.

- https://github.com/rrrrr/pppppp.git: This is the URL of the remote repository. In this case, it's a GitHub repository URL. This URL is what Git will use to communicate with the remote repository, enabling operations like git push, git pull, and git fetch.

#### Pushing changes

Push the branch main:

    git push origin -u main

Push all branches:

    git push --all

Take the last state from the remote:

    git fetch origin


### Renaming files

    git mv old_name new_name

### Remove file

The following command deletes the file from the Working directory and adds it in the staging.

    git rm file_to_delete.txt


## Restore previous versions

### Restore file in the Working directory

Undo Working directory changes. It uses chekout command, so we need to tell Git to use the current branch so we put "--" after the word chekout

    git chekout -- my_file

### Unstage files

To move file from Stage back to Working tree

    git reset HEAD file_to_reset


Git reset is a command, which changes to what commit the head of the branch is pointing and updating Stage and Working trees depending on the mode the reset command is set to work. Modes are:
- --hard: replaces both Stage and Working trees with the content of the new commit
- --mixed: replaces only Stage with the content of the new commit. This will cause git status to return all the changes between the Working and the new commit.
- --soft: no replacement is done in Stage and Working. This will cause git status to return all changes between the Working and the new commit as added for committing.

### Change the title of the last commit

To change the last commit. It takes all in the Repo and write it back to Staging, take whatever is in the Staging also and creates a new commit on the place of the previous one.

    git commit --amend -m "New message"

### Restore from a previous commit

#### A specific file

Restore a file from a specific commit in the past. let say the SHA of the commit we want to take the file is 0c307af2b9da52a112863b8b45a6b9ca7d61fa44 and we want to take the state of file commands.md

    git checkout 0c307af2b -- commands.md

The -- here presents that we keep working in the current branch. The file commands.md will be restored accoridingly to the commit stated + it will be saved in staging as well

#### The whole commit

If we want to revert the state of older commit, we will use git revert. This will create a new commit with the state of the commit with the provided SHA

    git revert 06327fb