# 📝 Git & GitHub Interview Q\&A (2–3 Years Experience)

This document contains **frequently asked interview questions and answers** based on Git & GitHub. It includes practical scenarios and real-world use cases tailored for developers with **2–3 years of experience**.

---

## 📌 Table of Contents

1. Basics & Configuration
2. Branching Strategies
3. Git Workflow & Collaboration
4. Git Rebase & Merge
5. Git Stash
6. Git Conflicts & Resolution
7. Git Hooks
8. Security & Sensitive Data Issues
9. Advanced Scenarios

---

## 🔹 1. Basics & Configuration

**Q1: How do you configure your Git username and email globall and tell the command of making the main as default branch during git initilization ?**
**A:**

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global init.defaultBranch main
```

This information is stored in commits you make.

**Q2: How do you check your Git configuration?**
**A:**

```bash
git config --list
```

---

## 🔹 2. Branching Strategies

**Q3: What is a branching strategy? Why is it important?**
**A:** A branching strategy defines how teams use branches to manage development, testing, and releases. It ensures smooth collaboration and avoids chaos.

* **Git Flow** → `main` for releases, `develop` for integration, feature/hotfix branches for tasks.
* **GitHub Flow** → `main` always deployable, short-lived feature branches merged via PR.
* **Trunk Based Development** → frequent commits to `main`, feature flags used.

**Q4: How do you create a new feature branch from an existing branch?**
**A:**

```bash
git checkout -b feature/login dev
```

This creates a branch `feature/login` from `dev`.

**Q5: How do you delete a branch locally and remotely?**
**A:**

```bash
# Local
git branch -d branch_name

# Remote
git push origin --delete branch_name
```

---

## 🔹 3. Git Workflow & Collaboration

**Q6: What’s the difference between `git pull` and `git fetch`?**
**A:**

* `git fetch`: Downloads new data from remote but does not merge.
* `git pull`: Fetches + merges changes into the current branch.

**Q7: How do you link your local repo to a remote GitHub repo?**
**A:**

```bash
git remote add origin https://github.com/user/repo.git
git remote set-url origin https://token@github.com/user/repo.git
git push -u origin main
```

---

## 🔹 4. Git Rebase & Merge

**Q8: What’s the difference between `git merge` and `git rebase`?**
**A:**

* **Merge**: Creates a merge commit combining histories → keeps history intact.
* **Rebase**: Rewrites history by moving commits on top of another branch → makes history linear.

**Q9: When should you use rebase instead of merge?**
**A:**

* Use **merge** when working in a shared branch (keeps history safe).
* Use **rebase** in feature branches to keep commit history clean before merging into `main`.

**Q10: Command to rebase `feature` onto `main`?**

```bash
git checkout feature
git rebase main
```

---

## 🔹 5. Git Stash

**Q11: What is `git stash` and when is it useful?**
**A:** `git stash` temporarily shelves (or stashes) changes without committing them. Useful when:

* You need to switch branches quickly without committing.
* You want to save unfinished work.

**Commands:**

```bash
git stash          # Save changes
git stash list     # View stashes
git stash pop      # Apply and remove latest stash
git stash apply    # Apply without removing
```

---

## 🔹 6. Git Conflicts & Resolution

**Q12: What causes merge conflicts in Git?**
**A:** Conflicts happen when two people edit the same part of a file differently, and Git cannot automatically decide.

**Q13: How do you resolve a merge conflict?**
**A:**

1. Open the conflicted file.
2. Manually resolve differences between `<<<<<<<`, `=======`, `>>>>>>>` markers.
3. Stage the resolved file → `git add file.txt`.
4. Commit the merge → `git commit`.

---

## 🔹 7. Git Hooks

**Q14: What are Git hooks?**
**A:** Git hooks are scripts that run automatically on certain Git events (like commit, push, merge). They help enforce policies.

**Example Use Cases:**

* Prevent committing secrets.
* Enforce commit message format.
* Run tests before pushing.

**Location:** `.git/hooks/`

**Example:** A `pre-commit` hook that runs lint:

```bash
#!/bin/sh
npm run lint || exit 1
```

---

## 🔹 8. Security & Sensitive Data Issues

**Q15: How do you know if someone accidentally pushed secrets (API keys/passwords) to GitHub?**
**A:** Use a mix of **platform alerts**, **automated scanners**, and **Git history searches**:

**A. Signals from GitHub (recommended):**

* **Secret scanning alerts** (Security tab → *Secret scanning*): GitHub detects many common providers' keys.
* **Push Protection warnings**: while pushing or opening a PR, GitHub may block/prompt if a secret pattern is detected.
* **Security → Alerts/Code scanning**: third‑party or GitHub Advanced Security rules may flag secrets in code.
* **Repo/Org email or webhook alerts**: configure notifications so the team gets notified immediately.

**B. Local/CI scanning (works anywhere):**

* Run dedicated scanners across the full history:

  * **gitleaks** (fast, popular)
  * **trufflehog** (entropy + regex rules)
  * **detect-secrets** (pre-commit friendly)
* Example (history grep for common patterns):

  ```bash
  # Search entire history for the AWS key prefix pattern
  git rev-list --all | xargs -I{} git grep -n --color -E "AKIA[0-9A-Z]{16}" {}

  # Search for words like 'SECRET|PASSWORD' in history
  git rev-list --all | xargs -I{} git grep -n -E "SECRET|PASSWORD|TOKEN|API_KEY" {}
  ```

**C. Manual review cues:**

* Large diff adding `.env`, `id_rsa`, `config.json`, or `.p12` files.
* Commits with messages like *"temp creds", "testing key"*.

---

**Q16: What immediate steps should you take if a secret was pushed?**
**A:**

1. **Revoke/rotate the credential** with the provider **immediately** (treat as compromised).
2. **Remove from current tip**: delete/replace the file and commit the fix.
3. **Purge from history** (so it’s not retrievable):

   * Recommended: **git filter-repo** (faster/safer; install once).

     ```bash
     # Remove a specific file from the entire history
     git filter-repo --path path/to/secret.file --invert-paths

     # Or remove lines matching a pattern from all blobs
     git filter-repo --replace-text <(printf "/API_KEY/==>REDACTED<
     ```

> ")
> \`\`\`

* Legacy (if filter-repo not available): **git filter-branch**

  ```bash
  git filter-branch --force --index-filter \
    'git rm --cached --ignore-unmatch path/to/secret.file' \
    --prune-empty --tag-name-filter cat -- --all
  ```

4. **Force-push** rewritten history and tags:

   ```bash
   git push origin --force --all
   git push origin --force --tags
   ```
5. **Notify collaborators** to re-clone or hard reset (history was rewritten).
6. **Invalidate caches** (CDN/build artifacts) if the secret could persist elsewhere.

---

**Q17: How do you prevent secrets from being committed again?**
**A:**

* **.gitignore**: add `.env`, `*.pem`, `*.p12`, `config.local.*`, etc.
* **Pre-commit hook** to block secrets:

  ```bash
  # .git/hooks/pre-commit (make executable)
  # Example: run gitleaks or detect-secrets
  gitleaks protect --staged || { echo "Secrets detected!"; exit 1; }
  ```
* **Repo/Org policy**: require PR reviews; block direct pushes to `main`.
* **Enable secret scanning & push protection** in the host platform.
* **Use environment secrets** (CI/CD secrets store, cloud KMS) instead of hardcoding.

---

**Q18: How do you find exactly which commit introduced the leaked secret?**
**A:**

* If you know part of the token:

  ```bash
  git log -S "partial_token_here" --source --all
  ```
* Binary or unknown content: use **gitleaks/trufflehog** to list offending commits and files.

---

## 🔹 9. Advanced Scenarios

**Q16: How do you restore a deleted file from Git history?**
**A:**

```bash
git checkout origin/master -- path/to/file
```

Or reset entire branch:

```bash
git reset --hard origin/master
```

**Q17: How do you roll back to a previous commit but keep changes staged?**
**A:**

```bash
git reset --soft <commit_id>
```

**Q18: How do you identify the commit that introduced a bug?**
**A:** Use `git bisect`:

```bash
git bisect start
git bisect bad          # mark current commit as bad
git bisect good <hash>  # mark known good commit
```

Git will help find the problematic commit.

---

✅ This covers **branching strategies, rebase, stash, conflicts, hooks, and security** scenarios — aligned for 2–3 years experience interviews.
