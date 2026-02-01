# Flashcards: System Administration

## How to use
Cover the answer column and test your memory.

| Question / Concept | Answer |
| :--- | :--- |
| **File storing user info** | `/etc/passwd` |
| **File storing encrypted passwords** | `/etc/shadow` |
| **Command to add a user** | `useradd` |
| **Command to delete a user + home dir** | `userdel -r` |
| **Command to modify user groups** | `usermod -aG` |
| **Switch user to root** | `sudo su -` |
| **Permission bit: SetUID** | 4000 (s) |
| **Permission bit: Sticky Bit** | 1000 (t) |
| **Command to see running processes** | `ps aux` |
| **Real-time process monitor** | `top` or `htop` |
| **Signal 15 (SIGTERM)** | Terminate gracefully (Default) |
| **Signal 9 (SIGKILL)** | Force kill |
| **Command to background a process** | `&` |
| **Command to manage services** | `systemctl` |
| **Debian/Ubuntu package manager** | `apt` |
| **Red Hat/CentOS package manager** | `dnf` or `yum` |
| **Command to update package list** | `apt update` |
| **Command to upgrade packages** | `apt upgrade` |
