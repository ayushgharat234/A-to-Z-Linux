# Variables and User Input

Scripts become powerful when they can store data and interact with the user.

---

## 1. Variables

In Bash, you don't need to declare data types (int, string, etc.).

### Defining Variables
*   **No spaces** around the `=` sign.

```bash
name="Ayush"
role="DevOps Engineer"
count=10
```

### Accessing Variables
Use the `$` symbol to access the value.

```bash
echo "My name is $name"
echo "I am a $role"
```

### Best Practice: Quotes
Always wrap variables in double quotes when printing or using them to handle spaces correctly.

```bash
filename="My Notes.txt"
rm "$filename"  # Safe
rm $filename    # Unsafe: tries to remove "My" and "Notes.txt"
```

---

## 2. User Input (`read`)

You can make your scripts interactive by asking the user for input.

```bash
#!/bin/bash

echo "What is your name?"
read username

echo "Hello, $username! Welcome to the server."
```

### Prompt Flag (`-p`)
You can simplify the above into one line:

```bash
read -p "Enter your age: " age
echo "You are $age years old."
```

### Silent Input (`-s`)
Useful for passwords.

```bash
read -s -p "Enter password: " password
echo
echo "Password saved (shhh)."
```

---

## 3. Command Arguments

You can pass arguments to your script when running it: `./script.sh arg1 arg2`.

*   `$1`: First argument.
*   `$2`: Second argument.
*   `$0`: Name of the script itself.
*   `$#`: Total number of arguments.
*   `$@`: All arguments as a list.

**Example: `greet.sh`**
```bash
#!/bin/bash
echo "Hello, $1!"
```

**Run:**
```bash
./greet.sh Alice
# Output: Hello, Alice!
```

---

## Summary
*   `var=value` (no spaces).
*   Use `"$var"` to access.
*   `read` takes user input.
*   `$1`, `$2` handle command-line arguments.
