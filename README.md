# Ansible Lab Management

This repository contains **Ansible playbooks and inventory** for managing a lab of Ubuntu PCs (192.168.4.101–192.168.4.130). It allows you to run simple tasks like ping tests and perform mass operations such as powering off all machines.

---

## **Install Ansible**

Install Ansible on your control machine (the system you run the commands from).

### Debian/Ubuntu

```bash
sudo apt update
sudo apt install -y ansible
```

### Fedora

```bash
sudo dnf install -y ansible
```

### Arch Linux

```bash
sudo pacman -S ansible
```

### Locale (optional)

```bash
export LANG=en_US.UTF-8
export LANGUAGE=en_US:en
export LC_ALL=en_US.UTF-8
```

### Verify

```bash
ansible --version
```

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
```

---

## **Commands**

Common commands are also kept in `command.txt`.

```bash
# Ping all lab PCs (connectivity test)
ansible -i inventory.ini ubuntu_lab -m ping -f 30

# Power off all lab PCs (requires sudo password)
ansible-playbook -i inventory.ini poweroff_lab.yml -f 30 --ask-become-pass
```

---

## **License**

See [LICENSE](LICENSE).
