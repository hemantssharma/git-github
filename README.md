Perfect 🚀 Let’s finalize this into a **complete, professional Git & GitHub Cheatsheet**.

I’ve expanded every section with:

* ✅ Commands
* ✅ Clear explanation
* ✅ Real-world **use cases & scenarios**

Here’s your **final README.md** 👇

````markdown
# 🚀 Git & GitHub Cheatsheet

A complete, professional guide with **essential Git commands**, **real-world scenarios**, and **best practices**.  
Perfect for **daily development**, **troubleshooting**, and **interviews**.  

---

## 📑 Table of Contents
- [🔧 Setup & Configuration](#-setup--configuration)
- [📂 Starting a Repository](#-starting-a-repository)
- [📌 Daily Workflow](#-daily-workflow)
- [📌 Staging & Committing](#-staging--committing)
- [🔄 Undo & Restore](#-undo--restore)
- [🌿 Branching](#-branching)
- [📤 Push & 📥 Pull](#-push--pull)
- [📜 Logs & History](#-logs--history)
- [📦 Stashing & Cleaning](#-stashing--cleaning)
- [🏷️ Tagging & Releases](#️-tagging--releases)
- [🎯 Advanced & Scenarios](#-advanced--scenarios)
- [📊 Visual Workflows](#-visual-workflows)

---

## 🔧 Setup & Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global --list
```
✔️ Configures your identity and verifies setup.  
💡 **Use case:** First-time setup on a new machine.

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
✔️ Copies an existing repository.  
💡 **Use case:** Work on a project hosted on GitHub.

---

## 📌 Daily Workflow

```bash
git status
```
✔️ Shows current changes (modified, staged, untracked).  
💡 **Use case:** Always check before staging/committing.

```bash
git add .
```
✔️ Stages all changes.  
💡 **Use case:** Prepares your modifications to be committed.

```bash
git commit -m "Your message"
```
✔️ Saves staged changes to history.  
💡 **Use case:** Meaningful commit messages help track project progress.

---

## 📌 Staging & Committing

```bash
git add file1 file2
```
✔️ Stage only specific files.  
💡 **Use case:** Commit only relevant changes, not everything.

```bash
git commit --amend
```
✔️ Modifies the last commit (message or staged files).  
💡 **Use case:** Fix typos or add forgotten changes before pushing.

---

## 🔄 Undo & Restore

```bash
git restore file.txt
```
✔️ Discards local modifications (before staging).  
💡 **Use case:** Undo accidental edits.

```bash
git reset --hard origin/master
```
✔️ Resets local branch to remote (removes local changes).  
💡 **Use case:** When your branch is broken and you want a fresh copy.

```bash
git checkout origin/master -- path/to/file
```
✔️ Restores a deleted file from remote branch.  
💡 **Use case:** Bring back a file you accidentally deleted.

---

## 🌿 Branching

```bash
git branch
```
✔️ Lists branches.  

```bash
git branch feature-x
```
✔️ Creates new branch `feature-x`.  
💡 **Use case:** Isolate new work from `main`.

```bash
git checkout feature-x
# or
git switch feature-x
```
✔️ Switches branch.  
💡 **Use case:** Move between features.

```bash
git branch -d feature-x
```
✔️ Deletes branch safely (only if merged).  

```bash
git branch -D feature-x
```
✔️ Force deletes branch.  
💡 **Use case:** Remove abandoned work.

---

## 📤 Push & 📥 Pull

```bash
git push origin branch-name
```
✔️ Uploads commits to GitHub.  
💡 **Use case:** Share work with team.

```bash
git pull origin branch-name
```
✔️ Fetches and merges updates from remote.  
💡 **Use case:** Sync with latest changes before coding.

```bash
git branch -M main
git push -u origin main
```
✔️ Renames local branch to `main` and sets remote default.  
💡 **Use case:** Standardize branch name (GitHub uses `main`).

---

## 📜 Logs & History

```bash
git log --oneline
```
✔️ Compact commit history.  

```bash
git log --graph --oneline --all
```
✔️ Visual graph of branches.  
💡 **Use case:** Debugging merge issues.

---

## 📦 Stashing & Cleaning

```bash
git stash
```
✔️ Saves uncommitted changes temporarily.  
💡 **Use case:** Switch branches without committing work-in-progress.

```bash
git stash pop
```
✔️ Restores latest stash.  

```bash
git clean -fd
```
✔️ Removes untracked files/folders.  
💡 **Use case:** Cleanup build artifacts.

---

## 🏷️ Tagging & Releases

```bash
git tag v1.0.0
git push origin v1.0.0
```
✔️ Create & push lightweight tag.  
💡 **Use case:** Mark releases or milestones.

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
```
✔️ Annotated tag (with message).  
💡 **Use case:** Best for production releases.

```bash
git reset --hard v1.0.0
```
✔️ Roll back to a tagged version.  
💡 **Use case:** Rollback after failed deployment.

---

## 🎯 Advanced & Scenarios

### 🔹 Merge unrelated histories
```bash
git merge dev --allow-unrelated-histories
```
✔️ Allows merging branches with no common ancestor.  
💡 **Use case:** Combining two separate projects.

### 🔹 Resolve merge conflicts
```bash
# Edit conflicted files manually
git add conflicted-file
git commit
```
✔️ Confirms resolved conflicts.  
💡 **Use case:** Happens when two people edit the same lines.

### 🔹 Rebase branch
```bash
git checkout feature-x
git rebase main
```
✔️ Re-applies commits on top of latest `main`.  
💡 **Use case:** Keeps history linear & clean.

### 🔹 Security & Sensitive Data Issues
- GitHub **Secret Scanning** alerts you if keys are committed.  
- Tools: `trufflehog`, `git-secrets`.  
- To remove secrets:  
  ```bash
  git filter-repo --path file-with-keys.txt --invert-paths
  git push origin --force
  ```  
💡 **Use case:** Accidentally pushed credentials → must rotate keys, purge history, and enable scanning.

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

✔️ Example flow:  
- Start from `main` → work in `dev` → branch out features → merge back → release with tags.

---

🔥 **Now you have:**
- Commands + explanations + scenarios  
- Advanced troubleshooting & security  
- Visual workflow  
- Professional formatting for GitHub
````

---
