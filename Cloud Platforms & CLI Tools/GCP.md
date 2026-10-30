# ☁️ Google Cloud CLI (GCP) – Installation & Commands Guide

A practical guide to installing, configuring, and managing **Google Cloud CLI** across different operating systems. This README covers authentication, projects, IAM, Compute Engine, Cloud Storage, VPC networking, Cloud SQL, Cloud Run, GKE, Artifact Registry, BigQuery, and Cloud Monitoring. ⚙️🚀

---

## 📌 1. Introduction

Google Cloud CLI is a command-line tool that allows users to interact with Google Cloud Platform services directly from a terminal.

- **Tool:** Google Cloud CLI
- **Developer:** Google
- **Primary Command:** `gcloud`
- **Additional Tools:** `gsutil`, `bq`, `kubectl`
- **Configuration:** JSON
- **Authentication:** Google Account, Service Account, Workload Identity Federation
- **Primary Purpose:** Cloud Resource Management and Automation

## 🧩 2. Google Cloud CLI Components

| Component | Description |
|---|---|
| gcloud | Main command-line tool for Google Cloud |
| gsutil | Legacy command-line tool for Cloud Storage |
| gcloud storage | Modern commands for Cloud Storage |
| bq | Command-line tool for BigQuery |
| kubectl | Command-line tool for Kubernetes |
| gke-gcloud-auth-plugin | Authentication plugin for GKE |
| gcloud components | Additional CLI tools and extensions |

## 💻 3. Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | Official interactive installer |
| Amazon Linux 2023 | Official interactive installer |
| Ubuntu | APT repository |
| RHEL | RPM repository / archive installer |
| Windows | PowerShell / Installer |
| macOS | Homebrew / Official installer |

---

## 🐧 4. Install Google Cloud CLI on Amazon Linux 2

Use Google's official interactive installer for a standalone Linux installation.

### 🔄 Step 1: Update System

```bash
sudo yum update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo yum install -y curl tar gzip
```

### 📥 Step 3: Download and Run Installer

```bash
curl https://sdk.cloud.google.com | bash
```

Follow the installation prompts.

When prompted, allow the installer to update your PATH and enable shell completion.

### 🔄 Step 4: Reload Shell

```bash
exec -l $SHELL
```

### ⚙️ Step 5: Initialize Google Cloud CLI

```bash
gcloud init
```

### 🔍 Step 6: Verify Installation

```bash
gcloud version
```

---

## 🐧 5. Install Google Cloud CLI on Amazon Linux 2023

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo dnf install -y curl tar gzip
```

### 📥 Step 3: Download and Run Installer

```bash
curl https://sdk.cloud.google.com | bash
```

### 🔄 Step 4: Reload Shell

```bash
exec -l $SHELL
```

### ⚙️ Step 5: Initialize Google Cloud CLI

```bash
gcloud init
```

### 🔍 Step 6: Verify Installation

```bash
gcloud version
```

---

## 🐧 6. Install Google Cloud CLI on Ubuntu

Google provides an official APT repository for Debian and Ubuntu systems.

### 🔄 Step 1: Update System

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates gnupg curl
```

### 🔑 Step 2: Import Google Cloud Signing Key

```bash
sudo mkdir -p /usr/share/keyrings

curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | \
  sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg

sudo chmod 644 /usr/share/keyrings/cloud.google.gpg
```

### 📦 Step 3: Add Google Cloud Repository

```bash
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | \
  sudo tee /etc/apt/sources.list.d/google-cloud-sdk.list
```

### 📥 Step 4: Install Google Cloud CLI

```bash
sudo apt-get update

sudo apt-get install -y google-cloud-cli
```

### 🔍 Step 5: Verify Installation

```bash
gcloud version
```

---

## 🐧 7. Install Google Cloud CLI on RHEL

Google provides an RPM repository for supported RHEL versions.

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🔑 Step 2: Import Google Cloud Signing Key

For RHEL 8 and RHEL 9:

```bash
sudo rpm --import https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
```

For RHEL 10, use Google's current signing key instructions in the official documentation.

### 📦 Step 3: Add Google Cloud Repository

For RHEL 8:

```bash
sudo tee /etc/yum.repos.d/google-cloud-sdk.repo << 'EOF'
[google-cloud-cli]
name=Google Cloud CLI
baseurl=https://packages.cloud.google.com/yum/repos/cloud-sdk-el8-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=0
gpgkey=https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
```

For RHEL 9:

```bash
sudo tee /etc/yum.repos.d/google-cloud-sdk.repo << 'EOF'
[google-cloud-cli]
name=Google Cloud CLI
baseurl=https://packages.cloud.google.com/yum/repos/cloud-sdk-el9-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=0
gpgkey=https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
```

### 🛠️ Step 4: Install Required Dependency

```bash
sudo dnf install -y libxcrypt-compat.x86_64
```

### 📥 Step 5: Install Google Cloud CLI

```bash
sudo dnf install -y google-cloud-cli
```

### 🔍 Step 6: Verify Installation

```bash
gcloud version
```

> For ARM64 or other RHEL releases, use the matching repository instructions from Google's official documentation rather than reusing the x86_64 repository URL.

---

## 🪟 8. Install Google Cloud CLI on Windows

### 📦 Method 1: Using PowerShell

Open PowerShell:

```powershell
(New-Object Net.WebClient).DownloadFile(
  "https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe",
  "$env:Temp\GoogleCloudSDKInstaller.exe"
)

& "$env:Temp\GoogleCloudSDKInstaller.exe"
```

Follow the installation wizard.

### 📦 Method 2: Download Installer Manually

Download the official installer:

[Google Cloud CLI Windows Installer](https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe)

### 🔍 Verify Installation

Open a new PowerShell terminal:

```powershell
gcloud version
```

### ⚙️ Initialize Google Cloud CLI

```powershell
gcloud init
```

---

## 🍎 9. Install Google Cloud CLI on macOS

### 📦 Method 1: Using Homebrew

```bash
brew update

brew install --cask gcloud-cli
```

### 📦 Method 2: Using Official Installer

```bash
curl https://sdk.cloud.google.com | bash
```

Follow the installation prompts.

### 🔄 Reload Shell

```bash
exec -l $SHELL
```

### 🔍 Verify Installation

```bash
gcloud version
```

---

## 🔄 10. Update Google Cloud CLI

### 📦 Standalone Installer Installation

```bash
gcloud components update
```

### 🐧 Ubuntu

```bash
sudo apt-get update

sudo apt-get install --only-upgrade -y google-cloud-cli
```

### 🐧 RHEL

```bash
sudo dnf update -y google-cloud-cli
```

### 🪟 Windows

Download and run the latest official installer:

[Google Cloud CLI Installer](https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe)

### 🍎 macOS – Homebrew

```bash
brew update

brew upgrade --cask gcloud-cli
```

### 🔍 Verify Updated Version

```bash
gcloud version
```

> The `gcloud components update` command is for standalone installations. When installed through APT, DNF, or Homebrew, use the respective package manager for updates.

---

## 🔐 11. Google Cloud CLI Authentication

Authentication allows Google Cloud CLI to access your Google Cloud resources.

### 🌐 Login to Google Account

```bash
gcloud auth login
```

This opens a browser for Google Account authentication.

### ⚙️ Initialize Google Cloud CLI

```bash
gcloud init
```

This helps configure:

- Google Account
- Google Cloud Project
- Default Compute Region
- Default Compute Zone

### 🔑 Configure Application Default Credentials

```bash
gcloud auth application-default login
```

Application Default Credentials (ADC) are used by Google Cloud client libraries and applications.

### 👤 Check Authenticated Accounts

```bash
gcloud auth list
```

### 🔍 Display Current Account

```bash
gcloud config get-value account
```

### 🚪 Logout

```bash
gcloud auth revoke
```

---

## 👤 12. Service Account Authentication

A Service Account is an identity used by applications and automated workloads to access Google Cloud resources.

### 📋 List Service Accounts

```bash
gcloud iam service-accounts list
```

### 🏗️ Create Service Account

```bash
gcloud iam service-accounts create cicd-service-account \
  --display-name="CI/CD Service Account"
```

### 🔍 Get Service Account Details

```bash
gcloud iam service-accounts describe \
  cicd-service-account@<PROJECT_ID>.iam.gserviceaccount.com
```

### 🔐 Grant IAM Role

```bash
gcloud projects add-iam-policy-binding <PROJECT_ID> \
  --member="serviceAccount:cicd-service-account@<PROJECT_ID>.iam.gserviceaccount.com" \
  --role="roles/viewer"
```

### 🔑 Authenticate Using Service Account Key

For environments where key-based authentication is specifically required:

```bash
gcloud auth activate-service-account \
  --key-file=service-account-key.json
```

### 🔍 Verify Authentication

```bash
gcloud auth list
```

> Prefer Workload Identity Federation or attached service accounts over downloading long-lived JSON keys. Never commit service account key files to GitHub.

---

## 📁 13. Google Cloud Project Management

A Google Cloud Project is the primary container for organizing resources, APIs, billing, and permissions.

### 📋 List Projects

```bash
gcloud projects list
```

### 🏗️ Create Project

Project IDs must be globally unique.

```bash
gcloud projects create my-gcp-project-123456
```

### 🔍 Get Project Details

```bash
gcloud projects describe my-gcp-project-123456
```

### 🔄 Set Default Project

```bash
gcloud config set project my-gcp-project-123456
```

### 📊 Display Current Project

```bash
gcloud config get-value project
```

### 🗑️ Delete Project

```bash
gcloud projects delete my-gcp-project-123456
```

> Project deletion can affect every resource inside the project. Verify the project ID before executing this command.

---

## ⚙️ 14. Google Cloud Configuration Management

Google Cloud CLI uses named configurations to manage multiple environments and projects.

### 📋 List Configurations

```bash
gcloud config configurations list
```

### 🏗️ Create Configuration

```bash
gcloud config configurations create development
```

### 🔄 Activate Configuration

```bash
gcloud config configurations activate development
```

### ⚙️ Set Project

```bash
gcloud config set project my-gcp-project-123456
```

### 🌍 Set Default Compute Region

```bash
gcloud config set compute/region asia-south1
```

### 📍 Set Default Compute Zone

```bash
gcloud config set compute/zone asia-south1-a
```

### 🔍 Display Current Configuration

```bash
gcloud config list
```

### 🗑️ Delete Configuration

```bash
gcloud config configurations delete development
```

---

## 🌍 15. Google Cloud Region and Zone Commands

### 📋 List Compute Regions

```bash
gcloud compute regions list
```

### 📋 List Compute Zones

```bash
gcloud compute zones list
```

### 🔍 Get Current Region

```bash
gcloud config get-value compute/region
```

### 🔍 Get Current Zone

```bash
gcloud config get-value compute/zone
```

### 🔄 Set Region

```bash
gcloud config set compute/region asia-south1
```

### 🔄 Set Zone

```bash
gcloud config set compute/zone asia-south1-a
```

---

## 🖥️ 16. Google Compute Engine Commands

Compute Engine provides virtual machines running on Google Cloud infrastructure.

### 📋 List VM Instances

```bash
gcloud compute instances list
```

### 🏗️ Create Linux VM

```bash
gcloud compute instances create dev-linux-vm \
  --zone=asia-south1-a \
  --machine-type=e2-micro \
  --image-family=debian-12 \
  --image-project=debian-cloud
```

### 🔍 Get VM Details

```bash
gcloud compute instances describe dev-linux-vm \
  --zone=asia-south1-a
```

### ▶️ Start VM

```bash
gcloud compute instances start dev-linux-vm \
  --zone=asia-south1-a
```

### ⏹️ Stop VM

```bash
gcloud compute instances stop dev-linux-vm \
  --zone=asia-south1-a
```

### 🔄 Restart VM

```bash
gcloud compute instances reset dev-linux-vm \
  --zone=asia-south1-a
```

### 🔑 Connect to Linux VM Using SSH

```bash
gcloud compute ssh dev-linux-vm \
  --zone=asia-south1-a
```

### 🌐 Get VM External IP

```bash
gcloud compute instances list \
  --format="table(name,zone,networkInterfaces[0].accessConfigs[0].natIP)"
```

### 🗑️ Delete VM

```bash
gcloud compute instances delete dev-linux-vm \
  --zone=asia-south1-a
```

---

## 🪣 17. Google Cloud Storage Commands

Google Cloud Storage provides object storage for files, backups, logs, and application data.

### 📋 List Storage Buckets

```bash
gcloud storage buckets list
```

### 🏗️ Create Storage Bucket

Bucket names must be globally unique.

```bash
gcloud storage buckets create gs://my-gcp-bucket-123456 \
  --location=asia-south1
```

### 🔍 Get Bucket Details

```bash
gcloud storage buckets describe gs://my-gcp-bucket-123456
```

### 📤 Upload File

```bash
gcloud storage cp file.txt gs://my-gcp-bucket-123456/
```

### 📥 Download File

```bash
gcloud storage cp gs://my-gcp-bucket-123456/file.txt .
```

### 📋 List Bucket Objects

```bash
gcloud storage ls gs://my-gcp-bucket-123456/
```

### 🔄 Synchronize Directory

```bash
gcloud storage rsync ./local-folder gs://my-gcp-bucket-123456/ \
  --recursive
```

### 🗑️ Delete Object

```bash
gcloud storage rm gs://my-gcp-bucket-123456/file.txt
```

### 🧹 Delete Bucket Contents

```bash
gcloud storage rm gs://my-gcp-bucket-123456/** \
  --recursive
```

### 🗑️ Delete Bucket

```bash
gcloud storage buckets delete gs://my-gcp-bucket-123456
```

---

## 🌐 18. Google Cloud VPC Networking Commands

Google Cloud VPC provides networking infrastructure for cloud resources.

### 📋 List VPC Networks

```bash
gcloud compute networks list
```

### 🏗️ Create VPC Network

```bash
gcloud compute networks create dev-vpc \
  --subnet-mode=custom
```

### 🔍 Get VPC Details

```bash
gcloud compute networks describe dev-vpc
```

### 🏗️ Create Subnet

```bash
gcloud compute networks subnets create public-subnet \
  --network=dev-vpc \
  --region=asia-south1 \
  --range=10.0.1.0/24
```

### 📋 List Subnets

```bash
gcloud compute networks subnets list
```

### 🔍 Describe Subnet

```bash
gcloud compute networks subnets describe public-subnet \
  --region=asia-south1
```

### 📋 List Firewall Rules

```bash
gcloud compute firewall-rules list
```

### 🔐 Create Firewall Rule

Allow SSH from a trusted source IP range:

```bash
gcloud compute firewall-rules create allow-ssh \
  --network=dev-vpc \
  --allow=tcp:22 \
  --source-ranges=<TRUSTED_SOURCE_CIDR>
```

### 📋 List Routes

```bash
gcloud compute routes list
```

### 📋 List External IP Addresses

```bash
gcloud compute addresses list
```

### 🗑️ Delete Firewall Rule

```bash
gcloud compute firewall-rules delete allow-ssh
```

---

## 🗄️ 19. Google Cloud SQL Commands

Cloud SQL is a managed relational database service supporting MySQL, PostgreSQL, and SQL Server.

### 📋 List Cloud SQL Instances

```bash
gcloud sql instances list
```

### 🏗️ Create MySQL Instance

```bash
gcloud sql instances create dev-mysql-db \
  --database-version=MYSQL_8_0 \
  --tier=db-f1-micro \
  --region=asia-south1
```

> Machine tiers and database versions depend on regional availability and current service support.

### 🔍 Get Instance Details

```bash
gcloud sql instances describe dev-mysql-db
```

### ▶️ Start / Activate Instance

```bash
gcloud sql instances patch dev-mysql-db \
  --activation-policy=ALWAYS
```

### ⏹️ Stop Instance

```bash
gcloud sql instances patch dev-mysql-db \
  --activation-policy=NEVER
```

### 📋 List Databases

```bash
gcloud sql databases list \
  --instance=dev-mysql-db
```

### 🏗️ Create Database

```bash
gcloud sql databases create appdb \
  --instance=dev-mysql-db
```

### 📋 List Database Users

```bash
gcloud sql users list \
  --instance=dev-mysql-db
```

### 🗑️ Delete Database Instance

```bash
gcloud sql instances delete dev-mysql-db
```

---

## 🐳 20. Google Artifact Registry Commands

Artifact Registry stores and manages Docker images and other build artifacts.

### 📋 List Repositories

```bash
gcloud artifacts repositories list \
  --location=asia-south1
```

### 🏗️ Create Docker Repository

```bash
gcloud artifacts repositories create docker-repo \
  --repository-format=docker \
  --location=asia-south1 \
  --description="Docker repository for applications"
```

### 🔐 Configure Docker Authentication

```bash
gcloud auth configure-docker asia-south1-docker.pkg.dev
```

### 📦 Tag Docker Image

```bash
docker tag myapp:latest \
  asia-south1-docker.pkg.dev/<PROJECT_ID>/docker-repo/myapp:v1
```

### 📤 Push Docker Image

```bash
docker push \
  asia-south1-docker.pkg.dev/<PROJECT_ID>/docker-repo/myapp:v1
```

### 📋 List Docker Images

```bash
gcloud artifacts docker images list \
  asia-south1-docker.pkg.dev/<PROJECT_ID>/docker-repo
```

### 🗑️ Delete Repository

```bash
gcloud artifacts repositories delete docker-repo \
  --location=asia-south1
```

---

## 🚀 21. Google Cloud Run Commands

Cloud Run is a managed platform for deploying containerized applications.

### 📋 List Cloud Run Services

```bash
gcloud run services list \
  --region=asia-south1
```

### 🚀 Deploy Container Image

```bash
gcloud run deploy my-web-service \
  --image=nginx \
  --region=asia-south1 \
  --allow-unauthenticated
```

### 🔍 Get Service Details

```bash
gcloud run services describe my-web-service \
  --region=asia-south1
```

### 📋 Get Service URL

```bash
gcloud run services describe my-web-service \
  --region=asia-south1 \
  --format="value(status.url)"
```

### 📜 View Cloud Run Logs

```bash
gcloud run services logs read my-web-service \
  --region=asia-south1
```

### 🗑️ Delete Cloud Run Service

```bash
gcloud run services delete my-web-service \
  --region=asia-south1
```

---

## ☸️ 22. Google Kubernetes Engine Commands

Google Kubernetes Engine (GKE) is a managed Kubernetes service.

### 📋 List GKE Clusters

```bash
gcloud container clusters list
```

### 🏗️ Create GKE Cluster

```bash
gcloud container clusters create dev-gke-cluster \
  --zone=asia-south1-a \
  --num-nodes=1
```

### 🔑 Get Cluster Credentials

```bash
gcloud container clusters get-credentials dev-gke-cluster \
  --zone=asia-south1-a
```

### 📋 Check Kubernetes Nodes

```bash
kubectl get nodes
```

### 📋 Check Pods

```bash
kubectl get pods --all-namespaces
```

### 🔍 Describe Cluster

```bash
gcloud container clusters describe dev-gke-cluster \
  --zone=asia-south1-a
```

### 🔄 Resize Cluster

```bash
gcloud container clusters resize dev-gke-cluster \
  --zone=asia-south1-a \
  --num-nodes=2
```

### 🗑️ Delete Cluster

```bash
gcloud container clusters delete dev-gke-cluster \
  --zone=asia-south1-a
```

> `kubectl` must be installed and authenticated for Kubernetes commands. Install the `gke-gcloud-auth-plugin` if required by your GKE environment.

---

## 🔐 23. Google Cloud IAM Commands

Identity and Access Management controls access to Google Cloud resources.

### 📋 Get Project IAM Policy

```bash
gcloud projects get-iam-policy <PROJECT_ID>
```

### 🔐 Grant Project Role to User

```bash
gcloud projects add-iam-policy-binding <PROJECT_ID> \
  --member="user:USER_EMAIL" \
  --role="roles/viewer"
```

### 🔍 List IAM Roles

```bash
gcloud iam roles list
```

### 📋 List Service Accounts

```bash
gcloud iam service-accounts list
```

### 🔐 Grant Role to Service Account

```bash
gcloud projects add-iam-policy-binding <PROJECT_ID> \
  --member="serviceAccount:SERVICE_ACCOUNT_EMAIL" \
  --role="roles/storage.objectViewer"
```

### 🚫 Remove IAM Role Binding

```bash
gcloud projects remove-iam-policy-binding <PROJECT_ID> \
  --member="user:USER_EMAIL" \
  --role="roles/viewer"
```

---

## 📊 24. Google Cloud Monitoring and Logging Commands

Google Cloud Operations provides monitoring, logging, alerting, and observability.

### 📋 List Log Entries

```bash
gcloud logging read "resource.type=gce_instance" \
  --limit=10
```

### 🔍 Read Logs from a Specific VM

```bash
gcloud logging read \
  "resource.type=gce_instance AND resource.labels.instance_id=<INSTANCE_ID>" \
  --limit=20
```

### 📋 List Log Sinks

```bash
gcloud logging sinks list
```

### 📋 List Monitoring Policies

```bash
gcloud monitoring policies list
```

### 📋 List Notification Channels

```bash
gcloud monitoring channels list
```

### 🔍 View Logging Help

```bash
gcloud logging --help
```

---

## 📊 25. BigQuery CLI Commands

BigQuery is a serverless data warehouse for large-scale analytics.

The `bq` command-line tool is included with the standard Google Cloud CLI installation.

### 📋 List Datasets

```bash
bq ls
```

### 🏗️ Create Dataset

```bash
bq mk --dataset my-gcp-project-123456:analytics
```

### 📋 List Tables

```bash
bq ls analytics
```

### 🔍 Show Table Details

```bash
bq show analytics.customers
```

### 🚀 Execute SQL Query

```bash
bq query --use_legacy_sql=false \
  'SELECT * FROM `my-gcp-project-123456.analytics.customers` LIMIT 10'
```

### 🗑️ Delete Dataset

```bash
bq rm -r -f my-gcp-project-123456:analytics
```

---

## 🧩 26. Google Cloud CLI Components

Components add additional command-line tools and functionality.

### 📋 List Installed Components

```bash
gcloud components list
```

### 📥 Install kubectl

```bash
gcloud components install kubectl
```

### 📥 Install App Engine Components

```bash
gcloud components install app-engine-python
```

### 🔄 Update Components

```bash
gcloud components update
```

### 🗑️ Remove Component

```bash
gcloud components remove kubectl
```

> The component manager is available with standalone installations. It is disabled for package-manager installations such as APT and DNF. Use the relevant package manager or official standalone installer instructions for those installations.

---

## 📄 27. Output and Query Options

Google Cloud CLI supports JSON, YAML, table, and other output formats.

### 📊 JSON Output

```bash
gcloud compute instances list --format=json
```

### 📋 Table Output

```bash
gcloud compute instances list --format=table
```

### 📝 CSV Output

```bash
gcloud compute instances list --format=csv
```

### 🔍 Filter Using Query

```bash
gcloud compute instances list \
  --filter="status=RUNNING"
```

### 📦 Select Specific Fields

```bash
gcloud compute instances list \
  --format="table(name,zone,status)"
```

### 💾 Save Output to File

```bash
gcloud compute instances list --format=json > instances.json
```

---

## 🔧 28. Useful Google Cloud CLI Commands

### 📌 General Commands

```bash
# Display CLI version
gcloud version

# Display CLI information
gcloud info

# Display general help
gcloud help

# Display command-specific help
gcloud compute instances create --help

# Initialize Google Cloud CLI
gcloud init

# Display current configuration
gcloud config list
```

### 🔍 Authentication Commands

```bash
# List authenticated accounts
gcloud auth list

# Login to Google Cloud
gcloud auth login

# Configure application default credentials
gcloud auth application-default login

# Revoke current account credentials
gcloud auth revoke
```

### 📦 Project Commands

```bash
# List projects
gcloud projects list

# Display active project
gcloud config get-value project

# Set active project
gcloud config set project <PROJECT_ID>
```

---

## 🧹 29. Uninstall Google Cloud CLI

### 🐧 Ubuntu

```bash
sudo apt-get remove -y google-cloud-cli

sudo rm -f /etc/apt/sources.list.d/google-cloud-sdk.list

sudo rm -f /usr/share/keyrings/cloud.google.gpg

sudo apt-get autoremove -y
```

### 🐧 RHEL

```bash
sudo dnf remove -y google-cloud-cli

sudo rm -f /etc/yum.repos.d/google-cloud-sdk.repo
```

### 🐧 Amazon Linux 2 / Amazon Linux 2023

For the standalone installation, the SDK is generally installed inside:

```text
~/google-cloud-sdk
```

Remove the installation directory:

```bash
rm -rf ~/google-cloud-sdk
```

Remove the Google Cloud CLI PATH and completion entries from your shell configuration file, such as `.bashrc` or `.bash_profile`.

### 🪟 Windows

Uninstall through:

```text
Settings → Apps → Installed Apps → Google Cloud CLI → Uninstall
```

### 🍎 macOS – Homebrew

```bash
brew uninstall --cask gcloud-cli
```

### 🍎 macOS – Standalone Installation

```bash
rm -rf ~/google-cloud-sdk
```

Remove its PATH and completion entries from your shell configuration file.

### 🗑️ Remove Local Configuration

Linux / macOS:

```bash
rm -rf ~/.config/gcloud
```

Windows PowerShell:

```powershell
Remove-Item -Recurse -Force "$env:APPDATA\gcloud"
```

> Removing local configuration deletes cached authentication and CLI settings. It does not delete your Google Cloud projects or cloud resources.

---

## 🛡️ 30. Security Best Practices

- Prefer Workload Identity Federation for CI/CD authentication.
- Use attached service accounts for Google Cloud workloads.
- Avoid long-lived service account JSON keys.
- Never commit credentials or key files to GitHub.
- Apply least-privilege IAM roles.
- Enable required APIs only.
- Verify the active project before performing critical operations.
- Use separate configurations for development and production.
- Monitor resource activity through Cloud Logging and Cloud Monitoring.
- Review billing and resource usage regularly.

### 🚫 Recommended .gitignore Entries

```gitignore
# Google Cloud configuration
.config/gcloud/

# Service account credentials
service-account*.json
*-key.json

# Environment variables
.env
.env.*

# Terraform state
*.tfstate
*.tfstate.*
```

---

## 📚 31. Official Documentation

- [Google Cloud CLI Documentation](https://cloud.google.com/cli)
- [Google Cloud CLI Installation](https://docs.cloud.google.com/sdk/docs/install-sdk)
- [Google Cloud CLI Initialization](https://docs.cloud.google.com/sdk/docs/initializing)
- [Google Cloud CLI Authentication](https://cloud.google.com/docs/authentication)
- [Google Cloud CLI Command Reference](https://cloud.google.com/sdk/gcloud/reference)
- [Google Cloud IAM](https://cloud.google.com/iam/docs)
- [Compute Engine](https://cloud.google.com/compute/docs)
- [Cloud Storage](https://cloud.google.com/storage/docs)
- [VPC Networking](https://cloud.google.com/vpc/docs)
- [Cloud SQL](https://cloud.google.com/sql/docs)
- [Cloud Run](https://cloud.google.com/run/docs)
- [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/docs)
- [Artifact Registry](https://cloud.google.com/artifact-registry/docs)
- [BigQuery](https://cloud.google.com/bigquery/docs)
- [Cloud Monitoring](https://cloud.google.com/monitoring/docs)
- [Cloud Logging](https://cloud.google.com/logging/docs)

---

**🚀 Learn • Configure • Automate • Manage**