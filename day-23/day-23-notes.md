### Task 1: Understanding Branches
Answer these in your `day-23-notes.md`:
1. What is a branch in Git?
2. Why do we use branches instead of committing everything to `main`?
3. What is `HEAD` in Git?
4. What happens to your files when you switch branches?


1- A branch is an independent line of development in git 

is is a separate workspace where you can make changes without affecting the main code

2- we use branches to work on new features , bug fixes or experiments without affecting the stable code in the main branch.

if every one commit directly to main

- bugs can reach production
- Team members may overwrite each others work.
- Testing becomes difficult.
- The main branch may become unstable.


Branches provide an isolated workspace where developers can make changes safely , test them and review them before merging into main.



3- HEAD is a pointer that tells git which commit and branch you are currently working on 

HEAD is the current position in git

4- when you switch branche , git updates your working directory to match the files stored in the target branch.



<<<<<<< HEAD





### Task 2: Branching Commands — Hands-On
In your `devops-git-practice` repo, perform the following:
1. List all branches in your repo
git branch-
to get the all the branch in the git and * is the current branch

git branch -v
show all commit and branch details


2. Create a new branch called `feature-1`
git bracnh feature-1
git checkout - feature-1 to create and switch the branch


3. Switch to `feature-1`
git checkout feature-1
git switch feature-1

4. Create a new branch and switch to it in a single command — call it `feature-2`

git checkout -b feature-2

5. Try using `git switch` to move between branches — how is it different from `git checkout`?

- both commands can be used to move between branches , but git switch is newer and simpler

git checkout feature-1 - switch the branch
git checkout -b feature-1 - create and switch the branch

git checkout
============
switch branches
create branches
restore files
checkout commits

git switch
==========
switching branches
createtig and switching branches

6. Make a commit on `feature-1` that does **not** exist on `main`
git switch feature-1

- create a file and added the code and commit 

git log --online

git switch main
and notice

7. Switch back to `main` — verify that the commit from `feature-1` is not there

git checkout main
and notice nothing is theere in this file and file does not exists

8. Delete a branch you no longer need
git branch -d feature-1


git checkout -d branch_name

9. Add all branching commands to your `git-commands.md`

### Task 3: Push to GitHub
1. Create a **new repository** on GitHub (do NOT initialize it with a README)
2. Connect your local `devops-git-practice` repo to the GitHub remote
3. Push your `main` branch to GitHub
4. Push `feature-1` branch to GitHub
5. Verify both branches are visible on GitHub
6. Answer in your notes: What is the difference between `origin` and `upstream`?



origin => Your own remote repository
upstream => the original source repository from which your repository was forked 



### Task 4: Pull from GitHub
1. Make a change to a file **directly on GitHub** (use the GitHub editor)
2. Pull that change to your local repo
3. Answer in your notes: What is the difference between `git fetch` and `git pull`?



git fetch 
=========

git fetch downloads the latest changes from the remote repository but does not modify my local branch

it updates the remote - tracking branches such as

origin / main

git fetch origin 


git pull
========
git pull download changes from the remote repository and immediatly merges them into my current branch


git pull origin main


### Task 5: Clone vs Fork
1. **Clone** any public repository from GitHub to your local machine
2. **Fork** the same repository on GitHub, then clone your fork
3. Answer in your notes:
   - What is the difference between clone and fork?
   - When would you clone vs fork?
   - After forking, how do you keep your fork in sync with the original repo?


-> a clone creates a copy of a git repository on your local machine.


you make changes locally , commit them and push them if you have permission.


a form create your own copy of some one else repository on github.


after forking you can clone your fork


clone
====
you own the repository
you are part of the project team
you already have write access.
you want a local copy of the repository.

fork
====

you do not have write access.
you want to contribute to an open source project.

you want your own github copy of the project
=======
### Task 2: Branching Commands — Hands-On
In your `devops-git-practice` repo, perform the following:
1. List all branches in your repo
2. Create a new branch called `feature-1`
3. Switch to `feature-1`
4. Create a new branch and switch to it in a single command — call it `feature-2`
5. Try using `git switch` to move between branches — how is it different from `git checkout`?
6. Make a commit on `feature-1` that does **not** exist on `main`
7. Switch back to `main` — verify that the commit from `feature-1` is not there
8. Delete a branch you no longer need
9. Add all branching commands to your `git-commands.md`
>>>>>>> 168f1bbbb2cf6f5c6217034681cfb79ff053c260
