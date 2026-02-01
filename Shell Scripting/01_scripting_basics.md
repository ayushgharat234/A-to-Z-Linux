# Shell Scripting Basics

Shell scripting is the art of chaining Linux commands together to automate tasks. A script is simply a file containing a series of commands that the shell executes line by line.

---

## 1. The Shebang (`#!`)

Every bash script should start with a **shebang** line. This tells the system which interpreter to use to run the script.

```bash
#!/bin/bash
```

*   `#!`: The "shebang" or "hashbang".
*   `/bin/bash`: The path to the Bash interpreter.

If you were writing a Python script, it would look like `#!/usr/bin/python3`.

## 2. Creating and Running Your First Script

### Step 1: Create the file
Use your favorite editor (nano or vim) to create a file ending in `.sh`.

```bash
nano hello.sh
```

**Content:**
```bash
#!/bin/bash
echo "Hello, Linux World!"
```

### Step 2: Make it executable
By default, new files are not executable for security reasons. You must grant execute permissions.

```bash
chmod +x hello.sh
```

### Step 3: Run it
To run a script for the current directory, you need to prefix it with `./`.

```bash
./hello.sh
# Output: Hello, Linux World!
```

---

## 3. Comments

Comments are lines ignored by the shell, used to explain code.

```bash
#!/bin/bash

# This is a comment
echo "This will print"  # Inline comments work too
```

---

## 4. Exit Status

Every command returns an **exit status** (a number) when it finishes.
*   `0`: Success.
*   `1-255`: Failure/Error.

You can check the status of the *last executed command* using the special variable `$?`.

```bash
ls /nonexistent_folder
echo $?
# Output: 2 (or another non-zero number indicating error)

ls ~
echo $?
# Output: 0 (Success)
```

In scripts, you can manually set the exit code using `exit`:

```bash
#!/bin/bash
echo "Something went wrong..."
exit 1
```

---

## Summary
*   Start scripts with `#!/bin/bash`.
*   Make them executable with `chmod +x`.
*   Run them with `./scriptname.sh`.
*   Use `exit` to signal success (0) or failure (non-zero).
