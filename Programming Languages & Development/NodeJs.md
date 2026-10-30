# 🟢 Node.js – Installation & Commands Guide

## 🚀 Introduction

**Node.js** is an open-source, cross-platform JavaScript runtime environment that allows developers to execute JavaScript code outside a web browser.

JavaScript was initially used mainly for frontend development inside browsers. Node.js made it possible to use JavaScript for backend development, server-side applications, command-line tools, automation scripts, APIs, and real-time applications.

Node.js is built on Google's **V8 JavaScript Engine**, the same engine used by Google Chrome.

### ⚙️ What is Node.js used for?

- 🌐 Backend development and REST APIs
- 🔌 Real-time applications (Chat applications, WebSockets)
- 📦 Package management and development tools
- 🤖 Automation scripts and CLI applications
- ⚡ Microservices and server-side applications
- 🖥️ Full-stack JavaScript development
- 🔄 Build tools used by React, Next.js, Vite, and other frontend frameworks

> **Important:** Node.js is not a programming language or a framework. It is a JavaScript runtime environment. JavaScript is the programming language, and Express.js is an example of a framework built for Node.js.

---

## 📚 History of Node.js

| Year | Milestone |
|---|---|
| 2008 | Google introduced the V8 JavaScript Engine with Chrome. |
| 2009 | Ryan Dahl started Node.js and introduced it publicly. |
| 2010 | npm became available as the package manager for Node.js. |
| 2011 | Node.js gained native Windows support. |
| 2014 | io.js was created as a fork of Node.js. |
| 2015 | Node.js and io.js communities reunited. Node.js Foundation was established. |
| 2019 | Node.js Foundation and JS Foundation merged to form the OpenJS Foundation. |

### 👨‍💻 Who created Node.js?

- **Creator:** Ryan Dahl
- **Initial development:** 2009
- **Original company association:** Joyent
- **JavaScript Engine:** Google V8
- **Current project governance:** OpenJS Foundation

### 💡 Why was Node.js created?

Traditional server-side applications often used a blocking I/O approach, where an operation could make a thread wait until the operation completed.

Ryan Dahl wanted a runtime that could handle many concurrent connections efficiently without creating a separate thread for every request.

Node.js introduced an event-driven, non-blocking I/O model to help solve this problem.

---

## 🧠 Node.js Architecture

Node.js uses several important components:

| Component | Description |
|---|---|
| V8 Engine | Executes JavaScript code. |
| Event Loop | Coordinates asynchronous operations and callbacks. |
| libuv | Provides asynchronous I/O and the event-loop implementation. |
| Thread Pool | Handles certain operations such as filesystem and cryptographic tasks. |
| Node.js APIs | Provide modules for filesystem, HTTP, networking, processes, and more. |

### 🔄 How Node.js handles requests

1. A request or operation enters the Node.js application.
2. Synchronous JavaScript code executes on the main JavaScript thread.
3. Asynchronous I/O operations are delegated to the relevant system APIs or libuv.
4. When an operation completes, its callback or continuation becomes eligible to run.
5. The Event Loop coordinates when JavaScript executes the resulting work.

> Node.js commonly runs JavaScript on a single main thread, but it is not entirely single-threaded. It can use additional threads and system-level asynchronous operations.

---

## 🆚 Node.js vs JavaScript vs Express.js

| Technology | Type | Purpose |
|---|---|---|
| JavaScript | Programming Language | Writes application logic. |
| Node.js | Runtime Environment | Executes JavaScript outside browsers. |
| Express.js | Web Framework | Builds APIs and web applications using Node.js. |
| npm | Package Manager | Installs and manages JavaScript packages. |
| npx | Package Execution Tool | Executes packages without requiring a permanent global installation. |

---

## 📦 Node.js Versions

Node.js follows a release cycle with different support stages.

- **Current:** Receives recent features and improvements.
- **Active LTS:** Stable release line receiving long-term support.
- **Maintenance LTS:** Receives maintenance and important fixes.
- **EOL:** End of Life; no longer receives normal support.

### 📊 Current Release Status

As of October 30, 2026:

| Version | Status |
|---|---|
| Node.js 26 | Active LTS |
| Node.js 24 | Active LTS |
| Node.js 22 | Maintenance LTS |
| Node.js 27 | Alpha |

**Recommendation:** Prefer an Active LTS release for production applications. Check the official release schedule before selecting a version.

🔗 https://nodejs.org/en/about/previous-releases

---

## 💻 System Requirements

Node.js is available for multiple operating systems and processor architectures.

| Requirement | Details |
|---|---|
| Operating System | Linux, Windows, macOS |
| Architecture | x64, ARM64 and supported platform-specific architectures |
| Processor | Modern 64-bit processor recommended |
| RAM | 2 GB minimum for basic development; 4 GB or more recommended |
| Storage | A few hundred MB for installation; additional space required for projects and packages |
| Network | Internet connection for downloading packages |

*Actual requirements depend on project size, installed dependencies, build tools, and workload.*

---

## 🖥️ Supported Operating Systems

| Operating System | Package Manager / Installation |
|---|---|
| Amazon Linux 2 | YUM / NVM |
| Amazon Linux 2023 | DNF / NVM |
| Ubuntu | APT / NVM |
| RHEL | YUM / DNF / NVM |
| Windows | Winget / NVM for Windows |
| macOS | Homebrew / NVM |

---

# 🔍 Package Management Commands

Package managers help install, update, search, inspect, and remove software packages from an operating system.

## 🐧 Amazon Linux 2 / RHEL / CentOS (YUM)

### 🔎 Search packages

```bash
yum search nodejs
yum search npm
```

### 📋 List available packages

```bash
yum list available
yum list available nodejs
```

### 📦 List installed packages

```bash
yum list installed
yum list installed nodejs
```

### ℹ️ Package information

```bash
yum info nodejs
yum info npm
```

### 📥 Install packages

```bash
sudo yum install nodejs -y
```

### 🔄 Update packages

```bash
sudo yum update
sudo yum update nodejs
```

### 🗑️ Remove packages

```bash
sudo yum remove nodejs -y
```

---

## 🐧 Amazon Linux 2023 / RHEL (DNF)

### 🔎 Search packages

```bash
dnf search nodejs
dnf search npm
```

### 📋 List available packages

```bash
dnf list available
dnf list available nodejs
```

### 📦 List installed packages

```bash
dnf list installed
dnf list installed nodejs
```

### ℹ️ Package information

```bash
dnf info nodejs
```

### 📥 Install packages

```bash
sudo dnf install nodejs -y
```

### 🔄 Update packages

```bash
sudo dnf update
sudo dnf update nodejs
```

### 🗑️ Remove packages

```bash
sudo dnf remove nodejs -y
```

---

## 🐧 Ubuntu / Debian (APT)

### 🔎 Search packages

```bash
apt search nodejs
apt search npm
```

### 📋 List available packages

```bash
apt list nodejs
apt list npm
```

### 📦 List installed packages

```bash
apt list --installed
apt list --installed | grep nodejs
```

### ℹ️ Package information

```bash
apt show nodejs
apt show npm
```

### 📥 Install packages

```bash
sudo apt update
sudo apt install nodejs npm -y
```

### 🔄 Update packages

```bash
sudo apt update
sudo apt upgrade
sudo apt install --only-upgrade nodejs npm
```

### 🗑️ Remove packages

```bash
sudo apt remove nodejs npm -y
sudo apt autoremove -y
```

> **Note:** Default OS repositories can contain older Node.js versions. For development, using NVM or an official Node.js installation source is generally more flexible.

---

# 📥 Node.js Installation

## 🐧 Amazon Linux 2

### Method 1: Install using NVM (Recommended)

NVM stands for Node Version Manager. It allows you to install and switch between multiple Node.js versions.

```bash
# Install required tools
sudo yum install curl -y

# Download and install NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.7/install.sh | bash

# Load NVM
source ~/.bashrc

# Install the latest LTS version
nvm install --lts

# Use the LTS version
nvm use --lts
```

### Method 2: Install using NodeSource

```bash
# Configure Node.js 26 repository
curl -fsSL https://rpm.nodesource.com/setup_26.x | sudo bash -

# Install Node.js
sudo yum install nodejs -y
```

---

## 🐧 Amazon Linux 2023

### Method 1: Install using NVM (Recommended)

```bash
# Install required tools
sudo dnf install curl -y

# Install NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.7/install.sh | bash

# Load NVM
source ~/.bashrc

# Install Node.js LTS
nvm install --lts

# Activate Node.js
nvm use --lts
```

### Method 2: Install using NodeSource

```bash
# Configure Node.js 26 repository
curl -fsSL https://rpm.nodesource.com/setup_26.x | sudo bash -

# Install Node.js
sudo dnf install nodejs -y
```

---

## 🐧 Ubuntu

### Method 1: Install using NVM (Recommended)

```bash
# Update package information
sudo apt update

# Install required tools
sudo apt install curl -y

# Install NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.7/install.sh | bash

# Load NVM
source ~/.bashrc

# Install Node.js LTS
nvm install --lts

# Activate Node.js
nvm use --lts
```

### Method 2: Install using NodeSource

```bash
# Update package information
sudo apt update

# Install required tools
sudo apt install curl -y

# Configure Node.js 26 repository
curl -fsSL https://deb.nodesource.com/setup_26.x | sudo -E bash -

# Install Node.js
sudo apt install nodejs -y
```

---

## 🐧 RHEL

### Method 1: Install using NVM (Recommended)

```bash
# Install required tools
sudo dnf install curl -y

# Install NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.7/install.sh | bash

# Load NVM
source ~/.bashrc

# Install Node.js LTS
nvm install --lts

# Activate Node.js
nvm use --lts
```

### Method 2: Install using NodeSource

```bash
# Configure Node.js 26 repository
curl -fsSL https://rpm.nodesource.com/setup_26.x | sudo bash -

# Install Node.js
sudo dnf install nodejs -y
```

*For older RHEL releases, package manager and repository compatibility may differ.*

---

## 🪟 Windows

### Method 1: Install using Winget

```powershell
# Search Node.js packages
winget search NodeJS

# Install Node.js LTS
winget install OpenJS.NodeJS.LTS

# Upgrade Node.js
winget upgrade OpenJS.NodeJS.LTS

# Uninstall Node.js
winget uninstall OpenJS.NodeJS.LTS
```

### Method 2: Install using NVM for Windows

Install NVM for Windows from its official GitHub repository:

https://github.com/coreybutler/nvm-windows

Open PowerShell or Command Prompt:

```powershell
# Check NVM version
nvm version

# List available Node.js versions
nvm list available

# Install Node.js 26
nvm install 26.13.0

# Switch to Node.js 26
nvm use 26.13.0

# List installed versions
nvm list
```

*If a command requires elevated permissions, run the terminal as Administrator.*

---

## 🍎 macOS

### Method 1: Install using Homebrew and NVM

```bash
# Install Homebrew if not already installed
# https://brew.sh/

# Install NVM
brew install nvm

# Create NVM directory
mkdir -p ~/.nvm

# Add NVM configuration to ~/.zshrc
echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
echo '[ -s "$(brew --prefix nvm)/nvm.sh" ] && \. "$(brew --prefix nvm)/nvm.sh"' >> ~/.zshrc

# Reload shell configuration
source ~/.zshrc

# Install Node.js LTS
nvm install --lts

# Activate Node.js
nvm use --lts
```

### Method 2: Install using Homebrew

```bash
# Install Node.js
brew install node

# Update Homebrew
brew update

# Upgrade Node.js
brew upgrade node

# Remove Node.js
brew uninstall node
```

---

# 🔍 Verify Node.js Installation

After installation, verify Node.js and npm:

```bash
# Check Node.js version
node --version

# Check npm version
npm --version

# Display Node.js executable path
which node

# Display npm executable path
which npm

# Display Node.js configuration
node --help

# Display npm configuration
npm config list
```

### 🧪 Run your first JavaScript program

Create a file named `app.js`.

```javascript
console.log("Hello from Node.js!");
```

Execute it:

```bash
node app.js
```

Expected output:

```text
Hello from Node.js!
```

---

# 📦 npm (Node Package Manager)

npm is the default package manager distributed with Node.js.

It helps developers install, update, manage, and publish reusable JavaScript packages.

### 🔍 Check npm version

```bash
npm --version
```

### 📦 Install packages

```bash
# Install a package locally
npm install express

# Install multiple packages
npm install express mongoose dotenv

# Install a package globally
npm install -g nodemon

# Install a specific version
npm install express@4

# Install development dependency
npm install --save-dev nodemon
```

### 📋 List installed packages

```bash
# List local packages
npm list

# List global packages
npm list -g

# Show direct dependencies
npm list --depth=0

# Show globally installed packages
npm list -g --depth=0
```

### 🔎 Package information

```bash
# Display package information
npm view express

# Display available versions
npm view express versions

# Display latest package version
npm view express version

# Display installed package information
npm show express
```

### 🔄 Update packages

```bash
# Update local dependencies within package.json version ranges
npm update

# Update a specific package
npm update express

# Update npm itself
npm install -g npm
```

### 🗑️ Uninstall packages

```bash
# Remove local package
npm uninstall express

# Remove development dependency
npm uninstall nodemon

# Remove global package
npm uninstall -g nodemon
```

### 🛠️ Other useful npm commands

```bash
# Check outdated packages
npm outdated

# Check dependency vulnerabilities
npm audit

# Attempt to fix compatible vulnerabilities
npm audit fix

# Display npm cache information
npm cache verify

# Clear npm cache
npm cache clean --force

# Display npm configuration
npm config list

# Display npm registry
npm config get registry
```

---

# ⚡ npx (Node Package Executor)

npx is a tool that comes with npm. It allows developers to execute packages without necessarily installing them globally.

### 📦 Examples

```bash
# Execute a package
npx cowsay "Hello Node.js"

# Create a Vite project
npx create-vite@latest my-app

# Create a React project using Vite
npm create vite@latest my-react-app -- --template react

# Check package help
npx create-vite --help
```

---

# 📁 Node.js Project Management

## 🏗️ Create a project

```bash
# Create project directory
mkdir my-node-project

# Navigate into project
cd my-node-project

# Initialize Node.js project
npm init

# Initialize with default configuration
npm init -y
```

## 📄 package.json

`package.json` is the main configuration file of a Node.js project.

It contains project information, dependencies, development dependencies, scripts, and other metadata.

Example:

```json
{
  "name": "my-node-project",
  "version": "1.0.0",
  "description": "My first Node.js project",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "node --watch index.js",
    "test": "node --test"
  },
  "dependencies": {
    "express": "^5.0.0"
  },
  "devDependencies": {
    "nodemon": "^3.0.0"
  }
}
```

*Package versions shown above are illustrative; use compatible versions for your project.*

## 🔐 package-lock.json

`package-lock.json` records the exact dependency tree resolved during installation.

It helps maintain consistent dependency installations across different environments.

```bash
# Generate or update lock file
npm install

# Install dependencies according to lock file
npm ci
```

> Commit `package-lock.json` to Git. Avoid manually editing it.

---

# 📚 Node.js Dependencies

Node.js projects commonly use two types of dependencies.

| Type | Purpose |
|---|---|
| dependencies | Packages required by the application at runtime. |
| devDependencies | Packages used during development, testing, or building. |

### 📦 Install dependencies

```bash
# Runtime dependency
npm install express

# Development dependency
npm install --save-dev nodemon
```

### 📋 Install dependencies from package.json

```bash
npm install
```

### 🚀 Install production dependencies only

```bash
npm install --omit=dev
```

---

# 🔄 NVM (Node Version Manager)

NVM helps developers manage multiple Node.js versions on a single machine.

It is useful when different projects require different Node.js versions.

### 📋 NVM commands (Linux / macOS)

```bash
# Check NVM version
nvm --version

# List available remote versions
nvm ls-remote

# Install a specific version
nvm install 24

# Install latest LTS version
nvm install --lts

# List installed versions
nvm ls

# Switch to a version
nvm use 24

# Set default Node.js version
nvm alias default 24

# Display current version
nvm current

# Uninstall a version
nvm uninstall 24
```

### 🪟 NVM for Windows commands

```powershell
# Display installed versions
nvm list

# Display available versions
nvm list available

# Install a version
nvm install 24.22.2

# Switch version
nvm use 24.22.2

# Uninstall a version
nvm uninstall 24.22.2
```

> **Note:** NVM for Linux/macOS and NVM for Windows are separate implementations. Their commands and behavior are not always identical.

---

# 🌐 Create a Basic HTTP Server

Node.js includes a built-in HTTP module. You can create a basic web server without installing an external framework.

Create `server.js`:

```javascript
const http = require("node:http");

const server = http.createServer((req, res) => {
    res.writeHead(200, {
        "Content-Type": "text/plain"
    });

    res.end("Hello from Node.js Server!");
});

server.listen(3000, () => {
    console.log("Server running at http://localhost:3000");
});
```

Run the server:

```bash
node server.js
```

Open:

```text
http://localhost:3000
```

---

# 🚀 Express.js Installation

Express.js is a lightweight web framework used to build APIs and web applications with Node.js.

### 📦 Install Express

```bash
npm install express
```

### 🏗️ Create an Express server

Create `server.js`:

```javascript
const express = require("express");

const app = express();

app.get("/", (req, res) => {
    res.send("Hello from Express.js!");
});

app.listen(3000, () => {
    console.log("Server running on port 3000");
});
```

Run:

```bash
node server.js
```

---

# 🧰 Useful Node.js CLI Commands

```bash
# Display Node.js version
node -v

# Display npm version
npm -v

# Execute JavaScript file
node app.js

# Run JavaScript in interactive mode
node

# Display Node.js help
node --help

# Display process information
node -p "process.version"

# Display Node.js platform
node -p "process.platform"

# Display system architecture
node -p "process.arch"

# Display Node.js installation path
which node

# Display npm global installation path
npm root -g

# Display npm global binary path
npm bin -g
```

*On Windows, use `where node` and `where npm` instead of `which`.*

---

# 🐳 Node.js with Docker

Node.js applications can be packaged and executed inside Docker containers.

### 📥 Pull Node.js image

```bash
docker pull node:26
```

### 🔍 Check image

```bash
docker images
```

### ▶️ Run Node.js container

```bash
docker run -it --rm node:26 node --version
```

### 🏗️ Example Dockerfile

```dockerfile
FROM node:26-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

### 🏗️ Build Docker image

```bash
docker build -t my-node-app .
```

### ▶️ Run container

```bash
docker run -d -p 3000:3000 --name node-container my-node-app
```

### 📋 Container management

```bash
# List running containers
docker ps

# View container logs
docker logs node-container

# Stop container
docker stop node-container

# Remove container
docker rm node-container
```

---

# 🗑️ Node.js Uninstallation

### 🐧 Amazon Linux 2

```bash
sudo yum remove nodejs -y
```

### 🐧 Amazon Linux 2023 / RHEL

```bash
sudo dnf remove nodejs -y
```

### 🐧 Ubuntu

```bash
sudo apt remove nodejs npm -y
sudo apt autoremove -y
```

### 🪟 Windows

```powershell
winget uninstall OpenJS.NodeJS.LTS
```

### 🍎 macOS

```bash
brew uninstall node
```

### 🧹 Remove NVM installation (Linux / macOS)

```bash
# Remove NVM directory
rm -rf ~/.nvm

# Remove NVM configuration from your shell profile
# Edit ~/.bashrc or ~/.zshrc and remove the NVM-related lines.
```

---

# ✅ Node.js Best Practices

- Use an Active LTS version for production applications.
- Use NVM to manage multiple Node.js versions.
- Keep `package.json` and `package-lock.json` under version control.
- Use environment variables for sensitive configuration.
- Avoid committing `.env` files containing secrets.
- Use `npm audit` to check dependency vulnerabilities.
- Prefer local project dependencies over unnecessary global installations.
- Use `npm ci` for reproducible CI/CD dependency installation.
- Keep dependencies updated and remove unused packages.
- Use Docker for consistent application environments.

---

# 📚 Official Documentation & Resources

| Resource | Link |
|---|---|
| Node.js Official Website | https://nodejs.org/ |
| Node.js Documentation | https://nodejs.org/docs/latest/api/ |
| Node.js Downloads | https://nodejs.org/en/download |
| Node.js Release Schedule | https://nodejs.org/en/about/previous-releases |
| npm Official Website | https://www.npmjs.com/ |
| npm Documentation | https://docs.npmjs.com/ |
| NVM (Linux / macOS) | https://github.com/nvm-sh/nvm |
| NVM for Windows | https://github.com/coreybutler/nvm-windows |
| Express.js Documentation | https://expressjs.com/ |
| Docker Official Node.js Image | https://hub.docker.com/_/node |

---

**🚀 Learning Node.js | Building Backend Applications | Exploring DevOps & CI/CD**