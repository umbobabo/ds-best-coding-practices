# Git Workflow

The Economist Digital Solutions teams use git for version control following the [Forking  Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow).

The advantage of the Forking Workflow is that contributions can be integrated without the need for everybody to push to a single central repository. Developers push to their own repositories, and only maintainer teams can push to the official repository. This allows  maintainers to accept commits from any developer without giving them write access to the official codebase. This approach scales easily and encourages sharing and collaboration on code bases across teams with minimal overhead required to manage merging and branching.

## Forking Workflow Overview

With the Forking Workflow every developer has their own private repository (fork) rather than working in a shared one. The developer will need to clone the shared main repository, usually hosted in the organisation account, to be able to open PRs from their personal repo against the main one. This means each developer has at least two git repositories for a single project: their fork and the main reposity.

## Setting Up Your Fork

When you're ready to collaborate on a project, rather than cloning the project, create a fork of the project. Github provide a link to create a Fork on the main page of the project's Github repo. This creates a personal version of the repo associated with your account only, where you can control who can push to it.

After creating your fork, clone it on your local machine. This serves as your private development environment, just like in other git workflows.

It is recommended you regularly pull the latest code from the main project into your fork. To do this, first add the project as an additional remote for your local project.

`git remote add upstream (upstream-github-url)`

You can review the remotes associated with your project by running:

`git remote -v`

Before making changes to your code, ensure you have the latest changes from the main project by doing a git pull from that remote.

`git pull upstream master`

If you've made commits to your local code and want to then incorporate changes in the main repo, you can use git rebase. With rebase, you can take all the changes that were committed on the main repo and replay them on another one into your local git history. This helps ensures there are no merge conflicts when you submit a pull request.

`git pull -r upstream master`


## Submitting PRs

The Forking Workflow typically follows a branching model. This means that complete feature branches will be purposed for merge into the original project's repository.

For feature development work tied to specific Jira stories, it is recommended to create a branch on your fork with the Jira ticket number in the branch. This automates integration between Jira and Github for tracking feature progress.

When your code is ready for review, push the local branch to your fork. In Github, submit a Pull Request comparing your fork's branch to the main repo's master branch. Once the code has gone through the full [Peer Review](CODE_REVIEW.md) process, it will be merged into the main repo's master branch.
