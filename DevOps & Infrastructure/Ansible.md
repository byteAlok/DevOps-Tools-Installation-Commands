# 🤖 Ansible – Installation & Commands Guide

A practical guide to installing, configuring, and using **Ansible** across different operating systems. This README covers installation, inventory management, SSH configuration, ad-hoc commands, playbooks, roles, collections, and commonly used Ansible commands. ⚙️🚀

---

## 📌 1. Introduction

Ansible is an open-source automation tool used for configuration management, application deployment, infrastructure automation, and orchestration.

- **Tool:** Ansible
- **Developer:** Red Hat / Ansible Community
- **Language:** Python
- **Configuration Language:** YAML
- **Connection:** SSH (Linux), WinRM / PSRP (Windows)
- **Architecture:** Agentless
- **Primary Purpose:** IT Automation and Configuration Management

## 🧩 2. Ansible Components

| Component | Description |
|---|---|
| Control Node | Machine where Ansible is installed and executed |
| Managed Node | Remote machine managed by Ansible |
| Inventory | Defines managed hosts and groups |
| Module | Performs specific tasks on managed nodes |
| Playbook | YAML file containing automation instructions |
| Task | Individual operation inside a play |
| Role | Reusable structure for organizing automation |
| Collection | Package containing roles, modules, and plugins |
| Ansible Galaxy | Repository for sharing and downloading Ansible content |
| Ansible Vault | Encrypts sensitive information |

## 💻 3. Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | Python / pipx |
| Amazon Linux 2023 | Python / pipx |
| Ubuntu | APT / pipx |
| RHEL | DNF / EPEL / pipx |
| Windows | WSL2 |
| macOS | Homebrew / pipx |

**Important:** Ansible runs on a Control Node. Windows can be managed by Ansible, but Windows itself is not natively supported as a Control Node. Use WSL2 on Windows.

---

## 📦 4. Package Management Commands

### 🔍 Search Available Packages

```bash
# Amazon Linux 2 / RHEL
yum search ansible

# Amazon Linux 2023
dnf search ansible

# Ubuntu
apt search ansible
```

### 📋 List Available Packages

```bash
# YUM
yum list available | grep ansible

# DNF
dnf list available | grep ansible

# APT
apt list ansible
```

### 📥 Check Installed Packages

```bash
# YUM
yum list installed | grep ansible

# DNF
dnf list installed | grep ansible

# APT
apt list --installed | grep ansible
```

### ℹ️ Package Information

```bash
# YUM
yum info ansible

# DNF
dnf info ansible

# APT
apt show ansible
```

### 🔄 Update Package Information

```bash
# YUM
sudo yum makecache

# DNF
sudo dnf makecache

# APT
sudo apt update
```

---

## 🐧 5. Install Ansible on Amazon Linux 2

Ansible can be installed using Python and pipx.

### 🔄 Update System

```bash
sudo yum update -y
```

### 🐍 Install Python and Required Packages

```bash
sudo yum install -y python3 python3-pip git
```

### 📦 Install pipx

```bash
python3 -m pip install --user pipx
```

### 🔗 Configure PATH

```bash
python3 -m pipx ensurepath
```

Open a new terminal or reload your shell configuration.

### 📥 Install Ansible

```bash
pipx install --include-deps ansible
```

### 🔍 Verify Installation

```bash
ansible --version
ansible-playbook --version
```

---

## 🐧 6. Install Ansible on Amazon Linux 2023

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🐍 Install Python and Required Packages

```bash
sudo dnf install -y python3 python3-pip git
```

### 📦 Install pipx

```bash
python3 -m pip install --user pipx
```

### 🔗 Configure PATH

```bash
python3 -m pipx ensurepath
```

Open a new terminal or reload your shell configuration.

### 📥 Install Ansible

```bash
pipx install --include-deps ansible
```

### 🔍 Verify Installation

```bash
ansible --version
```

---

## 🐧 7. Install Ansible on Ubuntu

### 🔄 Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### 🐍 Install Python and Required Packages

```bash
sudo apt install -y python3 python3-pip python3-venv pipx git
```

### 🔗 Configure pipx PATH

```bash
pipx ensurepath
```

Open a new terminal after running this command.

### 📥 Install Ansible

```bash
pipx install --include-deps ansible
```

### 🔍 Verify Installation

```bash
ansible --version
```

### 🔄 Upgrade Ansible

```bash
pipx upgrade --include-injected ansible
```

---

## 🐧 8. Install Ansible on RHEL

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🐍 Install Python and Required Packages

```bash
sudo dnf install -y python3 python3-pip git
```

### 📦 Install pipx

On RHEL systems where pipx is available through configured repositories:

```bash
sudo dnf install -y pipx
```

If pipx is not available, use a Python virtual environment instead.

### 📥 Install Ansible Using pipx

```bash
pipx ensurepath
pipx install --include-deps ansible
```

### 🔍 Verify Installation

```bash
ansible --version
```

---

## 🪟 9. Install Ansible on Windows Using WSL2

Ansible does not natively run as a Windows Control Node. Use Windows Subsystem for Linux (WSL2).

### 📥 Step 1: Install WSL

Open PowerShell as Administrator.

```powershell
wsl --install
```

### 🔄 Step 2: Restart Windows

Restart your system if requested and complete the Ubuntu setup.

### 🐧 Step 3: Open Ubuntu Terminal

Update the Ubuntu packages:

```bash
sudo apt update
sudo apt upgrade -y
```

### 🐍 Step 4: Install Python and pipx

```bash
sudo apt install -y python3 python3-pip python3-venv pipx git
```

### 📥 Step 5: Install Ansible

```bash
pipx ensurepath
pipx install --include-deps ansible
```

### 🔍 Step 6: Verify Installation

```bash
ansible --version
```

---

## 🍎 10. Install Ansible on macOS

### 📦 Method 1: Using Homebrew

```bash
brew update
brew install ansible
```

### 🔍 Verify Installation

```bash
ansible --version
```

### 📦 Method 2: Using pipx

```bash
brew install pipx
pipx ensurepath
pipx install --include-deps ansible
```

---

## 🔍 11. Ansible CLI Commands

### 📌 Version and Help

```bash
# Display Ansible version
ansible --version

# Display Ansible help
ansible --help

# Display playbook help
ansible-playbook --help

# Display inventory help
ansible-inventory --help
```

### ⚙️ Configuration Commands

```bash
# Display active configuration
ansible-config dump

# Display configuration with overridden values
ansible-config dump --only-changed

# Display configuration file
ansible-config view

# Display configuration documentation
ansible-config list
```

### 📋 Inventory Commands

```bash
# List all inventory hosts
ansible all --list-hosts

# Display inventory in graph format
ansible-inventory --graph

# Display inventory in JSON format
ansible-inventory --list

# Display host variables
ansible-inventory --host webserver1
```

---

## 🔐 12. SSH Configuration

Ansible commonly uses SSH to connect to Linux managed nodes.

### 🔑 Generate SSH Key

```bash
ssh-keygen -t ed25519
```

### 📤 Copy SSH Public Key to Remote Server

```bash
ssh-copy-id ec2-user@<REMOTE_SERVER_IP>
```

For Ubuntu-based EC2 instances:

```bash
ssh-copy-id ubuntu@<REMOTE_SERVER_IP>
```

### 🔍 Test SSH Connection

```bash
ssh ec2-user@<REMOTE_SERVER_IP>
```

### 📌 Check SSH Connectivity

```bash
ssh -v ec2-user@<REMOTE_SERVER_IP>
```

> Ensure the Control Node can reach the managed node over SSH and the required firewall/security-group rules allow the connection.

---

## 📁 13. Ansible Inventory

An inventory file defines the machines that Ansible will manage.

### 📂 Create Project Directory

```bash
mkdir ansible-project
cd ansible-project
```

### 📄 Create Inventory File

```bash
touch inventory.ini
```

### 📝 Example: inventory.ini

```ini
[webservers]
web1 ansible_host=192.168.1.10 ansible_user=ec2-user
web2 ansible_host=192.168.1.11 ansible_user=ec2-user

[databases]
db1 ansible_host=192.168.1.20 ansible_user=ubuntu

[all:vars]
ansible_ssh_private_key_file=~/.ssh/id_ed25519
```

### 🔍 Check Inventory

```bash
ansible-inventory -i inventory.ini --list
```

```bash
ansible-inventory -i inventory.ini --graph
```

---

## ⚡ 14. Ansible Ad-hoc Commands

Ad-hoc commands execute individual tasks without creating a playbook.

### 🔍 Test Connectivity

```bash
ansible all -i inventory.ini -m ping
```

### 🖥️ Check Remote Host Information

```bash
ansible all -i inventory.ini -m setup
```

### 📊 Check Disk Space

```bash
ansible all -i inventory.ini -m command -a "df -h"
```

### 🧠 Check Memory

```bash
ansible all -i inventory.ini -m command -a "free -h"
```

### 📦 Install Nginx on Ubuntu/Debian

```bash
ansible webservers -i inventory.ini -m apt \
  -a "name=nginx state=present update_cache=yes" \
  -b
```

### 📦 Install Nginx on Amazon Linux / RHEL

```bash
ansible webservers -i inventory.ini -m dnf \
  -a "name=nginx state=present" \
  -b
```

### ▶️ Start Nginx Service

```bash
ansible webservers -i inventory.ini -m service \
  -a "name=nginx state=started enabled=yes" \
  -b
```

### 📁 Create Directory

```bash
ansible all -i inventory.ini -m file \
  -a "path=/opt/app state=directory mode=0755" \
  -b
```

### 📄 Create File

```bash
ansible all -i inventory.ini -m file \
  -a "path=/tmp/hello.txt state=touch"
```

### 🔄 Restart Remote Server

```bash
ansible all -i inventory.ini -m reboot -b
```

---

## 📝 15. Ansible Playbooks

Playbooks are YAML files that define automation tasks.

### 📄 Create Playbook

```bash
touch install-nginx.yml
```

### 📝 Example: install-nginx.yml

```yaml
---
- name: Install and Start Nginx
  hosts: webservers
  become: yes

  tasks:
    - name: Update package cache
      ansible.builtin.apt:
        update_cache: yes
      when: ansible_os_family == "Debian"

    - name: Install Nginx
      ansible.builtin.package:
        name: nginx
        state: present

    - name: Start Nginx
      ansible.builtin.service:
        name: nginx
        state: started
        enabled: yes
```

### ▶️ Execute Playbook

```bash
ansible-playbook -i inventory.ini install-nginx.yml
```

### 🔍 Syntax Check

```bash
ansible-playbook --syntax-check install-nginx.yml
```

### 🧪 Dry Run

```bash
ansible-playbook -i inventory.ini install-nginx.yml --check
```

### 📊 Display Changes

```bash
ansible-playbook -i inventory.ini install-nginx.yml --diff
```

### 🔄 Execute with Verbose Output

```bash
ansible-playbook -i inventory.ini install-nginx.yml -v
```

```bash
ansible-playbook -i inventory.ini install-nginx.yml -vvv
```

### 🎯 Execute Specific Tags

```bash
ansible-playbook -i inventory.ini install-nginx.yml --tags nginx
```

### ⏭️ Skip Specific Tags

```bash
ansible-playbook -i inventory.ini install-nginx.yml --skip-tags nginx
```

---

## 📂 16. Ansible Variables

Variables help make playbooks reusable and configurable.

### 📝 Example: variables.yml

```yaml
---
- name: Install Application
  hosts: webservers
  become: yes

  vars:
    package_name: nginx
    service_name: nginx

  tasks:
    - name: Install package
      ansible.builtin.package:
        name: "{{ package_name }}"
        state: present

    - name: Start service
      ansible.builtin.service:
        name: "{{ service_name }}"
        state: started
```

### ▶️ Run Playbook with Extra Variables

```bash
ansible-playbook -i inventory.ini variables.yml \
  -e "package_name=nginx"
```

### 📌 Use a Variable File

```bash
ansible-playbook -i inventory.ini variables.yml \
  -e "@vars.yml"
```

---

## 🔔 17. Ansible Handlers

Handlers execute only when notified by a task.

### 📝 Example

```yaml
---
- name: Configure Nginx
  hosts: webservers
  become: yes

  tasks:
    - name: Update Nginx configuration
      ansible.builtin.copy:
        src: nginx.conf
        dest: /etc/nginx/nginx.conf
      notify: Restart Nginx

  handlers:
    - name: Restart Nginx
      ansible.builtin.service:
        name: nginx
        state: restarted
```

---

## 📦 18. Ansible Roles

Roles organize automation into reusable directories.

### 📂 Create Role Structure

```bash
ansible-galaxy role init nginx
```

### 📁 Common Role Structure

```text
nginx/
├── defaults/
│   └── main.yml
├── files/
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── templates/
├── tests/
└── vars/
    └── main.yml
```

### 🔍 Role Commands

```bash
# Initialize a role
ansible-galaxy role init nginx

# Install a role
ansible-galaxy role install geerlingguy.nginx

# List installed roles
ansible-galaxy role list

# Remove a role
ansible-galaxy role remove geerlingguy.nginx
```

---

## 🌐 19. Ansible Galaxy Commands

Ansible Galaxy provides reusable roles and collections.

### 📦 Collection Commands

```bash
# Search collections
ansible-galaxy collection search nginx

# Install collection
ansible-galaxy collection install community.general

# List installed collections
ansible-galaxy collection list

# Upgrade collection
ansible-galaxy collection install community.general --upgrade
```

### 📦 Role Commands

```bash
# Search roles
ansible-galaxy role search nginx

# Install role
ansible-galaxy role install geerlingguy.nginx

# List roles
ansible-galaxy role list
```

---

## 🔐 20. Ansible Vault Commands

Ansible Vault encrypts sensitive data such as passwords and secret variables.

```bash
# Create encrypted file
ansible-vault create secrets.yml

# Encrypt existing file
ansible-vault encrypt secrets.yml

# Decrypt file
ansible-vault decrypt secrets.yml

# Edit encrypted file
ansible-vault edit secrets.yml

# View encrypted file
ansible-vault view secrets.yml

# Change vault password
ansible-vault rekey secrets.yml
```

### ▶️ Run Playbook with Vault

```bash
ansible-playbook -i inventory.ini site.yml --ask-vault-pass
```

### 🔑 Use Vault Password File

```bash
ansible-playbook -i inventory.ini site.yml \
  --vault-password-file .vault_pass
```

Keep vault password files outside Git and restrict their file permissions.

---

## ⚙️ 21. Ansible Configuration File

Ansible uses `ansible.cfg` to define default settings.

### 📄 Create Configuration File

```bash
touch ansible.cfg
```

### 📝 Example: ansible.cfg

```ini
[defaults]
inventory = ./inventory.ini
remote_user = ec2-user
private_key_file = ~/.ssh/id_ed25519
host_key_checking = False
retry_files_enabled = False
```

> Disabling host key checking can weaken SSH security. Prefer managing trusted host keys in production.

### 🔍 Check Configuration

```bash
ansible-config dump --only-changed
```

---

## 🧰 22. Ansible Facts and Debugging

### 📊 Gather Facts

```bash
ansible all -i inventory.ini -m setup
```

### 🎯 Gather Specific Facts

```bash
ansible all -i inventory.ini -m setup \
  -a "filter=ansible_distribution*"
```

### 🐛 Debug Playbook

```yaml
---
- name: Debug Example
  hosts: all

  tasks:
    - name: Display message
      ansible.builtin.debug:
        msg: "Ansible is working successfully!"
```

### 🔍 Check Host Variables

```bash
ansible-inventory -i inventory.ini --host web1
```

---

## 🐳 23. Run Ansible Using Docker

### 📥 Pull Ansible Image

```bash
docker pull cytopia/ansible
```

### 🔍 Check Ansible Version

```bash
docker run --rm cytopia/ansible ansible --version
```

### ▶️ Run Ansible Playbook

```bash
docker run --rm -it \
  -v "$(pwd)":/ansible \
  -w /ansible \
  cytopia/ansible \
  ansible-playbook -i inventory.ini install-nginx.yml
```

Ensure the container has access to the SSH private key and inventory required for the managed hosts.

---

## 🧹 24. Uninstall Ansible

### 🐧 Amazon Linux 2 / Amazon Linux 2023 / RHEL

If installed using pipx:

```bash
pipx uninstall ansible
```

### 🐧 Ubuntu

If installed using pipx:

```bash
pipx uninstall ansible
```

If installed through APT:

```bash
sudo apt remove -y ansible
```

### 🍎 macOS

If installed through Homebrew:

```bash
brew uninstall ansible
```

If installed using pipx:

```bash
pipx uninstall ansible
```

### 🪟 Windows WSL2

Inside Ubuntu:

```bash
pipx uninstall ansible
```

---

## 🛡️ 25. Best Practices

- Use SSH keys instead of password-based authentication wherever possible.
- Use separate inventory files for development, staging, and production.
- Organize reusable automation into roles.
- Use Ansible Vault for sensitive information.
- Prefer fully qualified collection names (FQCN) in playbooks.
- Use `ansible.builtin` modules for built-in functionality.
- Validate playbooks before execution.
- Use `--check` and `--diff` when appropriate.
- Keep Ansible and collections updated.
- Avoid disabling SSH host key checking in production.
- Use least-privilege permissions on managed nodes.

---

## 📚 26. Official Documentation

- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Installation Guide](https://docs.ansible.com/projects/ansible/latest/installation_guide/)
- [Ansible CLI Documentation](https://docs.ansible.com/projects/ansible/latest/command_guide/command_line_tools.html)
- [Ansible Playbooks](https://docs.ansible.com/projects/ansible/latest/playbook_guide/)
- [Ansible Inventory](https://docs.ansible.com/projects/ansible/latest/inventory_guide/)
- [Ansible Roles](https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_reuse_roles.html)
- [Ansible Galaxy](https://galaxy.ansible.com/)
- [Ansible Vault](https://docs.ansible.com/projects/ansible/latest/vault_guide/)

---

**🚀 Learn • Automate • Configure • Manage**