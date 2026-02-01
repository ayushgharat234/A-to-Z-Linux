# Process Management

A running instance of a program is called a **process**. As a sysadmin, you must know how to monitor and control them.

---

## 1. Viewing Processes

### Static View: `ps`
Shows a snapshot of current processes.

```bash
ps       # Shows processes in current shell
ps aux   # Shows ALL processes for all users
```

**Common Flags**:
*   `a`: All users.
*   `u`: Display user/owner.
*   `x`: Show processes not attached to a terminal (daemons).

### Dynamic View: `top`
Shows real-time system stats (CPU, Memory).

*   **PID**: Process ID (Unique number).
*   **USER**: Owner.
*   **%CPU / %MEM**: Resource usage.
*   **Command**: The name of the process.

*Tip: `htop` is a colorful, more user-friendly alternative to `top`.*

---

## 2. Controlling Processes

### Killing a Process
Use the `kill` command with a PID.

```bash
kill 1234
```

### Signals
When you run `kill`, you are sending a **signal**.
*   **SIGTERM (15)**: Default. Asks the process to stop nicely (save data, close files).
*   **SIGKILL (9)**: Force kill. Like pulling the power plug. The process cannot ignore this.

```bash
kill -9 1234  # Force kill PID 1234
```

### Killing by Name
*   `killall firefox`: Kills all instances of firefox.
*   `pkill -u john`: Kills all processes owned by user 'john'.

---

## 3. Background Jobs

*   **&**: Run in background.
    ```bash
    python script.py &
    ```
*   **Ctrl+Z**: Pause current foreground process.
*   **bg**: Resume paused process in background.
*   **fg**: Bring background process to foreground.
*   **jobs**: List background jobs.

---

## 4. Managing Services (Systemd)

Most modern Linux systems use **Systemd** to manage background services (daemons) like web servers or databases.

**Command**: `systemctl`

```bash
# Start a service
sudo systemctl start nginx

# Stop a service
sudo systemctl stop nginx

# Restart (Stop + Start)
sudo systemctl restart nginx

# Reload (Reload config without stopping)
sudo systemctl reload nginx

# Enable (Start automatically on boot)
sudo systemctl enable nginx

# Check status
systemctl status nginx
```

---

## Summary
*   Use `top`/`htop` for monitoring.
*   Use `kill` (SIGTERM 15) first, `kill -9` (SIGKILL) only if stuck.
*   Use `systemctl` to manage long-running services.
