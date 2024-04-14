# Git

## Contents

- [Git](#git)
  - [Contents](#contents)
  - [Concepts](#concepts)
  - [Setup](#setup)
  - [Initialization](#initialization)
    - [Create a simple file in a folder](#create-a-simple-file-in-a-folder)
    - [Create a new repository on the command line](#create-a-new-repository-on-the-command-line)


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


