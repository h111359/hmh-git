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