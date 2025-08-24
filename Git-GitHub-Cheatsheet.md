Perfecf ��� A **Table of Contents (TOC)** will make your `README.md` much easier to navigate on GitHub.
Here’s the polished version with TOC, headings, emojis, and clean formatting:

---

````markdown
# ��� Git & GitHub Cheatsheet  

A quick reference guide for commonly used Git commands when working with GitHub.  

---

## ��� Table of Contents
- [��� Setup & Configuration](#-setup--configuration)
- [��� Starting a Repository](#-starting-a-repository)
- [��� Staging & Committing](#-staging--committing)
- [��� Undo & Restore](#-undo--restore)
- [��� Branching](#-branching)
- [��� Push & ��� Pull](#-push--pull)
- [��� Logs & History](#-logs--history)
- [��� Advanced](#-advanced)

---

## ��� Setup & Configuration
```bash
git --version
````

Check installed Git version.

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
git config --global --list
```

Configure your identity for all repositories.

---

## ��� Starting a Repository

```bash
git init
```

Initialize a new repository in the current directory.

```bash
git clone <repo-url>
```

Clone an existing repository from GitHub.

---

## ��� Staging & Committing

```bash
git status
```

Check which files are modified, staged, or untracked.

```bash
git add .                # Stage all changes
git add <file>           # Stage a specific file
git commit -m "message"  # Commit with a message
```

---

## ��� Undo & Restore

```bash
git restore <file>
```

Restore a modified/deleted file (before commit).

```bash
git rm --cached <file>
```

Unstage a file (keep it in working directory).

```bash
git reset --hard origin/master
```

⚠️ **Scenario:** If your local branch has diverged or you deleted files accidentally and want to **reset your branch exactly to match GitHub’s `master`**, this command will discard all local changes and overwrite with remote.

```bash
git checkout origin/master -- path/to/your_deleted_file
```

✅ **Scenario:** If you accidentally deleted just one file, use this to recover **only that file** from the remote branch without affecting others.

---

## ��� Branching

```bash
git branch
```

List local branches.

```bash
git branch <name>
```

Create a new branch.

```bash
git switch <branch>      # Switch to existing branch
git switch -c <branch>   # Create + switch
```

```bash
git branch -d <name>     # Delete branch (safe)
git branch -D <name>     # Force delete branch
git branch -M <new-name> # Rename branch
```

---

## ��� Push & ��� Pull

```bash
git remote add origin <repo-url>
git remote -v
```

Connect and verify remote.

```bash
git push -u origin master
```

Push the branch to GitHub for the first time and set upstream.

```bash
git push
```

Push latest commits.

```bash
git pull
```

Pull latest changes from remote.

```bash
git pull origin master
```

Pull a specific branch from remote.

---

## ��� Logs & History

```bash
git log --oneline
```

Compact commit history.

```bash
git branch -r
```

List remote branches.

```bash
git remote remove origin
git remote set-url origin <url>
```

Manage or update remote URLs.

---

## ��� Advanced

```bash
git rebase
```

Reapply commits on top of another branch.

```bash
git checkout origin/master -- <file>
```

Restore a specific file from remote branch.

---

✨ This cheatsheet should serve as a quick reference for day-to-day Git + GitHub usage!

```

---

✅ This is **GitHub-ready** — headings, emojis, TOC, scenarios, and formatting are clean.  

Do you also want me to **add some GitHub badges (like shields.io)** at the top for style (e.g., “Git”, “GitHub”, “Cheatsheet”)?
```
A **Table of Contents (TOC)** will make your `README.md` much easier to navigate on GitHub.
Here’s the polished version with TOC, headings, emojis, and clean formatting:

---

````markdown
# 📘 Git & GitHub Cheatsheet  

A quick reference guide for commonly used Git commands when working with GitHub.  

---

## 📑 Table of Contents
- [🔧 Setup & Configuration](#-setup--configuration)
- [📂 Starting a Repository](#-starting-a-repository)
- [📌 Staging & Committing](#-staging--committing)
- [🔄 Undo & Restore](#-undo--restore)
- [🌿 Branching](#-branching)
- [📤 Push & 📥 Pull](#-push--pull)
- [📜 Logs & History](#-logs--history)
- [🎯 Advanced](#-advanced)

---

## 🔧 Setup & Configuration
```bash
git --version
````

Check installed Git version.

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
git config --global --list
```

Configure your identity for all repositories.

---

## 📂 Starting a Repository

```bash
git init
```

Initialize a new repository in the current directory.

```bash
git clone <repo-url>
```

Clone an existing repository from GitHub.

---

## 📌 Staging & Committing

```bash
git status
```

Check which files are modified, staged, or untracked.

```bash
git add .                # Stage all changes
git add <file>           # Stage a specific file
git commit -m "message"  # Commit with a message
```

---

## 🔄 Undo & Restore

```bash
git restore <file>
```

Restore a modified/deleted file (before commit).

```bash
git rm --cached <file>
```

Unstage a file (keep it in working directory).

```bash
git reset --hard origin/master
```

⚠️ **Scenario:** If your local branch has diverged or you deleted files accidentally and want to **reset your branch exactly to match GitHub’s `master`**, this command will discard all local changes and overwrite with remote.

```bash
git checkout origin/master -- path/to/your_deleted_file
```

✅ **Scenario:** If you accidentally deleted just one file, use this to recover **only that file** from the remote branch without affecting others.

---

## 🌿 Branching

```bash
git branch
```

List local branches.

```bash
git branch <name>
```

Create a new branch.

```bash
git switch <branch>      # Switch to existing branch
git switch -c <branch>   # Create + switch
```

```bash
git branch -d <name>     # Delete branch (safe)
git branch -D <name>     # Force delete branch
git branch -M <new-name> # Rename branch
```

---

## 📤 Push & 📥 Pull

```bash
git remote add origin <repo-url>
git remote -v
```

Connect and verify remote.

```bash
git push -u origin master
```

Push the branch to GitHub for the first time and set upstream.

```bash
git push
```

Push latest commits.

```bash
git pull
```

Pull latest changes from remote.

```bash
git pull origin master
```

Pull a specific branch from remote.

---

## 📜 Logs & History

```bash
git log --oneline
```

Compact commit history.

```bash
git branch -r
```

List remote branches.

```bash
git remote remove origin
git remote set-url origin <url>
```

Manage or update remote URLs.

---

## 🎯 Advanced

```bash
git rebase
```

Reapply commits on top of another branch.

```bash
git checkout origin/master -- <file>
```

Restore a specific file from remote branch.

---

✨ This cheatsheet should serve as a quick reference for day-to-day Git + GitHub usage!

```

---

✅ This is **GitHub-ready** — headings, emojis, TOC, scenarios, and formatting are clean.  

Do you also want me to **add some GitHub badges (like shields.io)** at the top for style (e.g., “Git”, “GitHub”, “Cheatsheet”)?
```

