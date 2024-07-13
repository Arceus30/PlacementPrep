# Git - GitHub

### [Basic Sheet](https://quickref.me/git)

### [GitHub](https://quickref.me/github)

### Version Control

-   tracking and managing software code changes, for eg: GIT, Piper(used by google), etc.
-   Commit functionality not entire code (Clean commit)

### [Git (Piyush Garg) Workflow](https://app.eraser.io/workspace/P96VaUsW5o0FXVOTDzHY)

-   A central server is used to store single source of truth, for eg: Github, Gitlab, BitBucket

### Branching

[Branching](https://youtu.be/LF-rK5yPzVM?t=1635&si=aLEOQW2Fhq5A-96H)

### Merge and Rebase

-   Merge: all the commits of a branch are squashed into a single commit and if any problem / issue arises entire commit or branch is reverted
-   Rebase: the latest commit from main branch is linked to the first commit of another branch and head moves to the last commit of the branch, the history is retained but commits are polluted

### stash

-   when changes in the local machine are not staged and some commits are made in the server, then git will not allow to pull the changes from the server to local machine until commit in local machine is not made
-   to overcome this problem stashing is done, changes are stored in a temporary file which can be applied after the changes from the server are pull
