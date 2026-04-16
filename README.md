# 🚀 Git & GitHub — Complete Beginner's Tutorial

> **A hands-on, step-by-step guide to mastering Git and GitHub from scratch.**

[![GitHub stars](https://img.shields.io/github/stars/Deekshithb01/Git_learnner?style=social)](https://github.com/Deekshithb01/Git_learnner)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📋 Table of Contents

1. [What Is Git & GitHub?](#-what-is-git--github)
2. [Progress Tracker](#-progress-tracker)
3. [Installation & Setup](#-installation--setup)
4. [Git Basics](#-git-basics)
5. [GitHub Setup](#-github-setup)
6. [Creating a Repository](#-creating-a-repository)
7. [Commit, Push, Pull & Clone](#-commit-push-pull--clone)
8. [Branching & Merging](#-branching--merging)
9. [Pull Requests](#-pull-requests)
10. [Merge Conflicts](#-merge-conflicts)
11. [GitHub Issues](#-github-issues)
12. [GitHub Actions](#-github-actions)
13. [GitHub Pages](#-github-pages)
14. [VS Code & GitHub Desktop Tips](#-vs-code--github-desktop-tips)
15. [Beginner Exercises](#-beginner-exercises)
16. [Troubleshooting](#-troubleshooting)
17. [Quick Reference Cheat Sheet](#-quick-reference-cheat-sheet)

---

## 🤔 What Is Git & GitHub?

| Term       | What it means                                                                 |
|------------|-------------------------------------------------------------------------------|
| **Git**    | A free tool installed on your computer that tracks changes in your code.      |
| **GitHub** | A website that stores your Git repositories online so you can share & collaborate. |

Think of **Git** as a time machine for your code, and **GitHub** as Google Drive for your projects.

---

## ✅ Progress Tracker

Use this checklist as you work through the tutorial:

- [ ] Installed Git on my computer
- [ ] Configured my name and email in Git
- [ ] Created a GitHub account
- [ ] Created my first repository
- [ ] Made my first commit
- [ ] Pushed code to GitHub
- [ ] Cloned a repository
- [ ] Pulled latest changes
- [ ] Created a branch
- [ ] Merged a branch
- [ ] Opened a pull request
- [ ] Resolved a merge conflict
- [ ] Created a GitHub Issue
- [ ] Set up a GitHub Actions workflow
- [ ] Published a site with GitHub Pages

---

## 🛠 Installation & Setup

### Install Git

| OS      | Steps |
|---------|-------|
| **Windows** | Download from [git-scm.com](https://git-scm.com/download/win) and run the installer. |
| **macOS**   | Run `xcode-select --install` in Terminal, or install via [Homebrew](https://brew.sh): `brew install git` |
| **Linux**   | `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora) |

### Verify Installation

```bash
git --version
# Expected output: git version 2.x.x
```

### Configure Your Identity

Git tags every commit with your name and email. Set them once globally:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check your configuration:

```bash
git config --list
```

> 💡 **Tip:** Use `--local` instead of `--global` to set different credentials per project.

---

## 📖 Git Basics

### How Git Tracks Changes

Git uses three areas:

```
Working Directory  →  Staging Area  →  Repository (History)
   (your files)       (git add)          (git commit)
```

### Essential Commands

```bash
git init            # Initialize a new Git repo in the current folder
git status          # See what files have changed
git add <file>      # Stage a specific file
git add .           # Stage ALL changed files
git commit -m "message"   # Save staged changes with a description
git log             # View commit history
git log --oneline   # Compact one-line history
```

### Undoing Changes

```bash
git restore <file>          # Discard changes in working directory
git restore --staged <file> # Unstage a file (keep changes)
git revert <commit-hash>    # Create a new commit that undoes a previous one
git reset --soft HEAD~1     # Undo last commit but keep changes staged
```

> ⚠️ **Warning:** Avoid `git reset --hard` on shared branches — it rewrites history for everyone.

---

## 🐙 GitHub Setup

1. Go to [github.com](https://github.com) and click **Sign up**.
2. Choose a username, enter your email, and create a password.
3. Verify your email address.

### Connect Git to GitHub with SSH (Recommended)

```bash
# 1. Generate an SSH key
ssh-keygen -t ed25519 -C "you@example.com"
# Press Enter to accept defaults

# 2. Copy the public key
cat ~/.ssh/id_ed25519.pub

# 3. Add it to GitHub:
#    GitHub → Settings → SSH and GPG Keys → New SSH Key → Paste → Save

# 4. Test the connection
ssh -T git@github.com
# Expected: Hi <username>! You've successfully authenticated...
```

### Alternative: Use HTTPS with a Personal Access Token

If you prefer HTTPS, generate a token at **GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)** and use it as your password when prompted.

---

## 📁 Creating a Repository

### On GitHub (Recommended for Beginners)

1. Click the **+** icon → **New repository**.
2. Enter a repository name (e.g., `my-first-repo`).
3. Choose **Public** or **Private**.
4. Check **Add a README file**.
5. Click **Create repository**.

### On Your Computer

```bash
mkdir my-first-repo
cd my-first-repo
git init
echo "# My First Repo" > README.md
git add README.md
git commit -m "Initial commit"
```

Then link it to GitHub:

```bash
git remote add origin git@github.com:YourUsername/my-first-repo.git
git branch -M main
git push -u origin main
```

> 💡 **Tip:** `git remote -v` shows the remote URLs linked to your local repo.

---

## 🔄 Commit, Push, Pull & Clone

### The Daily Workflow

```bash
# 1. Check what changed
git status

# 2. Stage changes
git add .

# 3. Commit with a meaningful message
git commit -m "Add login form validation"

# 4. Push to GitHub
git push
```

### Clone an Existing Repository

```bash
git clone git@github.com:YourUsername/my-first-repo.git
# Or with HTTPS:
git clone https://github.com/YourUsername/my-first-repo.git

cd my-first-repo   # Enter the cloned folder
```

### Pull Latest Changes

Always pull before starting new work to stay in sync with teammates:

```bash
git pull
```

### Writing Good Commit Messages

| ❌ Bad                  | ✅ Good                              |
|------------------------|--------------------------------------|
| `fix stuff`            | `Fix null pointer in login handler`  |
| `update`               | `Update README with setup steps`     |
| `asdfgh`               | `Add unit tests for cart service`    |

> 💡 **Convention:** Use the imperative mood — *"Add feature"*, not *"Added feature"*.

---

## 🌿 Branching & Merging

Branches let you work on features or fixes in isolation without affecting the main codebase.

### Branch Commands

```bash
git branch                     # List all local branches
git branch feature/login       # Create a new branch
git switch feature/login       # Switch to the branch
git switch -c feature/signup   # Create AND switch in one command

git merge feature/login        # Merge a branch into the current branch
git branch -d feature/login    # Delete a merged branch
git branch -D feature/login    # Force-delete an unmerged branch
```

### Typical Branch Workflow

```bash
# Start on main, pull latest changes
git switch main
git pull

# Create a feature branch
git switch -c feature/add-navbar

# ... make changes ...
git add .
git commit -m "Add responsive navbar"

# Push the branch to GitHub
git push -u origin feature/add-navbar

# After review & merge, clean up
git switch main
git pull
git branch -d feature/add-navbar
```

> 💡 **Best Practice:** Never commit directly to `main`. Always use a feature branch.

---

## 🔀 Pull Requests

A **Pull Request (PR)** is a request to merge your branch into another branch. It's the heart of GitHub collaboration.

### How to Open a Pull Request

1. Push your branch to GitHub (`git push -u origin feature/your-branch`).
2. Go to your repository on GitHub.
3. Click the **"Compare & pull request"** button that appears.
4. Fill in a **title** and **description** explaining what you changed and why.
5. Assign **reviewers** if working with a team.
6. Click **"Create pull request"**.

### Good PR Description Template

```markdown
## What does this PR do?
Adds a responsive navbar with mobile hamburger menu.

## Why?
Fixes #12 — the current header breaks on screens < 768px.

## How to test
1. Clone the branch
2. Open index.html in a browser
3. Resize the window below 768px and verify the hamburger menu appears
```

### Reviewing & Merging

- **Review:** Collaborators can comment on specific lines.
- **Approve:** Click **"Review changes"** → **"Approve"**.
- **Merge:** Click **"Merge pull request"** → **"Confirm merge"**.
- **Delete branch:** Click **"Delete branch"** to keep things tidy.

---

## ⚔️ Merge Conflicts

A merge conflict happens when two branches change the same part of the same file.

### Identifying a Conflict

```bash
git merge feature/navbar
# CONFLICT (content): Merge conflict in index.html
# Automatic merge failed; fix conflicts and then commit the result.
```

### What a Conflict Looks Like

```
<<<<<<< HEAD
<h1>Welcome to My Site</h1>
=======
<h1>Hello World</h1>
>>>>>>> feature/navbar
```

- `<<<<<<< HEAD` — your current branch's version
- `=======` — the divider
- `>>>>>>> feature/navbar` — the incoming branch's version

### Resolving a Conflict

1. Open the conflicting file in your editor.
2. Choose which version to keep (or combine both), and **delete the conflict markers**.
3. Save the file.
4. Stage and commit the resolution:

```bash
git add index.html
git commit -m "Resolve merge conflict in index.html"
```

> 💡 **VS Code Tip:** VS Code highlights conflicts and offers one-click buttons: *Accept Current Change*, *Accept Incoming Change*, *Accept Both Changes*.

---

## 🐛 GitHub Issues

Issues are used to track bugs, feature requests, and tasks.

### Creating an Issue

1. Go to your repository → **Issues** tab → **New Issue**.
2. Write a clear **title** and **description**.
3. Add **labels** (e.g., `bug`, `enhancement`, `documentation`).
4. Assign it to a team member if needed.

### Closing Issues via Commits

Reference an issue number in your commit or PR message to automatically close it when merged to `main`:

```bash
git commit -m "Fix navbar overflow, closes #12"
```

Keywords that close issues: `closes`, `fixes`, `resolves` (case-insensitive).

### Issue Template Example

```markdown
**Describe the bug**
The navbar overflows on mobile screens.

**Steps to reproduce**
1. Open index.html
2. Resize the browser to < 768px
3. See the horizontal scrollbar

**Expected behavior**
Navbar collapses into a hamburger menu.

**Screenshots**
(attach screenshot here)
```

---

## ⚙️ GitHub Actions

GitHub Actions automates workflows — running tests, deploying code, sending notifications, and more.

### Creating Your First Workflow

1. In your repo, create the directory `.github/workflows/`.
2. Create a file, e.g., `ci.yml`.

### Example: Run Tests on Every Push

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

3. Commit and push this file. Go to the **Actions** tab in your repo to see the workflow run.

> 💡 **Tip:** GitHub provides many free starter workflows. Click **Actions** → **New workflow** to browse templates.

---

## 🌐 GitHub Pages

GitHub Pages lets you publish a website directly from your repository — for free!

### Publishing a Static Site

1. Go to your repo → **Settings** → **Pages**.
2. Under **Source**, select **Deploy from a branch**.
3. Choose the `main` branch and `/ (root)` folder. Click **Save**.
4. Your site will be live at `https://YourUsername.github.io/your-repo-name/` within a minute.

### Quick Example: Personal Portfolio

```bash
# Create a simple index.html
echo "<!DOCTYPE html>
<html>
  <head><title>My Portfolio</title></head>
  <body><h1>Hello, I'm learning Git!</h1></body>
</html>" > index.html

git add index.html
git commit -m "Add homepage"
git push
```

Then enable GitHub Pages as described above.

> 💡 **Tip:** Use [Jekyll](https://jekyllrb.com/) or a static site generator for more powerful GitHub Pages sites.

---

## 💻 VS Code & GitHub Desktop Tips

### VS Code

| Feature | How to Use |
|---------|-----------|
| **Source Control Panel** | Click the branch icon (Ctrl+Shift+G) to see changes, stage files, and commit without typing commands. |
| **Inline Diff** | Click a changed file in the Source Control panel to see a side-by-side diff. |
| **Conflict Resolution** | Conflict markers are highlighted with action buttons (*Accept Current*, *Accept Incoming*, *Accept Both*). |
| **GitLens Extension** | Install **GitLens** from the Extensions marketplace for powerful blame, history, and comparison views. |
| **Built-in Terminal** | Press Ctrl+` to open a terminal inside VS Code and run Git commands without switching windows. |

### GitHub Desktop

| Feature | How to Use |
|---------|-----------|
| **Clone Repo** | File → Clone repository → paste URL |
| **Create Branch** | Click the current branch name → **New Branch** |
| **Commit** | Stage files in the left panel, write a message at the bottom, click **Commit to \<branch\>** |
| **Push/Pull** | Click **Push origin** or **Fetch origin** in the toolbar |
| **Open in VS Code** | Repository → Open in Visual Studio Code |

> 💡 **Recommendation:** Start with GitHub Desktop to learn the concepts visually, then graduate to the command line for speed and power.

---

## 🏋️ Beginner Exercises

Complete these exercises in order to solidify your skills:

### Exercise 1 — Your First Repo
1. Create a new folder called `practice-repo` on your computer.
2. Initialize a Git repository inside it.
3. Create a file called `hello.txt` containing `Hello, Git!`.
4. Stage and commit it with the message `"Add hello.txt"`.

### Exercise 2 — GitHub Push
1. Create a new **public** repository called `practice-repo` on GitHub.
2. Link your local repo to it (`git remote add origin ...`).
3. Push your commit to GitHub.
4. Verify the file appears on GitHub.

### Exercise 3 — Branching
1. Create a branch called `feature/greeting`.
2. Edit `hello.txt` to say `Hello, Git and GitHub!`.
3. Commit the change on that branch.
4. Merge the branch back into `main`.

### Exercise 4 — Pull Request
1. Push `feature/greeting` to GitHub **before** merging.
2. Open a Pull Request on GitHub from `feature/greeting` → `main`.
3. Review the diff, then merge the PR on GitHub.
4. Pull the merged changes back to your local `main`.

### Exercise 5 — Simulate a Conflict
1. Create two branches from `main`: `branch-a` and `branch-b`.
2. On `branch-a`, change the first line of `hello.txt` to `Hi from Branch A!`.
3. On `branch-b`, change the same line to `Hi from Branch B!`.
4. Merge `branch-a` into `main`, then try to merge `branch-b` into `main`.
5. Resolve the conflict and complete the merge.

### Exercise 6 — GitHub Actions
1. Add a `.github/workflows/hello.yml` file to your repo.
2. Create a workflow that prints `Hello from GitHub Actions!` using `echo`.
3. Push and watch it run in the **Actions** tab.

---

## 🔧 Troubleshooting

### `git push` is rejected

```
! [rejected] main -> main (fetch first)
```

**Cause:** Remote has commits your local branch doesn't have.  
**Fix:**
```bash
git pull --rebase
git push
```

---

### `Permission denied (publickey)`

**Cause:** SSH key isn't set up or isn't added to GitHub.  
**Fix:** Follow the [SSH setup steps](#connect-git-to-github-with-ssh-recommended) above, then run `ssh -T git@github.com` to verify.

---

### `Please tell me who you are`

```
Author identity unknown
```

**Fix:**
```bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

---

### Accidentally committed to `main`

**Fix (if not pushed yet):**
```bash
git branch feature/my-work   # Save work to a new branch
git reset --soft HEAD~1       # Undo the commit on main (keep changes staged)
git restore --staged .        # Unstage everything
git switch feature/my-work    # Switch to the new branch
git add .
git commit -m "Move work to correct branch"
```

---

### `detached HEAD` state

**Cause:** You checked out a specific commit instead of a branch.  
**Fix:**
```bash
git switch main   # Go back to main branch
```

---

### Large file rejected by GitHub

GitHub blocks files larger than 100 MB.  
**Fix:** Use [Git LFS](https://git-lfs.github.com/) for large assets, or add the file to `.gitignore`.

---

## 📌 Quick Reference Cheat Sheet

```bash
# ── SETUP ──────────────────────────────────────────────────
git config --global user.name "Name"
git config --global user.email "email"

# ── STARTING ───────────────────────────────────────────────
git init                          # New local repo
git clone <url>                   # Copy remote repo locally

# ── DAILY WORKFLOW ─────────────────────────────────────────
git status                        # What changed?
git add .                         # Stage all changes
git add <file>                    # Stage one file
git commit -m "message"           # Save snapshot
git push                          # Upload to GitHub
git pull                          # Download from GitHub

# ── BRANCHES ───────────────────────────────────────────────
git branch                        # List branches
git switch -c <branch>            # Create & switch
git switch <branch>               # Switch branch
git merge <branch>                # Merge into current
git branch -d <branch>            # Delete merged branch

# ── HISTORY & DIFFS ────────────────────────────────────────
git log --oneline                 # Compact history
git diff                          # Unstaged changes
git diff --staged                 # Staged changes

# ── UNDOING ────────────────────────────────────────────────
git restore <file>                # Discard working changes
git restore --staged <file>       # Unstage a file
git revert <hash>                 # Undo commit (safe)
git reset --soft HEAD~1           # Undo last commit (keep changes)

# ── REMOTE ─────────────────────────────────────────────────
git remote -v                     # Show remotes
git remote add origin <url>       # Link to GitHub
git push -u origin <branch>       # Push new branch
```

---

## 🎉 You're on Your Way!

You've covered everything from `git init` to GitHub Actions and GitHub Pages. The best way to learn Git is to **use it every day** — even for personal projects, notes, or homework.

**Next steps:**
- ⭐ Star this repo if it helped you!
- 🍴 Fork it and add your own notes
- 📣 Share it with a friend learning to code
- 🔗 Explore [GitHub Skills](https://skills.github.com/) for interactive courses
- 📚 Read the [Pro Git Book](https://git-scm.com/book/en/v2) (free online)

---

*Made with ❤️ for beginners everywhere.*