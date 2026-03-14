# Ansible Lab Management

This repository contains **Ansible playbooks and inventory** for managing a lab of Ubuntu PCs (192.168.4.101–192.168.4.130). It allows you to run simple tasks like ping tests and perform mass operations such as powering off all machines.

---

## **Inventory**

All lab PCs are defined in `inventory.ini` under the group `[ubuntu_lab]`. Example:

```ini
[ubuntu_lab]
192.168.4.101
192.168.4.102
# ... up to 192.168.4.130

[ubuntu_lab:vars]
ansible_user=admin
ansible_become=true
ansible_become_method=sudo
