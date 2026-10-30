# 🔧 Git – Installation & Commands Guide

A practical guide to installing Git, managing packages, configuring Git and using commonly required Git commands across different operating systems.

## 📌 1. Introduction

Git is a distributed version control system used to track source-code changes, maintain project history and collaborate with other developers.

**Key Features:**
- 🔄 Version Control
- 🌿 Branch Management
- 🤝 Team Collaboration
- 📜 Commit History
- 🔀 Merge and Rebase
- ☁️ GitHub, GitLab and Bitbucket Integration

## 🖥️ 2. Supported Operating Systems

| Operating System | Package Manager |
|---|---|
| 🐧 Amazon Linux 2 | YUM |
| 🐧 Amazon Linux 2023 | DNF |
| 🟠 Ubuntu | APT |
| 🔴 RHEL 7 | YUM |
| 🔴 RHEL 8 / 9 / 10 | DNF |
| 🪟 Windows | winget / Chocolatey |
| 🍎 macOS | Homebrew |

---

## 📦 3. Package Management Commands

These commands help you search, list, inspect, install, update and remove Git packages.

### 🔍 Search Git Package

```bash
# Amazon Linux 2 / RHEL 7
yum search git

# Amazon Linux 2023 / RHEL 8+
dnf search git

# Ubuntu
apt search git
```

### 📋 List Available Git Packages

```bash
# YUM
yum list git*

# DNF
dnf list git*

# Ubuntu
apt list 'git*'
```

### 📋 List Installed Git Packages

```bash
# YUM
yum list installed git*

# DNF
dnf list installed git*

# Ubuntu
apt list --installed 'git*'
```

### ℹ️ Get Git Package Information

```bash
# YUM
yum info git

# DNF
dnf info git

# Ubuntu
apt show git
```

### 📥 Install Git

```bash
# Amazon Linux 2 / RHEL 7
sudo yum install git -y

# Amazon Linux 2023 / RHEL 8+
sudo dnf install git -y

# Ubuntu
sudo apt install git -y
```

### 🔄 Update Git

```bash
# YUM
sudo yum update git -y

# DNF
sudo dnf upgrade git -y

# Ubuntu
sudo apt install --only-upgrade git -y
```

### 🗑️ Remove Git

```bash
# YUM
sudo yum remove git -y

# DNF
sudo dnf remove git -y

# Ubuntu
sudo apt remove git -y
```

### 🔎 Check Package Manager Version

```bash
yum --version
dnf --version
apt --version
```

---

## ⚙️ 4. Git Installation

### 🐧 Amazon Linux 2

```bash
# Update system
sudo yum update -y

# Install Git
sudo yum install git -y

# Verify installation
git --version
```

### 🐧 Amazon Linux 2023

```bash
# Update system
sudo dnf update -y

# Install Git
sudo dnf install git -y

# Verify installation
git --version
```

### 🟠 Ubuntu

```bash
# Update package index
sudo apt update

# Install Git
sudo apt install git -y

# Verify installation
git --version
```

### 🔴 RHEL

```bash
# Update system
sudo dnf update -y

# Install Git
sudo dnf install git -y

# Verify installation
git --version
```

### 🪟 Windows – PowerShell

**Using winget:**

```powershell
winget search Git.Git

winget install --id Git.Git -e

git --version
```

**Using Chocolatey:**

```powershell
choco search git

choco install git -y

git --version
```

### 🍎 macOS – Homebrew

```bash
# Update Homebrew
brew update

# Search Git
brew search git

# Install Git
brew install git

# Verify installation
git --version
```

---

## 🔍 5. Git Verification Commands

### 📌 Check Git Version

```bash
git --version
```

### 📌 Check Git Installation Path

```bash
# Linux / macOS
which git

# Windows PowerShell
where.exe git
```

### 📌 Check Git Configuration

```bash
git config --list
```

### 📌 Check Global Configuration

```bash
git config --global --list
```

### 📌 Check Git Executable

```bash
git --exec-path
```

---

## ⚙️ 6. Git Initial Configuration

### 👤 Configure Username

```bash
git config --global user.name "Your Name"
```

### 📧 Configure Email

```bash
git config --global user.email "your-email@example.com"
```

### 🔎 Verify Configuration

```bash
git config --global --list
```

### ✏️ Open Global Configuration

```bash
git config --global --edit
```

### 🌍 Set Default Branch Name

```bash
git config --global init.defaultBranch main
```

### 🎨 Enable Colored Output

```bash
git config --global color.ui auto
```

---

## 🛠️ 7. Basic Git Commands

### 📁 Initialize Repository

```bash
git init
```

### 📋 Check Repository Status

```bash
git status
```

### ➕ Add Files to Staging Area

```bash
# Add specific file
git add README.md

# Add all files
git add .

# Add all tracked and untracked changes
git add -A
```

### 📸 Create Commit

```bash
git commit -m "Initial commit"
```

### 📜 View Commit History

```bash
git log
```

### 📜 Compact Commit History

```bash
git log --oneline
```

### 🌿 List Branches

```bash
git branch
```

### 🌱 Create Branch

```bash
git branch feature-branch
```

### 🔀 Switch Branch

```bash
git switch feature-branch
```

### 🌱 Create and Switch Branch

```bash
git switch -c feature-branch
```

### 🔗 Connect Remote Repository

```bash
git remote add origin REPOSITORY_URL
```

### 📤 Push Code

```bash
git push -u origin main
```

### 📥 Pull Latest Changes

```bash
git pull
```

### 📥 Clone Repository

```bash
git clone REPOSITORY_URL
```

---

## 🔑 8. SSH Key Configuration

SSH keys allow secure authentication with Git hosting services such as GitHub and GitLab.

### 🔐 Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

### 📋 Display Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

### 🔍 Test GitHub SSH Connection

```bash
ssh -T git@github.com
```

> Add your public key to your GitHub or GitLab account before testing the connection.

---

## 🧹 9. Git Maintenance Commands

### 🗑️ Remove Untracked Files (Preview)

```bash
git clean -n
```

### 🗑️ Remove Untracked Files

```bash
git clean -f
```

### 📦 Check Repository Size

```bash
git count-objects -vH
```

### 🔄 Fetch Remote Changes

```bash
git fetch
```

### 🔍 Compare Changes

```bash
git diff
```

### 📋 View Remote Repositories

```bash
git remote -v
```

### 🧪 Check Git Help

```bash
git help
git help config
git help commit
```

---

## 📖 10. Official Documentation

- 🔗 Git Official Website: https://git-scm.com/
- 📚 Git Documentation: https://git-scm.com/doc
- 📖 Git Book: https://git-scm.com/book/en/v2
- 🐙 GitHub Documentation: https://docs.github.com/

---

## 🎯 Happy Learning!

**Learn · Practice · Commit · Push · Collaborate** 🚀