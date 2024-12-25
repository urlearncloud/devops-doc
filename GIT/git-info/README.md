## VCS (Version Control System)


A Version Control System (VCS) is a software tool that helps manage and track changes to files, especially source code. 

VCS enables multiple people to work on the same project simultaneously, while keeping a record of every change made to the project over time. 



## Why Version Control is Important


#### Collaboration :- 

In team environments, developers and other stakeholders may work on the same files simultaneously.

VCS allows each individual to work on their own part of the project without conflicting with others' work.


#### Track Changes :- 

VCS provides a history of changes made to the project. 

This allows developers to view who made a change, what the change was, and when it occurred.

#### Undo Changes :- 

If a mistake is made, a VCS allows developers to revert to an earlier version of a file or the entire project, avoiding the loss of work.

#### Branching and Merging :- 

VCS allows the creation of branches, so developers can work on new features or fixes without affecting the main project. 

These branches can later be merged back.

#### Backup :- 

The VCS keeps a record of all versions, providing a backup for projects. 

In case of an issue (such as data corruption or accidental deletion), previous versions can be restored.



## Types of Version Control Systems

There are three primary types of version control systems :

#### Local Version Control Systems :-

In this type, version history is stored locally on a single machine, usually as a set of files that are copied each time a change is made. 

While simple, this setup does not facilitate collaboration, as there’s no shared central repository.

Example: RCS (Revision Control System).


#### Centralized Version Control Systems (CVCS) :-

In a CVCS, there is a central server that holds the repository, and every user gets their own working copy of the project from the central repository. 

Changes are recorded and synchronized with the central server, if the central server goes down, access to the repository is lost.

Example: Subversion (SVN), Perforce.

Advantages : Easier to manage, less storage required on individual machines, all users are aware of the repository status.

Disadvantages : Dependency on the central server, potential downtime if the server fails.


#### Distributed Version Control Systems (DVCS) :-

In a DVCS like Git, each developer has a complete local copy of the entire repository, including its history. 

This means that developers can work offline and only need to sync with the remote repository when necessary.

The distributed nature ensures that even if the central repository is lost, any of the local repositories can serve as a full backup.

Examples: Git, Mercurial.

Advantages : Full history on each local machine, supports offline work, faster due to local repositories.

Disadvantages : Can lead to redundant storage of data, more complex to manage and set up compared to CVCS



## Git

Git is a distributed version control system created by Linus Torvalds in 2005 for managing the development of the Linux kernel. 

It is one of the most popular VCS tools due to its powerful features, flexibility, and speed. 

Git allows multiple people to collaborate on a project, manage large codebases efficiently, and handle changes with ease.

Some key features of Git include :

#### Local repositories :- 

Every user has a full local copy of the repository, making Git fast and reliable even when offline.

#### Branching and Merging :- 

Git allows you to easily create branches (separate lines of development) and later merge them, helping with experimentation and collaboration.

#### Commit history :-

Git stores a history of all commits (changes), making it easy to revert to earlier versions or view the evolution of a project.

#### Distributed model :- 

Every user can work independently on their copy, with changes later synchronized (pushed/pulled) to a shared repository (often hosted on services like GitHub, GitLab, or Bitbucket).



## Git Life cycle


Git tracks changes through a series of steps, and understanding this workflow is essential for mastering version control with Git.

Here's a detailed breakdown of the Git lifecycle :

#### 1. Working Directory (Untracked or Modified)

This is where you start with your files on your local machine. 

When you first create or clone a repository, you have a working directory where all of your project files reside.

Untracked Files : Files that are present in your working directory but are not yet being tracked by Git. These are files that have not been added to the Git repository.

Modified Files : These are files that are already being tracked by Git but have been changed since the last commit. Git recognizes these as modified, but they are not yet saved (committed) to the repository.

Example :-

You create a new file, index.html. This file is untracked by Git.

You edit an existing file, style.css. This file is modified because it already exists in the repository.

#### 2. Staging Area (Index)

The staging area (also called the index) is a temporary storage area where changes are prepared before being committed to the repository. 

When you decide you want to track changes and commit them, you add those changes to the staging area.

Add Changes to Stage : The command  `git add <file>` adds a file to the staging area, marking it as ready for the next commit.

Review Changes : You can use  `git status`  to see which files are staged, modified, or untracked.

Example :-

You modify style.css and script.js. To prepare these changes for the next commit, you run :

git add style.css script.js

These files are now in the staging area.

#### 3. Committed (Local Repository)

Once your changes are staged, you can commit them to the local repository. 

A commit is a snapshot of your project at a particular point in time, including the staged changes.

Commit Command : The command  `git commit -m "Commit message"`  commits your staged changes to the repository.

Commit History : Each commit has a unique identifier (SHA hash) and contains a message that describes the changes made. This allows you to track the project’s history.

Each commit includes :-

A commit message explaining the changes.
    
A snapshot of the project at the time of the commit.
    
Metadata like the author and timestamp.
    
Example :-

You commit your changes to style.css and script.js

git commit -m "Fix styling and update JS logic"  ( This commit is saved to your local repository)


#### 4. Remote Repository

Once the changes are committed locally, you can push them to a remote repository. 

A remote repository is typically hosted on a service like GitHub, GitLab, or Bitbucket.

Pushing your commits ensures that other collaborators can see your changes and that the history of the project is updated.

Push Changes : The command  `git push origin <branch>`  uploads your commits to a remote repository.

The remote branch (often called origin) is the version of the repository hosted online.

Example :-

After committing locally, you push the changes to the remote main branch

git push origin master  ( Now, the changes are visible in the remote repository)

#### 5. Pull (Fetching Changes)

To keep your local repository up to date with the remote repository, you use the git pull command. 

This fetches any changes made by others and automatically merges them into your current branch.

Pull Command : The command  `git pull origin <branch>`  downloads and merges changes from the remote repository.

Git automatically performs a merge or rebase depending on the configuration.

Example :-

Before starting new work, you pull the latest changes from the remote main branch

git pull origin master  ( This ensures your local repository has the most recent updates before you start making new changes)




## Git Branching

Branching allows you to diverge from the main line of development and isolate work into separate "branches".

This is useful for working on new features, bug fixes, or experimental changes without affecting the main codebase (usually the main or master branch).

#### Key Branching Commands :-

`Create a new branch`

git branch <branch-name>


`Switch to a branch`

git checkout <branch-name>

or

git switch <branch-name>

`Create and switch to a new branch in one step`

git checkout -b <branch-name>

or

git switch -c <branch-name>

`List all branches`

git branch

This shows all local branches. The branch you are currently on will be marked with an asterisk (*).

`Delete a branch`

git branch -d <branch-name>

#### Example of Creating and Switching Branches

To create a new branch for a feature, say branch-1, and switch to it:

git branch branch-1

git checkout branch-1

Now, you can make changes, commit them, and push them to the remote repository when ready.


## Git Merging

When you finish working on a branch (like a feature branch), you can merge it back into another branch, usually the main/master branch. 

Merging incorporates the changes from one branch into another.

#### Key Merging Commands :-

Merge a branch into the current branch

git merge <branch-name>

Merge commit : If there are changes in both branches (the source and target), Git creates a merge commit that combines the changes.


#### Example of Merging


Switch to the main/master branch (or whichever branch you want to merge into)

git checkout main/master

Merge the feature branch branch-1 into main/master

git merge branch-1

If there are no conflicts, Git will automatically merge the branches, and you will have a new commit on the main/master branch that includes the changes from branch-1.


## Resolving Merge Conflicts


A merge conflict occurs when Git cannot automatically merge changes because both branches have modified the same part of a file in conflicting ways.

This usually happens when :-

Two developers modify the same lines in a file in different branches.

A file is deleted in one branch and modified in another.

When this happens, Git will stop the merge process and mark the conflicted files. You will need to manually resolve the conflicts and then complete the merge.


#### Steps for Resolving Merge Conflicts


Identify Conflicted Files : After a git merge or git pull, if there are conflicts, Git will notify you with a message like:

Automatic merge failed; fix conflicts and then commit the result.


You can also run :

git status

This will show a list of files that have conflicts, marked as unmerged.

Open Conflicted Files : Conflicted files will have conflict markers in them, showing the conflicting changes from both branches. 

