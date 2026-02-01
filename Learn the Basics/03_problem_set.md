# Linux Practice Problem Set
_A practice sheet based on the "Basic Linux Commands" module._

---

## Beginner Level: Get Comfortable in the Shell

**Focus**: File navigation, basic manipulation, viewing content, and simple permissions.

### Navigation & File System

1.  What command will show you your current directory?
2.  How do you move to the home directory using the `cd` command?
3.  Create a folder named `practice` and then a subfolder inside it called `scripts`.
4.  Delete an empty folder named `testdir`. What command would you use?
5.  List all files including hidden ones in the current directory using a single command.

### File Operations

6.  Create a text file called `notes.txt`.
7.  Copy `notes.txt` to a new file called `backup_notes.txt`.
8.  Move `notes.txt` into the `practice` directory.
9.  Delete a file named `old.txt` without being prompted for confirmation.

### Viewing Files

10. Use a command to quickly view the full contents of a file called `summary.txt`.
11. Which command lets you scroll through `longfile.txt` one page at a time?

---

## Skilled Level: Utility and Productivity

**Focus**: Permissions, searching, efficient workflows.

### Permissions

12. What does the permission string `-rw-r--r--` represent in terms of access?
13. Use `chmod` to give the owner full permissions and read/execute to everyone else on a file called `deploy.sh`.
14. Change the owner of `log.txt` to user `ayush` and group `devs`.

### Searching

15. Find all `.py` files under `/home/your_user/scripts/`.
16. Locate a file called `report.pdf` using a command that uses a database index.
17. How would you recursively search for the word "TODO" in a codebase?

### Editors

18. Open `script.sh` in `nano`, add some text, and save/exit the editor.
19. In `vim`, how do you:
    -   Enter insert mode?
    -   Save and quit?
    -   Quit without saving?

---

## Advanced Level: Real-World Scenarios

**Focus**: Combining tools, automating, advanced permissions, compression.

### Advanced Permissions & Ownership

20. A directory was created with the wrong group. How do you change only its group to `engineers`?
21. What will be the final permission of a new file if your `umask` is `0027`?

### Command Mastery

22. List only `.txt` files in the current directory, sorted by newest to oldest.
23. How would you find all files larger than 5MB inside `/var/log/`?
24. Count how many times the word `ERROR` appears in a log file called `syslog`.

### Compression

25. Create a `.tar.gz` archive of a directory called `project`.
26. Extract `backup.tar.bz2` into the current folder.
27. Compress `bigdata.csv` using `gzip`, then decompress it.

---

### Tip
Once you're done, try solving a few using only the terminal—no GUI, no help docs. That’s where the real learning happens.
