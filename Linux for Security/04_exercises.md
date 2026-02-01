# Linux for Security: Practice Set

---

## Level 1: Firewalls

### 1. Lock it Down
*   Check the status of UFW (`sudo ufw status`).
*   Allow port 22 (SSH). **Do this first!**
*   Enable the firewall.
*   Allow port 80 (HTTP).
*   Deny traffic from a specific IP (use `1.2.3.4` as a test).

---

## Level 2: Logging

### 2. The Investigator
*   Try to SSH into your machine with a wrong password 3 times.
*   Open `/var/log/auth.log` (or use `journalctl`).
*   Find the lines corresponding to your failed attempts.
*   Note the IP address logged.

### 3. User Audit
*   Run `last`.
*   Can you tell when the system was last rebooted? (Look for `reboot`).

---

## Level 3: Hardening

### 4. SSH Config
*   Open `/etc/ssh/sshd_config` (don't save changes unless you are sure).
*   Find the line `PermitRootLogin`. Change it to `no`.
*   Find `PasswordAuthentication`. If you have keys setup, change it to `no`.
*   (Don't forget to reload sshd service if you actually save).

---

## Tip
Security is a process, not a product. Regular audits are key!
