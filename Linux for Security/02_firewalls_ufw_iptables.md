# Firewalls: UFW and Iptables

A firewall controls incoming and outgoing network traffic.

---

## 1. UFW (Uncomplicated Firewall)

The default firewall for Ubuntu. It is a user-friendly wrapper around `iptables`.

### Status
```bash
sudo ufw status
# Output: Status: inactive (by default)
```

### Allowing Traffic
```bash
# Allow SSH (CRITICAL: Do this before enabling!)
sudo ufw allow ssh          # Allows port 22
sudo ufw allow 2222/tcp     # If you changed SSH port

# Allow Web
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

### Denying Traffic
```bash
# Block a specific IP
sudo ufw deny from 192.168.1.50
```

### Enable/Disable
```bash
sudo ufw enable
sudo ufw disable
```

---

## 2. Iptables (The Low Level)

`iptables` is older and more complex. It uses **Chains** (Input, Output, Forward).

*   **View Rules**: `sudo iptables -L`
*   **Flush (Delete) Rules**: `sudo iptables -F`

*Note: UFW is recommended for beginners.*

---

## Summary
*   Enable UFW on every server.
*   **Always allow SSH** first, or you will lock yourself out.
*   Default policy should be "Deny Input, Allow Output".
