# Git Cheatsheet

## ⚙️ Setup

```
git --version
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --list
```

## 📁 Repository

```
git init
git clone <url>
git status
```

|Command|Purpose|
|---|---|
|`git init`|Initialize Git repository|
|`git clone <url>`|Clone remote repository|
|`git status`|Check repository status|

---

## 📝 Basic Workflow

```
git add <file>
git add .
git commit -m "message"
git log
git log --oneline
```

```
Working Directory
       ↓ git add
Staging Area
       ↓ git commit
Local Repository
```

|Command|Purpose|
|---|---|
|`git add <file>`|Stage file|
|`git add .`|Stage all changes|
|`git commit -m "..."`|Create commit|
|`git log`|View commit history|
|`git log --oneline`|Compact history|

---

## 🌿 Branches

```
git branch
git branch <branch>
git checkout <branch>
git checkout -b <branch>
git branch -d <branch>
```

|Command|Purpose|
|---|---|
|`git branch`|List branches|
|`git branch feature`|Create branch|
|`git checkout feature`|Switch branch|
|`git checkout -b feature`|Create + switch|
|`git branch -d feature`|Delete branch|

### Modern alternative

```
git switch <branch>
git switch -c <branch>
```

---

## ☁️ Remote / GitHub

```
git remote -v
git remote add origin <url>

git push origin main
git push -u origin main

git pull
git fetch
```

|Command|Purpose|
|---|---|
|`git remote -v`|View remotes|
|`git remote add origin <url>`|Add remote|
|`git push`|Upload commits|
|`git pull`|Download + integrate changes|
|`git fetch`|Download changes without merging|

---

## 🔀 Merge

```
git checkout main
git merge feature
```

### Typical workflow

```
main
 ↓
create branch
 ↓
work + commit
 ↓
push
 ↓
Pull Request
 ↓
review
 ↓
merge → main
```

---

## ⚠️ Merge Conflicts

When Git cannot automatically merge changes:

```
<<<<<<< HEAD
Your changes
=======
Other changes
>>>>>>> branch
```

### Fix

1. Manually edit the conflicting file.
2. Remove conflict markers.
3. Stage the file.
4. Commit.

```
git add .
git commit -m "Resolve merge conflict"
```

---

## ↩️ Undo Changes

### Unstage file

```
git restore --staged <file>
```

### Discard file changes

```
git restore <file>
```

### Reset last commit

```
git reset --soft HEAD~1
git reset HEAD~1
git reset --hard HEAD~1
```

|Command|Result|
|---|---|
|`--soft`|Remove commit, keep staged changes|
|`--mixed`|Remove commit, keep unstaged changes|
|`--hard`|Remove commit + changes|

⚠️ Be careful with `--hard`.

---

## ↩️ Revert

Undo a commit by creating a **new commit**:

```
git revert <commit-hash>
```

### Reset vs Revert

```
reset  → rewrites history
revert → creates an undo commit
```

For shared/pushed work, **revert is generally safer**.

---

## 📦 Stash

Temporarily save uncommitted changes.

```
git stash
git stash list
git stash pop
git stash apply
git stash drop
```

### Common use

```
Working on Feature A
        ↓
git stash
        ↓
Switch branch
        ↓
Do other work
        ↓
Return to Feature A
        ↓
git stash pop
```

---

## 🔍 Useful Commands

```
git diff
git diff --staged
git show <commit>
git remote -v
git branch -a
git log --oneline --graph --all
```

|Command|Purpose|
|---|---|
|`git diff`|View unstaged changes|
|`git diff --staged`|View staged changes|
|`git show <commit>`|Show commit details|
|`git branch -a`|List local + remote branches|
|`git log --oneline --graph --all`|Visual history|

---

## 🧠 Must Remember

```
git init       → Create repository
git clone      → Copy repository
git status     → Check status
git add        → Stage
git commit     → Save snapshot
git log        → History

git branch     → Manage branches
git checkout   → Switch branch
git merge      → Combine branches

git push       → Upload
git pull       → Download + integrate
git fetch      → Download only

git reset      → Move/rewrite history
git revert     → Undo with new commit
git stash      → Temporarily save changes
```