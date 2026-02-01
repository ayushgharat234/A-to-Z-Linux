# Security Hardening Basics

Linux is secure by design, but you must configure it correctly to keep it that way.

---

## 1. Principle of Least Privilege

Never log in as root for daily tasks.
*   **Bad**: Running everything as `root` (UID 0).
*   **Good**: Using a standard user and `sudo` only when needed.

---

## 2. SSH Hardening

SSH is the front door. Lock it.

### Best Practices (Edit `/etc/ssh/sshd_config`)
1.  **Change the Port**: Run SSH on port 2222 (or similar) to avoid scanning scripts.
    ```text
    Port 2222
    ```
2.  **Disable Root Login**:
    ```text
    PermitRootLogin no
    ```
3.  **Use Keys Only**:
    ```text
    PasswordAuthentication no
    ```
4.  **Allow Specific Users**:
    ```text
    AllowUsers ayush deploy_bot
    ```

---

## 3. Fail2Ban

Install `fail2ban` to automatically ban IPs that show malicious signs (like too many failed password attempts).

```bash
sudo apt install fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

---

## 4. Automatic Updates

Security patches are useless if you don't install them. Use `unattended-upgrades`.

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

---

## Summary
*   Don't use root.
*   Harden SSH config.
*   Use Fail2Ban to block brute-force attacks.
*   Keep the system updated.
