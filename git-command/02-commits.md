## Stage

    git add .

## Commit

    git commit -m "Message"


If you want directly to commit, skipping the staging phase:

    git commit -a -m "message"
    git commit -am "message"

## Logs

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





