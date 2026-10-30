# 📊 Prometheus Node Exporter – Installation & Commands Guide

A practical guide to installing, configuring, and managing **Prometheus Node Exporter** on Linux servers. This README covers installation, systemd service configuration, metrics collection, Prometheus integration, security, and troubleshooting. ⚙️🚀

---

## 📌 1. Introduction

Node Exporter is a Prometheus exporter that collects hardware and operating system metrics from Linux machines and exposes them through an HTTP endpoint.

- **Tool:** Prometheus Node Exporter
- **Developer:** Prometheus Community
- **Language:** Go
- **Default Port:** 9100
- **Default Metrics Endpoint:** `/metrics`
- **Protocol:** HTTP
- **Primary Purpose:** Linux Server Monitoring

## 🧩 2. Metrics Collected by Node Exporter

| Metric Category | Description |
|---|---|
| CPU | CPU utilization and time |
| Memory | RAM usage and availability |
| Disk | Disk space and filesystem usage |
| Network | Network traffic and interface statistics |
| System Load | System load averages |
| Filesystem | Filesystem capacity and availability |
| Disk I/O | Disk read and write operations |
| System Information | Host and operating system details |

## 🏗️ 3. Monitoring Architecture

Node Exporter exposes system metrics, while Prometheus periodically scrapes the metrics endpoint and stores the collected data.

```text
       Linux Server / EC2
              |
              |
       Node Exporter
          Port 9100
              |
              | HTTP /metrics
              |
          Prometheus
          Port 9090
              |
              |
           Grafana
          Port 3000
```

---

## 💻 4. Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | Binary / systemd |
| Amazon Linux 2023 | Binary / systemd |
| Ubuntu | Binary / systemd |
| RHEL | Binary / systemd |
| Windows | Windows Exporter |
| macOS | Node Exporter binary |

**Note:** Node Exporter is primarily intended for Unix-like systems. For Windows server monitoring, use Prometheus Windows Exporter.

---

## 📦 5. Package Management Commands

### 🔍 Search Available Packages

```bash
# Amazon Linux 2 / RHEL
yum search node_exporter

# Amazon Linux 2023
dnf search node_exporter

# Ubuntu
apt search prometheus-node-exporter
```

### 📋 Check Installed Packages

```bash
# YUM
yum list installed | grep -i node-exporter

# DNF
dnf list installed | grep -i node-exporter

# APT
apt list --installed | grep prometheus-node-exporter
```

### ℹ️ Package Information

```bash
# YUM
yum info golang-github-prometheus-node-exporter

# DNF
dnf info golang-github-prometheus-node-exporter

# APT
apt show prometheus-node-exporter
```

> Package availability and package names depend on the configured repositories. The binary installation method below provides a consistent approach across Linux distributions.

---

## 🐧 6. Install Node Exporter on Amazon Linux 2

### 🔄 Step 1: Update System

```bash
sudo yum update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo yum install -y wget tar
```

### 📥 Step 3: Download Node Exporter

```bash
VERSION="1.12.1"

wget https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📦 Step 4: Extract Archive

```bash
tar -xvf node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📁 Step 5: Move Binary

```bash
sudo mv node_exporter-${VERSION}.linux-amd64/node_exporter /usr/local/bin/
```

### 👤 Step 6: Create System User

```bash
sudo useradd --system --no-create-home --shell /sbin/nologin node_exporter
```

### ⚙️ Step 7: Create systemd Service

```bash
sudo vi /etc/systemd/system/node_exporter.service
```

Add the following configuration:

```ini
[Unit]
Description=Prometheus Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

### 🔄 Step 8: Reload systemd

```bash
sudo systemctl daemon-reload
```

### ▶️ Step 9: Start Node Exporter

```bash
sudo systemctl enable --now node_exporter
```

### 🔍 Step 10: Verify Installation

```bash
node_exporter --version

sudo systemctl status node_exporter
```

---

## 🐧 7. Install Node Exporter on Amazon Linux 2023

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo dnf install -y wget tar
```

### 📥 Step 3: Download Node Exporter

```bash
VERSION="1.12.1"

wget https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📦 Step 4: Extract Archive

```bash
tar -xvf node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📁 Step 5: Install Binary

```bash
sudo mv node_exporter-${VERSION}.linux-amd64/node_exporter /usr/local/bin/
```

### 👤 Step 6: Create System User

```bash
sudo useradd --system --no-create-home --shell /sbin/nologin node_exporter
```

### ⚙️ Step 7: Configure systemd

```bash
sudo vi /etc/systemd/system/node_exporter.service
```

```ini
[Unit]
Description=Prometheus Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

### ▶️ Step 8: Enable and Start Service

```bash
sudo systemctl daemon-reload

sudo systemctl enable --now node_exporter
```

### 🔍 Step 9: Verify

```bash
node_exporter --version

sudo systemctl status node_exporter
```

---

## 🐧 8. Install Node Exporter on Ubuntu

### 🔄 Step 1: Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo apt install -y wget tar
```

### 📥 Step 3: Download Node Exporter

```bash
VERSION="1.12.1"

wget https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📦 Step 4: Extract Archive

```bash
tar -xvf node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📁 Step 5: Move Binary

```bash
sudo mv node_exporter-${VERSION}.linux-amd64/node_exporter /usr/local/bin/
```

### 👤 Step 6: Create System User

```bash
sudo useradd --system --no-create-home --shell /usr/sbin/nologin node_exporter
```

### ⚙️ Step 7: Create systemd Service

```bash
sudo vi /etc/systemd/system/node_exporter.service
```

```ini
[Unit]
Description=Prometheus Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

### ▶️ Step 8: Start Service

```bash
sudo systemctl daemon-reload

sudo systemctl enable --now node_exporter
```

### 🔍 Step 9: Verify

```bash
node_exporter --version

sudo systemctl status node_exporter
```

---

## 🐧 9. Install Node Exporter on RHEL

### 🔄 Step 1: Update System

```bash
sudo dnf update -y
```

### 🛠️ Step 2: Install Required Packages

```bash
sudo dnf install -y wget tar
```

### 📥 Step 3: Download Node Exporter

```bash
VERSION="1.12.1"

wget https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📦 Step 4: Extract Archive

```bash
tar -xvf node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📁 Step 5: Install Binary

```bash
sudo mv node_exporter-${VERSION}.linux-amd64/node_exporter /usr/local/bin/
```

### 👤 Step 6: Create System User

```bash
sudo useradd --system --no-create-home --shell /sbin/nologin node_exporter
```

### ⚙️ Step 7: Configure systemd

```bash
sudo vi /etc/systemd/system/node_exporter.service
```

```ini
[Unit]
Description=Prometheus Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

### ▶️ Step 8: Start Service

```bash
sudo systemctl daemon-reload

sudo systemctl enable --now node_exporter
```

### 🔍 Step 9: Verify

```bash
node_exporter --version

sudo systemctl status node_exporter
```

---

## 🔄 10. Generic Linux Installation for Different Architectures

The previous installation examples use Linux AMD64. For ARM-based servers, download the ARM64 binary instead.

### 🔍 Detect Architecture

```bash
uname -m
```

### 📥 Download Based on Architecture

```bash
VERSION="1.12.1"

case "$(uname -m)" in
  x86_64)
    ARCH="amd64"
    ;;
  aarch64)
    ARCH="arm64"
    ;;
  *)
    echo "Unsupported architecture"
    exit 1
    ;;
esac

wget https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-${ARCH}.tar.gz
```

### 📦 Extract and Install

```bash
tar -xvf node_exporter-${VERSION}.linux-${ARCH}.tar.gz

sudo mv node_exporter-${VERSION}.linux-${ARCH}/node_exporter /usr/local/bin/
```

Create the service user and systemd service using the configuration shown in the previous sections.

---

## ⚙️ 11. Node Exporter Service Commands

### ▶️ Start Service

```bash
sudo systemctl start node_exporter
```

### ⏹️ Stop Service

```bash
sudo systemctl stop node_exporter
```

### 🔄 Restart Service

```bash
sudo systemctl restart node_exporter
```

### 🔁 Reload systemd

```bash
sudo systemctl daemon-reload
```

### 🔌 Enable Service at Boot

```bash
sudo systemctl enable node_exporter
```

### 🚫 Disable Service at Boot

```bash
sudo systemctl disable node_exporter
```

### 📊 Check Service Status

```bash
sudo systemctl status node_exporter
```

### 📜 View Service Logs

```bash
sudo journalctl -u node_exporter
```

### 📜 Follow Live Logs

```bash
sudo journalctl -u node_exporter -f
```

---

## 🌐 12. Verify Node Exporter Metrics

Node Exporter listens on port `9100` by default.

### 🔍 Check Listening Port

```bash
sudo ss -tulnp | grep 9100
```

### 📊 Check Metrics Endpoint

```bash
curl http://localhost:9100/metrics
```

### 🔎 Display Only Node Metrics

```bash
curl -s http://localhost:9100/metrics | grep '^node_'
```

### 🔍 Check Specific Metrics

```bash
# CPU metrics
curl -s localhost:9100/metrics | grep node_cpu

# Memory metrics
curl -s localhost:9100/metrics | grep node_memory

# Filesystem metrics
curl -s localhost:9100/metrics | grep node_filesystem

# Network metrics
curl -s localhost:9100/metrics | grep node_network
```

### 🌍 Access from Browser

```text
http://<SERVER_PUBLIC_IP>:9100/metrics
```

For remote access, configure network access securely rather than exposing this endpoint publicly.

---

## 🔥 13. Configure Firewall and AWS Security Group

Node Exporter uses TCP port `9100` by default.

### 🐧 Ubuntu UFW

```bash
sudo ufw allow from <PROMETHEUS_SERVER_IP> to any port 9100 proto tcp
```

### 🐧 RHEL / Amazon Linux firewalld

```bash
sudo firewall-cmd --permanent \
  --add-rich-rule='rule family="ipv4" source address="<PROMETHEUS_SERVER_IP>/32" port port="9100" protocol="tcp" accept'

sudo firewall-cmd --reload
```

### ☁️ AWS Security Group

For an EC2 instance running Node Exporter:

| Setting | Value |
|---|---|
| Type | Custom TCP |
| Protocol | TCP |
| Port Range | 9100 |
| Source | Prometheus Server Security Group |
| Description | Prometheus Node Exporter Metrics |

**Security recommendation:** Never allow port `9100` from `0.0.0.0/0` in a production environment. Allow access only from the Prometheus server or trusted monitoring network.

---

## 📊 14. Configure Prometheus to Scrape Node Exporter

After installing Node Exporter, configure Prometheus to collect its metrics.

### 📄 Edit prometheus.yml

```bash
sudo vi /etc/prometheus/prometheus.yml
```

### 📝 Add Scrape Configuration

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: "node_exporter"
    static_configs:
      - targets:
          - "localhost:9100"
```

If Prometheus is running on a different server, replace `localhost` with the Node Exporter server's private IP address:

```yaml
scrape_configs:
  - job_name: "node_exporter"
    static_configs:
      - targets:
          - "10.0.1.25:9100"
```

### 🔄 Restart Prometheus

```bash
sudo systemctl restart prometheus
```

### 🔍 Check Prometheus Status

```bash
sudo systemctl status prometheus
```

### 🌐 Verify Target Status

Open the Prometheus Targets page:

```text
http://<PROMETHEUS_SERVER_IP>:9090/targets
```

The Node Exporter target should show:

```text
State: UP
```

---

## 📈 15. Useful Prometheus Queries for Node Exporter

### 🖥️ CPU Usage

```promql
100 - (avg by (instance) (
  rate(node_cpu_seconds_total{mode="idle"}[5m])
) * 100)
```

### 🧠 Memory Usage Percentage

```promql
100 * (
  1 - node_memory_MemAvailable_bytes /
  node_memory_MemTotal_bytes
)
```

### 💾 Disk Usage Percentage

```promql
100 * (
  1 -
  node_filesystem_avail_bytes{
    mountpoint="/",
    fstype!~"tmpfs|overlay"
  } /
  node_filesystem_size_bytes{
    mountpoint="/",
    fstype!~"tmpfs|overlay"
  }
)
```

### 🌐 Network Received Traffic

```promql
rate(node_network_receive_bytes_total[5m])
```

### 🌐 Network Transmitted Traffic

```promql
rate(node_network_transmit_bytes_total[5m])
```

### 📊 System Load Average

```promql
node_load1
```

### 💽 Available Filesystem Space

```promql
node_filesystem_avail_bytes
```

---

## ⚙️ 16. Node Exporter Collectors

Collectors determine which metrics Node Exporter exposes.

### 🔍 Display Available Options

```bash
node_exporter --help
```

### ▶️ Enable a Specific Collector

```bash
node_exporter --collector.textfile
```

### 🚫 Disable a Collector

```bash
node_exporter --no-collector.wifi
```

### 📁 Enable Textfile Collector

Create a directory:

```bash
sudo mkdir -p /var/lib/node_exporter/textfile_collector
```

Update the systemd service:

```ini
ExecStart=/usr/local/bin/node_exporter --collector.textfile.directory=/var/lib/node_exporter/textfile_collector
```

Reload and restart:

```bash
sudo systemctl daemon-reload
sudo systemctl restart node_exporter
```

### 📝 Create a Custom Metric

```bash
echo 'custom_backup_status 1' | \
sudo tee /var/lib/node_exporter/textfile_collector/backup.prom
```

Check the metric:

```bash
curl -s localhost:9100/metrics | grep custom_backup_status
```

---

## 🔄 17. Update Node Exporter

### 📌 Check Current Version

```bash
node_exporter --version
```

### 📥 Download New Version

Replace the version below with the desired release:

```bash
VERSION="1.12.1"

wget https://github.com/prometheus/node_exporter/releases/download/v${VERSION}/node_exporter-${VERSION}.linux-amd64.tar.gz
```

### 📦 Extract Archive

```bash
tar -xvf node_exporter-${VERSION}.linux-amd64.tar.gz
```

### ⏹️ Stop Service

```bash
sudo systemctl stop node_exporter
```

### 🔄 Replace Binary

```bash
sudo mv node_exporter-${VERSION}.linux-amd64/node_exporter /usr/local/bin/node_exporter
```

### ▶️ Restart Service

```bash
sudo systemctl daemon-reload
sudo systemctl start node_exporter
```

### 🔍 Verify Updated Version

```bash
node_exporter --version

sudo systemctl status node_exporter
```

---

## 🐳 18. Run Node Exporter Using Docker

Node Exporter monitors the host system. Running it in a container requires access to the host's namespaces and filesystem.

### 📥 Pull Image

```bash
docker pull prom/node-exporter:latest
```

### ▶️ Run Container

```bash
docker run -d \
  --name node-exporter \
  --restart unless-stopped \
  --net="host" \
  --pid="host" \
  -v "/:/host:ro,rslave" \
  prom/node-exporter:latest \
  --path.rootfs=/host
```

### 🔍 Verify Container

```bash
docker ps
```

### 📊 Check Metrics

```bash
curl http://localhost:9100/metrics
```

### ⏹️ Stop Container

```bash
docker stop node-exporter
```

### 🗑️ Remove Container

```bash
docker rm node-exporter
```

---

## 🪟 19. Windows Monitoring Alternative

For Windows servers, use **Prometheus Windows Exporter** instead of Node Exporter.

### 📦 Install Using winget

```powershell
winget install -e --id PrometheusCommunity.WindowsExporter
```

### 🔍 Verify Service

```powershell
Get-Service windows_exporter
```

### ▶️ Start Service

```powershell
Start-Service windows_exporter
```

### 🔍 Check Metrics

Windows Exporter commonly exposes metrics on port `9182`.

```powershell
Invoke-WebRequest http://localhost:9182/metrics
```

---

## 🧰 20. Troubleshooting Commands

### ❌ Service Not Starting

```bash
sudo systemctl status node_exporter

sudo journalctl -u node_exporter -xe
```

### ❌ Port 9100 Already in Use

```bash
sudo ss -tulnp | grep 9100
```

### ❌ Check Binary Permissions

```bash
ls -l /usr/local/bin/node_exporter
```

### ❌ Test Local Endpoint

```bash
curl -v http://localhost:9100/metrics
```

### ❌ Check Remote Connectivity

```bash
curl -v http://<NODE_EXPORTER_PRIVATE_IP>:9100/metrics
```

### ❌ Check Firewall Rules

```bash
# Ubuntu
sudo ufw status

# RHEL / Amazon Linux
sudo firewall-cmd --list-all
```

### ❌ Check Prometheus Target

```text
http://<PROMETHEUS_SERVER_IP>:9090/targets
```

---

## 🧹 21. Uninstall Node Exporter

### ⏹️ Stop and Disable Service

```bash
sudo systemctl stop node_exporter

sudo systemctl disable node_exporter
```

### 🗑️ Remove systemd Service

```bash
sudo rm -f /etc/systemd/system/node_exporter.service

sudo systemctl daemon-reload
```

### 🗑️ Remove Binary

```bash
sudo rm -f /usr/local/bin/node_exporter
```

### 👤 Remove System User

```bash
sudo userdel node_exporter
```

### 🔍 Verify Removal

```bash
systemctl status node_exporter
```

---

## 🛡️ 22. Best Practices

- Run Node Exporter using a dedicated non-login system user.
- Keep Node Exporter updated.
- Restrict port `9100` to trusted monitoring systems.
- Avoid exposing the metrics endpoint directly to the public internet.
- Use Prometheus to scrape metrics at an appropriate interval.
- Monitor CPU, memory, disk, and network metrics.
- Configure alerts for important infrastructure metrics.
- Use TLS and authentication where required for remote or untrusted networks.
- Verify that Node Exporter targets remain `UP` in Prometheus.

---

## 📚 23. Official Documentation

- [Prometheus Node Exporter](https://github.com/prometheus/node_exporter)
- [Node Exporter Installation Guide](https://prometheus.io/docs/guides/node-exporter/)
- [Prometheus Downloads](https://prometheus.io/download/)
- [Node Exporter Releases](https://github.com/prometheus/node_exporter/releases)
- [Prometheus Configuration](https://prometheus.io/docs/prometheus/latest/configuration/configuration/)
- [Prometheus Querying](https://prometheus.io/docs/prometheus/latest/querying/basics/)

---

**🚀 Monitor • Collect • Analyze • Optimize**