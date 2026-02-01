# Package Management

In Linux, software is managed via **packages**. A package manager handles installation, updates, and dependency resolution automatically.

---

## 1. Debian/Ubuntu (`apt`)

The Advanced Package Tool (APT) is the standard for Debian-based systems.

### Basic Commands
```bash
# Update the list of available packages (Do this first!)
sudo apt update

# Upgrade all installed packages to the latest version
sudo apt upgrade

# Install a package
sudo apt install git

# Remove a package
sudo apt remove git

# Remove a package + configuration files
sudo apt purge git

# Remove unused dependencies (Cleanup)
sudo apt autoremove
```

### Searching
```bash
apt search python3
apt show python3   # Show details
```

---

## 2. Red Hat/CentOS/Fedora (`dnf` / `yum`)

Modern RHEL systems use `dnf` (Dandified YUM). The syntax is very similar.

```bash
sudo dnf check-update
sudo dnf install httpd
sudo dnf remove httpd
```

---

## 3. Low-Level Tools (`dpkg` & `rpm`)

Sometimes you download a standalone `.deb` or `.rpm` file. You need low-level tools to install them.

**Debian (.deb)**
```bash
# Install
sudo dpkg -i package.deb

# If dependencies are missing, run this to fix:
sudo apt install -f
```

**Red Hat (.rpm)**
```bash
# Install
sudo rpm -ivh package.rpm
```

---

## 4. Repositories

Packages come from **repositories** (servers storing software).
*   **List**: `/etc/apt/sources.list`.
*   **Adding a PPA** (Personal Package Archive - Ubuntu):
    ```bash
    sudo add-apt-repository ppa:user/repo
    sudo apt update
    ```

---

## Summary
*   Always run `apt update` before installing.
*   Use `apt` for daily tasks, `dpkg` for standalone files.
*   Don't be afraid of `autoremove`—it keeps your system clean.
