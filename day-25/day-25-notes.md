### Task 1: Git Reset — Hands-On
1. Make 3 commits in your practice repo (commit A, B, C)
2. Use `git reset --soft` to go back one commit — what happens to the changes?
3. Re-commit, then use `git reset --mixed` to go back one commit — what happens now?
4. Re-commit, then use `git reset --hard` to go back one commit — what happens this time?
5. Answer in your notes:
   - What is the difference between `--soft`, `--mixed`, and `--hard`?
   - Which one is destructive and why?
   - When would you use each one?
   - Should you ever use `git reset` on commits that are already pushed?



changes for commit A



commit B




commit C

1. Make 3 commits (commit X, Y, Z)
2. Revert commit Y (the middle one) — what happens?
3. Check `git log` — is commit Y still in the history?
4. Answer in your notes:
   - How is `git revert` different from `git reset`?
   - Why is revert considered **safer** than reset for shared branches?
   - When would you use revert vs reset?

---


git reset
=========
moves the current branch (Head) to a previous commit . can remove commits and optionally kepp ot discard changes.

remove commit from history

it is not safe for shared and pushed branch avoid using it on push /shared branches becauses it rewrite history.

wheen you want tpo undo local commits that haven't been pushed yet or clean up commit history

git revert
==========
create a new commit that reverses the changes made by a previous commit.

it not remove commit from history 

it is safe for share and pushed branch. is preserved history and safely undoes changes.

when you need to undo changes in a share repository of after commits have already been pushed.








