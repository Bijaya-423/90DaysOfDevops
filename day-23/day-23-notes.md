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
