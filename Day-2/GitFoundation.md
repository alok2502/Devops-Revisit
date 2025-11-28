# ⚙️ Day 2 — Git Foundations (Forge Level 1)

## 🎯 Objective
Understand Git architecture and perform hands-on branching, merging, and conflict resolution.

## 🧩 Commands Practiced
| Concept | Command | What It Did (your words) |
|----------|----------|--------------------------|
| Initialize repo | `git init` | Created new Git repository locally |
| Add & Commit | `git add . && git commit -m "msg"` | Staged and saved changes in local repo |
| Branch creation | `git checkout -b feature/login` | Created & switched to new branch |
| Merge | `git merge feature/login` | Combined feature branch into main |
| Conflict resolution | manual edit + `git add` + `git commit` | Fixed conflicting lines manually |
| Undo commit | `git reset --soft HEAD~1` | Removed last commit, kept changes |
| Safe rollback | `git revert <commit-id>` | Reverted specific commit already pushed |
| View history | `git log --oneline --graph --decorate --all` | Visualized commit tree |

## 🧠 Learnings
- Git has 4 layers (working dir → staging → local → remote)  
- Merge vs Rebase difference  
- How to handle merge conflicts  
- Safe rollback strategies (`revert` vs `reset`)  
- Importance of clean branching in CI/CD  

## 🗣️ Interview Practice (your answers)
1. What happens when you push?
    When we run git push, the local branch’s HEAD pointer (latest commit reference) is sent to the remote repository.
    Git then updates the remote branch pointer to match the local one, transferring all missing commits.
    If the remote branch has diverged, Git will block the push until you pull and merge/rebase first.

2. How do you handle a bad commit in production?
    If a wrong commit is already pushed to remote, we can safely undo it using:
    git revert <commit-id>
    This creates a new commit that reverses the changes made by the bad commit without rewriting history, keeping the repository safe for others.

3. Merge vs Rebase?
    Both merge and rebase integrate changes from one branch into another, but they behave differently:

    Merge: Preserves full commit history by creating a new merge commit. It’s ideal for shared or long-lived branches because it shows when and how branches were merged.

    Rebase: Rewrites history by placing your commits on top of another branch, creating a cleaner, linear timeline. Best used for personal or feature branches before merging.

    🧩 Example:
    If main has 50 commits and feature has 30 commits, after rebasing, your 30 commits appear after the 50 commits of main, making the history linear.
    With merge, Git simply joins both histories together, showing all merge events.

4. Why is Git important in DevOps pipelines?
    Git is the single source of truth in a DevOps workflow.
    Every change to code, infrastructure, or configuration is version-controlled in Git.
    It enables collaboration, rollback, and traceability — essential for CI/CD pipelines to know exactly which version of code or IaC is being built, tested, or deployed.
    Without Git, automation would have no reliable base to track changes.


## Bonus Commands 
    git status                   # shows staged/unstaged files
    git diff                     # view code differences
    git reflog                   # shows every move HEAD made (useful to recover lost commits)
    git stash && git stash pop   # temporarily save work
    git remote -v                # verify remote URLs

