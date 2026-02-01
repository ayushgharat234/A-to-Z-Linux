# Web Servers: Nginx and Apache

Linux powers most of the web. As a DevOps engineer, you must know how to serve content.

---

## 1. Nginx (Engine-X)

Nginx is known for high performance and is often used as a **Reverse Proxy**.

### Installation
```bash
sudo apt update
sudo apt install nginx
```

### Key Directories
*   **Content**: `/var/www/html/` (Put your `index.html` here).
*   **Config**: `/etc/nginx/nginx.conf`.
*   **Virtual Hosts**: `/etc/nginx/sites-available/` and `/etc/nginx/sites-enabled/`.

### Basic Commands
```bash
sudo systemctl start nginx
sudo systemctl reload nginx  # Use after changing config
```

---

## 2. Apache (HTTPD)

Apache is older, highly customizable, and uses `.htaccess` files for per-directory config.

### Installation
```bash
sudo apt install apache2
```

### Key Directories
*   **Content**: `/var/www/html/`.
*   **Config**: `/etc/apache2/apache2.conf`.

---

## 3. Reverse Proxy Concept

A reverse proxy sits in front of your application (like a Node.js or Python app running on port 3000) and forwards traffic to it.

**Nginx Example:**
```nginx
server {
    listen 80;
    server_name myapp.com;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```
This allows you to serve your app on standard port 80 without running the app as root.

---

## Summary
*   Use **Nginx** for performance and reverse proxying.
*   Use **Apache** if you need flexible `.htaccess` support.
*   Always check config syntax (`nginx -t`) before reloading.
