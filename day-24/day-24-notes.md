### Task 1: Git Merge — Hands-On
1. Create a new branch `feature-login` from `main`, add a couple of commits to it
2. Switch back to `main` and merge `feature-login` into `main`
3. Observe the merge — did Git do a **fast-forward** merge or a **merge commit**?
4. Now create another branch `feature-signup`, add commits to it — but also add a commit to `main` before merging
5. Merge `feature-signup` into `main` — what happens this time?

i have write the something to commit in feature-login branch and push it and merge it



this is the second line o =f the feature-login branch



6. Answer in your notes:
   - What is a fast-forward merge?
   - When does Git create a merge commit instead?
   - What is a merge conflict? (try creating one intentionally by editing the same line in both branches)


a fast forward merge happens when the taget branches has not moved forward since the feature branch was created



git simply moves the branch pointer ahead without creating a new branch commit 


git create a merge commit when both branches have different commmits.