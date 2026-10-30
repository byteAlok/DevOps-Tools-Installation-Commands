# 🌍 Terraform – Installation & Commands Guide

A practical guide to installing, configuring, and using **Terraform CLI** across different operating systems. This README covers installation commands, configuration files, providers, initialization, planning, deployment, state management, and commonly used Terraform commands. ⚙️🚀

---

## 📌 1. Introduction

Terraform is an Infrastructure as Code (IaC) tool developed by HashiCorp. It allows you to define, provision, and manage infrastructure using configuration files.

- **Tool:** Terraform
- **Developer:** HashiCorp
- **Configuration Language:** HCL (HashiCorp Configuration Language)
- **File Extensions:** `.tf`, `.tf.json`
- **CLI:** Terraform CLI
- **Primary Purpose:** Infrastructure Automation

## 🧩 2. Terraform Components

| Component | Description |
|---|---|
| Terraform CLI | Executes Terraform commands |
| Provider | Connects Terraform to cloud platforms and services |
| Resource | Defines infrastructure components |
| Data Source | Reads existing infrastructure information |
| Module | Reusable Terraform configuration |
| State File | Tracks infrastructure managed by Terraform |
| Backend | Stores and manages Terraform state |
| Provisioner | Executes commands on local or remote machines |

## 💻 3. Supported Operating Systems

| Operating System | Package Manager / Method |
|---|---|
| Amazon Linux 2 | YUM |
| Amazon Linux 2023 | DNF |
| Ubuntu | APT |
| RHEL | YUM / DNF |
| Windows | Manual ZIP / Chocolatey |
| macOS | Homebrew |

---

## 📦 4. Package Management Commands

### 🔍 Search Available Packages

**Amazon Linux 2 / RHEL**
```bash
yum search terraform
```

**Amazon Linux 2023**
```bash
dnf search terraform
```

**Ubuntu**
```bash
apt search terraform
```

### 📋 List Available Packages

```bash
# YUM
yum list available | grep terraform

# DNF
dnf list available | grep terraform

# APT
apt list terraform
```

### 📥 Check Installed Packages

```bash
# YUM
yum list installed | grep terraform

# DNF
dnf list installed | grep terraform

# APT
apt list --installed | grep terraform
```

### ℹ️ Package Information

```bash
# YUM
yum info terraform

# DNF
dnf info terraform

# APT
apt show terraform
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

## 🐧 5. Install Terraform on Amazon Linux 2

### 🔄 Update System

```bash
sudo yum update -y
```

### 🛠️ Install Required Packages

```bash
sudo yum install -y yum-utils
```

### 🔗 Add HashiCorp Repository

```bash
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
```

### 📥 Install Terraform

```bash
sudo yum install -y terraform
```

### 🔍 Verify Installation

```bash
terraform version
```

---

## 🐧 6. Install Terraform on Amazon Linux 2023

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🛠️ Install Required Packages

```bash
sudo dnf install -y dnf-plugins-core
```

### 🔗 Add HashiCorp Repository

```bash
sudo dnf config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
```

### 📥 Install Terraform

```bash
sudo dnf install -y terraform
```

### 🔍 Verify Installation

```bash
terraform version
```

---

## 🐧 7. Install Terraform on Ubuntu

### 🔄 Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### 🛠️ Install Required Packages

```bash
sudo apt install -y gnupg software-properties-common wget
```

### 🔐 Add HashiCorp GPG Key

```bash
wget -O- https://apt.releases.hashicorp.com/gpg | \
sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

### 🔗 Add HashiCorp Repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(. /etc/os-release && echo ${UBUNTU_CODENAME:-$VERSION_CODENAME}) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list
```

### 📥 Install Terraform

```bash
sudo apt update
sudo apt install -y terraform
```

### 🔍 Verify Installation

```bash
terraform version
```

---

## 🐧 8. Install Terraform on RHEL

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🛠️ Install Required Packages

```bash
sudo dnf install -y yum-utils
```

### 🔗 Add HashiCorp Repository

```bash
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
```

### 📥 Install Terraform

```bash
sudo dnf install -y terraform
```

### 🔍 Verify Installation

```bash
terraform version
```

---

## 🪟 9. Install Terraform on Windows

### 📥 Method 1: Manual Installation

1. Visit the official Terraform installation page.
2. Download the Windows AMD64 ZIP package.
3. Extract the ZIP file.
4. Move `terraform.exe` into a permanent directory, for example:

```text
C:\Terraform
```

5. Add `C:\Terraform` to the Windows System Environment Variable `PATH`.
6. Open a new PowerShell terminal.

### 🔍 Verify Installation

```powershell
terraform version
```

### 📦 Method 2: Using Chocolatey

```powershell
choco install terraform -y
```

### 🔄 Upgrade Terraform

```powershell
choco upgrade terraform -y
```

---

## 🍎 10. Install Terraform on macOS

### 📦 Install Using Homebrew

```bash
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```

### 🔄 Upgrade Terraform

```bash
brew upgrade hashicorp/tap/terraform
```

### 🔍 Verify Installation

```bash
terraform version
```

---

## 🔍 11. Terraform CLI Commands

### 📌 Version Information

```bash
# Display Terraform version
terraform version

# Display Terraform help
terraform -help

# Help for a specific command
terraform plan -help
```

### 📁 Working Directory Commands

```bash
# Initialize the working directory
terraform init

# Reinitialize providers and modules
terraform init -upgrade

# Initialize with backend disabled
terraform init -backend=false

# Format Terraform files
terraform fmt

# Format files recursively
terraform fmt -recursive

# Check configuration syntax
terraform validate
```

### 📊 Planning and Deployment

```bash
# Preview infrastructure changes
terraform plan

# Save execution plan
terraform plan -out=tfplan

# Apply infrastructure changes
terraform apply

# Apply saved execution plan
terraform apply tfplan

# Apply without interactive approval
terraform apply -auto-approve

# Destroy managed infrastructure
terraform destroy

# Destroy without interactive approval
terraform destroy -auto-approve
```

### 📤 Output Commands

```bash
# Display all outputs
terraform output

# Display a specific output
terraform output instance_ip

# Display output in JSON format
terraform output -json
```

---

## 🧱 12. Terraform Configuration Files

Terraform configuration is generally written in HCL.

| File | Purpose |
|---|---|
| `main.tf` | Main infrastructure configuration |
| `provider.tf` | Provider configuration |
| `variable.tf` | Input variable declarations |
| `terraform.tfvars` | Variable values |
| `output.tf` | Output declarations |
| `versions.tf` | Terraform and provider version requirements |
| `.terraform.lock.hcl` | Provider dependency lock file |
| `terraform.tfstate` | Terraform state file |

### 📝 Example: versions.tf

```hcl
terraform {
  required_version = ">= 1.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 6.0"
    }
  }
}
```

### ☁️ Example: provider.tf

```hcl
provider "aws" {
  region = "us-east-1"
}
```

> Configure AWS credentials securely using an IAM role, environment variables, or AWS CLI profiles. Avoid hardcoding access keys in Terraform files.

### 🪣 Example: main.tf

```hcl
resource "aws_s3_bucket" "dev_bucket" {
  bucket = "my-terraform-dev-bucket-123456"
}
```

### 📤 Example: output.tf

```hcl
output "bucket_name" {
  value = aws_s3_bucket.dev_bucket.bucket
}
```

### ⚙️ Example: terraform.tfvars

```hcl
aws_region = "us-east-1"
```

---

## 🔄 13. Terraform Workflow

Terraform follows a common workflow when managing infrastructure.

### 1️⃣ Initialize

```bash
terraform init
```

Downloads required providers and initializes the working directory.

### 2️⃣ Format

```bash
terraform fmt
```

Formats Terraform configuration files.

### 3️⃣ Validate

```bash
terraform validate
```

Checks whether the configuration is syntactically valid.

### 4️⃣ Plan

```bash
terraform plan
```

Previews the changes Terraform intends to make.

### 5️⃣ Apply

```bash
terraform apply
```

Creates, updates, or deletes infrastructure according to the execution plan.

### 6️⃣ Destroy

```bash
terraform destroy
```

Destroys infrastructure managed by the current Terraform configuration and state.

---

## 🔌 14. Provider Commands

Providers allow Terraform to interact with cloud platforms and other services.

```bash
# Download providers and modules
terraform init

# Upgrade provider dependencies
terraform init -upgrade

# Display provider requirements
terraform providers

# Generate provider dependency lock file
terraform providers lock

# Display provider documentation-related help
terraform providers -help
```

### 🌐 Common Terraform Providers

| Provider | Purpose |
|---|---|
| AWS | Amazon Web Services |
| AzureRM | Microsoft Azure |
| Google | Google Cloud Platform |
| Kubernetes | Kubernetes clusters |
| Docker | Docker resources |
| GitHub | GitHub resources |

---

## 📦 15. Terraform Module Commands

Modules help organize and reuse Terraform configurations.

```bash
# Initialize modules
terraform init

# Display module tree
terraform get

# Update module dependencies
terraform get -update

# Display module-related information
terraform providers
```

---

## 🔐 16. Terraform State Commands

Terraform state tracks the resources managed by Terraform.

```bash
# List resources in state
terraform state list

# Display details of a resource
terraform state show aws_s3_bucket.dev_bucket

# Move a resource in state
terraform state mv aws_s3_bucket.old aws_s3_bucket.new

# Remove a resource from state
terraform state rm aws_s3_bucket.dev_bucket

# Pull current state
terraform state pull

# Push local state
terraform state push terraform.tfstate
```

⚠️ State files can contain sensitive information. Protect them carefully and prefer a secure remote backend for team environments.

---

## 🗂️ 17. Terraform Workspace Commands

Workspaces allow multiple state instances to be maintained for the same configuration.

```bash
# List workspaces
terraform workspace list

# Show current workspace
terraform workspace show

# Create a workspace
terraform workspace new dev

# Select a workspace
terraform workspace select dev

# Delete a workspace
terraform workspace delete dev
```

---

## 🔎 18. Terraform Import Commands

Import allows existing infrastructure to be brought under Terraform state management.

```bash
# Import an existing resource
terraform import aws_s3_bucket.dev_bucket my-existing-bucket

# Preview changes after import
terraform plan
```

Importing a resource into state does not automatically generate its complete configuration. Write the corresponding resource block in your `.tf` files.

---

## 🧪 19. Terraform Console and Graph

```bash
# Open interactive Terraform console
terraform console

# Generate dependency graph
terraform graph

# Generate graph in DOT format
terraform graph -type=plan
```

---

## 🐳 20. Run Terraform Using Docker

### 📥 Pull Terraform Image

```bash
docker pull hashicorp/terraform:latest
```

### 🔍 Check Terraform Version

```bash
docker run --rm hashicorp/terraform:latest version
```

### 📁 Run Terraform Inside a Project Directory

```bash
docker run --rm -it \
  -v "$(pwd)":/workspace \
  -w /workspace \
  hashicorp/terraform:latest init
```

```bash
docker run --rm -it \
  -v "$(pwd)":/workspace \
  -w /workspace \
  hashicorp/terraform:latest plan
```

---

## 🧹 21. Uninstall Terraform

### 🐧 Amazon Linux 2 / RHEL

```bash
sudo yum remove -y terraform
```

### 🐧 Amazon Linux 2023

```bash
sudo dnf remove -y terraform
```

### 🐧 Ubuntu

```bash
sudo apt remove -y terraform
```

Remove package configuration files if required:

```bash
sudo apt purge -y terraform
```

### 🪟 Windows

Remove `terraform.exe` from its installation directory and remove that directory from the System `PATH`.

For Chocolatey:

```powershell
choco uninstall terraform -y
```

### 🍎 macOS

```bash
brew uninstall hashicorp/tap/terraform
```

---

## 🛡️ 22. Best Practices

- Use remote state storage for team environments.
- Enable state locking where supported by the backend.
- Never commit sensitive state files or credentials to Git.
- Use `.gitignore` for local Terraform files.
- Pin provider versions and commit `.terraform.lock.hcl`.
- Run `terraform fmt` and `terraform validate` before applying.
- Always review `terraform plan` before production deployment.
- Use IAM roles and least-privilege permissions.
- Keep Terraform and providers updated.

### 🚫 Recommended .gitignore

```gitignore
# Terraform directories
.terraform/

# Terraform state files
*.tfstate
*.tfstate.*

# Terraform crash logs
crash.log
crash.*.log

# Variable files containing sensitive values
*.tfvars
*.tfvars.json

# Override files
override.tf
override.tf.json
*_override.tf
*_override.tf.json

# CLI configuration
.terraformrc
terraform.rc

# Saved plan files
*.tfplan
tfplan
```

> Keep `.terraform.lock.hcl` in Git. It helps maintain consistent provider selections across environments.

---

## 📚 23. Official Documentation

- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs)
- [Terraform Installation](https://developer.hashicorp.com/terraform/install)
- [Terraform CLI Commands](https://developer.hashicorp.com/terraform/cli/commands)
- [Terraform Language](https://developer.hashicorp.com/terraform/language)
- [Terraform Providers](https://registry.terraform.io/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)

---

**🚀 Learn • Build • Automate • Deploy**

