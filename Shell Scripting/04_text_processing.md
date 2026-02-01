# Text Processing and Redirection

Linux excels at correct text manipulation. These tools are the superpowers of a DevOps engineer.

---

## 1. Streams and Redirection

Every command has three streams:
1.  **Stdin (0)**: Input (keyboard).
2.  **Stdout (1)**: Output (screen).
3.  **Stderr (2)**: Error output (screen).

### Redirecting Output
*   `>`: Overwrite file with output.
    ```bash
    echo "New Log" > log.txt
    ```
*   `>>`: Append output to file.
    ```bash
    echo "Another line" >> log.txt
    ```

### Redirecting Errors
Redirect only error messages to a separated file.
```bash
ls /fake_folder 2> errors.txt
```

### Piping (`|`)
Send the output of one command as input to the next.
```bash
cat file.txt | grep "error" | wc -l
```
*(Read file -> Find "error" lines -> Count them)*

---

## 2. The Big Three: Grep, Awk, Sed

### `grep` (Search)
Finds lines matching a pattern.

```bash
grep "failed" /var/log/syslog    # Show failed attempts
grep -v "success" log.txt        # Show everything EXCEPT success
```

### `cut` (Slice)
Great for simple delimited files (like CSV).

```bash
# Extract 1st column from /etc/passwd (delimiter is :)
cut -d ":" -f 1 /etc/passwd
```

### `awk` (Field Processing)
More powerful than cut. Uses space/tab as default delimiter.

```bash
# Print the 2nd column of 'ls -l' (which is link count)
ls -l | awk '{print $2}'

# Print only if 3rd column (UID) > 1000 in /etc/passwd
awk -F ":" '$3 >= 1000 {print $1}' /etc/passwd
```

### `sed` (Stream Editor)
Search and replace text.

```bash
# Replace "hello" with "hi" (only first occurrence per line)
sed 's/hello/hi/' file.txt

# Replace GLOBALLY (all occurrences)
sed 's/hello/hi/g' file.txt

# Delete lines containing "error"
sed '/error/d' file.txt
```

---

## Summary
*   `|` pipes output to input.
*   `>` saves output to file.
*   `grep` searches lines.
*   `awk` processes columns.
*   `sed` replaces text.
