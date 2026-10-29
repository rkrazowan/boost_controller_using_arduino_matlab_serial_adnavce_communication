# How to Upload Any Project to GitHub using Git Bash

A step-by-step beginner-friendly guide on initializing, committing, and pushing any local project folder to a remote **GitHub repository** using **Git Bash** command-line tools.

---

## 📌 Commands Summary

| Step | Command | Description |
| :--- | :--- | :--- |
| **1. Initialize** | `git init` | Initializes an empty local Git repository in the current folder. |
| **2. Check Status** | `git status` | Displays untracked and modified files. |
| **3. Stage Files** | `git add .` | Stages all files and changes for commit. |
| **4. Commit** | `git commit -m "Your Commit Message"` | Saves staged changes with a descriptive message. |
| **5. Add Remote** | `git remote add origin <REPO_URL>` | Links local repository to your remote GitHub repo. |
| **6. Push Code** | `git push -u origin master` *(or `main`)* | Uploads local commits to the remote GitHub branch. |

---

## 🚀 Step-by-Step Tutorial

### Step 1: Create a GitHub Repository
1. Log in to [GitHub](https://github.com/).
2. Click **New Repository** (or the **+** icon at top right).
3. Set a repository name (e.g., `my-cool-project`).
4. Set visibility to **Public** or **Private**.
5. Do **not** initialize with `README`, `.gitignore`, or license if you want to push an existing local folder.
6. Click **Create repository**.
7. Copy the repository URL (e.g., `https://github.com/your-username/my-cool-project.git`).

---

### Step 2: Open Git Bash in Your Project Directory
1. Open File Explorer and navigate to your project folder.
2. Right-click inside the folder and select **Open Git Bash Here**.

---

### Step 3: Initialize Git & Stage Files
In the Git Bash terminal, run:

```bash
# Initialize local repository
git init

# Check untracked files
git status

# Stage all files
git add .

# Re-verify staged files (all files should appear green)
git status
