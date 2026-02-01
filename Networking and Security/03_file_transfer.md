# File Transfer using Command Line

Moving files between servers is a daily task. GUI tools (like FileZilla) exist, but the CLI is faster and scriptable.

---

## 1. SCP (Secure Copy)

Works exactly like `cp`, but over SSH.

**Syntax**: `scp source destination`

```bash
# Upload: Local -> Remote
scp file.txt user@server:/home/user/

# Download: Remote -> Local (Note the dot at the end)
scp user@server:/var/www/html/index.html .

# Recursive (Folders): Use -r
scp -r project_folder/ user@server:/home/user/
```

---

## 2. Rsync (Remote Sync)

Better than `scp` for large files or backups. It only transfers **differences** (deltas).

**Syntax**: `rsync [flags] source destination`

**Common Flags (`-avz`)**:
*   `-a`: Archive mode (preserves permissions, timestamps, etc.).
*   `-v`: Verbose.
*   `-z`: Compression (transfers faster).

```bash
# Sync local folder to remote
rsync -avz my_website/ user@server:/var/www/html/

# Delete files on destination if they don't exist on source
rsync -avz --delete my_website/ user@server:/var/www/html/
```

**Local Backups**:
Rsnyc works locally too!
```bash
rsync -av /home/user/Documents /media/external_drive/backup/
```

---

## 3. SFTP (Secure FTP)
Interactive file transfer session.

```bash
sftp user@server
> put file.txt    # Upload
> get file.txt    # Download
> ls              # List remote files
> lls             # List local files
> bye             # Exit
```

---

## Summary
*   Use `scp` for quick, one-off transfers.
*   Use `rsync` for backups and syncing large directories.
*   Use `sftp` if you prefer an interactive shell.
