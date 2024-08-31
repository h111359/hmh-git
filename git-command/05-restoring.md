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

#### Return to a previous commit in a Git repository and discard all changes made after that commit,

git log --oneline
git reset --hard <commit-hash>
git push origin HEAD --force
