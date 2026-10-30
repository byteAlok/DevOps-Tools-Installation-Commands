# 🐳 Docker – Installation & Commands Guide

## 🚀 Introduction

**Docker** is an open-source platform used to build, package, distribute, and run applications inside lightweight, isolated environments called containers.

Docker helps developers package an application along with its dependencies, libraries, and configuration so that it can run consistently across different environments.

### ⚙️ What is Docker used for?

- 📦 Application containerization
- 🚀 Application deployment
- 🔄 CI/CD pipeline automation
- 🧪 Testing applications in isolated environments
- ☁️ Cloud application deployment
- 🧩 Microservices architecture
- 🗄️ Running databases and other services
- ☸️ Kubernetes container orchestration
- 🔧 Development environment management

> **Important:** Docker is a containerization platform. It is not a virtual machine or an operating system.

---

## 📚 Docker Components

| Component | Description |
|---|---|
| Docker Engine | Core technology responsible for building and running containers. |
| Docker CLI | Command-line interface used to interact with Docker. |
| Docker Daemon | Background service that manages Docker objects. |
| Docker Image | Read-only template used to create containers. |
| Docker Container | Running or stopped instance created from an image. |
| Dockerfile | Text file containing instructions to build an image. |
| Docker Hub | Public container image registry. |
| Docker Registry | Storage and distribution system for container images. |
| Docker Compose | Tool used to define and manage multi-container applications. |
| Docker Volume | Persistent storage managed by Docker. |
| Docker Network | Enables communication between containers and external systems. |

---

## 🆚 Docker Engine vs Docker Desktop

| Docker Engine | Docker Desktop |
|---|---|
| Core containerization technology. | Desktop application providing a complete Docker environment. |
| Commonly installed directly on Linux. | Available for Windows, macOS, and Linux. |
| Uses Docker daemon and CLI. | Includes Docker Engine, CLI, and additional tools. |
| Suitable for servers and cloud environments. | Suitable for local development. |
| Managed using system services on Linux. | Managed through a desktop application. |

---

## 🧠 Docker Architecture

Docker follows a client-server architecture.

### ⚙️ Main Components

**1. Docker Client**

The Docker CLI allows users to communicate with the Docker daemon.

**2. Docker Daemon**

The Docker daemon manages images, containers, networks, and volumes.

**3. Docker Registry**

A registry stores and distributes Docker images. Docker Hub is a commonly used public registry.

### 🔄 Docker Architecture Flow

```text
          Docker Client
               |
               | Docker Commands
               v
         Docker Daemon
               |
       -------------------
       |        |        |
       v        v        v
     Images  Containers Networks
       |
       v
   Docker Registry
    (Docker Hub)
```

---

## 📦 Docker Release and Updates

Docker Engine and Docker Desktop receive regular updates containing new features, bug fixes, and security improvements.

Official downloads:

https://docs.docker.com/get-started/get-docker/

### 🔍 Check Installed Version

```bash
# Docker CLI version
docker --version

# Docker Engine and client information
docker version

# Complete Docker system information
docker info

# Docker Compose version
docker compose version
```

---

## 💻 System Requirements

Docker requirements depend on the operating system and installation method.

### 🐧 Linux

| Requirement | Details |
|---|---|
| Operating System | Supported Linux distributions |
| Architecture | Supported x86_64 and ARM64 architectures |
| Processor | 64-bit processor |
| RAM | 2 GB minimum recommended for basic usage; more for multiple containers |
| Storage | Depends on images, containers, volumes, and workloads |
| Virtualization | Linux kernel features required by Docker Engine |

### 🪟 Windows

| Requirement | Details |
|---|---|
| Operating System | Supported Windows 10/11 editions |
| Architecture | 64-bit processor |
| RAM | 8 GB or more recommended |
| WSL | WSL 2.1.5 or later for WSL 2 backend |
| Virtualization | Hardware virtualization enabled in BIOS/UEFI |

### 🍎 macOS

| Requirement | Details |
|---|---|
| Operating System | Current and two previous supported macOS major releases |
| Architecture | Intel or Apple Silicon |
| RAM | Minimum 4 GB |
| Virtualization | macOS virtualization support |

*Windows and macOS requirements refer to Docker Desktop. Linux Docker Engine has separate distribution-specific requirements.*

---

## 🖥️ Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | YUM / Docker repository |
| Amazon Linux 2023 | DNF / Docker repository |
| Ubuntu | APT / Docker repository |
| Debian | APT / Docker repository |
| RHEL | DNF / Docker repository |
| Windows | Docker Desktop / WSL 2 |
| macOS | Docker Desktop / Homebrew |

Official installation documentation:

https://docs.docker.com/engine/install/

---

# 🔍 Package Management Commands

Package managers help install, update, search, inspect, and remove Docker packages.

## 🐧 Amazon Linux 2 / RHEL (YUM)

### 🔎 Search packages

```bash
yum search docker
yum search docker-ce
```

### 📋 List available packages

```bash
yum list available
yum list available docker-ce
```

### 📦 List installed packages

```bash
yum list installed
yum list installed docker-ce
```

### ℹ️ Package information

```bash
yum info docker
yum info docker-ce
```

### 📥 Install packages

```bash
sudo yum install docker -y
```

### 🔄 Update packages

```bash
sudo yum update
sudo yum update docker
```

### 🗑️ Remove packages

```bash
sudo yum remove docker -y
```

---

## 🐧 Amazon Linux 2023 / RHEL (DNF)

### 🔎 Search packages

```bash
dnf search docker
dnf search docker-ce
```

### 📋 List available packages

```bash
dnf list available
dnf list available docker-ce
```

### 📦 List installed packages

```bash
dnf list installed
dnf list installed docker-ce
```

### ℹ️ Package information

```bash
dnf info docker
dnf info docker-ce
```

### 📥 Install packages

```bash
sudo dnf install docker -y
```

### 🔄 Update packages

```bash
sudo dnf update
sudo dnf update docker
```

### 🗑️ Remove packages

```bash
sudo dnf remove docker -y
```

---

## 🐧 Ubuntu / Debian (APT)

### 🔎 Search packages

```bash
apt search docker
apt search docker-ce
```

### 📋 List available packages

```bash
apt list docker.io
apt list docker-ce
```

### 📦 List installed packages

```bash
apt list --installed | grep docker
```

### ℹ️ Package information

```bash
apt show docker.io
apt show docker-ce
```

### 📥 Install packages

```bash
sudo apt update
sudo apt install docker.io -y
```

### 🔄 Update packages

```bash
sudo apt update
sudo apt upgrade
```

### 🗑️ Remove packages

```bash
sudo apt remove docker.io -y
sudo apt autoremove -y
```

> **Note:** `docker.io` is the distribution-maintained Docker package on Ubuntu. The official Docker repository provides `docker-ce`, `docker-ce-cli`, and related packages. The installation sections below use the official Docker repository.

---

# 📥 Docker Installation

## 🐧 Ubuntu

### Step 1: Update package information

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Remove conflicting packages

```bash
sudo apt remove docker.io docker-compose docker-doc docker-buildx docker-compose-v2 podman-docker containerd runc
```

### Step 3: Install required packages

```bash
sudo apt install ca-certificates curl -y
```

### Step 4: Create Docker keyring directory

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

### Step 5: Add Docker GPG key

```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg \
-o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Step 6: Add Docker repository

```bash
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```

### Step 7: Update package information

```bash
sudo apt update
```

### Step 8: Install Docker Engine and plugins

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### Step 9: Start Docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 10: Verify Docker

```bash
sudo systemctl status docker
docker --version
docker compose version
```

### Step 11: Test Docker installation

```bash
sudo docker run hello-world
```

---

## 🐧 Debian

### Step 1: Update packages

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Remove conflicting packages

```bash
sudo apt remove docker.io docker-compose docker-doc docker-buildx docker-compose-v2 podman-docker containerd runc
```

### Step 3: Install required packages

```bash
sudo apt install ca-certificates curl -y
```

### Step 4: Create keyring directory

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

### Step 5: Add Docker GPG key

```bash
sudo curl -fsSL https://download.docker.com/linux/debian/gpg \
-o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Step 6: Add Docker repository

```bash
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/debian
Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```

### Step 7: Update package information

```bash
sudo apt update
```

### Step 8: Install Docker

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### Step 9: Start Docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 10: Verify Docker

```bash
sudo docker run hello-world
docker --version
```

---

## 🐧 Amazon Linux 2023

### Step 1: Update packages

```bash
sudo dnf update -y
```

### Step 2: Install Docker

```bash
sudo dnf install docker -y
```

### Step 3: Start Docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 4: Verify Docker

```bash
sudo systemctl status docker
docker --version
```

### Step 5: Test Docker

```bash
sudo docker run hello-world
```

### Step 6: Enable Docker for current user

```bash
sudo usermod -aG docker $USER
```

Log out and log back in for group changes to take effect.

---

## 🐧 Amazon Linux 2

### Step 1: Update packages

```bash
sudo yum update -y
```

### Step 2: Install Docker

```bash
sudo amazon-linux-extras install docker -y
```

### Step 3: Start Docker

```bash
sudo service docker start
```

### Step 4: Enable Docker at startup

```bash
sudo chkconfig docker on
```

### Step 5: Add current user to Docker group

```bash
sudo usermod -aG docker ec2-user
```

### Step 6: Verify Docker

```bash
docker --version
sudo docker run hello-world
```

<badge color="warning">Legacy OS</badge>

Amazon Linux 2 reached the end of standard support on June 30, 2026. Prefer Amazon Linux 2023 for new deployments.

---

## 🐧 RHEL

### Step 1: Remove conflicting packages

```bash
sudo dnf remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine podman runc
```

### Step 2: Install required packages

```bash
sudo dnf install dnf-plugins-core -y
```

### Step 3: Add Docker repository

```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
```

### Step 4: Install Docker Engine

```bash
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### Step 5: Start Docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 6: Verify Docker

```bash
sudo systemctl status docker
docker --version
```

### Step 7: Test Docker

```bash
sudo docker run hello-world
```

---

## 🪟 Windows

Docker Desktop is the recommended way to use Docker on Windows.

### 📋 Requirements

- Windows 10 or Windows 11 supported edition.
- WSL 2.1.5 or later for the WSL 2 backend.
- Hardware virtualization enabled.
- 8 GB RAM recommended.
- 64-bit processor.

### Step 1: Install WSL 2

Open PowerShell as Administrator:

```powershell
wsl --install
```

### Step 2: Restart Windows

Restart your computer after WSL installation.

### Step 3: Check WSL version

```powershell
wsl --version
```

### Step 4: Set WSL 2 as default

```powershell
wsl --set-default-version 2
```

### Step 5: Download Docker Desktop

Official download:

https://www.docker.com/products/docker-desktop/

### Step 6: Install Docker Desktop

1. Run the Docker Desktop installer.
2. Select the WSL 2 backend.
3. Complete the installation.
4. Restart if required.
5. Open Docker Desktop.

### Step 7: Verify Docker

```powershell
docker --version
docker compose version
docker info
```

### Step 8: Test Docker

```powershell
docker run hello-world
```

### 🔧 Useful WSL Commands

```powershell
# List installed distributions
wsl --list --verbose

# Update WSL
wsl --update

# Shut down WSL
wsl --shutdown

# Check WSL status
wsl --status
```

---

## 🍎 macOS

Docker Desktop is the recommended installation method on macOS.

### Method 1: Docker Desktop

1. Visit the official Docker website.
2. Download the correct installer for Apple Silicon or Intel.
3. Open the downloaded DMG file.
4. Drag Docker into Applications.
5. Open Docker Desktop.
6. Complete the initial setup.

Official download:

https://www.docker.com/products/docker-desktop/

### 🔍 Verify Docker

```bash
docker --version
docker compose version
docker info
```

### Method 2: Homebrew

```bash
# Update Homebrew
brew update

# Install Docker Desktop
brew install --cask docker

# Open Docker Desktop
open -a Docker
```

### 🔄 Update Docker Desktop

```bash
brew upgrade --cask docker
```

---

# 🔍 Verify Docker Installation

After installation, execute the following commands.

```bash
# Docker CLI version
docker --version

# Client and server version
docker version

# Docker system information
docker info

# Docker Compose version
docker compose version

# Docker Buildx version
docker buildx version

# Test Docker installation
docker run hello-world
```

---

# 📦 Docker Image Commands

A Docker image is a read-only template used to create containers.

### 🔎 Search Images

```bash
docker search nginx
docker search ubuntu
docker search mysql
```

### 📥 Download Images

```bash
docker pull nginx
docker pull ubuntu
docker pull mysql
```

### 📋 List Images

```bash
docker images
```

### 🔍 Inspect Image

```bash
docker inspect nginx
```

### 📜 Image History

```bash
docker history nginx
```

### 🏷️ Rename / Tag Image

```bash
docker tag nginx my-nginx:v1
```

### 📤 Push Image to Docker Hub

```bash
# Login to Docker Hub
docker login

# Tag image with Docker Hub username
docker tag nginx YOUR_USERNAME/my-nginx:v1

# Push image
docker push YOUR_USERNAME/my-nginx:v1
```

### 🗑️ Remove Image

```bash
docker rmi nginx
```

### 🧹 Remove Unused Images

```bash
docker image prune
```

### 🧹 Remove All Unused Images

```bash
docker image prune -a
```

---

# 🚀 Docker Container Commands

A container is a running or stopped instance of a Docker image.

### ▶️ Run Container

```bash
docker run nginx
```

### 🔄 Run Container in Background

```bash
docker run -d nginx
```

### 🏷️ Run Container with Name

```bash
docker run -d --name my-nginx nginx
```

### 🌐 Port Mapping

```bash
docker run -d -p 8080:80 nginx
```

Open:

```text
http://localhost:8080
```

### 📋 List Running Containers

```bash
docker ps
```

### 📋 List All Containers

```bash
docker ps -a
```

### 🔍 Inspect Container

```bash
docker inspect my-nginx
```

### 📋 View Container Logs

```bash
docker logs my-nginx
```

### 🔄 Follow Live Logs

```bash
docker logs -f my-nginx
```

### ▶️ Start Container

```bash
docker start my-nginx
```

### 🛑 Stop Container

```bash
docker stop my-nginx
```

### 🔄 Restart Container

```bash
docker restart my-nginx
```

### ⏸️ Pause Container

```bash
docker pause my-nginx
```

### ▶️ Unpause Container

```bash
docker unpause my-nginx
```

### 🗑️ Remove Container

```bash
docker rm my-nginx
```

### 🗑️ Force Remove Container

```bash
docker rm -f my-nginx
```

### 🧹 Remove All Stopped Containers

```bash
docker container prune
```

---

# 🖥️ Execute Commands Inside Containers

### 🔌 Open Interactive Shell

```bash
docker exec -it my-nginx bash
```

If Bash is not available:

```bash
docker exec -it my-nginx sh
```

### 📋 List Processes

```bash
docker top my-nginx
```

### 📂 Copy Files into Container

```bash
docker cp index.html my-nginx:/usr/share/nginx/html/
```

### 📤 Copy Files from Container

```bash
docker cp my-nginx:/etc/nginx/nginx.conf ./nginx.conf
```

### 🔍 Container Resource Usage

```bash
docker stats
```

---

# 📁 Docker Volumes

Docker volumes provide persistent storage for containers.

Data stored in a Docker-managed volume can survive container removal.

### 📦 Create Volume

```bash
docker volume create my-volume
```

### 📋 List Volumes

```bash
docker volume ls
```

### 🔍 Inspect Volume

```bash
docker volume inspect my-volume
```

### 🚀 Use Volume with Container

```bash
docker run -d \
  --name my-nginx \
  -p 8080:80 \
  -v my-volume:/usr/share/nginx/html \
  nginx
```

### 🗑️ Remove Volume

```bash
docker volume rm my-volume
```

### 🧹 Remove Unused Volumes

```bash
docker volume prune
```

---

# 🌐 Docker Networks

Docker networks allow containers to communicate with each other and external systems.

### 📋 List Networks

```bash
docker network ls
```

### 📦 Create Network

```bash
docker network create my-network
```

### 🔍 Inspect Network

```bash
docker network inspect my-network
```

### 🚀 Run Container with Network

```bash
docker run -d \
  --name app-container \
  --network my-network \
  nginx
```

### 🔗 Connect Container to Network

```bash
docker network connect my-network app-container
```

### ❌ Disconnect Container

```bash
docker network disconnect my-network app-container
```

### 🗑️ Remove Network

```bash
docker network rm my-network
```

### 🧹 Remove Unused Networks

```bash
docker network prune
```

---

# 📝 Dockerfile Commands

A Dockerfile contains instructions used to build a Docker image.

| Instruction | Purpose |
|---|---|
| FROM | Defines the base image. |
| WORKDIR | Sets the working directory. |
| COPY | Copies files into the image. |
| ADD | Copies files and supports additional features such as archive extraction. |
| RUN | Executes commands during image building. |
| CMD | Defines the default command. |
| ENTRYPOINT | Defines the main executable. |
| EXPOSE | Documents the container port. |
| ENV | Defines environment variables. |
| ARG | Defines build-time variables. |
| USER | Sets the user for subsequent instructions. |
| VOLUME | Defines a mount point. |
| LABEL | Adds image metadata. |

### 📄 Example Dockerfile

```dockerfile
FROM nginx:alpine

WORKDIR /usr/share/nginx/html

COPY index.html .

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

### 🏗️ Build Docker Image

```bash
docker build -t my-web-app .
```

### 🏷️ Build with Version Tag

```bash
docker build -t my-web-app:v1 .
```

### 📋 List Built Images

```bash
docker images
```

### ▶️ Run Application

```bash
docker run -d -p 8080:80 --name web-container my-web-app:v1
```

Open:

```text
http://localhost:8080
```

---

# 🐳 Docker Compose

Docker Compose is a tool used to define and manage multi-container applications using a YAML configuration file.

It is useful when an application requires multiple services, such as:

- Web application
- Database
- Cache
- Backend API

### 📄 Example compose.yaml

```yaml
services:

  web:
    image: nginx:alpine
    container_name: nginx-web
    ports:
      - "8080:80"

  database:
    image: mysql:8
    container_name: mysql-db
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: appdb
    volumes:
      - mysql-data:/var/lib/mysql

volumes:
  mysql-data:
```

*The example password is for local learning only. Never use hardcoded sample credentials in production.*

### 🔍 Validate Compose File

```bash
docker compose config
```

### ▶️ Start Services

```bash
docker compose up
```

### 🚀 Start Services in Background

```bash
docker compose up -d
```

### 📋 List Services

```bash
docker compose ps
```

### 📋 View Logs

```bash
docker compose logs
```

### 🔄 Follow Live Logs

```bash
docker compose logs -f
```

### 🛑 Stop Services

```bash
docker compose stop
```

### ▶️ Start Existing Services

```bash
docker compose start
```

### 🔄 Restart Services

```bash
docker compose restart
```

### 🗑️ Remove Containers and Networks

```bash
docker compose down
```

### 🗑️ Remove Containers, Networks, and Volumes

```bash
docker compose down -v
```

> **Warning:** `docker compose down -v` removes Compose-managed volumes and can delete persistent database data.

---

# 🔄 Docker System Management

### 📊 Display Docker Disk Usage

```bash
docker system df
```

### 🧹 Remove Unused Docker Resources

```bash
docker system prune
```

### 🧹 Remove Unused Resources Including Images

```bash
docker system prune -a
```

### 📋 Display Docker Events

```bash
docker events
```

### 🔍 Display Docker Information

```bash
docker info
```

### 📋 Display Docker Context

```bash
docker context ls
```

### 🔄 Switch Docker Context

```bash
docker context use default
```

> **Warning:** Prune commands can remove resources you may want to keep. Review their effect before running them.

---

# 🔧 Docker Troubleshooting Commands

## 🐧 Linux

```bash
# Check Docker service status
sudo systemctl status docker

# Start Docker service
sudo systemctl start docker

# Restart Docker service
sudo systemctl restart docker

# View Docker service logs
sudo journalctl -u docker -n 100

# Follow Docker logs
sudo journalctl -u docker -f

# Check Docker version
docker version

# Check Docker system information
docker info

# Check disk space
df -h

# Check memory
free -h
```

## 🪟 Windows

```powershell
# Check Docker version
docker version

# Check Docker information
docker info

# Check WSL distributions
wsl --list --verbose

# Update WSL
wsl --update

# Restart WSL
wsl --shutdown
```

## 🐳 Common Docker Issues

| Problem | Possible Solution |
|---|---|
| Docker daemon not running | Start or restart Docker service. |
| Permission denied | Check Docker group permissions or use sudo. |
| Port already allocated | Use another host port. |
| Image not found | Verify image name, tag, and registry. |
| Container exits immediately | Inspect container logs. |
| No space left on device | Check Docker disk usage and unused resources. |
| Container cannot access network | Inspect Docker network configuration. |
| WSL 2 error | Check WSL installation and virtualization settings. |
| Docker build fails | Check Dockerfile instructions and build context. |

---

# 🔄 Docker Backup and Restore

## 📦 Backup Docker Volume

```bash
docker run --rm \
  -v my-volume:/source:ro \
  -v "$PWD":/backup \
  alpine \
  tar -czf /backup/my-volume-backup.tar.gz -C /source .
```

## ♻️ Restore Docker Volume

```bash
docker run --rm \
  -v my-volume:/target \
  -v "$PWD":/backup \
  alpine \
  tar -xzf /backup/my-volume-backup.tar.gz -C /target
```

*For production databases, use database-native backup tools and ensure application consistency before taking backups.*

---

# 🗑️ Docker Uninstallation

## 🐧 Ubuntu / Debian

```bash
# Stop Docker
sudo systemctl stop docker

# Remove Docker packages
sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Remove unused packages
sudo apt autoremove -y
```

## 🐧 Amazon Linux 2023 / RHEL

```bash
# Stop Docker
sudo systemctl stop docker

# Remove Docker packages
sudo dnf remove docker docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

## 🐧 Amazon Linux 2

```bash
sudo service docker stop
sudo yum remove docker -y
```

## 🪟 Windows

Uninstall Docker Desktop through:

```text
Settings → Apps → Installed Apps → Docker Desktop → Uninstall
```

## 🍎 macOS

If installed using Homebrew:

```bash
brew uninstall --cask docker
```

Alternatively, use Docker Desktop's uninstall option.

### ⚠️ Remove Docker Data

Docker data may remain after uninstalling Docker packages.

Linux Docker Engine commonly stores data under:

```text
/var/lib/docker/
/var/lib/containerd/
```

Remove these directories only if you intentionally want to delete all remaining Docker data.

---

# 🛡️ Docker Best Practices

- Use official and trusted base images.
- Prefer specific image tags instead of relying on `latest`.
- Keep Docker Engine and images updated.
- Use multi-stage builds to reduce image size.
- Avoid running containers as root when unnecessary.
- Do not store passwords or API keys inside Dockerfiles.
- Use environment variables or secure secret-management solutions.
- Use Docker volumes for persistent application data.
- Apply resource limits to production containers.
- Scan images for known vulnerabilities.
- Use `.dockerignore` to exclude unnecessary files.
- Avoid exposing unnecessary container ports.
- Regularly clean up unused resources.
- Back up important Docker volumes.

---

# 📚 Official Documentation & Resources

| Resource | Link |
|---|---|
| Docker Official Website | https://www.docker.com/ |
| Docker Documentation | https://docs.docker.com/ |
| Docker Engine Installation | https://docs.docker.com/engine/install/ |
| Docker Desktop Installation | https://docs.docker.com/desktop/ |
| Docker CLI Reference | https://docs.docker.com/reference/cli/docker/ |
| Docker Compose Documentation | https://docs.docker.com/compose/ |
| Dockerfile Reference | https://docs.docker.com/reference/dockerfile/ |
| Docker Hub | https://hub.docker.com/ |
| Docker Build Documentation | https://docs.docker.com/build/ |
| Docker Networking | https://docs.docker.com/engine/network/ |
| Docker Volumes | https://docs.docker.com/engine/storage/volumes/ |
| Docker Security | https://docs.docker.com/engine/security/ |

---

**🐳 Learning Docker | Containerizing Applications | Exploring DevOps & CI/CD**