
# 💻 Git Setup Instructions for Local Project → GitHub

This document outlines the exact steps to connect a **local folder** to a **new GitHub repository**, especially useful for Windows CMD users.

---

## 🧭 Step-by-Step Instructions

### 🔁 1. Open Command Prompt and Navigate to Project Folder

```cmd
D:
cd D:\Your\Project\Folder\Path
```

Make sure you're inside the folder that contains your project files (e.g., Snowflake notebooks or `.sql` scripts).

---

### 🔃 2. Initialize Git in the Folder

```cmd
git init
```

This sets up Git tracking in the current folder.

---

### 📦 3. Stage Files for Commit

- To stage **all files**:
  ```cmd
  git add .
  ```

- Or to stage a **specific file**:
  ```cmd
  git add "your_file_name.ipynb"
  ```

---

### ✅ 4. Check Git Status (Optional)

```cmd
git status
```

Shows which files are staged, unstaged, or untracked.

---

### 📥 5. Commit the Changes

```cmd
git commit -m "Initial commit"
```

This saves the current staged files to your local Git history.

---

### 🔗 6. Connect to Your GitHub Repository

```cmd
git remote add origin https://github.com/your-username/your-repo.git
```

> Replace the link above with your actual GitHub repository URL.

---

### 🔄 7. Rename Local Branch to Match GitHub

GitHub uses `main` as the default branch, but Git creates `master` by default locally. Fix that:

```cmd
git branch -m main
```

---

### 🚀 8. Push to GitHub

```cmd
git push -u origin main
```

This uploads your code to GitHub and sets `origin/main` as the upstream for future pushes.

---

### ✅ 9. Done!

Go to your GitHub repo and verify the files are there.

---

## 💡 Notes

- You only need to run `git remote add origin` **once per project**.
- The `-u` flag in `git push -u` ensures future `git push` commands don’t need to specify the remote/branch again.

---

### 🧹 Optional Cleanup Later

If you ever want to restart from scratch:

```cmd
rd /s /q .git
```

Then repeat the above steps to reinitialize and push again.

```
| Part   | Meaning                                                              |
| ------ | -------------------------------------------------------------------- |
| `rd`   | Remove Directory                                                     |
| `/s`   | Delete all subfolders and files inside it (recursive)                |
| `/q`   | Quiet mode — no confirmation prompts                                 |
| `.git` | The hidden folder Git uses to track changes, remotes, branches, etc. |
```
- NOTE: Actual files inside the folder will NOT be deleted.
---

### ⚠️ Git Push Rejection Fix

! [rejected]        main -> main (fetch first)
- error: failed to push some refs to 'https://github.com/username/repo'
- hint: Updates were rejected because the remote contains work that you do not
- hint: have locally. This is usually caused by another repository pushing to
- hint: the same ref. If you want to integrate the remote changes, use
- hint: 'git pull' before pushing again.

- This may happen when you created a repo with README and you local doesn't have this. 
- Even if your local has this README file, it may not sync causing this error


#### ✅ The Fix?

Pull the remote changes first using rebase, then push:

```
git pull origin main --rebase
git push origin main

NOTE: git pull origin main --rebase pulls the remote changes and re-applies your local changes on top of them
```
---

Happy coding! 🚀
