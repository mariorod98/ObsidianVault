up:: 
tags:: #state/seedling #on/git

# Git

## What is Git?
Git is a Distributed [[Version Control System]] (VSC) that tracks the history of changes as people and teams collaborate on a project together. It is the most common VSC used nowadays.

## How does git work?
Git works by tracking the **changes** made into the **files** that conform the **repository** of a project. 

Git has three environments where these changes live:
- The **working directory** is the place that holds the actual files of the repository. It is the place where you create, delete and modify files. ==It is the project's directory in your computer system==.
- The **stage** (or index) is an intermediate space between the **working directory** and the **repository**. It stores all the changes made in the **working directory** that you want to [[commit]] to the **repository**. It can be defined as a preview of your next commit.
- The **repository** contains the files of the project and the history of all the changes made. When you [[commit]] a change, the changes from the **stage** are stored in the repository's history with a unique UUID.

The git workflow consists on:
1. Modifying the files in your **working directory**.
2. Staging the changes you want to commit into the **stage**.
3.  Commiting the changes to the **repository**.

![[git_usage.png]]

## Git concepts
### Branch 
A **Branch** is a version of the repository that diverges from the main working project. In reality, it's just a pointer that points to a specific commit. When adding a new commit to the branch, it will be added as a son of the commit it is pointing to and then update itself to point to the newly created commit.

### Head
The **HEAD** is the representation of the last commit in the current checkout branch. When you switch branches with [[git checkout]], the HEAD revision changes, pointing to the new branch.

## Initializing a repository
### Commands
``git init`` creates and initializes new repository in the current directory. This adds a hidden subfolder *.git* that stores the internal data structure required for version control.
Options:
- ``-b <branch-name>`` Specifies the initial branch in the newly created repository. The default name is ``master``

### Example
**Start a new git repository for an existing project**
```git
git init
git add .
git commit -m "First commit"
```

## Commiting changes to a repository
### Commands
``git add`` stages a change, taking a snapshot of the current state of files added. Any change that has been staged will become part of the next commit in the project's history. It will not add ignored files by default.

``git commit`` saves the current stage to the project history.

``git status`` shows the status of the changes as untracked (not in the repository), modified (in the repository but not staged) or staged.

## Remote repositories
### Commands
``git clone`` creates a local copy of a repository that already exists remotely. The clone includes all the project's files, history and branches.

``git pull``  updates the local repository with updates from its remote counterpart. Developers use this command if a teammate has made commits to a branch on a remote, and they would like to reflect thos changes in their local environment.

``git push`` updates the remote repository with any commits made locally to a branch

``git merge`` merges lines of development together. This command is typically used to combine changes made on two distinct branches.

## Git folder structure

## References
[Git - gitglossary Documentation](https://git-scm.com/docs/gitglossary)
[Git Cheatsheet](https://rogerdudler.github.io/git-guide/files/git_cheat_sheet.pdf)
[A Visual Git Reference](https://marklodato.github.io/visual-git-guide/index-en.html)
[git - the simple guide - no deep shit!](https://rogerdudler.github.io/git-guide/)
[About Git - GitHub Docs](https://docs.github.com/en/get-started/using-git/about-git)
[States of a File in Git Working Directory - GeeksforGeeks](https://www.geeksforgeeks.org/states-of-a-file-in-git-working-directory/#:~:text=The%20Git%20directory%20contains%20the,included%20in%20the%20next%20commit.)
[Git - git-init Documentation](https://git-scm.com/docs/git-init)

---
Planted: 2022-08-11
Last tended: 2022-08-17