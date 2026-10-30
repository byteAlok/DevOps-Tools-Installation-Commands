# ☁️ AWS CLI – Installation & Commands Guide

A practical guide to installing, configuring, and managing **AWS Command Line Interface (AWS CLI)** across different operating systems. This README covers installation, authentication, profiles, IAM, EC2, S3, VPC, RDS, Lambda, CloudWatch, and commonly used AWS CLI commands. ⚙️🚀

---

## 📌 1. Introduction

AWS CLI is a command-line tool that allows users to interact with Amazon Web Services directly from a terminal.

- **Tool:** AWS Command Line Interface
- **Developer:** Amazon Web Services
- **Major Version:** AWS CLI v2
- **Configuration:** JSON / INI
- **Authentication:** IAM credentials, IAM Roles, IAM Identity Center
- **Primary Purpose:** AWS Resource Management and Automation

## 🧩 2. AWS CLI Components

| Component | Description |
|---|---|
| AWS CLI | Command-line interface for AWS services |
| AWS Profiles | Store multiple CLI configurations |
| Credentials File | Stores configured access credentials |
| Config File | Stores region, output format, and profile settings |
| IAM | Identity and Access Management |
| AWS STS | Provides temporary security credentials |
| AWS CloudShell | Browser-based shell with AWS CLI access |

## 💻 3. Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | Official AWS installer |
| Amazon Linux 2023 | Official AWS installer |
| Ubuntu | Official AWS installer |
| RHEL | Official AWS installer |
| Windows | PowerShell / MSI |
| macOS | Official installer / Homebrew |

---

## 🐧 4. Install AWS CLI on Amazon Linux 2

### 🔄 Step 1: Update System

```bash
sudo yum update -y
```

### 🗑️ Step 2: Remove Pre-installed AWS CLI

Amazon Linux 2 may include an older AWS CLI v1 package. Remove it before installing AWS CLI v2.

```bash
sudo yum remove awscli -y
```

### 🛠️ Step 3: Install Required Packages

```bash
sudo yum install -y curl unzip
```

### 📥 Step 4: Download AWS CLI v2 Installer

For AMD64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

For ARM64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
```

### 📦 Step 5: Extract Installer

```bash
unzip awscliv2.zip
```

### ⚙️ Step 6: Install AWS CLI

```bash
sudo ./aws/install
```

### 🔍 Step 7: Verify Installation

```bash
aws --version
```

---

## 🐧 5. Install AWS CLI on Amazon Linux 2023

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo dnf install -y curl unzip
```

### 📥 Step 3: Download AWS CLI v2 Installer

For AMD64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

For ARM64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
```

### 📦 Step 4: Extract Installer

```bash
unzip awscliv2.zip
```

### ⚙️ Step 5: Install AWS CLI

```bash
sudo ./aws/install
```

### 🔍 Step 6: Verify Installation

```bash
aws --version
```

---

## 🐧 6. Install AWS CLI on Ubuntu

### 🔄 Step 1: Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo apt install -y curl unzip
```

### 📥 Step 3: Download AWS CLI v2 Installer

For AMD64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

For ARM64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
```

### 📦 Step 4: Extract Installer

```bash
unzip awscliv2.zip
```

### ⚙️ Step 5: Install AWS CLI

```bash
sudo ./aws/install
```

### 🔍 Step 6: Verify Installation

```bash
aws --version
```

---

## 🐧 7. Install AWS CLI on RHEL

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo dnf install -y curl unzip
```

### 📥 Step 3: Download AWS CLI v2 Installer

For AMD64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

For ARM64:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
```

### 📦 Step 4: Extract Installer

```bash
unzip awscliv2.zip
```

### ⚙️ Step 5: Install AWS CLI

```bash
sudo ./aws/install
```

### 🔍 Step 6: Verify Installation

```bash
aws --version
```

---

## 🪟 8. Install AWS CLI on Windows

### 📦 Method 1: Using PowerShell

Open PowerShell:

```powershell
irm https://awscli.amazonaws.com/v2/install.ps1 | iex
```

### 📦 Method 2: Using MSI Installer

Download the official AWS CLI v2 installer:

```text
https://awscli.amazonaws.com/AWSCLIV2.msi
```

Or execute the following command in PowerShell:

```powershell
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

### 🔍 Verify Installation

```powershell
aws --version
```

---

## 🍎 9. Install AWS CLI on macOS

### 📦 Method 1: Using Official AWS Installer

Download the installer:

```bash
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
```

Install AWS CLI:

```bash
sudo installer -pkg AWSCLIV2.pkg -target /
```

### 📦 Method 2: Using Homebrew

```bash
brew update
brew install awscli
```

### 🔍 Verify Installation

```bash
aws --version
```

---

## 🔄 10. Update AWS CLI

For installations using the official AWS CLI v2 installer:

### 🐧 Linux / 🍎 macOS

```bash
aws update
```

For system-wide installations:

```bash
sudo aws update
```

### 🪟 Windows PowerShell

Run PowerShell as Administrator:

```powershell
aws update
```

### 🔍 Verify Updated Version

```bash
aws --version
```

> `aws update` is supported by current AWS CLI v2 releases starting from version 2.36.0. For older installations, follow the official installer update procedure.

---

## 🔐 11. Configure AWS CLI Credentials

AWS CLI requires authentication to access AWS resources.

### ⚙️ Configure AWS CLI

```bash
aws configure
```

It prompts for:

```text
AWS Access Key ID:
AWS Secret Access Key:
Default region name:
Default output format:
```

Example:

```text
AWS Access Key ID: YOUR_ACCESS_KEY
AWS Secret Access Key: YOUR_SECRET_KEY
Default region name: us-east-1
Default output format: json
```

### 📁 AWS Configuration Files

AWS CLI stores configuration in two commonly used files.

**Credentials file:**

```text
~/.aws/credentials
```

**Config file:**

```text
~/.aws/config
```

### 📝 Example: credentials

```ini
[default]
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_KEY
```

### 📝 Example: config

```ini
[default]
region = us-east-1
output = json
```

### 🔍 Verify AWS Identity

```bash
aws sts get-caller-identity
```

This displays the AWS account ID, caller ARN, and user ID associated with the active credentials.

> On EC2 instances, prefer an IAM Instance Profile instead of storing long-term access keys on the server.

---

## 👤 12. AWS CLI Profile Management

Profiles allow you to configure multiple AWS accounts or environments.

### 📌 Create Profiles

```bash
aws configure --profile dev
```

```bash
aws configure --profile production
```

### 🔍 List Profiles

```bash
aws configure list-profiles
```

### 📊 Display Active Configuration

```bash
aws configure list
```

### 🔍 Display Specific Profile Configuration

```bash
aws configure list --profile dev
```

### ▶️ Use a Specific Profile

```bash
aws s3 ls --profile dev
```

### 🌍 Set Default Profile

Linux / macOS:

```bash
export AWS_PROFILE=dev
```

Windows PowerShell:

```powershell
$env:AWS_PROFILE="dev"
```

### 🔄 Remove a Profile

Edit the following files and remove the relevant profile section:

```text
~/.aws/credentials
~/.aws/config
```

---

## 🔑 13. AWS IAM Commands

IAM manages users, groups, roles, and permissions.

### 👤 User Management

```bash
# List IAM users
aws iam list-users

# Get current IAM user
aws iam get-user

# Create IAM user
aws iam create-user --user-name dev-user

# Delete IAM user
aws iam delete-user --user-name dev-user
```

### 👥 Group Management

```bash
# List groups
aws iam list-groups

# Create group
aws iam create-group --group-name developers

# Delete group
aws iam delete-group --group-name developers
```

### 🔐 Policy Management

```bash
# List policies
aws iam list-policies

# Get policy details
aws iam get-policy --policy-arn <POLICY_ARN>

# List attached user policies
aws iam list-attached-user-policies --user-name dev-user
```

### 🎭 Role Management

```bash
# List roles
aws iam list-roles

# Get role details
aws iam get-role --role-name EC2-S3-Role

# List attached role policies
aws iam list-attached-role-policies --role-name EC2-S3-Role
```

---

## 🖥️ 14. AWS EC2 Commands

EC2 provides scalable virtual servers in AWS.

### 📋 List EC2 Instances

```bash
aws ec2 describe-instances
```

### 🔍 List Instances with Selected Information

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].[InstanceId,State.Name,InstanceType,PublicIpAddress]" \
  --output table
```

### 🚀 Start EC2 Instance

```bash
aws ec2 start-instances --instance-ids <INSTANCE_ID>
```

### ⏹️ Stop EC2 Instance

```bash
aws ec2 stop-instances --instance-ids <INSTANCE_ID>
```

### 🔄 Reboot EC2 Instance

```bash
aws ec2 reboot-instances --instance-ids <INSTANCE_ID>
```

### 🗑️ Terminate EC2 Instance

```bash
aws ec2 terminate-instances --instance-ids <INSTANCE_ID>
```

### 📊 Check Instance Status

```bash
aws ec2 describe-instance-status --instance-ids <INSTANCE_ID>
```

### 📦 List AMIs

```bash
aws ec2 describe-images --owners self
```

### 🔑 List Key Pairs

```bash
aws ec2 describe-key-pairs
```

### 🔒 List Security Groups

```bash
aws ec2 describe-security-groups
```

---

## 🪣 15. AWS S3 Commands

Amazon S3 is an object storage service.

### 📋 List All Buckets

```bash
aws s3 ls
```

### 🪣 Create Bucket

For `us-east-1`:

```bash
aws s3 mb s3://my-dev-bucket-123456
```

For other regions:

```bash
aws s3api create-bucket \
  --bucket my-dev-bucket-123456 \
  --region ap-south-1 \
  --create-bucket-configuration LocationConstraint=ap-south-1
```

### 📁 List Bucket Objects

```bash
aws s3 ls s3://my-dev-bucket-123456
```

### 📤 Upload File

```bash
aws s3 cp file.txt s3://my-dev-bucket-123456/
```

### 📥 Download File

```bash
aws s3 cp s3://my-dev-bucket-123456/file.txt .
```

### 🔄 Synchronize Directory

```bash
aws s3 sync ./local-folder s3://my-dev-bucket-123456/
```

### 📊 Check Bucket Size and Object Count

```bash
aws s3 ls s3://my-dev-bucket-123456 --recursive --summarize
```

### 🗑️ Delete Object

```bash
aws s3 rm s3://my-dev-bucket-123456/file.txt
```

### 🧹 Delete Bucket Contents

```bash
aws s3 rm s3://my-dev-bucket-123456 --recursive
```

### 🗑️ Delete Bucket

```bash
aws s3 rb s3://my-dev-bucket-123456
```

---

## 🌐 16. AWS VPC Commands

Amazon VPC provides isolated virtual networking in AWS.

### 📋 List VPCs

```bash
aws ec2 describe-vpcs
```

### 🏗️ Create VPC

```bash
aws ec2 create-vpc \
  --cidr-block 10.0.0.0/16
```

### 🔍 List Subnets

```bash
aws ec2 describe-subnets
```

### 🏗️ Create Subnet

```bash
aws ec2 create-subnet \
  --vpc-id <VPC_ID> \
  --cidr-block 10.0.1.0/24
```

### 🌐 List Internet Gateways

```bash
aws ec2 describe-internet-gateways
```

### 🔍 List Route Tables

```bash
aws ec2 describe-route-tables
```

### 🔒 List Network ACLs

```bash
aws ec2 describe-network-acls
```

### 🛡️ List Security Groups

```bash
aws ec2 describe-security-groups
```

### 🔌 List Network Interfaces

```bash
aws ec2 describe-network-interfaces
```

---

## 🗄️ 17. AWS RDS Commands

Amazon RDS is a managed relational database service.

### 📋 List RDS Instances

```bash
aws rds describe-db-instances
```

### 🔍 Get Specific DB Instance

```bash
aws rds describe-db-instances \
  --db-instance-identifier my-database
```

### 🚀 Start DB Instance

```bash
aws rds start-db-instance \
  --db-instance-identifier my-database
```

### ⏹️ Stop DB Instance

```bash
aws rds stop-db-instance \
  --db-instance-identifier my-database
```

### 🔄 Reboot DB Instance

```bash
aws rds reboot-db-instance \
  --db-instance-identifier my-database
```

### 📊 List DB Snapshots

```bash
aws rds describe-db-snapshots
```

### 📖 List Read Replicas

```bash
aws rds describe-db-instances \
  --query "DBInstances[?ReadReplicaSourceDBInstanceIdentifier!=null].[DBInstanceIdentifier,ReadReplicaSourceDBInstanceIdentifier]" \
  --output table
```

---

## ⚡ 18. AWS Lambda Commands

AWS Lambda runs code without managing servers.

### 📋 List Functions

```bash
aws lambda list-functions
```

### 🔍 Get Function Details

```bash
aws lambda get-function \
  --function-name my-function
```

### ▶️ Invoke Lambda Function

```bash
aws lambda invoke \
  --function-name my-function \
  response.json
```

### 📄 Invoke with JSON Payload

```bash
aws lambda invoke \
  --function-name my-function \
  --payload '{"name":"Alok"}' \
  --cli-binary-format raw-in-base64-out \
  response.json
```

### 📊 View Function Configuration

```bash
aws lambda get-function-configuration \
  --function-name my-function
```

### 📦 List Lambda Layers

```bash
aws lambda list-layers
```

---

## 📊 19. AWS CloudWatch Commands

CloudWatch provides monitoring, logs, metrics, and alarms.

### 📋 List Log Groups

```bash
aws logs describe-log-groups
```

### 🔍 List Log Streams

```bash
aws logs describe-log-streams \
  --log-group-name /aws/lambda/my-function
```

### 📜 Get Log Events

```bash
aws logs get-log-events \
  --log-group-name /aws/lambda/my-function \
  --log-stream-name <LOG_STREAM_NAME>
```

### 📊 List CloudWatch Metrics

```bash
aws cloudwatch list-metrics
```

### 🚨 List CloudWatch Alarms

```bash
aws cloudwatch describe-alarms
```

### 🔍 Get Metric Statistics

```bash
aws cloudwatch get-metric-statistics \
  --namespace AWS/EC2 \
  --metric-name CPUUtilization \
  --dimensions Name=InstanceId,Value=<INSTANCE_ID> \
  --statistics Average \
  --period 300 \
  --start-time <START_TIME_ISO8601> \
  --end-time <END_TIME_ISO8601>
```

---

## 🔐 20. AWS STS Commands

AWS Security Token Service provides temporary security credentials and identity information.

### 👤 Check Current AWS Identity

```bash
aws sts get-caller-identity
```

### 🔑 Assume IAM Role

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::<ACCOUNT_ID>:role/MyRole \
  --role-session-name MySession
```

### 🌍 Get Caller Identity Using Profile

```bash
aws sts get-caller-identity --profile dev
```

---

## 🌍 21. AWS Region and Availability Zone Commands

### 📋 List AWS Regions

```bash
aws ec2 describe-regions --all-regions
```

### 📍 List Availability Zones

```bash
aws ec2 describe-availability-zones
```

### ⚙️ Get Current Configured Region

```bash
aws configure get region
```

### 🔄 Set Default Region

```bash
aws configure set region ap-south-1
```

### 🌐 Specify Region in a Command

```bash
aws ec2 describe-instances --region us-east-1
```

---

## 📄 22. AWS CLI Output and Query Options

AWS CLI supports different output formats and query expressions.

### 📊 JSON Output

```bash
aws ec2 describe-instances --output json
```

### 📋 Table Output

```bash
aws ec2 describe-instances --output table
```

### 📝 Text Output

```bash
aws ec2 describe-instances --output text
```

### 🔎 Filter Using Query

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].InstanceId"
```

### 🔍 Filter by Instance State

```bash
aws ec2 describe-instances \
  --filters Name=instance-state-name,Values=running
```

### 📦 Save Output to File

```bash
aws ec2 describe-instances > instances.json
```

---

## 🔧 23. Useful AWS CLI Commands

### 📌 General Commands

```bash
# Display AWS CLI version
aws --version

# Display AWS CLI help
aws help

# Display EC2 service help
aws ec2 help

# Display S3 service help
aws s3 help
```

### 🔍 Configuration Commands

```bash
# Display all configuration
aws configure list

# List profiles
aws configure list-profiles

# Display configured region
aws configure get region
```

### 📊 Pagination and Result Control

```bash
# Limit the number of returned items
aws ec2 describe-instances --max-items 10

# Return a specific page size
aws ec2 describe-instances --page-size 5

# Disable pagination
aws ec2 describe-instances --no-paginate
```

---

## 🛡️ 24. AWS Authentication Best Practices

- Prefer IAM Roles for EC2, Lambda, ECS, and other AWS workloads.
- Prefer IAM Identity Center for workforce and multi-account access.
- Avoid creating long-term access keys unless absolutely necessary.
- Never hardcode AWS credentials in source code.
- Never upload `.aws/credentials` to GitHub.
- Apply least-privilege IAM permissions.
- Use temporary credentials wherever possible.
- Enable MFA for privileged identities.
- Rotate and revoke credentials when necessary.

### 🚫 Recommended .gitignore Entries

```gitignore
# AWS credentials
.aws/

# Environment variables
.env
.env.*

# Terraform state
*.tfstate
*.tfstate.*
```

---

## 🧹 25. Uninstall AWS CLI

### 🐧 Linux – Official Installer

For the default system-wide installation:

```bash
sudo rm -f /usr/local/bin/aws
sudo rm -f /usr/local/bin/aws_completer
sudo rm -rf /usr/local/aws-cli
```

### 🪟 Windows

Uninstall through:

```text
Settings → Apps → Installed Apps → AWS Command Line Interface → Uninstall
```

### 🍎 macOS – Homebrew

```bash
brew uninstall awscli
```

### 🍎 macOS – Official Installer

For the default installation:

```bash
sudo rm -f /usr/local/bin/aws
sudo rm -f /usr/local/bin/aws_completer
sudo rm -rf /usr/local/aws-cli
```

> Removing AWS CLI does not automatically delete your AWS credentials and configuration files. Remove `~/.aws/` separately only if you also intend to delete those local settings.

---

## 🛡️ 26. Best Practices

- Use AWS CLI v2 for new installations.
- Use named profiles for separate environments.
- Specify the AWS region explicitly when needed.
- Review resource IDs before deleting or terminating resources.
- Use `--output table` for readable terminal output.
- Use `--query` to extract required information.
- Use IAM roles instead of permanent credentials on EC2.
- Keep the AWS CLI updated.
- Monitor resource changes through CloudTrail and CloudWatch.
- Verify the active account using `aws sts get-caller-identity` before performing critical operations.

---

## 📚 27. Official Documentation

- [AWS CLI Documentation](https://docs.aws.amazon.com/cli/latest/userguide/)
- [AWS CLI Installation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- [AWS CLI Configuration](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)
- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/)
- [AWS IAM Documentation](https://docs.aws.amazon.com/iam/)
- [Amazon EC2 CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/ec2/)
- [Amazon S3 CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/s3/)
- [Amazon RDS CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/rds/)
- [AWS Lambda CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/lambda/)
- [Amazon CloudWatch CLI Reference](https://docs.aws.amazon.com/cli/latest/reference/cloudwatch/)

---

**🚀 Learn • Configure • Automate • Manage**