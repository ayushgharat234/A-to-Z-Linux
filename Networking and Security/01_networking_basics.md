# Networking Basics

Understanding how Linux interacts with the network is essential.

---

## 1. IP Addresses and Interfaces

**Command**: `ip addr` (Modern replacement for `ifconfig`)

```bash
# Show IP addresses
ip addr show

# Show routing table
ip route show
```

*   **Loopback (`lo`)**: `127.0.0.1` (Localhost).
*   **Ethernet (`eth0` / `enp3s0`)**: Wired connection.
*   **Wi-Fi (`wlan0`)**: Wireless connection.

---

## 2. Testing Connectivity

### Ping
Checks if a host is reachable.
```bash
ping google.com
# Use -c to limit requests
ping -c 4 8.8.8.8
```

### Curl
Transfers data from a server. Great for testing websites/APIs.
```bash
# Get the HTML of a page
curl google.com

# Get only headers (-I)
curl -I google.com
```

### Netstat / SS
Shows open ports and connections.
```bash
# Modern command: Socket Statistics
ss -tulpn

# Legacy command
netstat -tulpn
```
*   `-t`: TCP
*   `-u`: UDP
*   `-l`: Listening
*   `-p`: Process
*   `-n`: Numeric (show IPs instead of names)

---

## 3. DNS (Domain Name System)

DNS turns names (`google.com`) into IPs (`142.250.x.x`).

**Key Files**:
*   `/etc/hosts`: Local override map.
    ```text
    127.0.0.1 localhost
    192.168.1.50 devserver
    ```
*   `/etc/resolv.conf`: Sets the DNS nameservers (e.g., `nameserver 8.8.8.8`).

**Tools**:
*   `dig google.com`
*   `nslookup google.com`

---

## Summary
*   Use `ip addr` to find your IP.
*   Use `ping` to check connection.
*   Use `ss -tulpn` to check open ports.
*   `curl` is your browser in the terminal.
