# 🖥️ Basic Linux Commands

Welcome to your first steps in the Linux terminal! This section introduces fundamental commands that every Linux user must know.

---

## 📁 File and Directory Management in Linux

```vbnet
These commands are fundamental for navigating and managing the Linux filesystem. They form the foundation for anyone starting with Linux. Don’t overlook them—every recruiter and experienced engineer expects you to know these basics.
```

### 🧭 Navigation Commands

1) `pwd` - Print working directory 

    Displays the full path to your current working directory.
    ```bash
    pwd
    ```
    Output:
    ```vbnet
    /home/ayushgharat/Documents
    ```

2) `ls` - list directory contents

    Lists the files and directories in the current directory.

    ```bash 
    ls
    ```
    Output:
    ```vbnet
    Documents  Downloads  Music  Pictures
    ```

    Useful options:
    - `ls -l`: long format (permission, size, date)
    - `ls -a`: Show hidden files
    - `ls -la`: Combine both


3) `cd` - Change Directory

    Used to switch between directories. 

    ```bash
    $ cd Documents
    $ cd ..          # Go up one directory
    $ cd /           # Go to root
    $ cd ~           # Go to home directory
    ```

### 🏗️ Creating and Managing Directories

1) `mkdir` - Make Directory

    Creates a new directory 
    ```bash
    $ mkdir projects
    $ mkdir -p dev/python     # Create nested directories
    ```

2) `rmdir` - Remove Directory

    Removes an empty directory.
    ```bash
    $ rmdir projects
    ```
    **Note**: Will not work if the directory contains files.

3) `rm -r` - Recursively Remove

    Use this to delete directories with their content.
    ```bash
    $ rm -r projects/
    ```
    **Be cautious**: This permanently deletes files.


### 📦 File Manipulation

1) `touch` - Create an Empty File

    Creates one or more empty files.

    ```bash
    $ touch file.txt
    ```

2) `cp` - Copy Files or Directories

    Copies a file or folder.
    ```bash
    $ cp file.txt backup.txt
    $ cp -r myfolder/ backup_folder/   # Copy a directory recursively
    ```

3) `mv` - Move or Rename Files

    Moves or renames files or directories 
    ```bash
    $ mv file.txt /tmp/
    $ mv oldname.txt newname.txt   # Renaming
    ```

4) `rm` - Remove Files

    Deletes files permanently

    ```bash
    $ rm file.txt
    $ rm -f force_delete.txt      # Force deletion without prompt
    ```

---

## 📝 Viewing and Editing Files

```vbnet
These commands allow you to view, create, and edit text files directly from the command line—an essential skill for working efficiently in any Linux environment.
```

### 🔍 Viewing Files

1) `cat` - Concatenate and Display File content

    Displays the entire content of a file in one go.

    ```bash
    cat file.txt
    ```

    Can also be used to create small files:
    ```bash
    $ cat > newfile.txt
    Type your content here
    Press CTRL + D to save
    ```

2) `less` - View Large Files Page-by-Page

    Allows you to scroll through a file forward and backward.
    ```bash
    less longfile.txt
    ```
    -  Use `↑ ↓`, `PgUp`, `PgDn`, and `press q` to quit.

3) `more` - iew Large Files (Limited)

    Displays one page at a time (like less, but more primitive).
    ```bash
    more file.txt
    ```

    - Space = next page | q = quit | b = back

### ✍️ Editing Files

1) `nano` - Simple Terminal Text Editor

    Beginner-friendly and easy-to-use terminal editor.

    ```bash
    nano file.txt
    ```
    Basic shortcuts:
    - Ctrl + O: Save
    - Ctrl + X: Exit
    - Ctrl + K: Cut line
    - Ctrl + U: Paste line

2) `vi` / `vim` - Advanced Terminal Text Editor

    A powerful and widely used text editor.

    ```bash
    vi file.txt
    ```
    Modes in vi/vim:

    - Normal mode (default): Use keys for commands.

    - Insert mode: Type text (i to enter).

    - Command mode: For actions like save, quit (:).

    Common commands:

    - `i`: Insert mode

    - `Esc`: Back to normal mode

    - `:w`: Save

    - `:q`: Quit

    - `:wq`: Save and quit

    - `:q!`: Quit without saving

---

## 🔍 Searching and Finding Files in Linux

```vbnet
Linux provides powerful commands to search for files, find their locations, and extract specific content—making it easy to navigate and manage even the largest systems efficiently.
```


1) `find` - Search for files and directories

    Searches recursively from a specified directory.

    ```bash
    find /path/to/search -name "filename.txt"
    ```

    **Examples**:
    - Find a file by name
        ```bash
        find . -name "myfile.txt"
        ```

    - Find all `.py` files
        ```bash
        find /home/user -type f -name "*.py"
        ```

2) `locate` - Fast File Search via Database

    Faster than find but uses an index that must be updated

    ```bash
    locate filename.txt 
    ```

    Update the database manually (if needed)
    ```bash
    sudo updatedb
    ```


3) `grep` - Search Inside Files

    Searches for patterns inside files using regular expressions.

    ```bash
    grep "hello" file.txt
    ```

    Common flags:
    - `-i`: Ignore case
    - `-r`: Recursive 
    - `-n`: Show line numbers

    Examples:
    ```bash
    grep -rin "main" ~/projects/
    ```

4) `which` - Find the Path of the Executables

    Shows the locations of a command's binary
    ```bash
    which python
    ```

    Example output:
    ```bash
    /usr/bin/python
    ```
---

## 🔐 File Permissions and Ownership in Linux
```vbnet
In Linux, every file and directory comes with permissions and ownership. Grasping these concepts is crucial for controlling access and ensuring system security.
```

### 🔍 Understanding File Permissions

Run `ls -l` to view permissions:
```bash
$ ls -l file.txt
```

Output:
```vbnet
-rw-r--r-- 1 user group 123 May 16 10:00 file.txt
```

Breakdown: 

- `-` → Type(`-` file, `d` directory, `l` link)
- `rw-` →  Owner permissions (read/write)
- `r--` →  Group Permissions (read)
- `r--` →  Others permissions (read)

#### 🧩 What Determines These Defaults?

When a new file or directory is created, its default permissions are controlled by something called the **umask**.

You can check your current umask with:

```bash
umask
```

Example Output:
```
0022
```

This `umask` value is subtracted from the system's base permissions:

- **Files** usually start with base permissions of `666` (read & write for all).
- **Directories** usually start with `777` (read, write & execute for all).

#### 🔧 How it works:

- **File base**: `666`  
  **Umask**: `022`  
  **Final permission**: `644` → `rw-r--r--`

- **Directory base**: `777`  
  **Umask**: `022`  
  **Final permission**: `755` → `rwxr-xr-x`

Understanding how `umask` works helps you **predict and control** the default permissions for newly created files and directories. This is especially useful in collaborative environments or when setting up secure systems.

<br></br>

1) `chmod`: Change File Permissions

    You can modify file access using **symbolic** or **numeric (octal)** modes
    #### 🔢 Numeric Mode

    | Number | Permission |
    |--------|------------|
    | 7      | rwx        |
    | 6      | rw-        |
    | 5      | r-x        |
    | 4      | r--        |
    | 0      | ---        |

    ```bash
    chmod 755 script.sh
    ```

     This gives:

    - Owner: rwx

    - Group: r-x

    - Others: r-x

    #### 🔣 Symbolic Mode
    ```bash
    chmod u+x myfile     # add execute to user
    chmod g-w myfile     # remove write from group
    chmod o=r myfile     # set others to read-only
    ```

2) `chown` - Change Ownership

    Changes a file's owner and group

    ```bash
    chown user:group file
    ```
    Example:
    ```bash
    sudo chown ayush:devs report.txt
    ```

3) `chgrp` - Change Group Only

    Changes group ownership without changing the file owner
    ```bash
    chgrp devs report.txt
    ```

---

## 🗜️ File Compression in Linux
```vbnet
Linux provides powerful tools to compress and decompress files and directories. These tools help you save disk space and make it easier and faster to transfer files between systems.
```

1) `tar` - Archive Multiple Files

    - `tar` (tape archive) is used to bundle multiple files into a single archive file, optionally compressing it.

    ```bash
    tar -cvf archive.tar file1.txt file2.txt
    ```

    - `c`: create archive 
    - `v`: verbose output
    - `f`: filename of output

    Extract a  ``.tar`` file:
    ```bash
    tar -xvf archive.tar
    ```

    Create a compressed archive (`.tar.gz` or `.tar.bz2`):
    ```bash
    tar -czvf archive.tar.gz folder/
    tar -cjvf archive.tar.bz2 folder/
    ```

    Extract a compressed archive:
    ```bash
    tar -xzvf archive.tar.gz
    tar -xjvf archive.tar.bz2
    ```


2) `zip` - Create Zip Archive

    Widely used and compatible with Windows.

    Compress:
    ```bash
    zip compressed.zip file1 file2 folder/
    ```

    Unzip:
    ```bash
    unzip compressed.zip
    ```


3) `gzip` - Compress Single Files

    Best for compressing individual files, not directories.

    Compress:
    ```bash
    gzip filename.txt     # Creates filename.txt.gz
    ```

    Decompress:
    ```bash
    gunzip filename.txt.gz
    ```


4. `bzip` - High Compression Ratio

    Slower than gzip, but better compression.

    Compress:
    ```bash
    bzip2 filename.txt     # Creates filename.txt.bz2
    ```

    Decompress:
    ```bash
    bunzip2 filename.txt.bz2
    ```

    **Notes**:

    - ``tar`` is typically combined with ``gzip`` or ``bzip2``.

    - ``zip`` archives preserve directory structure.

    - ``gzip/bzip2`` overwrite original files by default.

---
        
## 🧭 Wrapping Up

By now, you've explored the most essential Linux commands for navigating the filesystem, editing files, managing permissions, and working with archives. These tools form the core of everyday Linux usage and give you the confidence to interact with the system through the terminal.

But this is just the beginning.

To truly unlock the power of Linux, we need to go deeper—into the world of the **shell**. This is where the magic happens: automation, scripting, and custom workflows.

So, what exactly is the Linux shell?  
How do you write your own scripts?  
How can you automate tasks like a pro?

```vbnet
Let’s dive into the next section: Shell Basics 🚀
```

<style>
.tooltip-img:hover::after {
  content: url(C:/Users/Gharat/OneDrive/Pictures/Screenshots/Screenshot 2025-05-16 173453.png);
  position: absolute;
  z-index: 100;
}
</style>

But before you do, make sure to check out the [Problem Set<span class="tooltip-img"></span>](./03_problem_set.md) file to reinforce what you’ve learned with some hands-on practice!
