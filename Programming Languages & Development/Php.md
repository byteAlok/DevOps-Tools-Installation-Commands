# 🐘 PHP – Installation & Commands Guide

## 🚀 Introduction

**PHP (Hypertext Preprocessor)** is an open-source, general-purpose scripting language primarily used for server-side web development.

PHP executes on the server and generates dynamic content that can be delivered to web browsers. It can also be used for command-line scripts, automation, APIs, and backend applications.

### ⚙️ What is PHP used for?

- 🌐 Backend and server-side web development
- 🔌 REST API development
- 🗄️ Database connectivity (MySQL, PostgreSQL, SQLite)
- 🛒 E-commerce applications
- 📝 Content Management Systems (WordPress, Drupal)
- 🧩 Web application development using Laravel and Symfony
- 🤖 Automation and command-line applications

> **Important:** PHP is a programming language, not a web server. It can work with Apache and Nginx, or run its own built-in development server.

---

## 📚 History of PHP

| Year | Milestone |
|---|---|
| 1994 | Rasmus Lerdorf started developing PHP tools. |
| 1995 | PHP was publicly released as Personal Home Page Tools. |
| 1997 | PHP 2 was released. |
| 1998 | PHP 3 was released and PHP became known as PHP: Hypertext Preprocessor. |
| 2000 | PHP 4 was released, powered by the Zend Engine. |
| 2004 | PHP 5 was released with improved object-oriented programming and Zend Engine 2. |
| 2015 | PHP 7 was released with major performance improvements. |
| 2020 | PHP 8.0 introduced features such as JIT compilation and union types. |
| 2025 | PHP 8.5 was released. |

### 👨‍💻 Who created PHP?

- **Creator:** Rasmus Lerdorf
- **Initial development:** 1994
- **First public release:** 1995
- **Original name:** Personal Home Page Tools
- **Current full form:** PHP: Hypertext Preprocessor
- **License:** PHP License

### 💡 Why was PHP created?

Rasmus Lerdorf initially developed PHP tools to manage and track visits to his personal website.

Over time, these tools evolved into a scripting language capable of generating dynamic web pages and handling server-side operations.

---

## 🧠 How PHP Works

PHP code is executed on the server rather than directly in the browser.

### 🔄 Request–Response Flow

1. A user opens a website in a browser.
2. The browser sends an HTTP request to the web server.
3. The web server passes the PHP request to the PHP runtime, commonly through PHP-FPM or an integrated server module.
4. PHP executes the application code.
5. PHP can communicate with databases and other services.
6. The server returns the generated response to the browser.

**Example:** A PHP application can retrieve customer information from MySQL and generate an HTML page containing that information.

---

## 🆚 PHP vs Composer vs Laravel

| Technology | Type | Purpose |
|---|---|---|
| PHP | Programming Language | Writes server-side application logic. |
| Composer | Dependency Manager | Installs and manages PHP packages. |
| Laravel | PHP Framework | Builds web applications and APIs. |
| Symfony | PHP Framework | Builds structured web applications and services. |
| PHP-FPM | Process Manager | Manages PHP worker processes, commonly used with Nginx. |
| Apache | Web Server | Handles HTTP requests and can execute PHP through supported integrations. |
| Nginx | Web Server | Commonly forwards PHP requests to PHP-FPM. |

---

## 📦 PHP Versions

PHP receives regular feature, bug-fix, and security updates.

### 📊 Supported Release Branches

As of October 30, 2026:

| Version | Support status |
|---|---|
| PHP 8.5 | Active support |
| PHP 8.4 | Active support |
| PHP 8.3 | Security support |
| PHP 8.2 | Security support until December 31, 2026 |
| PHP 8.1 and older | End of Life |

**Recommendation:** Use PHP 8.5 for new projects when your application and dependencies support it. For existing applications, select a supported version compatible with the project.

Official release information:

https://www.php.net/supported-versions.php

---

## 💻 System Requirements

PHP can run on Linux, Windows, and macOS.

| Requirement | Details |
|---|---|
| Operating System | Linux, Windows, macOS |
| Architecture | Supported x64 and ARM64 platforms |
| Processor | Modern processor recommended |
| RAM | 2 GB minimum for basic development; 4 GB or more recommended |
| Storage | Depends on PHP extensions, Composer packages, and project size |
| Web Server | Apache, Nginx, or PHP built-in development server |
| Database | MySQL, PostgreSQL, SQLite, or other supported databases |

*Actual requirements depend on application size and workload.*

---

## 🖥️ Supported Operating Systems

| Operating System | Package Manager / Installation |
|---|---|
| Amazon Linux 2 | YUM / Amazon Linux Extras |
| Amazon Linux 2023 | DNF |
| Ubuntu | APT |
| RHEL | DNF / YUM |
| Windows | Official PHP binaries / Scoop / Chocolatey |
| macOS | Homebrew |

---

# 🔍 Package Management Commands

Package managers help install, update, search, inspect, and remove software packages from an operating system.

## 🐧 Amazon Linux 2 / RHEL / CentOS (YUM)

### 🔎 Search packages

```bash
yum search php
yum search php-cli
```

### 📋 List available packages

```bash
yum list available
yum list available 'php*'
```

### 📦 List installed packages

```bash
yum list installed
yum list installed 'php*'
```

### ℹ️ Package information

```bash
yum info php
yum info php-cli
```

### 📥 Install packages

```bash
sudo yum install php php-cli php-mysqlnd -y
```

### 🔄 Update packages

```bash
sudo yum update
sudo yum update 'php*'
```

### 🗑️ Remove packages

```bash
sudo yum remove php php-cli -y
```

---

## 🐧 Amazon Linux 2023 / RHEL (DNF)

### 🔎 Search packages

```bash
dnf search php
dnf search php-cli
```

### 📋 List available packages

```bash
dnf list available
dnf list available 'php*'
```

### 📦 List installed packages

```bash
dnf list installed
dnf list installed 'php*'
```

### ℹ️ Package information

```bash
dnf info php
```

### 📥 Install packages

```bash
sudo dnf install php php-cli php-fpm php-mysqlnd -y
```

### 🔄 Update packages

```bash
sudo dnf update
sudo dnf update 'php*'
```

### 🗑️ Remove packages

```bash
sudo dnf remove php php-cli -y
```

---

## 🐧 Ubuntu / Debian (APT)

### 🔎 Search packages

```bash
apt search php
apt search php-cli
```

### 📋 List available packages

```bash
apt list php-cli
apt list 'php*'
```

### 📦 List installed packages

```bash
apt list --installed
apt list --installed | grep php
```

### ℹ️ Package information

```bash
apt show php
apt show php-cli
```

### 📥 Install packages

```bash
sudo apt update

sudo apt install php php-cli php-fpm php-mysql php-xml php-curl php-mbstring php-zip -y
```

### 🔄 Update packages

```bash
sudo apt update
sudo apt upgrade
sudo apt install --only-upgrade php php-cli -y
```

### 🗑️ Remove packages

```bash
sudo apt remove php php-cli -y
sudo apt autoremove -y
```

> **Note:** The PHP version available through the default OS repository depends on the operating system release and configured repositories. Check the available version before installation if you need a specific release.

---

# 📥 PHP Installation

## 🐧 Amazon Linux 2

<badge color="warning">Legacy OS – Standard support ended June 30, 2026</badge>

Amazon Linux 2 has reached the end of standard support. Prefer Amazon Linux 2023 for new deployments.

### 🔍 Check available PHP topics

```bash
amazon-linux-extras list | grep php
```

### 📥 Install PHP

If a suitable PHP topic is available in your configured repositories:

```bash
# Enable an available PHP topic
sudo amazon-linux-extras enable php8.2

# Refresh package metadata
sudo yum clean metadata

# Install PHP and common extensions
sudo yum install php php-cli php-common php-mysqlnd -y
```

### 🔍 Verify installation

```bash
php --version
php -m
```

*The available PHP topic and version depend on the Amazon Linux 2 repository state. Do not use this legacy OS for new production deployments.*

---

## 🐧 Amazon Linux 2023

### 📥 Install PHP

```bash
# Update package information
sudo dnf update -y

# Search available PHP packages
sudo dnf search php

# Install PHP and commonly used extensions
sudo dnf install php php-cli php-common php-fpm php-mysqlnd php-xml php-mbstring php-curl php-zip -y
```

### 🔍 Verify installation

```bash
php --version
php -m
```

### ⚙️ Start PHP-FPM

```bash
sudo systemctl start php-fpm
sudo systemctl enable php-fpm
sudo systemctl status php-fpm
```

*The version provided by the configured Amazon Linux repositories may differ from the latest upstream PHP release.*

---

## 🐧 Ubuntu

### 📥 Install PHP

```bash
# Update package information
sudo apt update

# Install PHP CLI, PHP-FPM, and common extensions
sudo apt install php php-cli php-fpm php-mysql php-xml php-mbstring php-curl php-zip -y
```

### 🔍 Verify installation

```bash
php --version
php -m
```

### ⚙️ Find and start PHP-FPM

PHP-FPM service names are generally versioned on Ubuntu.

```bash
# Find installed PHP-FPM service
systemctl list-units --type=service | grep php
```

Use the matching service name:

```bash
sudo systemctl start php8.5-fpm
sudo systemctl enable php8.5-fpm
sudo systemctl status php8.5-fpm
```

*Replace `php8.5-fpm` with the actual installed service name.*

---

## 🐧 RHEL

### 📥 Install PHP

```bash
# Update package information
sudo dnf update -y

# Search PHP packages
sudo dnf search php

# Install PHP and common extensions
sudo dnf install php php-cli php-common php-fpm php-mysqlnd php-xml php-mbstring php-curl php-zip -y
```

### 🔍 Verify installation

```bash
php --version
php -m
```

### ⚙️ Start PHP-FPM

```bash
sudo systemctl start php-fpm
sudo systemctl enable php-fpm
sudo systemctl status php-fpm
```

*Available versions depend on your RHEL release and enabled repositories.*

---

## 🪟 Windows

PHP can be installed on Windows using official PHP binaries or package managers.

### Method 1: Official PHP binaries

1. Visit the official PHP for Windows website.
2. Download the required PHP version and architecture.
3. Extract the ZIP file into a directory, for example `C:\php`.
4. Add `C:\php` to the Windows PATH environment variable.
5. Open a new PowerShell terminal.

Official download:

https://windows.php.net/download/

### 🔍 Verify installation

```powershell
php --version
php --ini
php -m
```

### Method 2: Scoop

```powershell
# Install PHP
scoop install php

# Update PHP
scoop update php

# Uninstall PHP
scoop uninstall php
```

### Method 3: Chocolatey

```powershell
# Install PHP
choco install php -y

# Upgrade PHP
choco upgrade php -y

# Uninstall PHP
choco uninstall php -y
```

*Package availability and versions depend on the package manager repository.*

---

## 🍎 macOS

### Method 1: Homebrew

```bash
# Update Homebrew
brew update

# Install PHP
brew install php

# Check PHP version
php --version

# Upgrade PHP
brew upgrade php

# Uninstall PHP
brew uninstall php
```

### 🔍 Check PHP location

```bash
which php
php --ini
```

---

# 🔍 Verify PHP Installation

After installation, use the following commands.

```bash
# Display PHP version
php --version

# Display PHP version information
php -v

# Display PHP configuration
php --ini

# List loaded PHP modules
php -m

# Display PHP configuration details
php -i

# Display PHP executable location (Linux/macOS)
which php

# Display PHP executable location (Windows)
where.exe php
```

---

# 🧪 Run Your First PHP Program

Create a file named `index.php`.

```php
<?php

echo "Hello from PHP!";

?>
```

Execute it using the PHP CLI:

```bash
php index.php
```

Expected output:

```text
Hello from PHP!
```

---

# ⚡ PHP CLI Commands

PHP CLI (Command Line Interface) allows developers to execute PHP scripts directly from the terminal.

### 📄 Execute PHP files

```bash
php index.php
php app.php
php script.php
```

### 🧪 Execute PHP code directly

```bash
php -r 'echo "Hello PHP";'
```

### 🔍 Check PHP syntax

```bash
php -l index.php
```

### 📋 Display loaded extensions

```bash
php -m
```

### 🔎 Display a specific configuration value

```bash
php -r 'echo PHP_VERSION;'
php -r 'echo PHP_OS;'
php -r 'echo PHP_SAPI;'
```

### 📖 Display CLI help

```bash
php --help
```

---

# 📦 PHP Extensions

PHP extensions add additional functionality to the PHP runtime.

Examples include database connectivity, XML processing, image manipulation, and encryption.

| Extension | Purpose |
|---|---|
| mysqli | MySQL database connectivity |
| pdo_mysql | MySQL connectivity through PDO |
| curl | HTTP requests and network communication |
| mbstring | Multibyte string handling |
| xml | XML processing |
| zip | ZIP archive handling |
| gd | Image processing |
| openssl | Cryptographic operations |
| bcmath | Arbitrary precision mathematics |
| intl | Internationalization |
| fileinfo | File type detection |

### 🔍 List installed extensions

```bash
php -m
```

### 🔎 Check a specific extension

```bash
php -m | grep curl
php -m | grep mysqli
php -m | grep pdo_mysql
```

### 📋 Display extension information

```bash
php --ri curl
php --ri mysqli
```

### 📥 Install extensions

**Ubuntu / Debian:**

```bash
sudo apt install php-curl php-mysql php-xml php-mbstring php-zip php-gd -y
```

**Amazon Linux 2023 / RHEL:**

```bash
sudo dnf install php-curl php-mysqlnd php-xml php-mbstring php-zip php-gd -y
```

**Amazon Linux 2:**

```bash
sudo yum install php-curl php-mysqlnd php-xml php-mbstring php-zip php-gd -y
```

*Extension package names vary by distribution and PHP version.*

---

# 🎼 Composer (PHP Dependency Manager)

Composer is a dependency manager for PHP. It helps developers install and manage external PHP libraries and packages.

It is similar to npm in the Node.js ecosystem.

### 📥 Install Composer

Official installation instructions:

https://getcomposer.org/download/

**Ubuntu / Debian:**

```bash
sudo apt update
sudo apt install composer -y
```

**Amazon Linux 2023 / RHEL:**

```bash
sudo dnf install composer -y
```

**macOS:**

```bash
brew install composer
```

**Windows:**

Download and run the official Composer installer:

https://getcomposer.org/Composer-Setup.exe

### 🔍 Verify Composer

```bash
composer --version
```

### 📦 Composer commands

```bash
# Initialize a PHP project
composer init

# Install dependencies
composer install

# Add a package
composer require monolog/monolog

# Add a development dependency
composer require --dev phpunit/phpunit

# Update dependencies within allowed version constraints
composer update

# Update a specific package
composer update monolog/monolog

# Remove a package
composer remove monolog/monolog

# List installed packages
composer show

# Display outdated packages
composer outdated

# Validate composer.json and composer.lock
composer validate

# Check platform requirements
composer check-platform-reqs

# Clear Composer cache
composer clear-cache

# Display Composer help
composer help
```

### 📄 Important Composer files

| File | Purpose |
|---|---|
| composer.json | Defines project metadata and dependencies. |
| composer.lock | Records the exact resolved dependency versions. |
| vendor/ | Contains installed Composer dependencies. |
| vendor/autoload.php | Loads Composer-managed classes automatically. |

> Commit `composer.json` and `composer.lock` to Git. Normally, do not commit the `vendor/` directory.

---

# 📁 PHP Project Management

## 🏗️ Create a project

```bash
# Create project directory
mkdir my-php-project

# Navigate into project
cd my-php-project

# Create PHP file
touch index.php
```

On Windows PowerShell:

```powershell
mkdir my-php-project
cd my-php-project
New-Item index.php -ItemType File
```

## 📄 Example project structure

```text
my-php-project/
│
├── index.php
├── config.php
├── composer.json
├── composer.lock
└── vendor/
```

## 🧩 Example PHP application

`index.php`:

```php
<?php

$name = "Developer";

echo "Welcome, " . $name . "!";

?>
```

Run:

```bash
php index.php
```

---

# 🌐 PHP Built-in Development Server

PHP provides a built-in web server for local development and testing.

### ▶️ Start the server

```bash
php -S localhost:8000
```

Open the browser:

```text
http://localhost:8000
```

### 📁 Start the server with a specific document root

```bash
php -S localhost:8000 -t public
```

### 🌍 Allow access from other machines on the network

```bash
php -S 0.0.0.0:8000
```

> **Security warning:** PHP's built-in server is intended for development and testing. Do not use it as a production web server.

---

# ⚙️ PHP Configuration (php.ini)

`php.ini` is the main PHP configuration file.

It controls settings such as memory limits, upload limits, execution time, error reporting, and extension loading.

### 🔍 Locate php.ini

```bash
php --ini
```

### 📋 Display loaded configuration

```bash
php -i
```

### ⚙️ Common configuration settings

```ini
; Maximum memory available to a PHP script
memory_limit = 256M

; Maximum execution time
max_execution_time = 60

; Maximum file upload size
upload_max_filesize = 20M

; Maximum POST request size
post_max_size = 25M

; Enable error reporting
display_errors = On

; Log errors
log_errors = On
```

> For production environments, disable `display_errors` and enable appropriate error logging. Configuration changes may require restarting PHP-FPM or the relevant web server.

---

# 🛡️ Recent Security Updates

PHP regularly releases security updates to fix vulnerabilities and improve application security.

## 🔴 October 21, 2026 – Critical Remote Code Execution Vulnerabilities

On October 21, 2026, the PHP development team released security updates addressing two critical vulnerabilities that could allow unauthenticated Remote Code Execution (RCE).

**Affected vulnerabilities:**

| CVE | Description |
|---|---|
| CVE-2026-109618 | Remote Code Execution through out-of-memory handling and memory corruption. |
| CVE-2026-109619 | Remote Code Execution through stale internal request state. |

Both vulnerabilities were rated critical. The risk applies to PHP installations serving web requests, including PHP-FPM, Apache with mod_php, php-cgi, FrankenPHP, and LiteSpeed.

### 🚨 Fixed PHP Versions

| PHP Branch | Minimum Fixed Version |
|---|---:|
| PHP 8.5 | 8.5.12 |
| PHP 8.4 | 8.4.27 |
| PHP 8.3 | 8.3.36 |
| PHP 8.2 | 8.2.35 |

**Important:** The PHP team stated that there are no complete workarounds for these vulnerabilities. Updating to a fixed release is the recommended action.

### 🔄 Update PHP Packages

**Ubuntu / Debian:**

```bash
sudo apt update
sudo apt upgrade
```

If you want to update PHP packages specifically:

```bash
sudo apt install --only-upgrade 'php*'
```

**Amazon Linux 2023 / RHEL:**

```bash
sudo dnf clean metadata
sudo dnf update 'php*'
```

**Amazon Linux 2:**

```bash
sudo yum clean metadata
sudo yum update 'php*'
```

**Windows:**

1. Visit the official PHP for Windows download page.
2. Download a patched PHP build compatible with your application.
3. Replace the old PHP installation.
4. Verify the active PHP executable and restart the relevant services.

https://windows.php.net/download/

### 🔍 Verify the Installed Version

```bash
php --version
```

For example, a PHP 8.5 installation should report version 8.5.12 or a later patched release.

### ⚙️ Restart PHP-FPM After Updating

**Amazon Linux 2023 / RHEL:**

```bash
sudo systemctl restart php-fpm
sudo systemctl status php-fpm
```

**Ubuntu:**

```bash
sudo systemctl restart php8.5-fpm
sudo systemctl status php8.5-fpm
```

Replace the service name with the installed PHP-FPM version.

### ⚠️ Important Security Notes

- Update all internet-facing PHP installations.
- Update PHP CLI and web-serving PHP installations.
- Check the PHP version used by Apache, Nginx, and PHP-FPM.
- Restart affected PHP workers and web services after patching.
- Verify whether your Linux distribution has backported the security fix.
- Do not assume that a package update succeeded without checking the installed version and vendor security advisory.

**Official security advisory:** https://www.php.net/archive/2026.php

---

# 🐳 PHP with Docker

PHP applications can run inside Docker containers without requiring PHP to be installed directly on the host machine.

### 📥 Pull PHP image

```bash
docker pull php:8.5-cli
```

### 🔍 Check downloaded images

```bash
docker images
```

### ▶️ Run PHP container

```bash
docker run --rm php:8.5-cli php --version
```

### 🏗️ Example Dockerfile

```dockerfile
FROM php:8.5-cli

WORKDIR /app

COPY . .

CMD ["php", "index.php"]
```

### 🏗️ Build Docker image

```bash
docker build -t my-php-app .
```

### ▶️ Run container

```bash
docker run --rm my-php-app
```

### 🌐 Run PHP development server in Docker

```bash
docker run --rm -p 8000:8000 -v "$PWD":/app -w /app php:8.5-cli php -S 0.0.0.0:8000
```

Open:

```text
http://localhost:8000
```

---

# 🗑️ PHP Uninstallation

### 🐧 Amazon Linux 2

```bash
sudo yum remove php php-cli -y
```

### 🐧 Amazon Linux 2023 / RHEL

```bash
sudo dnf remove php php-cli -y
```

### 🐧 Ubuntu

```bash
sudo apt remove php php-cli php-fpm -y
sudo apt autoremove -y
```

### 🪟 Windows

If installed using Scoop:

```powershell
scoop uninstall php
```

If installed using Chocolatey:

```powershell
choco uninstall php -y
```

If installed using official binaries, remove the PHP installation directory and its PATH entry.

### 🍎 macOS

```bash
brew uninstall php
```

---

# ✅ PHP Best Practices

- Use a currently supported PHP version.
- Apply security updates as soon as possible.
- Keep PHP and its extensions updated.
- Use Composer to manage project dependencies.
- Commit `composer.lock` to version control.
- Use environment variables for sensitive configuration.
- Never commit database passwords or API keys to Git.
- Validate and sanitize user input.
- Use prepared statements for database queries.
- Disable error display in production.
- Use PHP-FPM with Nginx or Apache for suitable production deployments.
- Use Docker to maintain consistent development and deployment environments.
- Regularly check official PHP security advisories.

---

# 📚 Official Documentation & Resources

| Resource | Link |
|---|---|
| PHP Official Website | https://www.php.net/ |
| PHP Documentation | https://www.php.net/docs.php |
| PHP Downloads | https://www.php.net/downloads.php |
| PHP Supported Versions | https://www.php.net/supported-versions.php |
| PHP Security Advisories | https://www.php.net/archive/2026.php |
| PHP for Windows | https://windows.php.net/ |
| Composer Official Website | https://getcomposer.org/ |
| Composer Documentation | https://getcomposer.org/doc/ |
| Laravel Documentation | https://laravel.com/docs |
| Symfony Documentation | https://symfony.com/doc/current/ |
| Docker PHP Image | https://hub.docker.com/_/php |

---

**🐘 Learning PHP | Building Backend Applications | Exploring DevOps & CI/CD**