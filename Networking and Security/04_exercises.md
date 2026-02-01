# Networking & Security Exercises

---

## Level 1: Connectivity

### 1. Discovery
*   Find the local IP address of your machine.
*   Find the "Loopback" address. What interface is it on?

### 2. Diagnosis
*   `ping` google.com. What is the time (latency) in ms?
*   `curl` google.com. What happens? Now try `curl -I google.com`. What is the difference?

### 3. Ports
*   Run the command to see all listening ports on your machine.
*   Is port 22 (SSH) open?

---

## Level 2: Remote Access

### 4. The Keymaster
*   Generate an SSH key pair (`id_ed25519`).
*   Check your `~/.ssh/` directory. Can you identify the private key vs public key?
*   *(Bonus)*: If you have two machines (or a VM), try to set up passwordless login using `ssh-copy-id`.

### 5. Config Alias
*   Create an entry in `~/.ssh/config` for a GitHub server or any remote server you use, so you can type `ssh my-server` instead of the full user/IP combo.

---

## Level 3: Transfers

### 6. The Backup Script
*   Create a directory `source` with 5 text files.
*   Create an empty directory `dest`.
*   Use `rsync` to sync them.
*   Modify one file in `source`. Run `rsync` again. Notice how it only copies the changed file?

---

## Tip
Networking is all about connections. If a command hangs, it's usually a Firewall or DNS issue!
