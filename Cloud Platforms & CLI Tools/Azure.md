# 🔷 Azure CLI – Installation & Commands Guide

A practical guide to installing, configuring, and managing **Microsoft Azure Command-Line Interface (Azure CLI)** across different operating systems. This README covers authentication, subscriptions, resource groups, virtual machines, storage accounts, networking, App Service, Azure Container Registry, AKS, Key Vault, and monitoring commands. ⚙️🚀

---

## 📌 1. Introduction

Azure CLI is a cross-platform command-line tool that allows users to interact with Microsoft Azure services directly from a terminal.

- **Tool:** Azure Command-Line Interface
- **Developer:** Microsoft
- **Command:** `az`
- **Configuration:** JSON
- **Authentication:** Microsoft Entra ID, Service Principal, Managed Identity
- **Primary Purpose:** Azure Resource Management and Automation

## 🧩 2. Azure CLI Components

| Component | Description |
|---|---|
| Azure CLI | Command-line interface for Azure services |
| Azure Account | Manages Azure subscriptions and account context |
| Resource Group | Logical container for Azure resources |
| Azure Resource Manager | Deployment and management layer |
| Microsoft Entra ID | Identity and authentication service |
| Service Principal | Application identity for automation |
| Managed Identity | Azure-managed identity for workloads |
| Azure Cloud Shell | Browser-based shell with Azure CLI preinstalled |
| CLI Extensions | Additional commands for Azure services |

## 💻 3. Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | Docker container |
| Amazon Linux 2023 | Docker container |
| Ubuntu | Microsoft APT repository |
| RHEL 8 / 9 / 10 | Microsoft RPM repository |
| Windows | WinGet / MSI |
| macOS | Homebrew |

> **Note:** Microsoft does not list Amazon Linux 2 or Amazon Linux 2023 among its supported native Linux package-installation distributions. For these systems, this guide uses Microsoft's official Azure CLI Docker image instead of presenting an unverified native installation command.

---

## 🐧 4. Install Azure CLI on Ubuntu

### 🔄 Step 1: Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo apt install -y ca-certificates curl apt-transport-https gnupg lsb-release
```

### 🔑 Step 3: Import Microsoft Signing Key

```bash
sudo mkdir -p /etc/apt/keyrings

curl -sLS https://packages.microsoft.com/keys/microsoft.asc | \
  gpg --dearmor | \
  sudo tee /etc/apt/keyrings/microsoft.gpg > /dev/null

sudo chmod go+r /etc/apt/keyrings/microsoft.gpg
```

### 📦 Step 4: Add Azure CLI Repository

```bash
AZ_DIST=$(lsb_release -cs)

echo "Types: deb
URIs: https://packages.microsoft.com/repos/azure-cli/
Suites: ${AZ_DIST}
Components: main
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/microsoft.gpg" | \
sudo tee /etc/apt/sources.list.d/azure-cli.sources
```

### 📥 Step 5: Install Azure CLI

```bash
sudo apt update
sudo apt install -y azure-cli
```

### 🔍 Step 6: Verify Installation

```bash
az version
```

---

## 🐧 5. Install Azure CLI on RHEL

The following commands use Microsoft's RPM repository.

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🔑 Step 2: Import Microsoft Signing Key

For RHEL 8 and RHEL 9:

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

For RHEL 10:

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft-2025.asc
```

### 📦 Step 3: Add Microsoft Repository

For RHEL 8:

```bash
sudo dnf install -y https://packages.microsoft.com/config/rhel/8/packages-microsoft-prod.rpm
```

For RHEL 9:

```bash
sudo dnf install -y https://packages.microsoft.com/config/rhel/9.0/packages-microsoft-prod.rpm
```

For RHEL 10:

```bash
sudo dnf install -y https://packages.microsoft.com/config/rhel/10/packages-microsoft-prod.rpm
```

### 📥 Step 4: Install Azure CLI

```bash
sudo dnf install -y azure-cli
```

### 🔍 Step 5: Verify Installation

```bash
az version
```

> RHEL 7 is no longer supported for current Azure CLI updates. Version 2.38.2 was the last supported release.

---

## 🐧 6. Use Azure CLI on Amazon Linux 2

Amazon Linux 2 does not have an officially documented native Azure CLI package installation path in Microsoft's supported Linux installation instructions.

You can run Azure CLI using Microsoft's official Docker image.

### 🛠️ Step 1: Install Docker

```bash
sudo amazon-linux-extras install docker -y
```

### ▶️ Step 2: Start Docker

```bash
sudo systemctl enable --now docker
```

### 📥 Step 3: Pull Azure CLI Image

```bash
sudo docker pull mcr.microsoft.com/azure-cli:latest
```

### 🚀 Step 4: Run Azure CLI

```bash
sudo docker run -it --rm \
  mcr.microsoft.com/azure-cli:latest
```

### 🔍 Step 5: Verify Installation

Inside the container:

```bash
az version
```

---

## 🐧 7. Use Azure CLI on Amazon Linux 2023

Amazon Linux 2023 is also not listed among Microsoft's supported native Linux package-installation distributions.

Use the official Azure CLI Docker image.

### 🛠️ Step 1: Install Docker

```bash
sudo dnf update -y
sudo dnf install -y docker
```

### ▶️ Step 2: Start Docker

```bash
sudo systemctl enable --now docker
```

### 📥 Step 3: Pull Azure CLI Image

```bash
sudo docker pull mcr.microsoft.com/azure-cli:latest
```

### 🚀 Step 4: Run Azure CLI

```bash
sudo docker run -it --rm \
  mcr.microsoft.com/azure-cli:latest
```

### 🔍 Step 5: Verify Installation

```bash
az version
```

---

## 🪟 8. Install Azure CLI on Windows

### 📦 Method 1: Using WinGet

Open PowerShell:

```powershell
winget install --exact --id Microsoft.AzureCLI
```

### 📦 Method 2: Using MSI Installer

Download the official 64-bit installer:

```text
https://aka.ms/installazurecliwindowsx64
```

Or install using PowerShell:

```powershell
$ProgressPreference = 'SilentlyContinue'

Invoke-WebRequest `
  -Uri https://aka.ms/installazurecliwindowsx64 `
  -OutFile .\AzureCLI.msi

Start-Process msiexec.exe -Wait -ArgumentList '/I', 'AzureCLI.msi', '/quiet'

Remove-Item .\AzureCLI.msi
```

### 🔍 Verify Installation

Close and reopen the terminal:

```powershell
az version
```

---

## 🍎 9. Install Azure CLI on macOS

### 📦 Method 1: Using Homebrew

```bash
brew update
brew install azure-cli
```

### 🔍 Verify Installation

```bash
az version
```

> Microsoft's current Homebrew installation guidance requires macOS 13 or later.

---

## 🔄 10. Update Azure CLI

### 🌍 Method 1: Using Azure CLI

```bash
az upgrade
```

This updates Azure CLI and, by default, its installed extensions.

### 🐧 Ubuntu

```bash
sudo apt update
sudo apt install --only-upgrade -y azure-cli
```

### 🐧 RHEL

```bash
sudo dnf update -y azure-cli
```

### 🪟 Windows

```powershell
winget upgrade --exact --id Microsoft.AzureCLI
```

### 🍎 macOS

```bash
brew update
brew upgrade azure-cli
```

### 🔍 Verify Updated Version

```bash
az version
```

---

## 🔐 11. Azure CLI Authentication

Azure CLI needs authentication before it can manage Azure resources.

### 🌐 Login to Azure

```bash
az login
```

A browser window opens for Microsoft account authentication.

### 🔑 Login Using Device Code

```bash
az login --use-device-code
```

Useful when a browser is unavailable on the machine.

### 👤 Check Logged-in Account

```bash
az account show
```

### 📋 List Available Subscriptions

```bash
az account list --output table
```

### 🔄 Select Subscription

```bash
az account set --subscription "<SUBSCRIPTION_ID>"
```

### 🔍 Verify Active Subscription

```bash
az account show --output table
```

### 🚪 Logout

```bash
az logout
```

---

## 👤 12. Azure Service Principal Authentication

A Service Principal is an application identity used for automated authentication, such as CI/CD pipelines.

### 🏗️ Create Service Principal

```bash
az ad sp create-for-rbac \
  --name "cicd-service-principal" \
  --role Contributor \
  --scopes /subscriptions/<SUBSCRIPTION_ID>
```

The command returns values including:

- `appId`
- `password`
- `tenant`

Store these credentials securely.

### 🔐 Login Using Service Principal

```bash
az login \
  --service-principal \
  --username "<APP_ID>" \
  --password "<CLIENT_SECRET>" \
  --tenant "<TENANT_ID>"
```

> For production automation, prefer workload identity federation or managed identity where supported. Avoid storing client secrets directly in scripts or Git repositories.

---

## 📦 13. Azure Resource Group Commands

A Resource Group is a logical container for Azure resources.

### 📋 List Resource Groups

```bash
az group list --output table
```

### 🏗️ Create Resource Group

```bash
az group create \
  --name dev-resource-group \
  --location centralindia
```

### 🔍 Get Resource Group Details

```bash
az group show \
  --name dev-resource-group
```

### 📊 List Resources in Resource Group

```bash
az resource list \
  --resource-group dev-resource-group \
  --output table
```

### 🔄 Update Resource Group Tags

```bash
az group update \
  --name dev-resource-group \
  --set tags.Environment=Development
```

### 🗑️ Delete Resource Group

```bash
az group delete \
  --name dev-resource-group \
  --yes
```

> Deleting a Resource Group deletes the resources contained in it. Verify the target before executing this command.

---

## 🌍 14. Azure Region Commands

### 📋 List Available Locations

```bash
az account list-locations --output table
```

### 🔍 List Locations with Selected Information

```bash
az account list-locations \
  --query "[].{Name:name,DisplayName:displayName}" \
  --output table
```

### 📍 Check Current Subscription

```bash
az account show \
  --query "{Subscription:name,ID:id,Tenant:tenantId}" \
  --output table
```

---

## 🖥️ 15. Azure Virtual Machine Commands

Azure Virtual Machines provide scalable compute resources.

### 📋 List Virtual Machines

```bash
az vm list --output table
```

### 🏗️ Create Linux Virtual Machine

```bash
az vm create \
  --resource-group dev-resource-group \
  --name dev-linux-vm \
  --image Ubuntu2204 \
  --size Standard_B1s \
  --admin-username azureuser \
  --generate-ssh-keys
```

### 🏗️ Create Windows Virtual Machine

```bash
az vm create \
  --resource-group dev-resource-group \
  --name dev-windows-vm \
  --image Win2022AzureEditionCore \
  --size Standard_B2s \
  --admin-username azureuser \
  --admin-password "<STRONG_PASSWORD>"
```

### 🔍 Get VM Details

```bash
az vm show \
  --resource-group dev-resource-group \
  --name dev-linux-vm \
  --output table
```

### ▶️ Start VM

```bash
az vm start \
  --resource-group dev-resource-group \
  --name dev-linux-vm
```

### ⏹️ Stop VM

```bash
az vm stop \
  --resource-group dev-resource-group \
  --name dev-linux-vm
```

### 🛑 Deallocate VM

```bash
az vm deallocate \
  --resource-group dev-resource-group \
  --name dev-linux-vm
```

### 🔄 Restart VM

```bash
az vm restart \
  --resource-group dev-resource-group \
  --name dev-linux-vm
```

### 🗑️ Delete VM

```bash
az vm delete \
  --resource-group dev-resource-group \
  --name dev-linux-vm \
  --yes
```

### 🌐 Get VM Public IP

```bash
az vm list-ip-addresses \
  --resource-group dev-resource-group \
  --name dev-linux-vm \
  --output table
```

---

## 🌐 16. Azure Virtual Network Commands

Azure Virtual Network provides private networking for Azure resources.

### 📋 List Virtual Networks

```bash
az network vnet list --output table
```

### 🏗️ Create Virtual Network

```bash
az network vnet create \
  --resource-group dev-resource-group \
  --name dev-vnet \
  --address-prefix 10.0.0.0/16 \
  --subnet-name public-subnet \
  --subnet-prefix 10.0.1.0/24
```

### 🔍 List Subnets

```bash
az network vnet subnet list \
  --resource-group dev-resource-group \
  --vnet-name dev-vnet \
  --output table
```

### 🏗️ Create Another Subnet

```bash
az network vnet subnet create \
  --resource-group dev-resource-group \
  --vnet-name dev-vnet \
  --name private-subnet \
  --address-prefix 10.0.2.0/24
```

### 📋 List Network Security Groups

```bash
az network nsg list --output table
```

### 🏗️ Create Network Security Group

```bash
az network nsg create \
  --resource-group dev-resource-group \
  --name dev-nsg
```

### 🔐 Create NSG Security Rule

```bash
az network nsg rule create \
  --resource-group dev-resource-group \
  --nsg-name dev-nsg \
  --name Allow-SSH \
  --priority 1000 \
  --direction Inbound \
  --access Allow \
  --protocol Tcp \
  --destination-port-ranges 22
```

> Restrict SSH and RDP access to trusted source IP ranges in production instead of allowing unrestricted access.

### 📋 List Public IP Addresses

```bash
az network public-ip list --output table
```

### 📋 List Network Interfaces

```bash
az network nic list --output table
```

---

## 🪣 17. Azure Storage Account Commands

Azure Storage provides Blob, File, Queue, and Table storage services.

### 📋 List Storage Accounts

```bash
az storage account list --output table
```

### 🏗️ Create Storage Account

Storage account names must be globally unique and contain only lowercase letters and numbers.

```bash
az storage account create \
  --name devstorage123456 \
  --resource-group dev-resource-group \
  --location centralindia \
  --sku Standard_LRS \
  --kind StorageV2
```

### 🔍 Get Storage Account Details

```bash
az storage account show \
  --name devstorage123456 \
  --resource-group dev-resource-group
```

### 📋 List Blob Containers

```bash
az storage container list \
  --account-name devstorage123456 \
  --auth-mode login \
  --output table
```

### 🏗️ Create Blob Container

```bash
az storage container create \
  --name documents \
  --account-name devstorage123456 \
  --auth-mode login
```

### 📤 Upload File to Blob Storage

```bash
az storage blob upload \
  --account-name devstorage123456 \
  --container-name documents \
  --name file.txt \
  --file ./file.txt \
  --auth-mode login
```

### 📥 Download Blob

```bash
az storage blob download \
  --account-name devstorage123456 \
  --container-name documents \
  --name file.txt \
  --file downloaded-file.txt \
  --auth-mode login
```

### 📋 List Blobs

```bash
az storage blob list \
  --account-name devstorage123456 \
  --container-name documents \
  --auth-mode login \
  --output table
```

### 🗑️ Delete Blob

```bash
az storage blob delete \
  --account-name devstorage123456 \
  --container-name documents \
  --name file.txt \
  --auth-mode login
```

> For Microsoft Entra ID authentication, the signed-in identity needs the appropriate Storage data-plane role, such as Storage Blob Data Contributor, for upload and download operations.

---

## 🌐 18. Azure App Service Commands

Azure App Service is a platform for hosting web applications and APIs.

### 📋 List App Service Plans

```bash
az appservice plan list --output table
```

### 🏗️ Create App Service Plan

```bash
az appservice plan create \
  --name dev-app-plan \
  --resource-group dev-resource-group \
  --location centralindia \
  --sku B1 \
  --is-linux
```

### 🚀 Create Web App

```bash
az webapp create \
  --resource-group dev-resource-group \
  --plan dev-app-plan \
  --name dev-webapp-123456 \
  --runtime "DOTNETCORE:8.0"
```

> App Service runtimes and available versions change over time. Check supported runtimes before creating a new application.

### 📋 List Web Apps

```bash
az webapp list --output table
```

### 🔍 Get Web App Details

```bash
az webapp show \
  --resource-group dev-resource-group \
  --name dev-webapp-123456
```

### 📦 Deploy ZIP Package

```bash
az webapp deploy \
  --resource-group dev-resource-group \
  --name dev-webapp-123456 \
  --src-path ./publish.zip \
  --type zip
```

### 🔄 Restart Web App

```bash
az webapp restart \
  --resource-group dev-resource-group \
  --name dev-webapp-123456
```

### ⏹️ Stop Web App

```bash
az webapp stop \
  --resource-group dev-resource-group \
  --name dev-webapp-123456
```

### ▶️ Start Web App

```bash
az webapp start \
  --resource-group dev-resource-group \
  --name dev-webapp-123456
```

### 📜 View Application Logs

```bash
az webapp log tail \
  --resource-group dev-resource-group \
  --name dev-webapp-123456
```

---

## 🐳 19. Azure Container Registry Commands

Azure Container Registry (ACR) is a managed container image registry.

### 📋 List Registries

```bash
az acr list --output table
```

### 🏗️ Create Container Registry

```bash
az acr create \
  --resource-group dev-resource-group \
  --name devregistry123456 \
  --sku Basic
```

### 🔐 Login to ACR

```bash
az acr login --name devregistry123456
```

### 📋 List Repositories

```bash
az acr repository list \
  --name devregistry123456 \
  --output table
```

### 📋 List Image Tags

```bash
az acr repository show-tags \
  --name devregistry123456 \
  --repository myapp \
  --output table
```

### 📤 Push Docker Image

```bash
docker tag myapp:latest devregistry123456.azurecr.io/myapp:v1

docker push devregistry123456.azurecr.io/myapp:v1
```

---

## ☸️ 20. Azure Kubernetes Service Commands

Azure Kubernetes Service (AKS) is a managed Kubernetes service.

### 📋 List AKS Clusters

```bash
az aks list --output table
```

### 🏗️ Create AKS Cluster

```bash
az aks create \
  --resource-group dev-resource-group \
  --name dev-aks-cluster \
  --node-count 1 \
  --generate-ssh-keys
```

### 🔑 Get AKS Credentials

```bash
az aks get-credentials \
  --resource-group dev-resource-group \
  --name dev-aks-cluster
```

### 📋 List Cluster Nodes

```bash
kubectl get nodes
```

### 📋 List Pods

```bash
kubectl get pods --all-namespaces
```

### 🔄 Scale AKS Node Pool

```bash
az aks scale \
  --resource-group dev-resource-group \
  --name dev-aks-cluster \
  --node-count 2
```

### 🔍 Show AKS Details

```bash
az aks show \
  --resource-group dev-resource-group \
  --name dev-aks-cluster \
  --output table
```

### 🗑️ Delete AKS Cluster

```bash
az aks delete \
  --resource-group dev-resource-group \
  --name dev-aks-cluster \
  --yes
```

---

## 🔐 21. Azure Key Vault Commands

Azure Key Vault securely stores secrets, keys, and certificates.

### 📋 List Key Vaults

```bash
az keyvault list --output table
```

### 🏗️ Create Key Vault

```bash
az keyvault create \
  --name dev-keyvault-123456 \
  --resource-group dev-resource-group \
  --location centralindia
```

### 🔐 Store a Secret

```bash
az keyvault secret set \
  --vault-name dev-keyvault-123456 \
  --name DatabasePassword \
  --value "<SECRET_VALUE>"
```

### 🔍 Retrieve a Secret

```bash
az keyvault secret show \
  --vault-name dev-keyvault-123456 \
  --name DatabasePassword
```

### 📋 List Secrets

```bash
az keyvault secret list \
  --vault-name dev-keyvault-123456 \
  --output table
```

### 🗑️ Delete a Secret

```bash
az keyvault secret delete \
  --vault-name dev-keyvault-123456 \
  --name DatabasePassword
```

> Key Vault access depends on its configured permission model and the signed-in identity's permissions. Avoid printing secret values in shared terminals or CI/CD logs.

---

## 📊 22. Azure Monitor Commands

Azure Monitor provides metrics, logs, alerts, and monitoring capabilities.

### 📋 List Activity Logs

```bash
az monitor activity-log list \
  --output table
```

### 📊 List Metric Definitions

```bash
az monitor metrics list-definitions \
  --resource <RESOURCE_ID> \
  --output table
```

### 🔍 Get Resource Metrics

```bash
az monitor metrics list \
  --resource <RESOURCE_ID> \
  --metric "Percentage CPU" \
  --interval PT5M
```

### 🚨 List Metric Alerts

```bash
az monitor metrics alert list \
  --resource-group dev-resource-group \
  --output table
```

### 📋 List Action Groups

```bash
az monitor action-group list \
  --resource-group dev-resource-group \
  --output table
```

---

## 🧩 23. Azure CLI Extensions

Extensions add additional commands and capabilities to Azure CLI.

### 📋 List Installed Extensions

```bash
az extension list --output table
```

### 📥 Install an Extension

```bash
az extension add --name <EXTENSION_NAME>
```

### 🔄 Update Extensions

```bash
az extension update --name <EXTENSION_NAME>
```

### 🔄 Update All Extensions

```bash
az extension update --all
```

### 🗑️ Remove an Extension

```bash
az extension remove --name <EXTENSION_NAME>
```

---

## 📄 24. Azure CLI Output and Query Options

Azure CLI supports multiple output formats and JMESPath queries.

### 📊 JSON Output

```bash
az vm list --output json
```

### 📋 Table Output

```bash
az vm list --output table
```

### 📝 TSV Output

```bash
az vm list --output tsv
```

### 📄 YAML Output

```bash
az vm list --output yaml
```

### 🔍 Filter Using Query

```bash
az vm list \
  --query "[].{Name:name,Location:location,Size:hardwareProfile.vmSize}" \
  --output table
```

### 📦 Save Output to File

```bash
az vm list --output json > virtual-machines.json
```

### 🔎 Get Only Resource Names

```bash
az resource list \
  --query "[].name" \
  --output tsv
```

---

## 🔧 25. Useful Azure CLI Commands

### 📌 General Commands

```bash
# Display Azure CLI version
az version

# Display general help
az help

# Display account information
az account show

# Display current configuration
az config get

# Search Azure CLI command documentation
az find "az vm create"

# Display command-specific help
az vm create --help
```

### 🔍 Resource Management

```bash
# List all resources
az resource list --output table

# List resources in a resource group
az resource list \
  --resource-group dev-resource-group \
  --output table

# Get a resource by ID
az resource show --ids <RESOURCE_ID>

# Delete a resource by ID
az resource delete --ids <RESOURCE_ID>
```

### ⚙️ Set Default Configuration

```bash
# Set default location
az config set defaults.location=centralindia

# Set default resource group
az config set defaults.group=dev-resource-group

# View current configuration
az config get
```

### 🔄 Remove Default Configuration

```bash
az config unset defaults.location
az config unset defaults.group
```

---

## 🧹 26. Uninstall Azure CLI

### 🐧 Ubuntu

```bash
sudo apt remove -y azure-cli

sudo rm -f /etc/apt/sources.list.d/azure-cli.sources

sudo rm -f /etc/apt/keyrings/microsoft.gpg

sudo apt autoremove -y
```

### 🐧 RHEL

```bash
sudo dnf remove -y azure-cli
```

Remove the Microsoft repository configuration if it is no longer required:

```bash
sudo rm -f /etc/yum.repos.d/azure-cli.repo
```

### 🪟 Windows

```text
Settings → Apps → Installed Apps → Azure CLI → Uninstall
```

### 🍎 macOS

```bash
brew uninstall azure-cli
```

### 🐧 Amazon Linux 2 / Amazon Linux 2023

If you used Docker, remove the Azure CLI image:

```bash
sudo docker rmi mcr.microsoft.com/azure-cli:latest
```

### 🗑️ Remove Local Azure CLI Configuration

Linux / macOS:

```bash
rm -rf ~/.azure
```

Windows PowerShell:

```powershell
Remove-Item -Recurse -Force "$HOME\.azure"
```

> Removing the local configuration directory deletes cached login and CLI settings. It does not delete your Azure cloud resources.

---

## 🛡️ 27. Security Best Practices

- Use Microsoft Entra ID authentication.
- Prefer Managed Identity for Azure-hosted workloads.
- Use workload identity federation for supported CI/CD platforms.
- Apply least-privilege RBAC permissions.
- Avoid storing credentials in source code.
- Never upload Azure credentials or secret files to GitHub.
- Use Azure Key Vault to manage application secrets.
- Verify the active subscription before creating or deleting resources.
- Use resource tags to organize environments and costs.
- Review resource permissions and activity logs regularly.

### 🚫 Recommended .gitignore Entries

```gitignore
# Azure CLI configuration
.azure/

# Environment variables
.env
.env.*

# Terraform state
*.tfstate
*.tfstate.*
```

---

## 📚 28. Official Documentation

- [Azure CLI Documentation](https://learn.microsoft.com/en-us/cli/azure/)
- [Azure CLI Installation](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
- [Azure CLI Command Reference](https://learn.microsoft.com/en-us/cli/azure/reference-index)
- [Azure CLI Authentication](https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli)
- [Azure Account Commands](https://learn.microsoft.com/en-us/cli/azure/account)
- [Azure Resource Groups](https://learn.microsoft.com/en-us/cli/azure/group)
- [Azure Virtual Machines](https://learn.microsoft.com/en-us/cli/azure/vm)
- [Azure Networking](https://learn.microsoft.com/en-us/cli/azure/network)
- [Azure Storage](https://learn.microsoft.com/en-us/cli/azure/storage)
- [Azure App Service](https://learn.microsoft.com/en-us/cli/azure/webapp)
- [Azure Container Registry](https://learn.microsoft.com/en-us/cli/azure/acr)
- [Azure Kubernetes Service](https://learn.microsoft.com/en-us/cli/azure/aks)
- [Azure Key Vault](https://learn.microsoft.com/en-us/cli/azure/keyvault)
- [Azure Monitor](https://learn.microsoft.com/en-us/cli/azure/monitor)

---

**🚀 Learn • Configure • Automate • Manage**