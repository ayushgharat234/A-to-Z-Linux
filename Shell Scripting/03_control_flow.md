# Control Flow: Decisions and Loops

Just like any programming language, Bash allows your scripts to make decisions and repeat tasks.

---

## 1. Conditional Statements (`if-else`)

This allows the script to execute code only if a condition is true.

### Syntax
Pay attention to the spaces inside the square brackets `[ ]`. They are mandatory.

```bash
if [ condition ]; then
    # commands
elif [ another_condition ]; then
    # commands
else
    # commands
fi
```

### Comparison Operators

**Numbers:**
*   `-eq`: Equal to
*   `-ne`: Not equal to
*   `-gt`: Greater than
*   `-lt`: Less than
*   `-ge`: Greater than or equal to
*   `-le`: Less than or equal to

**Strings:**
*   `=`: Equal to
*   `!=`: Not equal to
*   `-z`: String is empty
*   `-n`: String is not empty

**Files:**
*   `-f`: File exists
*   `-d`: Directory exists
*   `-x`: File is executable

### Example: Check if a user exists
```bash
#!/bin/bash

read -p "Enter username: " user

if id "$user" &>/dev/null; then
    echo "User $user exists!"
else
    echo "User $user does not exist."
fi
```

### Logical Operators
*   `&&` (AND): Both conditions must be true.
*   `||` (OR): At least one condition must be true.

```bash
if [ "$age" -gt 18 ] && [ "$has_id" = "yes" ]; then
    echo "You can enter."
fi
```

---

## 2. Loops

Loops let you repeat actions.

### `for` Loops
Iterate over a list of items or numbers.

**Style 1: List**
```bash
for item in apple banana cherry; do
    echo "I like $item"
done
```

**Style 2: Ranges**
```bash
for i in {1..5}; do
    echo "Number: $i"
done
```

**Style 3: C-Style**
```bash
for ((i=0; i<5; i++)); do
    echo "Counter: $i"
done
```

### `while` Loops
Run as long as a condition is true.

```bash
count=1
while [ $count -le 5 ]; do
    echo "Count is $count"
    ((count++))  # Increment
done
```

---

## Summary
*   Use `if [ ... ]; then ... fi` for logic.
*   Remember spaces inside `[  ]`.
*   Use `for` loops to iterate lists/files.
*   Use `while` loops for conditions.
