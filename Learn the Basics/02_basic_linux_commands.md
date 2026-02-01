# Basic Linux Commands

Welcome to your first steps in the Linux terminal. This section introduces fundamental commands that every Linux user must know. These commands are the building blocks for navigating and managing the filesystem.

---

## File and Directory Management

Understanding how to navigate and manage files is crucial. In Linux, everything is a file—documents, commands, and even devices.

### Navigation Commands

**1. `pwd` - Print Working Directory**

Displays the full path to your current location in the filesystem.

```bash
pwd
# Output: /home/user/Documents
```

**2. `ls` - List Directory Contents**

Lists files and directories.

```bash 
ls           # List files
ls -l        # Long format (size, permissions, date)
ls -a        # Show hidden files (starting with .)
ls -lh       # Long format with human-readable sizes (MB, GB)
```

**3. `cd` - Change Directory**

Used to switch between directories.

```bash
cd Documents      # Go to Documents
cd ..             # Go up one level
cd /              # Go to the root directory
cd ~              # Go to your home directory
cd -              # Go back to the previous directory
```

### Creating and Managing Directories

**1. `mkdir` - Make Directory**

Creates a new folder.

```bash
mkdir projects
mkdir -p dev/python/src     # Create nested directories at once
```

**2. `rmdir` - Remove Directory**

Removes an **empty** directory.

```bash
rmdir projects
```

**3. `rm` - Remove Files and Directories**

*   `rm file.txt`: Delete a file.
*   `rm -r folder/`: Recursively delete a folder and its contents.
*   `rm -rf folder/`: Force recursively delete (use with caution).

### File Manipulation

**1. `touch` - Create Empty File**

Updates the timestamp of a file or creates it if it doesn't exist.

```bash
touch newfile.txt
```

**2. `cp` - Copy Files**

```bash
cp source.txt dest.txt
cp -r source_folder/ dest_folder/    # Copy directory recursively
```

**3. `mv` - Move or Rename**

```bash
mv file.txt /tmp/           # Move file
mv oldname.txt newname.txt  # Rename file
```

---

## Viewing and Editing Files

**1. `cat` - Concatenate**

Displays the full content of a file.

```bash
cat file.txt
```

**2. `less` - Paged Viewer**

View large files page-by-page. Use arrow keys to scroll, `q` to quit.

```bash
less huge_log_file.log
```

**3. `head` and `tail`**

*   `head -n 5 file.txt`: Show first 5 lines.
*   `tail -n 5 file.txt`: Show last 5 lines (great for checking new log entries).
*   `tail -f file.txt`: Follow the file as it grows (real-time monitoring).

### Text Editors

**1. `nano`**

A beginner-friendly editor.
*   `nano file.txt` to open.
*   `Ctrl+O` to save, `Ctrl+X` to exit.

**2. `vim`**

A powerful, modal editor.
*   `vim file.txt` to open.
*   Press `i` for Insert mode (to type).
*   Press `Esc` to exit Insert mode.
*   Type `:wq` to save and quit.

---

## Searching and Finding Files

**1. `find`**

Search for files by name, size, type, etc.

```bash
find . -name "*.py"             # Find all Python files in current directory
find /var/log -size +50M        # Find files larger than 50MB
```

**2. `grep`**

Search for specific text *inside* files.

```bash
grep "error" server.log
grep -r "functionName" ./src/   # Recursive search in folder
grep -i "user" file.txt         # Case-insensitive search
```

**3. `which`**

Shows the full path of a command executable.

```bash
which python3
# Output: /usr/bin/python3
```

---

## File Permissions and Ownership

Linux is a multi-user system, so permissions are critical for security.

### Understanding `ls -l`

Running `ls -l` gives output like:
`-rw-r--r-- 1 owner group 4096 Jan 1 12:00 file.txt`

*   **First Char**: `-` (file), `d` (directory).
*   **Next 3 (`rw-`)**: **Owner** permissions (Read, Write, No Execute).
*   **Next 3 (`r--`)**: **Group** permissions (Read only).
*   **Next 3 (`r--`)**: **Others** permissions (Read only).

### Changing Permissions (`chmod`)

You can use numbers (octal) or symbols.

*   **Numeric**:
    *   `7` = Read (4) + Write (2) + Execute (1)
    *   `6` = Read (4) + Write (2)
    *   `chmod 755 script.sh`: Owner gets rwx, everyone else gets rx.

*   **Symbolic**:
    *   `chmod +x script.sh`: Add execute permission for everyone.
    *   `chmod u+w file.txt`: Add write permission for the user (owner).

### Changing Ownership (`chown`)

```bash
sudo chown user:group file.txt
sudo chown -R user:group folder/   # Recursive change
```

---

## File Compression

**1. `tar` (Tape Archive)**

The standard for bundling files.

```bash
tar -cvf archive.tar folder/       # Create archive
tar -xvf archive.tar               # Extract archive
tar -czvf archive.tar.gz folder/   # Create compressed gzip archive
tar -xzvf archive.tar.gz           # Extract gzip archive
```

**2. `zip` and `unzip`**

Commonly used for cross-platform compatibility.

```bash
zip -r data.zip data_folder/
unzip data.zip
```

---

## Wrapping Up

You now have the tools to navigate, manipulate, and secure files in Linux. These commands are the daily drivers for any sysadmin or developer.

Next, we will practice these commands with some problem sets, or you can jump ahead to **Shell Scripting** to start automating your workflow.

