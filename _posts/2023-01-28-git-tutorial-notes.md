---
title: "Course Notes: Git and GitHub"
date: 2023-01-28T18:30:00+05:30
toc: true
toc_label: "Notes"
---

This is the summary of what I learned from Kunal Kushwaha's YouTube Course on Git and GitHub, and a few extra notes taken while researching.

Kunal's Video:

{% include video id="apGV9Kg7ics" provider="youtube" %}

# What is Git?

[Git](https://git-scm.com/downloads) is a version control system for tracking changes in computer files and coordinating work on those files among multiple people. It is primarily used for source code management in software development, but it can be used to keep track of changes in any set of files. With Git, developers can review and manage revisions of their code, collaborate with others on a project, and easily merge contributions from multiple people. Other examples of a version control system: SVN.

# What is GitHub?

[GitHub](https://github.com/) is a web-based platform that uses Git for version control and source code management. It provides a centralized place for developers to store, share, and collaborate on software projects. GitHub offers a variety of features such as bug tracking, feature requests, task management, and wikis for documentation. It is also a social platform for developers, where they can follow their peers, discover new projects and contribute to open source software. It is widely used by developers and organizations around the world to host and review code, manage projects, and build software. Other examples: BitBucket.

# How are Git and GitHub different?

Git and GitHub are related but they are different things. Git is a version control system, a tool to manage your source code history. It's a command line tool, but there are also some graphical user interface for git like GitKraken, SourceTree etc.

GitHub is a web-based platform built on top of Git. It provides a frontend to the Git command-line tool, but also adds additional features such as a web-based interface for managing and reviewing code, access control, and collaboration tools like bug tracking, feature requests, and wikis for documentation.

In short, Git is a tool, GitHub is a service for projects that use Git. You can use Git without ever touching GitHub, but you can't use GitHub without using Git.

# Git Concepts

Here are some key concepts and commands for working with Git:

- __Repository__: A repository, or "repo" for short, is the place where all the files and their revisions are stored. You can have multiple repos on your local machine, and you can also connect to remote repos on GitHub or other Git hosting services.

- __Cloning__: To start working on a project, you first need to create a local copy of the repo. This is called "cloning" and it is done using the command `git clone <repo_url>`. This will create a new directory with the same name as the repo and copy all the files and their revision history into it.

- __Committing__: Once you have made changes to the files in your local repo, you need to save those changes. This is done by "committing" the changes. You can use `git add <file>` to stage the changes for commit and `git commit -m "message"` to commit the changes with a message describing the changes.

- __Pushing__: After committing your changes, you can push them to the remote repository by using the command `git push`. This will upload your commits to the remote repo, making them available for others to see and collaborate on.

- __Pulling__: To get the latest changes from the remote repository, you can use the command `git pull`. This will download the new commits and merge them with your local repo.

- __Branching__: Git allows you to create multiple branches of a repo, each with its own set of commits. This allows you to work on multiple features or fixes at the same time without interfering with each other. You can use `git branch <branchname>` to create a new branch and `git checkout <branchname>` to switch to that branch.

These are the basic concepts and commands of Git, but there are many more advanced features and options available. To learn more about Git, you can refer to the official documentation.

# Working with a Git Repository

## Initializing a Repository

In the terminal, navigate to the project directory and run `git init` command to initialize a Git Repository.

## Committing in a Repository

After making changes to the directory like adding/altering files etc. we run the `git status` command to view the changes. It shows the changes which are not recorded in the git’s history.

To put these files on the staging area, we run the `git add .` command in the project directory. You can also add only a particular file to the staging area e.g. `git add names.txt`

Now, if you check git status, you’ll see them in the staging area, waiting for it to be committed to the history.

To commit all the files from the staging area to the history we run the `git commit -m "message"` command. We can put a meaningful commit message to understand the project history easily. For eg. if we are creating a new *names.txt* file, we can put the commit message as “*added names.txt file*” 

Now, if you check git status again, you’ll see no files in the staging area, as the we have committed them.

To remove a certain file from the staging area, we can run the following command 
`git restore --staged names.txt` 

## To View Commit History

To view all the commits present in the history we can run the following command `git log`

## Reseting to an Older Commit

To reset your directory to a previous commit state, we run the following command with that commit’s hash ID. `git reset <hash_id>` For e.g the hash id is f12345 for a commit made two days ago, then the command will look like `git reset f12345` Now the directory will be reset to how it looked like two days ago. And all the commits after that time will be in the unstaged area.

## Git Stash

If you are currently working on something, but it is not ready for commit it, and you have another task come up, which requires a clean codebase, you can put the changed files to the staging area and stash them using the command `git stash` This will store the current status of the directory in the stash, and clean up the directory to the current commit. 

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/git-tutorial-notes/git-stash-image.png" alt="git-stash-terminal-screenshot">

To get those files back from the stash, you can do a `git stash pop` command and get them in the staging area.

To clear the stash, you can run `git stash clear` command. *(Note: if there are files in the stash, they will be permanently deleted.)*

# Using Git with GitHub

Login to GitHub and create a new repository or connect a current one to your current local git repository using the following command `git remote add origin <github_repo_url>` 

In the above command, we add a remote repository link and give it’s name as ‘*origin*’.

To get all the remote urls that are attached to your current repository, it can be viewed by the following command `git remote -v`

To copy the changes made in the local repository to the remote one, we run the command `git push origin master` here master is the branch name. In this command, we push our changes to the ‘*master*’ branch of the remote repository link named as ‘*origin*’

## Branching | Pull Requests | Forking

To create a new branch called ‘feature’ we use the command `git branch feature` 

HEAD is the one which holds the current active branch… for eg. the HEAD is pointing to the main branch, then all the subsequent commits will be added in main branch. But if we run the command `git checkout feature` the HEAD is then pointing to the feature branch, and all the subsequent commits will get added to the feature branch.

While you are working on the feature branch, commits may still happen on the main branch. To copy your current commits to the main branch, we run the command `git merge feature` to merge feature branch with the main branch.

While working with repositories created by other users, we need to first fork it to our account’s repositories to be able to make changes to the codebase. The fork will create an exact copy of the codebase in your account, and we can git clone it to our local system with the command 
`git clone <forked_repo_url>`

You can add the original repository (the repo from where you have forked it) to your local repositories configuration as an upstream remote repository link `git remote add upstream <upstream_repo_url>`

You can’t push to the upstream URL since you don’t have access to it.

You can push files to your feature branch using the command `git push origin feature`

It is always ideal to create a new branch for each bug or feature. If we create a single branch and push all the commits to it, there will be only a single pull request (associated with that branch) with all these different commits. It is very difficult to reveiw these many changes at once.

You can use force push if you want to overwrite the commits made in the remote repository using the command `git push origin feature -f` To elaborate further, for example, you mistakenly commited an erroneous file and pushed it to remote repository. In order to solve this situation, you can reset to an older commit, add the unstaged objects to the staging area and put them in the stash. Now, your tree is clean, and is pointing to an older commit, you want to push these changes to the remote repository, so you use the force push command to undo the erroneous commit from the remote repository.

If there are changes made in upstream repository, which are not synced in the forked repository, you have to manually update the forked repository. You can directly fetch upstream from GitHub, or you can follow these commands to update it from your local terminal. First, get the latest commits from all remote repositories using the command `git fetch --all --prune` (—all means all the branches, and —prune means all the deleted ones will also be fetched). Second, checkout to the main branch `git checkout main` and reset your local repository to the upstream/main repository using the command `git reset --hard upstream/main` Now, the commits from the upstream repository are visible in your local repository. You can push these changes to the forked repository using the command `git push origin main`

Another way to do the above things is using the git pull command `git pull upstream main` This will get the latest commits from the upstream main branch to your local repository. And then run `git push origin main` to sync the local repository with the forked repository. These two commands: git pull and git push will sync the upstream repository with the forked repository.

You can also learn more from here: [Learn Git Branching](https://learngitbranching.js.org/)

## Other Commands

### Squashing Commits

If you want to combine multiple commits into a single commit, we can use the rebase command. `git rebase -i <older_commit_id>` This will open all the commits made after the older commit id in an interactive text editor in terminal. Here you can replace ‘pick’ with ‘s’ to squash multiple commits into a single commit.

eg. Here the two ‘s’ commits will be squashed into the most recent ‘pick’ commit. (The cryptic number is the commit ID and the numbers at the right 1, 2, etc. are the commit messages.)

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/git-tutorial-notes/git-squash-image.png" alt="git-squash-terminal-screenshot">

### Merge Conflict

Merge conflicts occur when two branches have made changes to the same lines in a file, and Git is unable to automatically merge the changes. When this happens, you will need to manually resolve the conflict before you can complete the merge. Here's the general process for resolving merge conflicts in Git:

- Checkout the branch you want to merge into: Use the command `git checkout <branch>` to switch to the branch that you want to merge into. For example, if you want to merge changes from a branch called "feature" into your "master" branch, you would use `git checkout master`.

- Initiate the merge: Use the command `git merge <branch>` to initiate the merge. For example, if you want to merge changes from the "feature" branch into the "master" branch, you would use `git merge feature`.

- Resolve conflicts: If there are conflicts, Git will indicate which files have conflicts. You can use your preferred text editor to open the files and look for the conflict markers. You will need to manually edit the file to decide what changes to keep and what changes to discard.

- Add the resolved files: Once you've resolved the conflicts, use the command `git add <file>` to mark the file as resolved. This tells Git that you've made the necessary changes and are ready to continue with the merge.

- Complete the merge: Use the command `git commit` to complete the merge. You will be prompted to add a commit message, which should describe the changes that you've made to resolve the conflicts.

- Push the changes: Finally, use the command `git push` to push the changes to the remote repository. This will ensure that your collaborators are aware of the changes that you've made, and that they can merge the changes into their own branches.

# Commonly-Used Git Commands Summarized

- `git init`: This command is used to initialize a new Git repository. It creates a new subdirectory named .git that contains all of the necessary files for the repo, including the object database, the index file, and the HEAD pointer.

- `git status`: This command shows the current status of the repo, including which files have been modified, which files are staged for commit, and which branch you are currently on. It also shows any untracked files that are not being tracked by Git.

- `git add`: This command stages changes for commit. You can use git add <file> to stage specific files, or git add . to stage all changes in the current directory. Once changes are staged, you can use git commit to commit them.

- `git commit`: This command records changes to the repo. You need to specify a commit message with -m "message" to describe the changes you have made. The commit message should be in present tense and should summarize the changes made.

- `git log`: This command displays the commit history of the repo. It shows the SHA-1 hash, author, date and message of the commits in the repo.

- `git diff`: This command shows the differences between the working tree and the index or between two commits. It is useful to see the changes made before committing them.

- `git branch`: This command is used to create, list and delete branches. git branch will list all the branches in the repo and git branch <branchname> will create a new branch.

- `git checkout`: This command is used to switch between branches or commits. git checkout <branchname> will switch to that branch and git checkout <commit-SHA> will switch to a specific commit.

- `git merge`: This command is used to merge changes from one branch into another. It is typically used to combine changes made in a feature branch with the main branch.

- `git pull`: This command is used to fetch and integrate changes from a remote repository. It is a combination of git fetch and git merge.

- `git push`: This command is used to upload commits to a remote repository. It is typically used to share your changes with other collaborators.

# Advanced Git Commands Summarized

Here are some advanced Git commands that are less commonly used, but can be useful in certain situations:

- `git stash`: This command allows you to temporarily save changes that you have made to the working directory, but haven't committed yet. It is useful when you need to switch branches or pull in changes from the remote repository, but don't want to commit your changes first. You can use `git stash save "message"` to save your changes and `git stash apply` to apply them later.

- `git rebase`: This command allows you to modify the commit history of a branch. It is used to combine multiple commits into a single commit, or to change the order of commits. It can be used to make the commit history more readable and easier to understand.

- `git bisect`: This command is used to find the commit that introduced a bug. It works by binary search and you have to specify a "good" commit that does not have the bug, and a "bad" commit that does have the bug. Git will then automatically check out commits in the middle of the range, and you can use `git bisect good` or `git bisect bad` to mark them as good or bad until it finds the commit that introduced the bug.

- `git reflog`: This command shows a log of all the references that git has been aware of. It includes branch heads, tags, and other refs. It can be used to recover lost commits or branch heads that have been deleted by mistake.

- `git cherry-pick`: This command allows you to select specific commits from one branch and apply them to another branch. It is useful when you want to merge changes from one branch into another, but don't want to merge all of the commits.

- `git submodule`: This command allows you to include other Git repos within your repo. It is useful when you have a large project that depends on several smaller projects. You can use `git submodule add <repo_url>` to add a submodule and `git submodule update` to update all the submodules.

- `git filter-branch`: This command allows you to make changes to the entire history of a branch. It is useful when you need to remove sensitive data from a repo, or to change the author information of a commit.

Keep in mind that these commands can be dangerous to use if you are not familiar with them, as they can modify the commit history, which can cause conflicts with other collaborators and make it difficult to understand the history of the repository. It's always a good idea to create a backup copy of your repo before using these commands, and to consult the official documentation or ask for help from more experienced Git users.