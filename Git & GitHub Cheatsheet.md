# 🚀 Git & GitHub Cheatsheet

A complete guide with **essential Git commands**, **real-world scenarios**, and **best practices**.
Perfect for daily development and quick reference.

---

## 📑 Table of Contents

* [🔧 Setup & Configuration](#-setup--configuration)
* [📂 Starting a Repository](#-starting-a-repository)
* [📌 Daily Workflow](#-daily-workflow)
* [📌 Staging & Committing](#-staging--committing)
* [🔄 Undo & Restore](#-undo--restore)
* [🌿 Branching](#-branching)
* [📤 Push & 📥 Pull](#-push--pull)
* [📜 Logs & History](#-logs--history)
* [📦 Stashing & Cleaning](#-stashing--cleaning)
* [🏷️ Tagging & Releases](#️-tagging--releases)
* [🎯 Advanced & Scenarios](#-advanced--scenarios)
* [📊 Visual Workflows](#-visual-workflows)

---

## 🔧 Setup & Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global --list
git config --global init.defaultBranch main
```

✔️ Set your identity for commits.
💡 **Use case:** Required before first commit so GitHub knows who you are.

---

## 📂 Starting a Repository

```bash
git init
```

✔️ Initializes a new Git repository in the current folder.
💡 **Use case:** Starting a brand-new project locally.

```bash
git clone <repo-url>
```

✔️ Clones an existing repo from GitHub.
💡 **Use case:** Get a working copy of a project.

---

## 📌 Daily Workflow

```bash
git status
```

✔️ Shows current changes, staged/untracked files.
💡 **Use case:** Always run before committing.

```bash
git add .
```

✔️ Stages all changes for commit.
💡 **Use case:** Save changes to Git history.

```bash
git commit -m "message"
```

✔️ Records changes in local history.
💡 **Use case:** Describes what you changed.

```bash
git pull origin branch
```

✔️ Fetches & merges latest changes.
💡 **Use case:** Sync with teammates before pushing.

```bash
git push origin branch
```

✔️ Pushes commits to GitHub.
💡 **Use case:** Share your work remotely.

---

## 📌 Staging & Committing

```bash
git add file.txt
```

✔️ Stage a specific file.

```bash
git reset file.txt
```

✔️ Unstage a file.

💡 **Use case:** Control exactly what goes into a commit.

---

## 🔄 Undo & Restore

```bash
git restore file.txt
```

## 🔄 Add remote origion and establish connection between local and remote

```bash

git remote add origin https://github.com/user/repo.git
git remote set-url origin https://token@github.com/user/repo.git

```

```bash
git remote add origin https://github.com/hemantssharma/git-github-testing
git remote set-url origin https://<token>@github.com/hemantssharma/git-github-testing
```
**For example:** above command.

```bash
git restore file.txt
```

✔️ Discards local modifications.

```bash
git checkout origin/master -- path/to/file
```

✔️ Restores deleted file from remote.

```bash
git reset --hard origin/master
```

✔️ Resets branch to match remote exactly.
💡 **Use case:** Fix mistakes or recover deleted files.

---

## 🌿 Branching

```bash
git branch
```

✔️ List branches.

```bash
git branch feature-login
```

✔️ Create a new branch.
💡 **Use case:** Develop new feature safely.

```bash
git checkout feature-login
# or
git switch feature-login
```

✔️ Switch to a branch.

```bash
git branch -d feature-login
```

✔️ Delete branch safely (only if merged).

```bash
git branch -D feature-login
```

✔️ Force delete branch (not merged).

---

## 📤 Push & 📥 Pull

```bash
git push -u origin main
```

✔️ Pushes current branch & sets upstream.

```bash
git pull origin dev
```

✔️ Pulls latest code into `dev`.

💡 **Use case:** Keep local & remote in sync.

---

## 📜 Logs & History

```bash
git log --oneline
```

✔️ Compact commit history.

```bash
git log --graph --oneline --all
```

✔️ Visualize branches & merges.

💡 **Use case:** Debugging merge conflicts.

---

## 📦 Stashing & Cleaning

```bash
git stash
```

✔️ Saves uncommitted changes temporarily.

```bash
git stash pop
```

✔️ Restores stashed changes.

```bash
git clean -fd
```

✔️ Remove untracked files.

💡 **Use case:** Switch branches without losing work.

---

## 🏷️ Tagging & Releases

```bash
git tag v1.0.0
```

✔️ Create lightweight tag.

```bash
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0
```

✔️ Annotated tag for release.

```bash
git tag
```

✔️ List tags.

💡 **Use case:** Mark stable releases, hotfix rollbacks, CI/CD deployments.

---

## 🎯 Advanced & Scenarios

### 🔹 Rename default branch

```bash
git branch -M main
git push -u origin main
```

✔️ Rename branch to `main` & push upstream.

---

### 🔹 Merge unrelated histories

```bash
git checkout main
git merge dev --allow-unrelated-histories
```

✔️ Used when branches have no common history.

---

### 🔹 Accidentally deleted a file

```bash
git checkout origin/master -- path/to/file
```

---

### 🔹 Security issue – secrets pushed to repo

* **Detection**: GitHub Secret Scanning, push protection, CI tools, or searching history
* **Fix**:

  1. Rotate the leaked key immediately
  2. Remove it from Git history (`git filter-repo` or `git filter-branch`)
  3. Force push clean history
  4. Add patterns to `.gitignore`
* **Prevention**: Pre-commit hooks, scanning tools, and reviews.

---

## 📊 Visual Workflows

```mermaid
gitGraph
    commit id: "Initial Commit"
    branch dev
    checkout dev
    commit id: "Feature work"
    branch feature-login
    checkout feature-login
    commit id: "Login page"
    commit id: "Auth fix"
    checkout dev
    merge feature-login
    commit id: "Prepare for release"
    checkout main
    merge dev
    commit id: "Release v1.0.0"
    tag id: "v1.0.0"
```

✔️ Typical flow: `main` → `dev` → feature branches → merge → release with tag.

---
