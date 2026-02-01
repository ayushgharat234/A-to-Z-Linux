# Remote Access with SSH

Secure Shell (SSH) is the primary way to manage Linux servers remotely.

---

## 1. Connecting to a Server

**Syntax**: `ssh user@host`

```bash
ssh root@192.168.1.5
ssh ayush@devserver.com
```

### Common Flags
*   `-p 2222`: Specify a custom port (default is 22).
*   `-i key.pem`: Use a specific identity file (private key).

---

## 2. SSH Keys (Passwordless Login)

Typing passwords every time is tedious and less secure. Keys are better.

### Step 1: Generate a Key Pair
Run this on your **local machine**.
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
*   **Public Key** (`.pub`): Shared with servers (The Lock).
*   **Private Key**: Kept secret on your machine (The Key).

### Step 2: Copy Public Key to Server
```bash
ssh-copy-id ayush@remote_server
```
Now you can log in without a password!

---

## 3. SSH Configuration (`~/.ssh/config`)

Instead of typing:
`ssh -i ~/.ssh/mykey.pem ubuntu@ec2-54-123-45-67.compute-1.amazonaws.com`

You can configure aliases.

**Edit `~/.ssh/config`:**
```config
Host myserver
    HostName ec2-54-123-45-67.compute-1.amazonaws.com
    User ubuntu
    IdentityFile ~/.ssh/mykey.pem
```

**Now just run:**
```bash
ssh myserver
```

---

## 4. Security Best Practices

Edit `/etc/ssh/sshd_config` on the server to harden security:

1.  **Disable Root Login**: `PermitRootLogin no`
2.  **Disable Password Auth**: `PasswordAuthentication no` (Force key-based login).

Always reload SSH after changing config: `sudo systemctl reload ssh`.

---

## Summary
*   Always use SSH keys instead of passwords.
*   Use `~/.ssh/config` to save time.
*   Disable root login on production servers.
