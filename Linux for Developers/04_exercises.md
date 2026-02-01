# Linux for Developers: Practice Set

---

## Level 1: Git Mastery

### 1. The Setup
*   Initialize a new git repository in a folder called `git-practice`.
*   Create a file `main.py` and commit it.
*   Create a file `secrets.env`.
*   Create a `.gitignore` to ensure `secrets.env` is **never** tracked.
*   Run `git status` to verify.

### 2. Branching
*   Create a branch `feature-x`.
*   Switch to it.
*   Add a new file `feature.txt` and commit.
*   Switch back to `main`.
*   Merge `feature-x` into `main`.

---

## Level 2: Docker Dojo

### 3. The Web Server
*   Run an Nginx container in the background (`-d`).
*   Map port 8080 on your host to port 80 in the container (`-p`).
*   Open your browser (or use `curl`) to visit `localhost:8080`. Did it work?
*   Stop and remove the container.

### 4. The Builder
*   Create a file named `Dockerfile`.
*   Use `FROM ubuntu:latest`.
*   Run a command to install `python3`.
*   Build the image with the tag `my-python-image`.
*   Run it interactively.

---

## Level 3: Environment

### 5. Virtual Environments
*   Create a Python virtual environment called `sandbox`.
*   Activate it.
*   Install a package (like `colorama`).
*   Verify where python is running from (`which python`). It should be inside `sandbox`.
*   Deactivate.

---

## Tip
Git and Docker are the bread and butter of modern software engineering. Muscle memory here pays off!
