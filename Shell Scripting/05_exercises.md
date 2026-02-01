# Shell Scripting Exercises

Sharpen your skills by building these scripts. Try to write them without looking at the solutions first!

---

## Level 1: The Basics

### 1. The Greeter
Write a script called `greet.sh` that:
1.  Asks the user for their name.
2.  Asks for their favorite programming language.
3.  Prints a sentence using both inputs (e.g., "Hello Alice, Python is cool!").

### 2. Is it Root?
Write a script `check_root.sh` that checks if the script is being run as the root user.
*   *Hint*: The UID for root is always 0. You can check the `$EUID` variable.

---

## Level 2: Automation

### 3. Simple Backup
Create a script `backup.sh` that:
1.  Target: Takes a filename as an argument (`$1`).
2.  Action: Copies it to a `backups` folder (create if not exists).
3.  Naming: Appends the current date to the filename (e.g., `file_2023-10-25.txt`).
*   *Hint*: Use `date +%F`.

### 4. File Organizer
Create a script `organize.sh` that:
1.  Looks at the current directory.
2.  Moves all `.jpg` files to an `images` folder.
3.  Moves all `.txt` files to a `documents` folder.
4.  Prints how many files were moved.

---

## Level 3: Text Processing

### 5. Log Analyzer
You have a log file called `app.log`.
```text
INFO: User Alice logged in
ERROR: Database connection failed
INFO: User Bob logged in
ERROR: Timeout waiting for service
```
Write a script that:
1.  Counts the number of "ERROR" lines.
2.  Prints "System Critical" if errors > 5, otherwise "System Stable".

### 6. User Audit
Write a one-liner using pipe `|` that lists just the usernames of all users who have a UID greater than 1000 from `/etc/passwd`.
*   *Hint*: `/etc/passwd` uses `:` as a delimiter. Use `awk` or `cut`.

---

## Debugging Tip
If your script isn't working, run it with `bash -x ./script.sh`. This prints every command before executing it, showing you exactly what's happening!
