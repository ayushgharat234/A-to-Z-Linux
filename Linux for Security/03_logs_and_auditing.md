# Logs and Auditing

To detect potential breaches, you must know what is happening on your system.

---

## 1. Key Log Files (`/var/log/`)

*   `/var/log/syslog` (or `messages`): General system events.
*   `/var/log/auth.log` (or `secure`): **Authentication attempts** (SSH logins, sudo usage).
*   `/var/log/dmesg`: Kernel boot messages.
*   `/var/log/nginx/access.log`: Web server traffic.

---

## 2. Checking Logs

### Live Monitoring
Use `tail -f` to see logs as they happen.
```bash
tail -f /var/log/auth.log
```

### Journalctl (Systemd Logs)
Modern Linux uses `journald` to collect logs.

```bash
# Show all logs
journalctl

# Show logs for specific service
journalctl -u ssh

# Show logs from current boot only
journalctl -b

# Follow live output (like tail -f)
journalctl -f
```

---

## 3. Auditing Users

### Who is logged in?
```bash
w
# or
who
```

### Who logged in previously?
```bash
last
```

### Who failed to log in?
```bash
lastb
# (Usually requires root)
```

---

## Summary
*   Check `/var/log/auth.log` for suspicious logins.
*   Use `journalctl -u service` to debug crash services.
*   Use `last` to audit user activity.
