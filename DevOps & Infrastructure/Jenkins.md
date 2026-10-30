# ⚙️ Jenkins – Installation & Commands Guide

## 🚀 Introduction

**Jenkins** is a free, open-source automation server used to automate software development tasks such as building, testing, integrating, and deploying applications.

Jenkins is widely used in Continuous Integration (CI) and Continuous Delivery/Deployment (CD) pipelines.

### 🛠️ Common Uses

- 🔄 Automating CI/CD pipelines
- 🏗️ Building applications
- 🧪 Running automated tests
- 📦 Packaging applications
- 🚀 Automating deployments
- 🐳 Building Docker images
- ☸️ Deploying applications to Kubernetes
- 🔗 Integrating GitHub, GitLab, AWS, and other tools

---

## 📦 Jenkins Versions

Jenkins provides two main release types:

| Release | Description |
|---|---|
| LTS | Long-Term Support; recommended for production. |
| Weekly | Frequent releases with newer features. |

**Recommendation:** Use the latest supported LTS release for production environments.

Official downloads: https://www.jenkins.io/download/

---

## ☕ Java Requirements

Jenkins requires Java to run because Jenkins is developed using Java.

For Jenkins 2.580.2 LTS, Java 21 or Java 25 is required.

| Java Version | Compatibility |
|---|---|
| Java 25 | Supported |
| Java 21 | Supported |
| Java 17 | Not supported by this Jenkins release |
| Java 11 | Not supported |

### 🔍 Verify Java

```bash
java --version
javac --version
which java
echo $JAVA_HOME
```

### 📥 Install Java 21

**Ubuntu / Debian:**

```bash
sudo apt update
sudo apt install fontconfig openjdk-21-jre -y
```

**Amazon Linux 2023:**

```bash
sudo dnf install fontconfig java-21-amazon-corretto-headless -y
```

**RHEL:**

```bash
sudo dnf install fontconfig java-21-openjdk -y
```

**macOS:**

```bash
brew install openjdk@21
```

**Windows:**

Download Java 21 from:

https://adoptium.net/

---

## 💻 System Requirements

| Resource | Minimum | Recommended |
|---|---|---|
| RAM | 256 MB | 4 GB or more |
| Storage | 1 GB | 50 GB or more |
| CPU | Depends on workload | 2 or more cores |
| Java | Java 21 or 25 | Java 21 or 25 |
| Network | Network connectivity | Stable network connection |

*Actual requirements depend on the number of jobs, plugins, users, and build workloads.*

---

## 🖥️ Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | YUM / RPM / Docker |
| Amazon Linux 2023 | DNF / RPM / Docker |
| Ubuntu | APT / Docker |
| RHEL | YUM / DNF / Docker |
| Windows | MSI Installer |
| macOS | Homebrew / Docker |

---

# 🔍 Package Management Commands

## 🐧 Amazon Linux 2 / RHEL (YUM)

### 🔎 Search packages

```bash
yum search jenkins
yum search java
```

### 📋 List available packages

```bash
yum list available
yum list available jenkins
```

### 📦 List installed packages

```bash
yum list installed
yum list installed jenkins
```

### ℹ️ Package information

```bash
yum info jenkins
```

### 📥 Install Jenkins

```bash
sudo yum install jenkins -y
```

### 🔄 Update Jenkins

```bash
sudo yum update jenkins
```

### 🗑️ Remove Jenkins

```bash
sudo yum remove jenkins -y
```

---

## 🐧 Amazon Linux 2023 / RHEL (DNF)

### 🔎 Search packages

```bash
dnf search jenkins
dnf search java
```

### 📋 List available packages

```bash
dnf list available
dnf list available jenkins
```

### 📦 List installed packages

```bash
dnf list installed
dnf list installed jenkins
```

### ℹ️ Package information

```bash
dnf info jenkins
```

### 📥 Install Jenkins

```bash
sudo dnf install jenkins -y
```

### 🔄 Update Jenkins

```bash
sudo dnf update jenkins
```

### 🗑️ Remove Jenkins

```bash
sudo dnf remove jenkins -y
```

---

## 🐧 Ubuntu / Debian (APT)

### 🔎 Search packages

```bash
apt search jenkins
```

### 📋 List available packages

```bash
apt list jenkins
```

### 📦 List installed packages

```bash
apt list --installed | grep jenkins
```

### ℹ️ Package information

```bash
apt show jenkins
```

### 📥 Install Jenkins

```bash
sudo apt update
sudo apt install jenkins -y
```

### 🔄 Update Jenkins

```bash
sudo apt update
sudo apt install --only-upgrade jenkins -y
```

### 🗑️ Remove Jenkins

```bash
sudo apt remove jenkins -y
sudo apt autoremove -y
```

---

# 📥 Jenkins Installation

## 🐧 Ubuntu

### Step 1: Update packages

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Install Java 21

```bash
sudo apt install fontconfig openjdk-21-jre -y
```

### Step 3: Verify Java

```bash
java --version
```

### Step 4: Add Jenkins repository signing key

```bash
sudo mkdir -p /etc/apt/keyrings

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
```

### Step 5: Add Jenkins LTS repository

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ | \
sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

### Step 6: Update package information

```bash
sudo apt update
```

### Step 7: Install Jenkins

```bash
sudo apt install jenkins -y
```

### Step 8: Start Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Step 9: Verify Jenkins

```bash
sudo systemctl status jenkins
```

### Step 10: Access Jenkins

```text
http://YOUR_SERVER_PUBLIC_IP:8080
```

---

## 🐧 Amazon Linux 2023

### Step 1: Update packages

```bash
sudo dnf update -y
```

### Step 2: Install Java 21

```bash
sudo dnf install fontconfig java-21-amazon-corretto-headless -y
```

### Step 3: Verify Java

```bash
java --version
```

### Step 4: Add Jenkins repository

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/rpm-stable/jenkins.repo
```

### Step 5: Import Jenkins signing key

```bash
sudo rpm --import https://pkg.jenkins.io/rpm-stable/jenkins.io-2026.key
```

### Step 6: Install Jenkins

```bash
sudo dnf install jenkins -y
```

### Step 7: Reload systemd

```bash
sudo systemctl daemon-reload
```

### Step 8: Start Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Step 9: Verify Jenkins

```bash
sudo systemctl status jenkins
```

### Step 10: Access Jenkins

```text
http://YOUR_SERVER_PUBLIC_IP:8080
```

---

## 🐧 RHEL

### Step 1: Update packages

```bash
sudo dnf update -y
```

### Step 2: Install Java 21

```bash
sudo dnf install fontconfig java-21-openjdk -y
```

### Step 3: Verify Java

```bash
java --version
```

### Step 4: Add Jenkins repository

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/rpm-stable/jenkins.repo
```

### Step 5: Import Jenkins signing key

```bash
sudo rpm --import https://pkg.jenkins.io/rpm-stable/jenkins.io-2026.key
```

### Step 6: Install Jenkins

```bash
sudo dnf install jenkins -y
```

### Step 7: Reload systemd

```bash
sudo systemctl daemon-reload
```

### Step 8: Start Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Step 9: Verify Jenkins

```bash
sudo systemctl status jenkins
```

---

## 🐧 Amazon Linux 2

<badge color="warning">Legacy OS – Standard support ended June 30, 2026</badge>

Amazon Linux 2 has reached the end of standard support. Prefer Amazon Linux 2023 for new installations.

### Step 1: Check available Java packages

```bash
sudo yum search java-21
```

### Step 2: Install a compatible Java 21 runtime

Install Java 21 using a vendor-supported installation method.

```bash
java --version
```

### Step 3: Add Jenkins repository

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/rpm-stable/jenkins.repo
```

### Step 4: Import Jenkins signing key

```bash
sudo rpm --import \
https://pkg.jenkins.io/rpm-stable/jenkins.io-2026.key
```

### Step 5: Install Jenkins

```bash
sudo yum install jenkins -y
```

### Step 6: Start Jenkins

```bash
sudo systemctl daemon-reload
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Step 7: Verify Jenkins

```bash
sudo systemctl status jenkins
```

*If the OS or repository cannot provide a compatible Java runtime, use Amazon Linux 2023 or Docker.*

---

## 🪟 Windows

Jenkins provides an official Windows MSI installer.

### 📥 Installation Steps

1. Download the Jenkins LTS Windows installer.
2. Install Java 21 or Java 25.
3. Run the Jenkins MSI installer.
4. Select the installation directory.
5. Configure the Jenkins service account.
6. Select the Jenkins port (default: 8080).
7. Select the Java installation directory.
8. Complete the installation.

Official download:

https://www.jenkins.io/download/

### 🔍 Verify Java

```powershell
java --version
```

### ⚙️ Jenkins Windows Service Commands

```powershell
# Check Jenkins service
Get-Service Jenkins

# Start Jenkins
Start-Service Jenkins

# Stop Jenkins
Stop-Service Jenkins

# Restart Jenkins
Restart-Service Jenkins

# Check status
Get-Service Jenkins
```

### 🌐 Access Jenkins

```text
http://localhost:8080
```

---

## 🍎 macOS

### Step 1: Install Java 21

```bash
brew install openjdk@21
```

### Step 2: Install Jenkins LTS

```bash
brew install jenkins-lts
```

### Step 3: Start Jenkins

```bash
brew services start jenkins-lts
```

### Step 4: Verify Jenkins service

```bash
brew services list
```

### Step 5: Restart Jenkins

```bash
brew services restart jenkins-lts
```

### Step 6: Stop Jenkins

```bash
brew services stop jenkins-lts
```

### 🌐 Access Jenkins

```text
http://localhost:8080
```

---

# 🔐 Jenkins Initial Configuration

After installation, Jenkins requires an initial setup.

### Step 1: Access Jenkins

```text
http://localhost:8080
```

### Step 2: Retrieve Initial Admin Password

**Linux:**

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

**Windows PowerShell:**

```powershell
Get-Content "$env:ProgramData\Jenkins\.jenkins\secrets\initialAdminPassword"
```

**Docker:**

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

### Step 3: Unlock Jenkins

1. Copy the initial administrator password.
2. Paste it into the Jenkins unlock page.
3. Click Continue.

### Step 4: Install Plugins

Select:

```text
Install suggested plugins
```

### Step 5: Create Administrator User

Enter the username, password, full name, and email.

### Step 6: Finish Setup

Click Save and Finish.

---

# ⚙️ Jenkins Service Management

### ▶️ Start Jenkins

```bash
sudo systemctl start jenkins
```

### 🛑 Stop Jenkins

```bash
sudo systemctl stop jenkins
```

### 🔄 Restart Jenkins

```bash
sudo systemctl restart jenkins
```

### 🔍 Check Jenkins status

```bash
sudo systemctl status jenkins
```

### 🚀 Enable Jenkins at startup

```bash
sudo systemctl enable jenkins
```

### ❌ Disable automatic startup

```bash
sudo systemctl disable jenkins
```

### 📋 View Jenkins logs

```bash
sudo journalctl -u jenkins
```

### 📋 Follow live logs

```bash
sudo journalctl -u jenkins -f
```

### 📋 View recent logs

```bash
sudo journalctl -u jenkins -n 100
```

---

# 🌐 Jenkins Ports and Firewall

| Port | Purpose |
|---|---|
| 8080 | Jenkins Web UI |
| 50000 | Inbound agent communication when TCP agent listener is enabled |
| 443 | HTTPS through a reverse proxy |
| 80 | HTTP through a reverse proxy |

### 🔓 Ubuntu Firewall (UFW)

```bash
# Allow Jenkins Web UI
sudo ufw allow 8080/tcp

# Check firewall status
sudo ufw status
```

### 🔓 RHEL / Amazon Linux Firewall (firewalld)

```bash
# Allow Jenkins Web UI
sudo firewall-cmd --permanent --add-port=8080/tcp

# Apply changes
sudo firewall-cmd --reload

# Check allowed ports
sudo firewall-cmd --list-ports
```

### ☁️ AWS EC2 Security Group

If Jenkins is installed on an AWS EC2 instance:

- Allow TCP port 8080 only from your trusted IP address for initial access.
- Configure HTTPS through a reverse proxy for production.
- Do not expose Jenkins administration interfaces publicly without suitable protection.
- Avoid exposing port 50000 unless inbound agent communication is required.

---

# 📁 Important Jenkins Directories

### 🐧 Linux

```text
/var/lib/jenkins/
```

### 🪟 Windows

```text
C:\ProgramData\Jenkins\.jenkins\
```

### 🐳 Docker

```text
/var/jenkins_home/
```

### 📂 Important Files and Directories

| File / Directory | Purpose |
|---|---|
| config.xml | Main Jenkins configuration |
| jobs/ | Job configurations and build information |
| plugins/ | Installed plugins |
| users/ | User information |
| secrets/ | Sensitive security data |
| credentials.xml | Stored credential configuration |
| workspace/ | Job working directories |
| nodes/ | Agent configuration |

---

# 🔌 Jenkins Plugins

Plugins extend Jenkins functionality and allow integration with different tools.

| Plugin | Purpose |
|---|---|
| Git Plugin | Git repository integration |
| GitHub Plugin | GitHub integration |
| Pipeline Plugin | Pipeline creation and execution |
| Docker Pipeline | Docker integration |
| Credentials Plugin | Secure credential management |
| Maven Integration Plugin | Maven build integration |
| NodeJS Plugin | Node.js environment management |
| SSH Agent Plugin | SSH authentication |
| Kubernetes Plugin | Kubernetes agent integration |
| Email Extension Plugin | Email notifications |

### ⚙️ Install Plugins

1. Open Jenkins Dashboard.
2. Go to Manage Jenkins.
3. Open Plugins.
4. Select Available Plugins.
5. Search for the required plugin.
6. Select Install.

---

# 🏗️ Jenkins Jobs and Pipelines

### 📦 Common Job Types

| Job Type | Purpose |
|---|---|
| Freestyle Project | Basic job configured through Jenkins UI |
| Pipeline | Defines automation workflows as code |
| Multibranch Pipeline | Discovers and builds repository branches |
| Organization Folder | Discovers repositories and branches |
| Maven Project | Provides Maven-oriented build configuration |

### 🔄 Create a Freestyle Project

1. Open Jenkins Dashboard.
2. Click New Item.
3. Enter the project name.
4. Select Freestyle Project.
5. Configure source code management.
6. Configure build triggers.
7. Add build steps.
8. Save and execute the job.

---

# 📝 Jenkinsfile – Pipeline as Code

A Jenkinsfile defines the automated steps Jenkins should execute.

It is normally stored in the root directory of the application's Git repository.

### 📄 Example Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
```

### 🧠 Pipeline Components

| Component | Purpose |
|---|---|
| pipeline | Defines the Pipeline. |
| agent | Specifies where the Pipeline executes. |
| stages | Groups execution stages. |
| stage | Defines an individual stage. |
| steps | Contains commands and actions. |
| post | Defines actions after Pipeline execution. |
| environment | Defines environment variables. |
| parameters | Defines user-provided build parameters. |
| triggers | Defines automatic execution triggers. |

---

# 🔗 Jenkins with GitHub

### 🔄 Example Workflow

```text
Developer
    |
    v
Push Code to GitHub
    |
    v
GitHub Webhook
    |
    v
Jenkins
    |
    v
Checkout Repository
    |
    v
Build Application
    |
    v
Run Tests
    |
    v
Deploy Application
```

### ⚙️ Integration Steps

1. Install Git and GitHub-related plugins.
2. Configure Git in Jenkins.
3. Configure GitHub repository URL.
4. Add credentials for private repositories.
5. Configure a GitHub webhook.
6. Configure the Jenkins job or Multibranch Pipeline.
7. Add a Jenkinsfile to the repository.
8. Push code and verify Pipeline execution.

### 🔔 Example GitHub Webhook URL

```text
http://YOUR_JENKINS_SERVER/github-webhook/
```

*For production, use HTTPS and a securely reachable Jenkins endpoint.*

---

# 🐳 Jenkins with Docker

### 📥 Pull Jenkins LTS Image

```bash
docker pull jenkins/jenkins:2.580.2-jdk21
```

### 🔍 Check Docker Images

```bash
docker images
```

### 📦 Create Jenkins Docker Volume

```bash
docker volume create jenkins_home
```

### ▶️ Run Jenkins Container

```bash
docker run -d \
  --name jenkins \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:2.580.2-jdk21
```

### 🔍 Check Running Containers

```bash
docker ps
```

### 📋 View Jenkins Logs

```bash
docker logs jenkins
```

### 🔐 Get Initial Admin Password

```bash
docker exec jenkins \
cat /var/jenkins_home/secrets/initialAdminPassword
```

### 🛑 Stop Jenkins Container

```bash
docker stop jenkins
```

### ▶️ Start Jenkins Container

```bash
docker start jenkins
```

### 🔄 Restart Jenkins Container

```bash
docker restart jenkins
```

### 🗑️ Remove Jenkins Container

```bash
docker rm -f jenkins
```

> **Important:** Removing the container does not remove the named `jenkins_home` volume. Jenkins data can survive container replacement.

---

# 🔧 Jenkins CLI Commands

Jenkins provides a command-line interface (CLI) for interacting with the Jenkins controller.

### 📥 Download Jenkins CLI

```bash
wget http://localhost:8080/jnlpJars/jenkins-cli.jar
```

### 🔍 Display CLI Help

```bash
java -jar jenkins-cli.jar -s http://localhost:8080 help
```

### 📋 List Jenkins Jobs

```bash
java -jar jenkins-cli.jar -s http://localhost:8080 list-jobs
```

### ▶️ Build a Job

```bash
java -jar jenkins-cli.jar -s http://localhost:8080 build JOB_NAME
```

### 🔄 Restart Jenkins

```bash
java -jar jenkins-cli.jar -s http://localhost:8080 safe-restart
```

*For authenticated Jenkins instances, configure the appropriate user API token and authentication options.*

---

# 🔍 Jenkins Troubleshooting Commands

### 🐧 Linux

```bash
# Check Jenkins status
sudo systemctl status jenkins

# Check Jenkins logs
sudo journalctl -u jenkins -n 100

# Follow live logs
sudo journalctl -u jenkins -f

# Restart Jenkins
sudo systemctl restart jenkins

# Check Java version
java --version

# Check port 8080
sudo ss -tulpn | grep 8080

# Check disk usage
df -h

# Check memory
free -h
```

### 🐳 Docker

```bash
# List containers
docker ps -a

# Check logs
docker logs jenkins

# Inspect container
docker inspect jenkins

# Check volume
docker volume inspect jenkins_home

# Execute shell inside container
docker exec -it jenkins bash
```

### ⚠️ Common Jenkins Issues

| Problem | Possible Solution |
|---|---|
| Jenkins service fails to start | Check Java compatibility and service logs. |
| Port 8080 already in use | Identify the process or configure another port. |
| Initial password not found | Check the correct Jenkins Home directory. |
| Plugin installation fails | Check internet access, proxy, and plugin compatibility. |
| Git command not found | Install Git and configure its executable path. |
| Build fails | Inspect console output and verify required tools. |
| Disk space exhausted | Inspect old workspaces, builds, and logs. |
| Agent disconnected | Check network connectivity and agent configuration. |

---

# 🔄 Jenkins Backup and Restore

### 📦 Backup Jenkins Home

For a Linux installation, stop Jenkins before taking a simple filesystem backup.

```bash
# Stop Jenkins
sudo systemctl stop jenkins

# Create backup archive
sudo tar -czf jenkins-backup.tar.gz /var/lib/jenkins

# Start Jenkins
sudo systemctl start jenkins
```

### 📋 Verify Backup

```bash
ls -lh jenkins-backup.tar.gz
```

### ♻️ Restore Backup

```bash
# Stop Jenkins
sudo systemctl stop jenkins

# Restore backup
sudo tar -xzf jenkins-backup.tar.gz -C /

# Set ownership
sudo chown -R jenkins:jenkins /var/lib/jenkins

# Start Jenkins
sudo systemctl start jenkins
```

> **Security:** Jenkins backups contain sensitive credentials and secrets. Store backups securely and restrict access.

---

# 🛡️ Jenkins Security Best Practices

- Use a supported Jenkins LTS release.
- Keep Java updated to a supported version.
- Regularly update Jenkins plugins.
- Enable authentication and authorization.
- Use role-based access control where appropriate.
- Store passwords and API tokens in Jenkins Credentials.
- Never hardcode secrets inside Jenkinsfiles.
- Use HTTPS through a properly configured reverse proxy.
- Restrict access to port 8080.
- Avoid exposing Jenkins administration interfaces publicly.
- Use dedicated agents for build and deployment workloads.
- Back up Jenkins Home regularly.
- Review user permissions and security advisories.

---

# 🗑️ Jenkins Uninstallation

### 🐧 Ubuntu / Debian

```bash
# Stop Jenkins
sudo systemctl stop jenkins

# Remove Jenkins package
sudo apt remove jenkins -y

# Remove unused packages
sudo apt autoremove -y
```

### 🐧 Amazon Linux 2023 / RHEL

```bash
sudo systemctl stop jenkins
sudo dnf remove jenkins -y
```

### 🐧 Amazon Linux 2

```bash
sudo systemctl stop jenkins
sudo yum remove jenkins -y
```

### 🪟 Windows

```text
Settings → Apps → Installed Apps → Jenkins → Uninstall
```

### 🍎 macOS

```bash
brew services stop jenkins-lts
brew uninstall jenkins-lts
```

### 🐳 Docker

```bash
# Remove Jenkins container
docker rm -f jenkins

# Remove Jenkins data only if no longer needed
docker volume rm jenkins_home
```

---

# 📚 Official Documentation & Resources

| Resource | Link |
|---|---|
| Jenkins Official Website | https://www.jenkins.io/ |
| Jenkins Documentation | https://www.jenkins.io/doc/ |
| Jenkins Downloads | https://www.jenkins.io/download/ |
| Jenkins LTS Changelog | https://www.jenkins.io/changelog-stable/ |
| Jenkins Java Support Policy | https://www.jenkins.io/doc/book/platform-information/support-policy-java/ |
| Jenkins Linux Installation | https://www.jenkins.io/doc/book/installing/linux/ |
| Jenkins Windows Installation | https://www.jenkins.io/doc/book/installing/windows/ |
| Jenkins Docker Installation | https://www.jenkins.io/doc/book/installing/docker/ |
| Jenkins Pipeline Documentation | https://www.jenkins.io/doc/book/pipeline/ |
| Jenkins Plugin Directory | https://plugins.jenkins.io/ |
| Jenkins GitHub Repository | https://github.com/jenkinsci/jenkins |
| Jenkins Security Advisories | https://www.jenkins.io/security/ |

---

**⚙️ Jenkins Installation | Configuration | Commands | CI/CD Automation**