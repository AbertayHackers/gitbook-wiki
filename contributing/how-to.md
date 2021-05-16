---
description: Guide to contributing to the wiki via Github
---
# How to Contribute

You will need a Github account and a place where you can use git.

First you need to fork the repo, clone it, then synchronise it with the main repo:

1. Create a fork of the [main repository](https://github.com/AbertayHackers/gitbook-wiki)
2. Clone your fork: `git clone https://github.com/[username]/gitbook-wiki`
3. Add the main repo as an upstream remote: `git remote add --track master upstream https://github.com/AbertayHackers/gitbook-wiki`

Before you make any changes, you should always synchronise your fork to the remote repository:

1. Pull the remote changes to your local upstream branch: `git fetch upstream`
2. Merge those changes with your local master branch: `git merge upstream/master`

With this done, you can now edit or add wiki files.
Once you've made the changes, you'll need to commit them, push them, then create a pull request:

1. Add the changed files: `git add [files u changed, or a wildcard, or a folder]`
2. Commit the changes locally: `git commit -m "description of the changes you've made"`
3. Push the changes to your fork on Github: `git push`
4. Finally, go to https://github.com/[username]/gitbook-wiki/pulls and open a pull request to request that your changes be added to the site.
