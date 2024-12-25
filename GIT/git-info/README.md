## VCS (Version Control System)


A Version Control System (VCS) is a software tool that helps manage and track changes to files, especially source code. 

VCS enables multiple people to work on the same project simultaneously, while keeping a record of every change made to the project over time. 



## Why Version Control is Important


### Collaboration :- 

In team environments, developers and other stakeholders may work on the same files simultaneously.

VCS allows each individual to work on their own part of the project without conflicting with others' work.


### Track Changes :- 

VCS provides a history of changes made to the project. 

This allows developers to view who made a change, what the change was, and when it occurred.

### Undo Changes :- 

If a mistake is made, a VCS allows developers to revert to an earlier version of a file or the entire project, avoiding the loss of work.

### Branching and Merging :- 

VCS allows the creation of branches, so developers can work on new features or fixes without affecting the main project. 

These branches can later be merged back.

### Backup :- 

The VCS keeps a record of all versions, providing a backup for projects. 

In case of an issue (such as data corruption or accidental deletion), previous versions can be restored.



## Types of Version Control Systems

There are three primary types of version control systems :

### Local Version Control Systems :-

In this type, version history is stored locally on a single machine, usually as a set of files that are copied each time a change is made. 

While simple, this setup does not facilitate collaboration, as there’s no shared central repository.

Example: RCS (Revision Control System).


### Centralized Version Control Systems (CVCS) :-

In a CVCS, there is a central server that holds the repository, and every user gets their own working copy of the project from the central repository. 

Changes are recorded and synchronized with the central server, if the central server goes down, access to the repository is lost.

Example: Subversion (SVN), Perforce.

Advantages : Easier to manage, less storage required on individual machines, all users are aware of the repository status.

Disadvantages : Dependency on the central server, potential downtime if the server fails.


### Distributed Version Control Systems (DVCS) :-

In a DVCS like Git, each developer has a complete local copy of the entire repository, including its history. 

This means that developers can work offline and only need to sync with the remote repository when necessary.

The distributed nature ensures that even if the central repository is lost, any of the local repositories can serve as a full backup.

Examples: Git, Mercurial.

Advantages : Full history on each local machine, supports offline work, faster due to local repositories.

Disadvantages : Can lead to redundant storage of data, more complex to manage and set up compared to CVCS
