# 🚀 DevOps Tools Installation Commands

A practical collection of installation commands and setup guides for popular DevOps ⚙️, Cloud ☁️, Programming 💻, and Infrastructure 🏗️ tools across different operating systems.

This repository brings together essential installation commands, package management instructions, dependencies, initial configurations, version verification, updates, and uninstallation procedures in one organized place.

The goal is to make software installation and environment setup easier, faster, and more reliable by providing OS-specific commands and practical setup instructions.

## 🎯 Repository Purpose

Setting up development and infrastructure environments often requires installing multiple tools across different operating systems. However, installation procedures, package managers, dependencies, package names, and configuration methods can vary from one operating system to another.

This repository provides a centralized collection of installation guides to simplify these tasks.

Whether you are preparing a Linux server, configuring a local development machine, setting up cloud CLI tools, or installing infrastructure automation tools, you can find the relevant commands and setup instructions here.

## 🖥️ Supported Operating Systems

Installation instructions are organized according to the operating systems and distributions supported by individual tools.

| Operating System | Package Manager / Method |
|---|---|
| 🟠 Ubuntu | APT |
| 🐧 Amazon Linux 2 | YUM |
| 🐧 Amazon Linux 2023 | DNF |
| 🔴 RHEL | YUM / DNF |
| 🪟 Windows | winget / Chocolatey / Official Installers |
| 🍎 macOS | Homebrew / Official Installers |

> **Note:** Not every tool supports all listed operating systems. Package availability and installation methods may also vary depending on the OS version and enabled repositories.

## 📂 Repository Structure

```text
DevOps-Tools-Installation-Commands/
│
├── Programming Languages & Development
│   ├── Dotnet.md
│   ├── Java.md
│   ├── NodeJs.md
│   ├── Php.md
│   └── Python.md
│
├── Version Control
│   └── Git.md
│
├── DevOps & Infrastructure
│   ├── Ansible.md
│   ├── Docker.md
│   ├── Jenkins.md
│   ├── Kubernates.md
│   └── Terraform.md
│
├── Cloud Platforms & CLI Tools
│   ├── AWS.md
│   ├── Azure.md
│   └── GCP.md
│
├── Monitoring & Observability
│   ├── Prometheus-Grafana-PagerDuty-Monitoring.md
│   └── Prometheus-NodeExporter.md
│
└── README.md
```

## 📚 Installation Guides

Individual Markdown files contain installation commands and setup instructions for different tools and platforms.

### 💻 Programming Languages & Development Tools

| Tool | Installation Guide |
|---|---|
| ☕ Java | [Java.md](Programming%20Languages%20%26%20Development/Java.md) |
| 🟣 .NET | [Dotnet.md](Programming%20Languages%20%26%20Development/Dotnet.md) |
| 🐍 Python | [Python.md](Programming%20Languages%20%26%20Development/Python.md) |
| 🐘 PHP | [Php.md](Programming%20Languages%20%26%20Development/Php.md) |
| 🟢 Node.js | [NodeJs.md](Programming%20Languages%20%26%20Development/NodeJs.md) |

### 🔀 Version Control

| Tool | Installation Guide |
|---|---|
| 🔧 Git | [Git.md](Version%20Control/Git.md) |

### ⚙️ DevOps & Infrastructure Tools

| Tool | Installation Guide |
|---|---|
| 🐳 Docker | [Docker.md](DevOps%20%26%20Infrastructure/Docker.md) |
| 🔨 Jenkins | [Jenkins.md](DevOps%20%26%20Infrastructure/Jenkins.md) |
| 🏗️ Terraform | [Terraform.md](DevOps%20%26%20Infrastructure/Terraform.md) |
| 🔧 Ansible | [Ansible.md](DevOps%20%26%20Infrastructure/Ansible.md) |
| ☸️ Kubernetes | [Kubernates.md](DevOps%20%26%20Infrastructure/Kubernates.md) |

### ☁️ Cloud Platforms & CLI Tools

| Platform | Installation Guide |
|---|---|
| 🟠 Amazon Web Services (AWS) | [AWS.md](Cloud%20Platforms%20%26%20CLI%20Tools/AWS.md) |
| 🔵 Microsoft Azure | [Azure.md](Cloud%20Platforms%20%26%20CLI%20Tools/Azure.md) |
| 🌐 Google Cloud Platform (GCP) | [GCP.md](Cloud%20Platforms%20%26%20CLI%20Tools/GCP.md) |

### 📊 Monitoring & Observability Tools

| Tool / Stack | Installation Guide |
|---|---|
| 📈 Prometheus Node Exporter | [Prometheus-NodeExporter.md](Monitoring%20%26%20Observability/Prometheus-NodeExporter.md) |
| 📊 Prometheus, Grafana & PagerDuty | [Prometheus-Grafana-PagerDuty-Monitoring.md](Monitoring%20%26%20Observability/Prometheus-Grafana-PagerDuty-Monitoring.md) |

## 🛠️ What Each Guide Covers

Depending on the tool and operating system, individual installation guides include:

- 🔍 **Package Management:** Searching for packages, listing available and installed packages, and checking package information.
- 📦 **Dependencies:** Identifying and installing required dependencies and prerequisites.
- 🚀 **Installation:** Step-by-step installation commands for supported operating systems.
- ⚙️ **Initial Configuration:** Setting up environment variables, PATH, and essential configurations.
- ✅ **Verification:** Checking installed versions, executable paths, and confirming successful installation.
- 🔄 **Version Management:** Managing or switching between available versions wherever supported.
- 🔧 **Useful Commands:** Essential commands for managing and working with installed tools.
- 🧹 **Uninstallation:** Removing installed packages and related components.
- 🔗 **Official References:** Links to official installation documentation and resources.

## 💡 How This Repository Helps Solve Installation Problems

Installing DevOps and development tools is not always straightforward. Different operating systems follow different installation procedures, and the same tool may require different package names, dependencies, or configuration steps.

This repository helps address common installation and setup challenges.

### 🐧 1. Different Package Managers Across Operating Systems

**Problem:** A command that works on Ubuntu may not work on Amazon Linux or RHEL because they use different package managers.

**Solution:** Guides provide OS-specific commands using the appropriate package manager.

```bash
# Ubuntu
sudo apt update
sudo apt install git -y

# Amazon Linux 2
sudo yum install git -y

# Amazon Linux 2023
sudo dnf install git -y
```

### 📦 2. Package Name and Availability Differences

**Problem:** Package names and available versions can differ across Linux distributions. Sometimes the required package is not available in the currently enabled repositories.

**Solution:** Package search, listing, and information commands help identify available packages before installation.

```bash
# Ubuntu
apt search openjdk

# Amazon Linux 2
yum search java

# Amazon Linux 2023
dnf search java
```

### 🔧 3. Missing Dependencies and Prerequisites

**Problem:** Some tools require additional packages, dependencies, repositories, or prerequisite configurations before installation.

**Solution:** Installation guides provide the required setup commands and dependencies wherever applicable.

### ⚙️ 4. Environment Variables and PATH Configuration

**Problem:** A tool may be installed successfully but its executable might not be recognized in a new terminal. Some tools also require environment variables such as `JAVA_HOME`.

**Solution:** Guides include environment variable and PATH configuration instructions wherever required.

```bash
# Example: JAVA_HOME configuration
export JAVA_HOME=/usr/lib/jvm/java-21-amazon-corretto

export PATH=$JAVA_HOME/bin:$PATH

# Verify configuration
echo $JAVA_HOME
java -version
```

### 🔐 5. Permission and Administrator Issues

**Problem:** Installing or managing system-level packages often requires elevated privileges.

**Solution:** Linux installation commands use `sudo` where necessary, while Windows instructions identify the appropriate PowerShell or administrator-level operations.

### ❌ 6. Installation Verification and Troubleshooting

**Problem:** An installation command may complete without confirming whether the tool is correctly installed or accessible.

**Solution:** Guides include version checks, executable location commands, and other verification steps to help identify common setup issues.

```bash
# Check installed version
git --version

# Locate executable
which git
```

### 🔄 7. Updating and Removing Installed Tools

**Problem:** Managing outdated installations or removing unnecessary packages can become confusing when different operating systems use different commands.

**Solution:** Relevant guides include OS-specific update and uninstallation instructions.

## 🌟 Key Benefits

- 📚 **Centralized Collection:** Keep installation commands for multiple tools organized in one repository.
- 🖥️ **Multi-OS Support:** Find installation instructions for Linux distributions, Windows, and macOS wherever supported.
- ⚡ **Faster Environment Setup:** Reduce the time spent searching for installation commands and prerequisites.
- 🔧 **Practical Configuration:** Follow initial configuration instructions instead of stopping at package installation.
- 🔍 **Easy Verification:** Confirm whether tools are installed and accessible through version and path checks.
- 🔄 **Simplified Maintenance:** Find commands for updating, managing, and uninstalling tools.
- 🧩 **Reusable Reference:** Revisit the same installation instructions whenever setting up a new machine, server, or environment.
- 🎯 **Consistent Organization:** Follow a similar documentation structure across different tools.

## 🔗 Official Documentation

For the latest installation instructions, version compatibility, and platform-specific requirements, refer to the official documentation.

| Tool | Official Documentation |
|---|---|
| 🔧 Git | [Git Documentation](https://git-scm.com/doc) |
| ☕ Java | [Java Documentation](https://docs.oracle.com/en/java/) |
| 🟣 .NET | [.NET Documentation](https://learn.microsoft.com/en-us/dotnet/) |
| 🐍 Python | [Python Documentation](https://docs.python.org/3/) |
| 🐘 PHP | [PHP Documentation](https://www.php.net/docs.php) |
| 🟢 Node.js | [Node.js Documentation](https://nodejs.org/en/docs) |
| 🐳 Docker | [Docker Documentation](https://docs.docker.com/) |
| 🔨 Jenkins | [Jenkins Documentation](https://www.jenkins.io/doc/) |
| 🏗️ Terraform | [Terraform Documentation](https://developer.hashicorp.com/terraform/docs) |
| 🔧 Ansible | [Ansible Documentation](https://docs.ansible.com/) |
| ☸️ Kubernetes | [Kubernetes Documentation](https://kubernetes.io/docs/) |
| ☁️ AWS | [AWS Documentation](https://docs.aws.amazon.com/) |
| 🔵 Azure | [Azure Documentation](https://learn.microsoft.com/en-us/azure/) |
| 🌐 GCP | [Google Cloud Documentation](https://cloud.google.com/docs) |
| 📈 Prometheus | [Prometheus Documentation](https://prometheus.io/docs/) |
| 📊 Grafana | [Grafana Documentation](https://grafana.com/docs/) |

## ⚠️ Important Notes

- Always check the operating system version before executing installation commands.
- Use the appropriate package manager for your Linux distribution.
- Package availability may depend on enabled repositories and configured sources.
- Follow official documentation for the latest supported versions and installation procedures.
- Review commands before executing them, especially those involving system-level changes or package removal.
- Some tools may require additional configuration after installation.

## 👨‍💻 Maintained By

**Alok Maurya** | [byteAlok](https://github.com/byteAlok)

💼 **Full Stack Engineer**

🌐 Portfolio & Projects: [aloksde.com](https://aloksde.com)

---

### 🎯 Install · Configure · Verify · Manage

*Keeping essential installation commands and setup instructions organized in one place.* 🚀
