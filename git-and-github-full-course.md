
---

# Comprehensive Git and GitHub Course

## Introduction
Git is a distributed version control system that allows you to track changes in your code, collaborate with others, and manage projects efficiently. GitHub is a platform built on top of Git that provides hosting for Git repositories, collaboration tools, and more. In this course, you’ll learn Git from scratch and how to use GitHub effectively.

### Prerequisites
- A computer (Windows, macOS, or Linux)
- Basic command-line knowledge (optional but helpful)
- A GitHub account (free tier is fine)

---

## Table of Contents
1. [Installing Git](#1-installing-git)
2. [Git Basics](#2-git-basics)
   - [What is Version Control?](#what-is-version-control)
   - [Configuring Git](#configuring-git)
   - [Initializing a Repository](#initializing-a-repository)
   - [Staging and Committing](#staging-and-committing)
   - [Viewing History](#viewing-history)
3. [Working with Branches](#3-working-with-branches)
   - [Creating and Switching Branches](#creating-and-switching-branches)
   - [Merging Branches](#merging-branches)
   - [Handling Merge Conflicts](#handling-merge-conflicts)
4. [Undoing Changes](#4-undoing-changes)
   - [Unstaging Files](#unstaging-files)
   - [Reverting Commits](#reverting-commits)
   - [Resetting Changes](#resetting-changes)
5. [Introduction to GitHub](#5-introduction-to-github)
   - [Setting Up a GitHub Account](#setting-up-a-github-account)
   - [Creating a Repository](#creating-a-repository)
   - [Pushing to GitHub](#pushing-to-github)
   - [Cloning and Forking](#cloning-and-forking)
6. [Collaboration on GitHub](#6-collaboration-on-github)
   - [Pull Requests](#pull-requests)
   - [Issues and Project Boards](#issues-and-project-boards)
   - [Collaborating with Teams](#collaborating-with-teams)
7. [Advanced Git Concepts](#7-advanced-git-concepts)
   - [Rebasing](#rebasing)
   - [Stashing](#stashing)
   - [Cherry-Picking](#cherry-picking)
   - [Git Tags](#git-tags)
8. [Best Practices](#8-best-practices)
9. [Troubleshooting](#9-troubleshooting)
10. [Resources](#10-resources)

---

## 1. Installing Git

### Step 1: Download Git
- Go to [git-scm.com](https://git-scm.com/).
- Download the version for your operating system (Windows, macOS, or Linux).
- Run the installer and follow the prompts. Default settings are usually fine for beginners.

### Step 2: Verify Installation
Open a terminal (Command Prompt, PowerShell, or Terminal) and type:
```bash
git --version
```
You should see something like `git version 2.43.0`. If not, reinstall Git.

---

## 2. Git Basics

### What is Version Control?
Version control systems (VCS) track changes to files over time. Git is a distributed VCS, meaning every user has a full copy of the repository, including its history.

### Configuring Git
Before using Git, set up your identity:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
- `--global` applies these settings to all Git projects on your machine.
- Check your config with:
```bash
git config --list
```

### Initializing a Repository
A repository (repo) is a directory where Git tracks changes.
1. Create a new folder:
```bash
mkdir my-project
cd my-project
```
2. Initialize Git:
```bash
git init
```
This creates a hidden `.git` folder that stores the repository’s data.

### Staging and Committing
Git uses a three-step workflow:
1. **Working Directory**: Your project files.
2. **Staging Area**: Files ready to be committed.
3. **Commit History**: Permanent snapshots of changes.

- Add a file (e.g., `index.html`):
```bash
echo "<h1>Hello Git</h1>" > index.html
```
- Stage the file:
```bash
git add index.html
```
- Commit the change:
```bash
git commit -m "Initial commit"
```
- `-m` specifies a commit message (keep it short and descriptive).

### Viewing History
- Check the status of your repo:
```bash
git status
```
- View commit history:
```bash
git log
```
- For a compact view:
```bash
git log --oneline
```

---

## 3. Working with Branches

### Creating and Switching Branches
Branches allow you to work on different features or fixes independently.
- Create a new branch:
```bash
git branch feature-branch
```
- Switch to it:
```bash
git checkout feature-branch
```
- Or combine both steps:
```bash
git checkout -b feature-branch
```
- List all branches:
```bash
git branch
```

### Merging Branches
To combine changes from one branch into another:
1. Switch to the target branch (e.g., `main`):
```bash
git checkout main
```
2. Merge the feature branch:
```bash
git merge feature-branch
```
- If there are no conflicts, Git merges automatically.

### Handling Merge Conflicts
Conflicts occur when the same part of a file is changed differently in two branches.
1. Git will pause the merge and mark conflicts in the file:
```plaintext
<<<<<<< HEAD
<p>Main content</p>
=======
<p>Feature content</p>
>>>>>>> feature-branch
```
2. Edit the file to resolve the conflict, then:
```bash
git add <file>
git commit
```

---

## 4. Undoing Changes

### Unstaging Files
If you accidentally staged a file:
```bash
git restore --staged <file>
```

### Reverting Commits
To undo a commit but keep changes in the working directory:
```bash
git revert <commit-hash>
```
Find the hash with `git log`.

### Resetting Changes
- Discard uncommitted changes:
```bash
git restore <file>
```
- Reset to a previous commit (careful, this rewrites history):
```bash
git reset --hard <commit-hash>
```

---

## 5. Introduction to GitHub

### Setting Up a GitHub Account
- Go to [github.com](https://github.com) and sign up.
- Verify your email.

### Creating a Repository
1. Click “New” on GitHub’s homepage.
2. Name your repo (e.g., `my-project`).
3. Choose public or private, then click “Create repository.”

### Pushing to GitHub
1. Link your local repo to GitHub:
```bash
git remote add origin https://github.com/username/my-project.git
```
2. Push your code:
```bash
git push -u origin main
```
- `-u` sets the upstream branch for future pushes.

### Cloning and Forking
- **Clone**: Copy a repo to your local machine:
```bash
git clone https://github.com/username/my-project.git
```
- **Fork**: Copy someone else’s repo to your GitHub account via the “Fork” button on GitHub.

---

## 6. Collaboration on GitHub

### Pull Requests
A pull request (PR) lets you propose changes to a repo.
1. Push a branch to GitHub:
```bash
git push origin feature-branch
```
2. On GitHub, click “Compare & pull request.”
3. Add a description and submit.

### Issues and Project Boards
- **Issues**: Report bugs or suggest features via the “Issues” tab.
- **Project Boards**: Organize tasks using GitHub’s Kanban-style boards.

### Collaborating with Teams
- Add collaborators via the “Settings” tab in your repo.
- Use `@mentions` in issues/PRs to notify team members.

---

## 7. Advanced Git Concepts

### Rebasing
Rebasing rewrites history by moving your branch’s base:
```bash
git checkout feature-branch
git rebase main
```
- Resolve conflicts if they arise, then:
```bash
git rebase --continue
```

### Stashing
Temporarily save uncommitted changes:
```bash
git stash
```
- Retrieve them later:
```bash
git stash pop
```

### Cherry-Picking
Apply a specific commit from one branch to another:
```bash
git cherry-pick <commit-hash>
```

### Git Tags
Mark a specific commit (e.g., for releases):
```bash
git tag v1.0.0
git push origin v1.0.0
```

---

## 8. Best Practices
- Write clear, concise commit messages (e.g., “Fix login bug”).
- Commit often but logically (one change per commit).
- Use branches for features or fixes.
- Pull before pushing to avoid conflicts:
```bash
git pull origin main
```
- Keep your main branch stable.

---

## 9. Troubleshooting
- **“Detached HEAD”**: You’re not on a branch. Checkout a branch:
```bash
git checkout main
```
- **Merge conflicts**: Manually edit files and commit.
- **Push rejected**: Pull first, resolve conflicts, then push again.

---

## 10. Resources
- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Learning Lab](https://lab.github.com/)
- [Pro Git Book](https://git-scm.com/book/en/v2) (free online)
Here you go, Haile — **clean, exam-ready notes** on all the key Git operations you asked about. This will help you move confidently when handling branches, conflicts, remotes, and more.

---

# **📘 Git Branch & Conflict Handling — Complete Notes**

## **1. Renaming a Branch**

### **A. Rename the branch you are currently on**

```bash
git branch -m new-branch-name
```

### **B. Rename a branch you are not currently on**

```bash
git branch -m old-branch-name new-branch-name
```

### **C. Rename a branch that exists on a remote**

1. Rename locally:

   ```bash
   git branch -m old-name new-name
   ```

2. Delete the old branch name from remote:

   ```bash
   git push origin --delete old-name
   ```

3. Push the renamed one:

   ```bash
   git push origin new-name
   ```

4. Set upstream:

   ```bash
   git push --set-upstream origin new-name
   ```

---

## **2. Deleting Branches**

### **A. Delete a local branch**

```bash
git branch -d branch-name
```

💡 Use `-D` to force-delete:

```bash
git branch -D branch-name
```

### **B. Delete a remote branch**

```bash
git push origin --delete branch-name
```

---

# **3. Handling Merge Conflicts During Pull**

Git sometimes stops pulling because both your local and remote branches changed the same lines.
You can choose to: **keep local changes**, or **accept incoming remote changes**.

---

## **A. Accept ALL Local Changes while pulling**

This means *your local code overwrites whatever is on the remote*.

### **Method 1 — Using merge strategy**

```bash
git pull -X ours
```

✔ Keeps your local code
✔ Uses remote commits only for merge structure
✖ Remote file content is ignored

---

## **B. Accept ALL Incoming / Remote Changes while pulling**

This means *remote overwrites everything on your machine*.

### **Method 1 — Using merge strategy**

```bash
git pull -X theirs
```

✔ Keeps remote code
✔ Ignores conflicting local content

---

## **C. Completely discard local changes and force your branch to match remote**

```bash
git fetch origin
git reset --hard origin/branch-name
```

⚠ *This deletes ALL local changes.*

---

# **4. Switching to a Remote Branch**

Remote branches can’t be switched directly — you have to create a local tracking branch.

### **A. First fetch the remote branches**

```bash
git fetch
```

### **B. Create a local branch that tracks a remote branch**

```bash
git checkout -b local-branch-name origin/remote-branch-name
```

### **Example**

Switching to remote branch `dev`:

```bash
git checkout -b dev origin/dev
```

---

# **5. Other Important Notes**

## **A. View all branches (local + remote)**

```bash
git branch -a
```

## **B. View only remote branches**

```bash
git branch -r
```

## **C. Set an upstream branch**

If your local branch is not linked:

```bash
git push --set-upstream origin branch-name
```

## **D. Rename the default branch (e.g., master → main)**

```bash
git branch -m master main
git push -u origin main
git push origin --delete master
```

## **E. See which branch you are on**

```bash
git status
```

## **F. Show the last commits in graph format**

```bash
git log --oneline --graph --all
```

## **G. Stash local changes before switching branches**

```bash
git stash
```

Restore later:

```bash
git stash pop
```

---

# **Need this as a printable PDF?**

Say **"convert this to PDF"** and I’ll generate it instantly.


---

## Conclusion
You’ve now learned the essentials of Git and GitHub! Practice these commands by creating a small project, collaborating with friends, or contributing to open-source repos. Git is a powerful tool, and mastery comes with consistent use. Happy coding!

--- 

tion!
