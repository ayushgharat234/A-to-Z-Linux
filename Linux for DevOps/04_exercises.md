# Linux for DevOps: Practice Set

---

## Level 1: Web Servers

### 1. Hello Nginx
*   Install Nginx.
*   Find the default `index.html` (usually in `/var/www/html`).
*   Replace its content with "<h1>Hello from DevOps!</h1>".
*   Visit `http://localhost` (or your IP) to see the change.

### 2. The Reverse Proxy
*   Run a simple Python server on port 8000: `python3 -m http.server 8000`.
*   Configure Nginx to listen on port 80 and forward requests to port 8000.
*   Reload Nginx and visit port 80. You should see the Python server!

---

## Level 2: CI/CD Logic

### 3. The Pipeline
*   Create a file `.github/workflows/test.yml` in a repo.
*   Add a step that runs `echo "Running Tests..."`.
*   Push to GitHub and watch the "Actions" tab.

---

## Level 3: Ansible

### 4. The Inventory
*   Create a file `hosts.ini` with:
    ```ini
    [local]
    localhost
    ```

### 5. The Playbook
*   Create `setup.yml` that uses the `apt` module to ensure `htop` is installed.
*   Run it: `ansible-playbook -i hosts.ini setup.yml --connection=local`.

---

## Tip
Infrastructure as Code (IaC) is about repeatability. If you do it twice, script it once!
