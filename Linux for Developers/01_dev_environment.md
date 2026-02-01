# Setting up a Development Environment

Linux is the preferred OS for developers. Here is how to set up your tools.

---

## 1. The Compiler Collection (`build-essential`)

If you want to compile C/C++ code or install certain Python modules, you need compilers.

```bash
sudo apt update
sudo apt install build-essential
```
This installs `gcc`, `g++`, and `make`.

---

## 2. Python Setup

Most Linux distros come with Python 3 pre-installed.

```bash
python3 --version
```

### Managing Packages (`pip` and `venv`)
Always use virtual environments to avoid messing up system packages.

```bash
# Install venv module
sudo apt install python3-venv

# Create a virtual environment
python3 -m venv myenv

# Activate it
source myenv/bin/activate

# Install packages safely
pip install requests
```

---

## 3. Node.js (Using NVM)

Don't use `apt install nodejs`. It usually installs an ancient version. Use **NVM** (Node Version Manager).

1.  **Install NVM** (Check GitHub for latest curl command).
2.  **Install Node**:
    ```bash
    nvm install --lts
    ```
3.  **Switch Versions**:
    ```bash
    nvm use 16
    nvm use 18
    ```

---

## 4. Text Editors (VS Code)

While `vim` is great, VS Code is key for modern dev.

### Remote SSH Extension
If you are working on a remote Linux server, install the **Remote - SSH** extension in VS Code on your laptop. It allows you to edit files on the server as if they were local!

---

## Summary
*   Install `build-essential` for C/native tools.
*   Use `venv` for Python.
*   Use `nvm` for Node.js.
