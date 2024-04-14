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