# Modified Git Flow
The Economist Digital Solutions Mobile Team uses [Git Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow) with the [Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) rather than forking.

## Feature branch workflow
The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the master branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch will never contain broken code, which is a huge advantage for continuous integration environments.

The Git Feature Branch Workflow is a composable workflow that can be leveraged by other high-level Git workflows.

Feature branches generally take the form of the jira ticket numbers. This allows Jira to record the history of the ticket and whether it has been merged and deployed.

(https://github.com/sandeepasrani/ds-best-coding-practices/blob/modified-git-flow/Deployment-Git.png)

## Gitflow Workflow
Gitflow is ideally suited for projects that have a scheduled release cycle.

Instead of a single master branch, this workflow uses two branches to record the history of the project. The master branch stores the official release history, and the develop branch serves as an integration branch for features. It's also convenient to tag all commits in the master branch with a version number.

Each new feature should reside in its own branch, which can be pushed to the central repository for backup/collaboration. But, instead of branching off of master, feature branches use develop as their parent branch. When a feature is complete, it gets merged back into develop by (Submitting a PR)[#####Submitting PR's]. Features should never interact directly with master.

#### Hotfix Branches
Hotfix branches arises from an unplanned state when critical issues in production code needs to be addressed immediately. Hotfix branch is branched off from master and must be merge back into development and master. Note that when hotfix branch is merged into master it becomes a new (hotfix) release that is pushed to production.

#### Commits
Create small, logical commits over large monolithic changes of codes. Git history is much more clear this way and git tools such as blame and bisect are less useful with large commits. It’s also a good practice to review your own commits before pushing them so unnecessary mistakes are prevented early.

Commit message subject should be short, not very short, informative, self explanatory and when someone look at it after time, it should be clear what has been done.

#### Submitting PR's
Each pull request has to be reviewed. All review comments should be added to the pull request by reviewer and addressed by developer who created pull request. When all comments are resolved, pull request and its associated feature branch can be merged into development branch.

Refer to [Peer Review](CODE_REVIEW.md) process.
