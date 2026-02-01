# Git Basics in Linux

Git is the version control system of the web.

---

## 1. Setup

Configure your identity (do this once).

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

## 2. The Workflow

### Initialize
Turn a folder into a repository.
```bash
git init
```

### Clone
Download an existing repo.
```bash
git clone https://github.com/user/repo.git
```

### The Cycle
1.  **Modify** files.
2.  **Stage** changes:
    ```bash
    git add file.txt
    git add .  # Stage all
    ```
3.  **Commit** changes:
    ```bash
    git commit -m "Fixed bug in login"
    ```
4.  **Push** to remote (GitHub/GitLab):
    ```bash
    git push origin main
    ```

---

## 3. Branching

Don't push straight to main! Use branches.

```bash
# Create and switch to a new branch
git switch -c feature-login

# Switch back
git switch main

# Merge feature into main
git merge feature-login
```

---

## 4. Ignoring Files (`.gitignore`)

Create a file named `.gitignore` to prevent secret keys or build artifacts from being uploaded.

**Example `.gitignore`:**
```text
node_modules/
.env
__pycache__/
*.log
```

---

## Summary
*   `git init` -> `git add` -> `git commit`.
*   Never commit secrets (use `.gitignore`).
*   Work on branches.
