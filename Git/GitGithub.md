# Git - GitHub

#### 1. [Basic Sheet](https://quickref.me/git)

#### 2. [GitHub](https://quickref.me/github)

#### 3. Version Control

-   tracking and managing software code changes, for eg: GIT, Piper(used by google), etc.
-   Commit functionality not entire code (Clean commit)

#### 4. [Git (Piyush Garg) Workflow](https://app.eraser.io/workspace/P96VaUsW5o0FXVOTDzHY)

-   A central server is used to store single source of truth, for eg: Github, Gitlab, BitBucket

#### 5. Branching

[Branching (Youtube)](https://youtu.be/LF-rK5yPzVM?t=1635&si=aLEOQW2Fhq5A-96H)

#### 6. Merge and Rebase

-   Merge: all the commits of a branch are squashed into a single commit and if any problem / issue arises entire commit or branch is reverted
-   Rebase: the latest commit from main branch is linked to the first commit of another branch and head moves to the last commit of the branch, the history is retained but commits are polluted

#### 7. stash

-   when changes in the local machine are not staged and some commits are made in the server, then git will not allow to pull the changes from the server to local machine until commit in local machine is not made
-   to overcome this problem stashing is done, changes are stored in a temporary file which can be applied after the changes from the server are pull
