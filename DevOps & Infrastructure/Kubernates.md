# ☸️ Kubernetes – Installation & Commands Guide

A practical guide to installing, configuring, and managing **Kubernetes** across different operating systems. This README covers Kubernetes tools, cluster setup, kubectl commands, Pods, Deployments, Services, ConfigMaps, Secrets, Namespaces, and commonly used administration commands. ⚙️🚀

---

## 📌 1. Introduction

Kubernetes (K8s) is an open-source container orchestration platform used to deploy, scale, manage, and monitor containerized applications.

- **Tool:** Kubernetes
- **Developed By:** Google (originally), now maintained by CNCF
- **Configuration Language:** YAML
- **Container Runtime:** containerd, CRI-O
- **CLI:** kubectl
- **Cluster Setup Tool:** kubeadm
- **Primary Purpose:** Container Orchestration

## 🧩 2. Kubernetes Components

### 🎛️ Control Plane Components

| Component | Description |
|---|---|
| API Server | Entry point for Kubernetes API requests |
| etcd | Stores cluster data and configuration |
| Scheduler | Assigns Pods to suitable Nodes |
| Controller Manager | Maintains the desired cluster state |
| Cloud Controller Manager | Integrates Kubernetes with cloud providers |

### 🖥️ Worker Node Components

| Component | Description |
|---|---|
| Kubelet | Ensures containers are running inside Pods |
| Kube-proxy | Handles network rules and Service traffic |
| Container Runtime | Runs containers, such as containerd or CRI-O |

### 🛠️ Kubernetes Tools

| Tool | Purpose |
|---|---|
| kubectl | Communicates with Kubernetes clusters |
| kubeadm | Bootstraps Kubernetes clusters |
| kubelet | Runs on cluster nodes |
| Minikube | Runs a local Kubernetes cluster |
| KIND | Runs Kubernetes clusters using containers |
| Helm | Manages Kubernetes applications using charts |

## 💻 3. Supported Operating Systems

| Operating System | Installation Method |
|---|---|
| Amazon Linux 2 | Manual / legacy RPM setup |
| Amazon Linux 2023 | DNF / RPM repository |
| Ubuntu | APT repository |
| RHEL | DNF / RPM repository |
| Windows | winget / Chocolatey / WSL2 |
| macOS | Homebrew |

**Important:** `kubectl` can be installed on Windows and macOS. Kubernetes cluster nodes using kubeadm require Linux. For local learning, Minikube and KIND are convenient options.

---

## 📦 4. Package Management Commands

### 🔍 Search Available Packages

```bash
# Amazon Linux 2 / RHEL
yum search kubectl

# Amazon Linux 2023
dnf search kubectl

# Ubuntu
apt search kubectl
```

### 📋 List Available Packages

```bash
# YUM
yum list available | grep -E 'kubectl|kubeadm|kubelet'

# DNF
dnf list available | grep -E 'kubectl|kubeadm|kubelet'

# APT
apt list kubectl kubeadm kubelet
```

### 📥 Check Installed Packages

```bash
# YUM
yum list installed | grep -E 'kubectl|kubeadm|kubelet'

# DNF
dnf list installed | grep -E 'kubectl|kubeadm|kubelet'

# APT
apt list --installed | grep -E 'kubectl|kubeadm|kubelet'
```

### ℹ️ Package Information

```bash
# YUM
yum info kubectl

# DNF
dnf info kubectl

# APT
apt show kubectl
```

---

## 🐧 5. Install kubectl on Amazon Linux 2

`kubectl` is the command-line tool used to communicate with a Kubernetes cluster.

### 🔄 Update System

```bash
sudo yum update -y
```

### 📥 Download kubectl

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

### 🔐 Install kubectl

```bash
chmod +x kubectl
sudo mv kubectl /usr/local/bin/kubectl
```

### 🔍 Verify Installation

```bash
kubectl version --client
```

> Amazon Linux 2 is a legacy platform. Check its support status and compatibility before using it for a new Kubernetes cluster. Prefer a currently supported Linux distribution for cluster nodes.

---

## 🐧 6. Install Kubernetes Tools on Amazon Linux 2023

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🔗 Add Kubernetes Repository

The following example uses the Kubernetes v1.37 package repository.

```bash
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.37/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.37/rpm/repodata/repomd.xml.key
exclude=kubelet kubeadm kubectl cri-tools kubernetes-cni
EOF
```

### 📥 Install Kubernetes Tools

```bash
sudo dnf install -y kubelet kubeadm kubectl --disableexcludes=kubernetes
```

### ▶️ Enable kubelet

```bash
sudo systemctl enable --now kubelet
```

### 🔍 Verify Installation

```bash
kubeadm version
kubelet --version
kubectl version --client
```

---

## 🐧 7. Install Kubernetes Tools on Ubuntu

### 🔄 Update System

```bash
sudo apt update
sudo apt upgrade -y
```

### 🛠️ Install Required Packages

```bash
sudo apt install -y apt-transport-https ca-certificates curl gpg
```

### 📁 Create Keyring Directory

```bash
sudo mkdir -p -m 755 /etc/apt/keyrings
```

### 🔐 Add Kubernetes Repository Key

```bash
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.37/deb/Release.key | \
sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg
```

### 🔗 Add Kubernetes Repository

```bash
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.37/deb/ /' | \
sudo tee /etc/apt/sources.list.d/kubernetes.list
```

### 📥 Install Kubernetes Tools

```bash
sudo apt update
sudo apt install -y kubelet kubeadm kubectl
```

### 🔒 Hold Kubernetes Packages

```bash
sudo apt-mark hold kubelet kubeadm kubectl
```

### ▶️ Enable kubelet

```bash
sudo systemctl enable --now kubelet
```

### 🔍 Verify Installation

```bash
kubeadm version
kubelet --version
kubectl version --client
```

---

## 🐧 8. Install Kubernetes Tools on RHEL

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🔗 Add Kubernetes Repository

```bash
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.37/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.37/rpm/repodata/repomd.xml.key
exclude=kubelet kubeadm kubectl cri-tools kubernetes-cni
EOF
```

### 📥 Install Kubernetes Tools

```bash
sudo dnf install -y kubelet kubeadm kubectl --disableexcludes=kubernetes
```

### ▶️ Enable kubelet

```bash
sudo systemctl enable --now kubelet
```

### 🔍 Verify Installation

```bash
kubeadm version
kubelet --version
kubectl version --client
```

---

## 🪟 9. Install Kubernetes Tools on Windows

For Windows, you can install `kubectl` directly. To run a local Kubernetes cluster, use Docker Desktop, Minikube, or KIND with the required container environment.

### 📦 Method 1: Using winget

Open PowerShell:

```powershell
winget install -e --id Kubernetes.kubectl
```

### 📦 Method 2: Using Chocolatey

```powershell
choco install kubernetes-cli -y
```

### 🔍 Verify Installation

```powershell
kubectl version --client
```

### 🐧 Method 3: Using WSL2

```powershell
wsl --install
```

Inside Ubuntu:

```bash
sudo apt update
sudo apt install -y curl
```

Follow the Ubuntu kubectl installation instructions in Section 7 if you only need the Kubernetes CLI.

---

## 🍎 10. Install Kubernetes Tools on macOS

### 📦 Install kubectl Using Homebrew

```bash
brew update
brew install kubectl
```

### 🔍 Verify Installation

```bash
kubectl version --client
```

### 📦 Install Minikube

```bash
brew install minikube
```

### 🔍 Verify Minikube

```bash
minikube version
```

---

## 🧰 11. Kubernetes CLI Commands

### 📌 Version Information

```bash
# Kubernetes client version
kubectl version --client

# Kubernetes cluster version
kubectl version

# Client version in YAML format
kubectl version --client -o yaml

# Display cluster information
kubectl cluster-info
```

### 📋 Cluster Information

```bash
# Display cluster nodes
kubectl get nodes

# Display all namespaces
kubectl get namespaces

# Display cluster components
kubectl get componentstatuses

# Display cluster information
kubectl cluster-info
```

> `kubectl get componentstatuses` is deprecated in modern Kubernetes releases. Prefer `kubectl get nodes` and `kubectl cluster-info` for basic checks.

---

## 🖥️ 12. Node Management Commands

Nodes are the machines that run Kubernetes workloads.

```bash
# List all nodes
kubectl get nodes

# Display detailed node information
kubectl get nodes -o wide

# Describe a specific node
kubectl describe node <NODE_NAME>

# Display nodes in YAML
kubectl get nodes -o yaml

# Display node labels
kubectl get nodes --show-labels

# Add a label to a node
kubectl label nodes <NODE_NAME> environment=production

# Remove a node label
kubectl label nodes <NODE_NAME> environment-

# Mark node as unschedulable
kubectl cordon <NODE_NAME>

# Allow scheduling on node
kubectl uncordon <NODE_NAME>

# Drain node before maintenance
kubectl drain <NODE_NAME> --ignore-daemonsets
```

---

## 📦 13. Pod Management Commands

Pods are the smallest deployable units in Kubernetes.

```bash
# List Pods
kubectl get pods

# List Pods in all namespaces
kubectl get pods -A

# Display detailed Pod information
kubectl get pods -o wide

# Describe a Pod
kubectl describe pod <POD_NAME>

# Create a Pod
kubectl run nginx --image=nginx

# Delete a Pod
kubectl delete pod <POD_NAME>

# Display Pod YAML
kubectl get pod <POD_NAME> -o yaml

# Watch Pod status
kubectl get pods -w

# Display Pod logs
kubectl logs <POD_NAME>

# Follow Pod logs
kubectl logs -f <POD_NAME>

# Execute command inside a Pod
kubectl exec -it <POD_NAME> -- /bin/sh
```

---

## 🚀 14. Deployment Management Commands

Deployments manage application replicas and rolling updates.

```bash
# Create Deployment
kubectl create deployment nginx --image=nginx

# List Deployments
kubectl get deployments

# Describe Deployment
kubectl describe deployment nginx

# Scale Deployment
kubectl scale deployment nginx --replicas=3

# Update Deployment image
kubectl set image deployment/nginx nginx=nginx:latest

# Check rollout status
kubectl rollout status deployment/nginx

# Display rollout history
kubectl rollout history deployment/nginx

# Undo the last rollout
kubectl rollout undo deployment/nginx

# Restart Deployment
kubectl rollout restart deployment/nginx

# Delete Deployment
kubectl delete deployment nginx
```

---

## 🌐 15. Service Management Commands

Services expose applications running inside Pods.

### 📌 Service Types

| Service Type | Purpose |
|---|---|
| ClusterIP | Internal cluster communication |
| NodePort | Exposes service through a node port |
| LoadBalancer | Exposes service using an external load balancer |
| ExternalName | Maps a service to an external DNS name |

### 🔧 Service Commands

```bash
# List Services
kubectl get services

# List Services in all namespaces
kubectl get services -A

# Create ClusterIP Service
kubectl expose deployment nginx --port=80 --type=ClusterIP

# Create NodePort Service
kubectl expose deployment nginx --port=80 --type=NodePort

# Create LoadBalancer Service
kubectl expose deployment nginx --port=80 --type=LoadBalancer

# Describe Service
kubectl describe service nginx

# Delete Service
kubectl delete service nginx
```

---

## 🗂️ 16. Namespace Management Commands

Namespaces logically separate resources inside a cluster.

```bash
# List Namespaces
kubectl get namespaces

# Create Namespace
kubectl create namespace dev

# Create another Namespace
kubectl create namespace production

# Display resources in a Namespace
kubectl get all -n dev

# Describe Namespace
kubectl describe namespace dev

# Delete Namespace
kubectl delete namespace dev

# Set default Namespace for current context
kubectl config set-context --current --namespace=dev
```

---

## ⚙️ 17. ConfigMap Commands

ConfigMaps store non-sensitive configuration data.

```bash
# Create ConfigMap from literal values
kubectl create configmap app-config \
  --from-literal=APP_ENV=production

# Create ConfigMap from a file
kubectl create configmap app-config \
  --from-file=config.properties

# List ConfigMaps
kubectl get configmaps

# Describe ConfigMap
kubectl describe configmap app-config

# Display ConfigMap YAML
kubectl get configmap app-config -o yaml

# Delete ConfigMap
kubectl delete configmap app-config
```

---

## 🔐 18. Secret Management Commands

Secrets store sensitive information such as passwords and tokens.

```bash
# Create Secret from literal values
kubectl create secret generic db-secret \
  --from-literal=username=admin \
  --from-literal=password='change-this-password'

# Create Secret from a file
kubectl create secret generic app-secret \
  --from-file=credentials.txt

# List Secrets
kubectl get secrets

# Describe Secret
kubectl describe secret db-secret

# Display Secret YAML
kubectl get secret db-secret -o yaml

# Delete Secret
kubectl delete secret db-secret
```

> Kubernetes Secret data is base64-encoded, not automatically encrypted. Configure encryption at rest and appropriate RBAC permissions for production environments.

---

## 📄 19. YAML Configuration Commands

Kubernetes resources can be created and managed through YAML files.

### 📝 Example: pod.yaml

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

### 📝 Example: deployment.yaml

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

### 📝 Example: service.yaml

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30080
```

### ▶️ Apply YAML Configuration

```bash
# Create or update resources
kubectl apply -f pod.yaml

# Apply Deployment
kubectl apply -f deployment.yaml

# Apply Service
kubectl apply -f service.yaml

# Apply all YAML files in a directory
kubectl apply -f ./manifests/

# Delete resources defined in YAML
kubectl delete -f deployment.yaml
```

### 🔍 Validate and Inspect

```bash
# Validate without sending changes to the API server
kubectl apply --dry-run=client -f deployment.yaml

# Server-side dry run
kubectl apply --dry-run=server -f deployment.yaml

# Display resource YAML
kubectl get deployment nginx-deployment -o yaml
```

---

## 📊 20. Monitoring and Troubleshooting Commands

```bash
# Display all resources in current Namespace
kubectl get all

# Display events
kubectl get events

# Display events sorted by time
kubectl get events --sort-by=.metadata.creationTimestamp

# Describe Pod
kubectl describe pod <POD_NAME>

# Display Pod logs
kubectl logs <POD_NAME>

# Display logs from previous container instance
kubectl logs <POD_NAME> --previous

# Display resource usage
kubectl top nodes

# Display Pod resource usage
kubectl top pods

# Display resource usage in all Namespaces
kubectl top pods -A

# Explain a Kubernetes resource
kubectl explain deployment

# Explain a specific resource field
kubectl explain deployment.spec
```

> `kubectl top` requires Metrics Server to be installed and working in the cluster.

---

## 🔑 21. Kubernetes Context Management

A context identifies the cluster, user, and Namespace used by kubectl.

```bash
# Display current context
kubectl config current-context

# List all contexts
kubectl config get-contexts

# Display current configuration
kubectl config view

# Switch context
kubectl config use-context <CONTEXT_NAME>

# Set default Namespace
kubectl config set-context --current --namespace=dev

# Delete a context
kubectl config delete-context <CONTEXT_NAME>
```

---

## 📦 22. Helm Commands

Helm is a package manager for Kubernetes.

### 📥 Install Helm

**Ubuntu / Linux using the official installation script:**

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

### 🍎 macOS

```bash
brew install helm
```

### 🪟 Windows

```powershell
winget install Helm.Helm
```

### 🔍 Verify Installation

```bash
helm version
```

### ⚙️ Common Helm Commands

```bash
# Add a Helm repository
helm repo add bitnami https://charts.bitnami.com/bitnami

# Update repositories
helm repo update

# Search charts
helm search repo nginx

# List installed releases
helm list

# Install a chart
helm install my-nginx bitnami/nginx

# Upgrade a release
helm upgrade my-nginx bitnami/nginx

# Display release status
helm status my-nginx

# Uninstall a release
helm uninstall my-nginx
```

---

## 🏠 23. Install Minikube for Local Kubernetes

Minikube creates a local Kubernetes cluster for learning and development.

### 🐧 Linux Installation

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### 🪟 Windows Installation

```powershell
winget install Kubernetes.minikube
```

### 🍎 macOS Installation

```bash
brew install minikube
```

### 🔍 Verify Installation

```bash
minikube version
```

### 🚀 Start Minikube Cluster

```bash
minikube start
```

### 📊 Cluster Commands

```bash
# Check cluster status
minikube status

# Display cluster information
kubectl cluster-info

# List nodes
kubectl get nodes

# Open Kubernetes dashboard
minikube dashboard

# Stop cluster
minikube stop

# Delete cluster
minikube delete
```

### 📦 Deploy Nginx on Minikube

```bash
kubectl create deployment nginx --image=nginx

kubectl expose deployment nginx --type=NodePort --port=80

minikube service nginx
```

---

## 🧪 24. Install KIND (Kubernetes IN Docker)

KIND runs local Kubernetes clusters using Docker or Podman containers.

### 📥 Linux Installation

```bash
[ "$(uname -m)" = "x86_64" ] && ARCH=amd64
[ "$(uname -m)" = "aarch64" ] && ARCH=arm64

curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-${ARCH}

chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### 🍎 macOS

```bash
brew install kind
```

### 🪟 Windows

```powershell
winget install Kubernetes.kind
```

### 🔍 Verify Installation

```bash
kind version
```

### 🚀 Create Cluster

```bash
kind create cluster --name dev-cluster
```

### 📊 Cluster Commands

```bash
# List clusters
kind get clusters

# Display cluster nodes
kubectl get nodes

# Delete cluster
kind delete cluster --name dev-cluster
```

---

## 🏗️ 25. Bootstrap a Kubernetes Cluster Using kubeadm

`kubeadm` helps initialize a Kubernetes cluster with a Control Plane and Worker Nodes.

**Prerequisites:**

- Linux machines for Control Plane and Worker Nodes.
- A compatible container runtime, such as containerd.
- Network connectivity between cluster nodes.
- Unique hostname, MAC address, and product UUID for each node.
- Required ports and firewall rules configured.
- Swap disabled or appropriately configured.
- Compatible versions of kubeadm, kubelet, and kubectl.

### 🔄 Step 1: Disable Swap

Run on every node:

```bash
sudo swapoff -a
```

To disable swap persistently, edit `/etc/fstab` and comment out the swap entry.

### ⚙️ Step 2: Configure Kernel Modules

```bash
sudo modprobe overlay
sudo modprobe br_netfilter
```

Load the modules automatically after reboot:

```bash
cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
overlay
br_netfilter
EOF
```

### 🌐 Step 3: Configure Network Parameters

```bash
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-iptables = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.ipv4.ip_forward = 1
EOF
```

Apply the configuration:

```bash
sudo sysctl --system
```

### 📦 Step 4: Install and Configure Container Runtime

Install a compatible container runtime such as containerd on every node.

Configure containerd to use systemd cgroups:

```bash
sudo mkdir -p /etc/containerd

containerd config default | \
sudo tee /etc/containerd/config.toml
```

In `/etc/containerd/config.toml`, configure:

```toml
SystemdCgroup = true
```

Ensure the setting is under the appropriate `runc.options` section.

Restart containerd:

```bash
sudo systemctl restart containerd
sudo systemctl enable containerd
```

### ▶️ Step 5: Enable kubelet

```bash
sudo systemctl enable --now kubelet
```

### 🚀 Step 6: Initialize Control Plane

Run only on the Control Plane node:

```bash
sudo kubeadm init --pod-network-cidr=10.244.0.0/16
```

The command prints a `kubeadm join` command. Save it securely because Worker Nodes will use it to join the cluster.

### 🔐 Step 7: Configure kubectl

Run on the Control Plane node:

```bash
mkdir -p $HOME/.kube

sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

### 🌐 Step 8: Install Pod Network (CNI)

Example using Flannel:

```bash
kubectl apply -f https://github.com/flannel-io/flannel/releases/latest/download/kube-flannel.yml
```

Ensure the CNI configuration and Pod CIDR are compatible.

### 🔗 Step 9: Join Worker Nodes

Run the `kubeadm join` command generated during `kubeadm init` on each Worker Node.

Example format:

```bash
sudo kubeadm join <CONTROL_PLANE_IP>:6443 \
  --token <TOKEN> \
  --discovery-token-ca-cert-hash sha256:<HASH>
```

### 🔍 Step 10: Verify Cluster

On the Control Plane:

```bash
kubectl get nodes

kubectl get pods -A

kubectl cluster-info
```

---

## 🔄 26. Kubernetes Upgrade Commands

Kubernetes upgrades require a controlled version-by-version process.

```bash
# Check kubeadm version
kubeadm version

# Check current cluster version
kubectl version

# Check node versions
kubectl get nodes

# Check available kubeadm upgrade plans
sudo kubeadm upgrade plan
```

Upgrade kubeadm, kubelet, and kubectl using the official upgrade procedure for your Linux distribution and target Kubernetes minor version.

> Do not blindly run a normal system package upgrade for Kubernetes components. Follow the official kubeadm upgrade guide and respect Kubernetes version-skew policies.

---

## 🧹 27. Reset and Uninstall Kubernetes

### 🔄 Reset kubeadm Node

```bash
sudo kubeadm reset -f
```

### 🧹 Remove kubeconfig

```bash
rm -rf $HOME/.kube
```

### 📦 Ubuntu

```bash
sudo apt-mark unhold kubelet kubeadm kubectl

sudo apt remove -y kubelet kubeadm kubectl

sudo apt autoremove -y
```

### 📦 Amazon Linux 2023 / RHEL

```bash
sudo dnf remove -y kubelet kubeadm kubectl
```

### 🧹 Remove CNI Configuration

```bash
sudo rm -rf /etc/cni/net.d
```

> Resetting a node does not automatically remove every container image, CNI file, or application data. Review the machine before deleting additional directories or resetting a production cluster.

---

## 🛡️ 28. Best Practices

- Use supported Kubernetes versions.
- Keep `kubectl` within one minor version of the cluster.
- Use RBAC for access control.
- Use namespaces to organize workloads.
- Configure resource requests and limits.
- Use readiness, liveness, and startup probes.
- Store sensitive information in Kubernetes Secrets or an external secret manager.
- Enable encryption at rest for sensitive cluster data.
- Use Network Policies to control Pod communication.
- Back up etcd regularly.
- Review logs, events, and resource usage.
- Follow the official Kubernetes upgrade procedure.

---

## 📚 29. Official Documentation

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Kubernetes Installation Tools](https://kubernetes.io/docs/tasks/tools/)
- [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Install kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
- [Create a Cluster with kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)
- [Kubernetes Objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/)
- [Kubernetes Workloads](https://kubernetes.io/docs/concepts/workloads/)
- [Kubernetes Services](https://kubernetes.io/docs/concepts/services-networking/service/)
- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)
- [KIND Documentation](https://kind.sigs.k8s.io/)
- [Helm Documentation](https://helm.sh/docs/)

---

**🚀 Learn • Deploy • Scale • Orchestrate**