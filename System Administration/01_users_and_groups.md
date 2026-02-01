# User and Group Management

In Linux, managing users and access is a core responsibility of a System Administrator.

---

## 1. Key Configuration Files

Before running commands, understand where Linux stores user data:

*   `/etc/passwd`: Stores user account information (publicly readable).
    *   Format: `username:x:UID:GID:comment:home:shell`
*   `/etc/shadow`: Stores encrypted passwords (only root can read).
*   `/etc/group`: Stores group information.

---

## 2. Managing Users

### Adding a User
The `useradd` command creates a new user.

```bash
# Create user 'john' with a home directory (-m) and bash shell (-s)
sudo useradd -m -s /bin/bash john

# Set a password for the new user
sudo passwd john
```

### Modifying a User (`usermod`)
Used to change attributes of an existing user.

```bash
# Add 'john' to the 'devs' group (-aG means append to group)
sudo usermod -aG devs john

# Lock a user account (prevent login)
sudo usermod -L john

# Unlock a user account
sudo usermod -U john
```

### Deleting a User
```bash
# Delete user 'john' and their home directory (-r)
sudo userdel -r john
```

---

## 3. Managing Groups

Groups allow you to organize users and manage permissions efficiently.

```bash
# Create a new group
sudo groupadd developers

# Delete a group
sudo groupdel developers
```

### Managing Group Members
You can use `gpasswd` to manage group memberships.

```bash
# Add user to group
sudo gpasswd -a john developers

# Remove user from group
sudo gpasswd -d john developers
```

---

## 4. Switching Users (`su` vs `sudo`)

*   `su john`: Switch to user 'john'. Requires john's password.
*   `su - john`: Switch to 'john' and **load their environment variables**.
*   `sudo command`: Run a single command with root privileges (requires *your* password).

---

## Summary
*   Always use `-m` when creating users to ensure they have a home folder.
*   `/etc/shadow` is where the secrets live.
*   Use `usermod -aG` to add users to secondary groups without removing them from others.
