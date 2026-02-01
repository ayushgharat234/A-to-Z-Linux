# System Administration Exercises

These scenarios mimic real-world tasks you'll handle as a SysAdmin.

---

## Level 1: User Management

### 1. New Hire Onboarding
*   Create a user named `junior_dev`.
*   Assign them a home directory and `/bin/bash` as their shell.
*   Create a group called `frontend`.
*   Add `junior_dev` to the `frontend` group.

### 2. Lockout
*   Lock the `junior_dev` account so they cannot log in.
*   Verify the status (check `/etc/shadow` or try to `su`).
*   Unlock the account.

---

## Level 2: Permissions & Safety

### 3. The Secure Report
*   Create a file `finance_report.txt` as your current user.
*   Change the owner to `root` (use sudo).
*   Set permissions so **only** the owner can read/write it, and no one else can do anything (000 for group/others).

### 4. Shared Directory
*   Create a directory `/opt/shared_project`.
*   Create a group `collab`.
*   Change the group capability of the directory to `collab`.
*   Set the **SGID** bit on the directory so any new file created inside belongs to the `collab` group.

---

## Level 3: Process & Service Control

### 5. The Rogue Process
*   Run `sleep 1000 &` in your terminal to create a background process.
*   Find its PID using `ps` or `jobs`.
*   Kill it gracefully (`SIGTERM`).

### 6. Web Server Management
*   Install `nginx` or `apache2` using your package manager.
*   Start the service.
*   Enable it to start on boot.
*   Check its status to ensure it's "active (running)".

### 7. Audit
*   Find all processes running as the `root` user.
*   *(Optional)*: Count how many there are.

---

## Tip
Use `sudo` wisely. In production, double-check every command before hitting Enter!
