# 🔒 Ansible – Base Hardening for Linux Servers

## 📌 Overview
This project automates **baseline hardening** of Linux servers using **Ansible**.  
It focuses on security best practices to reduce the attack surface while keeping the system functional for daily use.

### Features
- ✅ Create an **admin user** with SSH keys
- ✅ Configure **passwordless sudo**
- ✅ Enable and configure **UFW firewall** (allow only 22/80/443)
- ✅ Install and configure **Fail2Ban** for SSH brute-force protection
- ✅ Apply **SSH hardening** (disable root login & password authentication)
- ✅ Configure **unattended-upgrades** (optional)
- ✅ Deploy a custom **MOTD banner** with system info
- ✅ Fully **idempotent** playbook (safe to re-run)

---

## 📂 Project Structure
ansible-base-hardening/
├── inventories/
├── roles/
│ └── base_hardening/
│ ├── tasks/
│ ├── templates/
│ └── handlers/
├── site.yml
└── images/

## ⚙️ Usage
1. Clone the repository:
```bash
git clone https://github.com/Matiaslb14/ansible-base-hardening.git
cd ansible-base-hardening

2. Run the playbook (skip upgrade if you want faster execution):

ansible-playbook site.yml -K --skip-tags upgrade

3. ansible-playbook site.yml -K --tags upgrade

📸 Screenshots
✅ Ansible Run

🔒 Validation (UFW, Fail2Ban, SSH, MOTD)

🔍 Verification

After running the playbook, validate the following on the target server:

# User creation & sudo
id secops
sudo -n true && echo "OK sudo"

# Firewall
sudo ufw status

# Fail2Ban
systemctl is-active fail2ban
sudo fail2ban-client status sshd

# SSH hardening
grep -E '^(PasswordAuthentication|PermitRootLogin)' /etc/ssh/sshd_config

# MOTD
cat /etc/motd


👨‍💻 Author

Matías Andrés Lagos Barra
