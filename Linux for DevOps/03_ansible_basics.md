# Automation with Ansible

Ansible is a configuration management tool. It allows you to control hundreds of servers from one machine.

---

## 1. How it Works

*   **Agentless**: You don't need to install software on the target servers. It just uses **SSH**.
*   **Declarative**: You tell Ansible *what* you want (e.g., "Nginx should be installed"), and it handles the *how*.

---

## 2. Inventory

A file listing your servers.

```ini
[webservers]
192.168.1.10
192.168.1.11

[dbservers]
192.168.1.20
```

---

## 3. Playbooks

Playbooks are written in YAML and describe the tasks.

**Example: `install_nginx.yml`**
```yaml
---
- name: Setup Web Server
  hosts: webservers
  become: true  # Run as root (sudo)

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start Nginx
      service:
        name: nginx
        state: started
```

---

## 4. Running a Playbook

```bash
ansible-playbook -i inventory.ini install_nginx.yml
```

---

## Summary
*   **Inventory**: List of servers.
*   **Playbook**: List of Instructions (YAML).
*   **Module**: The tools (apt, copy, service) doing the work.
