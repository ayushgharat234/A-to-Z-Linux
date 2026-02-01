# Advanced Permissions and ACLs

You already know `chmod` and `chown`, but system administration requires more granular control.

---

## 1. Special Permissions

Beyond Read (4), Write (2), and Execute (1), there are three special permissions:

### SetUID (SUID) - `4000`
*   **Function**: When a file is executed, it runs with the permissions of the **owner** (usually root), not the user running it.
*   **Example**: `passwd` command needs to edit `/etc/shadow`, so it has SUID.
*   **Symbol**: `s` in the owner execute spot (`-rwsr-xr-x`).
*   **Command**: `chmod u+s file` or `chmod 4755 file`.

### SetGID (SGID) - `2000`
*   **Function (Files)**: Runs with group permissions.
*   **Function (Directories)**: Any new file created inside inherits the directory's **group**, not the creator's primary group. Great for shared folders.
*   **Symbol**: `s` in the group execute spot (`drwxr-sr-x`).
*   **Command**: `chmod g+s folder` or `chmod 2755 folder`.

### Sticky Bit - `1000`
*   **Function**: On directories, it prevents users from deleting each other's files. Only the owner or root can delete.
*   **Example**: `/tmp` directory.
*   **Symbol**: `t` in the other execute spot (`drwxrwxrwt`).
*   **Command**: `chmod +t folder` or `chmod 1777 folder`.

---

## 2. Access Control Lists (ACLs)

Standard permissions (Owner/Group/Other) are sometimes too limiting. What if you want to give read access to specific user `alice` but write access to `bob`, without changing groups?

**Use ACLs.**

### Checking ACLs
```bash
getfacl filename
```

### Setting ACLs (`setfacl`)

**Syntax**: `u:user:perms` or `g:group:perms`

```bash
# Give user 'alice' read-write access to file.txt
setfacl -m u:alice:rw file.txt

# Give group 'interns' read-only access
setfacl -m g:interns:r file.txt

# Remove permissions for alice
setfacl -x u:alice file.txt

# Remove all ACLs
setfacl -b file.txt
```

---

## Summary
*   **SUID**: Run as owner (dangerous if misused).
*   **SGID**: Inherit group ownership (great for collaboration).
*   **Sticky Bit**: Prevent deletion (for public folders).
*   **ACLs**: Fine-grained access for specific users/groups.
