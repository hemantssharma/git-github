**Git Cheatsheet**

1. I’ll add a **Table of Contents** at the top (with clickable links).
2. I’ll include a **Visual Git Workflow Diagram** (using Mermaid flowchart so GitHub renders it beautifully).

Here’s your **final improved README.md**:

````markdown
# 🚀 Git & GitHub Cheatsheet

A complete guide with **essential Git commands**, **real-world scenarios**, and **best practices**.  
Perfect for daily development and quick reference.  

---

## 📑 Table of Contents
- [Setup & Configuration](#-setup--configuration)
- [Starting a Repository](#-starting-a-repository)
- [Daily Workflow](#-daily-workflow)
- [Branching](#-branching)
- [Rename & Set Default Branch](#-rename--set-default-branch)
- [Restoring & Resetting](#-restoring--resetting)
- [Remote Repositories](#-remote-repositories)
- [Merging Branches](#-merging-branches)
- [Tagging & Releases](#-️-tagging--releases)
- [Common Scenarios](#-common-scenarios)
- [Checking Logs](#-checking-logs)
- [Quick Tips](#-quick-tips)
- [Visual Git Workflow](#-visual-git-workflow)

---

## 🔧 Setup & Configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global --list
````

✔️ Configure your identity globally for all repositories.

---

## 📂 Starting a Repository

```bash
git init                  # Initialize new repo
git clone <repo-url>      # Clone an existing repo
```

✔️ Use `git init` for new projects, `git clone` for existing ones.

---

## 📌 Daily Workflow

```bash
git status                # Check status of changes
git add .                 # Stage all changes
git commit -m "message"   # Commit changes
git push origin branch    # Push changes to GitHub
git pull origin branch    # Pull latest changes
```

✔️ Repeat these steps daily for smooth sync with GitHub.

---

## 🌿 Branching

```bash
git branch                # List branches
git branch feature-x      # Create a new branch
git checkout feature-x    # Switch to branch
git switch feature-x      # Alternative way to switch
git branch -d feature-x   # Delete branch (safe)
git branch -D feature-x   # Force delete branch
```

✔️ Branching is best practice for working on new features without affecting main code.

---

## 🔄 Rename & Set Default Branch

```bash
git branch -M main        # Rename current branch to 'main'
git push -u origin main   # Push main to GitHub & set as upstream
```

✔️ GitHub now uses **main** as default (instead of master).

---

## 📥 Restoring & Resetting

```bash
git restore <file>        # Restore a deleted/modified file before commit
git checkout origin/master -- path/to/file   # Restore deleted file from remote
git reset --hard origin/master               # Reset local branch to remote
```

✔️ Useful when files are **accidentally deleted or corrupted** locally.

---

## 🌍 Remote Repositories

```bash
git remote -v                                # Show remotes
git remote add origin <url>                  # Add a remote
git remote set-url origin <new-url>          # Change remote URL
git push -u origin branch-name               # Push & link branch
```

✔️ Use remotes to connect your local repo with GitHub.

---

## 🔀 Merging Branches

```bash
git checkout main
git merge dev
```

✔️ Merges `dev` branch into `main`.
❌ If histories are unrelated, use locally:

```bash
git merge dev --allow-unrelated-histories
```

⚠️ Not possible directly from GitHub UI when histories differ.

---

## 🏷️ Tagging & Releases

Tags let you **mark specific points in Git history** — usually used for **releases, milestones, or stable versions**.
Unlike branches, **tags never move** once created.

### 📌 Creating Tags

```bash
git tag v1.0.0                       # Lightweight tag
git tag -a v1.0.0 -m "First release" # Annotated tag
git push origin v1.0.0                # Push a tag
```

### 🔧 Use Cases & Scenarios

* ✅ **Marking stable releases**

  ```bash
  git tag -a v1.0.0 -m "Initial production release"
  git push origin v1.0.0
  ```
* ✅ **Hotfix & rollback**

  ```bash
  git reset --hard v1.0.0
  git push origin main --force
  ```
* ✅ **CI/CD deployments**

  ```bash
  git tag -a v2.0.0 -m "Major update"
  git push origin v2.0.0
  ```
* ✅ **Library/API versioning**

  ```bash
  git tag -a v3.1.4 -m "Bug fixes"
  git push origin v3.1.4
  ```

### 🧹 Managing Tags

```bash
git tag                # List tags
git tag -d v1.0.0      # Delete local tag
git push origin --delete v1.0.0   # Delete remote tag
```

✨ **Tip:** Always use annotated tags for official releases.

---

## 🧩 Common Scenarios

### 🔹 Accidentally Deleted a File

```bash
git checkout origin/master -- path/to/file
```

### 🔹 Sync Local with Remote (force overwrite)

```bash
git reset --hard origin/master
```

### 🔹 Create Feature Branch from Current Work

```bash
git checkout -b feature-login
```

### 🔹 Merge Dev into Main (unrelated histories)

```bash
git checkout main
git merge dev --allow-unrelated-histories
```

---

## 📊 Checking Logs

```bash
git log --oneline       # Compact history
git log --graph --oneline --all  # Visual branch history
```

✔️ Helpful for debugging branch merges.

---

## 🎯 Quick Tips

* Always `git pull` before `git push` to avoid conflicts.
* Use feature branches for new development.
* Use tags for releases, not branches.
* Never commit secrets (passwords, API keys).

---

## 🖼️ Visual Git Workflow

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

✔️ This diagram shows a **typical workflow**:

* Start from `main` → work in `dev` → branch out for features → merge back → release with a tag.

---

🔥 Now your README has:

* A **clickable Table of Contents**
* A **Visual Git Workflow diagram**
* All your scenarios + extra best practices

---

Do you also want me to create a **PDF version of this cheatsheet** (with same styling + diagram) so you can keep it offline?
