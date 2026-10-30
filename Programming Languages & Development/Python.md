# 🐍 Python – Installation & Commands Guide

A practical guide to installing, configuring and managing Python across different operating systems, including package management, virtual environments, pip, modules and application execution.

## 📌 1. Introduction

Python is a high-level, interpreted, general-purpose programming language used in automation, web development, data science, artificial intelligence, machine learning, scripting and DevOps.

### 🕰️ Python Generations

| Technology | Versions | Status |
|---|---|---|
| 🏛️ Python 1.x | 1.0 – 1.6 | Legacy |
| 🏛️ Python 2.x | 2.0 – 2.7 | End of Life |
| 🚀 Python 3.x | 3.0 onwards | Modern Python |

**Important:**

- Python 2.7 reached End of Life on January 1, 2020.
- Python 3 is the actively maintained generation.
- Python 3.15 is the latest stable feature release as of October 2026.
- Python 3.14 is also actively maintained and can be a good compatibility choice for projects whose dependencies have not yet adopted 3.15.

### 🧩 Python Components

| Component | Purpose |
|---|---|
| 🐍 Python Interpreter | Executes Python code |
| 📦 pip | Python package installer |
| 📚 PyPI | Python Package Index |
| 🧪 venv | Creates isolated environments |
| ⚙️ Python Modules | Reusable Python code |
| 📋 requirements.txt | Records project dependencies |
| 🔧 pipx | Installs and isolates Python CLI applications |

---

# 🖥️ 2. Supported Operating Systems

| Operating System | Package Manager |
|---|---|
| 🐧 Amazon Linux 2 | YUM |
| 🐧 Amazon Linux 2023 | DNF |
| 🟠 Ubuntu | APT |
| 🔴 RHEL 7 | YUM |
| 🔴 RHEL 8 / 9 / 10 | DNF |
| 🪟 Windows | winget / Chocolatey |
| 🍎 macOS | Homebrew |

> **Note:** Linux distributions may ship different Python versions. The version available through the package manager depends on the OS release and enabled repositories.

---

# 📦 3. Package Management Commands

These commands help search, list, inspect, install, update and remove Python packages.

### 🔍 Search Python Packages

```bash
# Amazon Linux 2 / RHEL 7
yum search python3

# Amazon Linux 2023 / RHEL 8+
dnf search python3

# Ubuntu
apt search python3
```

### 📋 List Available Python Packages

```bash
# YUM
yum list available 'python*'

# DNF
dnf list available 'python*'

# Ubuntu
apt list 'python3*'
```

### 📋 List Installed Python Packages

```bash
# YUM
yum list installed 'python*'

# DNF
dnf list installed 'python*'

# Ubuntu
apt list --installed 'python3*'
```

### ℹ️ Get Python Package Information

```bash
# YUM
yum info python3

# DNF
dnf info python3

# Ubuntu
apt show python3
```

### 🔎 Search Python Development Packages

```bash
# YUM
yum search python3-devel

# DNF
dnf search python3-devel

# Ubuntu
apt search python3-dev
```

### 🔎 Search pip Packages

```bash
# YUM
yum search python3-pip

# DNF
dnf search python3-pip

# Ubuntu
apt search python3-pip
```

### 🗑️ Remove Python Packages

```bash
# YUM
sudo yum remove python3-pip -y

# DNF
sudo dnf remove python3-pip -y

# Ubuntu
sudo apt remove python3-pip -y
```

> ⚠️ **Warning:** Never blindly remove the system Python interpreter. Linux operating-system utilities may depend on it. Remove only packages you understand and no longer need.

---

# 🐧 4. Python Installation – Amazon Linux

## 🐧 4.1 Amazon Linux 2

### 🔄 Update System

```bash
sudo yum update -y
```

### 🔍 Search Python Packages

```bash
yum search python3
```

### 📋 List Available Python Packages

```bash
yum list available 'python*'
```

### 📋 List Installed Python Packages

```bash
yum list installed 'python*'
```

### 📦 Install Python 3

```bash
sudo yum install python3 -y
```

### 📦 Install pip

```bash
sudo yum install python3-pip -y
```

### 📦 Install Development Tools

```bash
sudo yum install python3-devel gcc -y
```

### 🔍 Verify Installation

```bash
python3 --version

pip3 --version
```

## 🐧 4.2 Amazon Linux 2023

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🔍 Search Python Packages

```bash
dnf search python3
```

### 📋 List Available Python Packages

```bash
dnf list available 'python*'
```

### 📋 List Installed Python Packages

```bash
dnf list installed 'python*'
```

### 📦 Install Python 3

```bash
sudo dnf install python3 -y
```

### 📦 Install pip

```bash
sudo dnf install python3-pip -y
```

### 📦 Install Development Tools

```bash
sudo dnf install python3-devel gcc -y
```

### 🔍 Verify Installation

```bash
python3 --version

pip3 --version
```

> **Note:** Amazon Linux may provide versioned Python packages such as `python3.11` or other versions. Check `dnf list available 'python*'` to see what your particular release offers.

---

# 🟠 5. Python Installation – Ubuntu

### 🔄 Update Package Index

```bash
sudo apt update
```

### 🔍 Search Python Packages

```bash
apt search python3
```

### 📋 List Available Python Packages

```bash
apt list 'python3*'
```

### 📋 List Installed Python Packages

```bash
apt list --installed 'python3*'
```

### 📦 Install Python 3

```bash
sudo apt install python3 -y
```

### 📦 Install pip

```bash
sudo apt install python3-pip -y
```

### 📦 Install Virtual Environment Support

```bash
sudo apt install python3-venv -y
```

### 📦 Install Development Headers

```bash
sudo apt install python3-dev build-essential -y
```

### 🔍 Get Package Information

```bash
apt show python3

apt show python3-pip
```

### 🔍 Verify Installation

```bash
python3 --version

pip3 --version
```

---

# 🔴 6. Python Installation – RHEL

## 🔴 RHEL 8 / 9 / 10

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🔍 Search Python Packages

```bash
dnf search python3
```

### 📋 List Available Python Packages

```bash
dnf list available 'python*'
```

### 📋 List Installed Python Packages

```bash
dnf list installed 'python*'
```

### 📦 Install Python 3

```bash
sudo dnf install python3 -y
```

### 📦 Install pip

```bash
sudo dnf install python3-pip -y
```

### 📦 Install Development Tools

```bash
sudo dnf install python3-devel gcc -y
```

### 🔍 Verify Installation

```bash
python3 --version

pip3 --version
```

## 🔴 RHEL 7

### 🔄 Update System

```bash
sudo yum update -y
```

### 🔍 Search Python Packages

```bash
yum search python3
```

### 📋 List Available Python Packages

```bash
yum list available 'python*'
```

### 📦 Install Python 3

```bash
sudo yum install python3 -y
```

### 📦 Install pip

```bash
sudo yum install python3-pip -y
```

### 🔍 Verify Installation

```bash
python3 --version

pip3 --version
```

> **Note:** Python versions available on RHEL 7 depend on enabled repositories and software collections. RHEL 7 is an older platform; use a supported RHEL release for new deployments.

---

# 🪟 7. Python Installation – Windows

Windows supports Python through the official installer, winget and Chocolatey.

### 🔍 Search Python Versions

```powershell
winget search Python.Python
```

### 📦 Install Python 3.15

```powershell
winget install --id Python.Python.3.15 -e
```

### 📦 Install Python 3.14

```powershell
winget install --id Python.Python.3.14 -e
```

### 📦 Install Using Chocolatey

```powershell
choco search python

choco install python --version=3.15.2 -y
```

> Chocolatey package versions can differ from the Python release version. Check the available package version before installing.

### 🔍 Verify Installation

```powershell
python --version

py --version

pip --version

py -0p
```

### 📂 Check Python Installation Path

```powershell
where.exe python

where.exe pip
```

### 📖 Official Download Page

https://www.python.org/downloads/windows/

> **Important:** During installation using the official Windows installer, select **Add Python to PATH** if you want to run Python from any terminal.

---

# 🍎 8. Python Installation – macOS

### 🔄 Update Homebrew

```bash
brew update
```

### 🔍 Search Python Packages

```bash
brew search python
```

### 📦 Install Latest Python Formula

```bash
brew install python
```

### 📦 Install a Specific Python Version

```bash
brew install python@3.14
```

### 🔍 Verify Installation

```bash
python3 --version

pip3 --version
```

### 📂 Check Installation Path

```bash
which python3

which pip3
```

### 📖 Official Download Page

https://www.python.org/downloads/macos/

> **Note:** Homebrew formula availability changes with time. Check `brew search python` for available versions.

---

# 🔍 9. Python Verification Commands

### 🐍 Check Python Version

```bash
python --version

python3 --version
```

### 📦 Check pip Version

```bash
pip --version

pip3 --version
```

### 📂 Locate Python Executable

```bash
# Linux / macOS
which python3

# Windows PowerShell
where.exe python
```

### 🔍 Display Python Installation Details

```bash
python3 -c "import sys; print(sys.version)"
```

### 📍 Display Python Executable Path

```bash
python3 -c "import sys; print(sys.executable)"
```

### 📋 Display Python Search Paths

```bash
python3 -c "import sys; print(sys.path)"
```

### 📋 List Python Environment Information

```bash
python3 -m site
```

---

# 📦 10. pip – Python Package Management

pip is the standard Python package installer used to install and manage third-party libraries from PyPI and other package indexes.

**Important:** Prefer `python -m pip` over calling `pip` directly. This ensures that pip runs using the intended Python interpreter.

### 🔍 Check pip Version

```bash
python -m pip --version
```

Linux:

```bash
python3 -m pip --version
```

Windows:

```powershell
py -m pip --version
```

### 🔄 Upgrade pip

```bash
python -m pip install --upgrade pip
```

### 🔍 Search PyPI Packages

```bash
python -m pip index versions requests
```

### 📦 Install a Package

```bash
python -m pip install requests
```

### 📦 Install Multiple Packages

```bash
python -m pip install requests flask django
```

### 📦 Install a Specific Package Version

```bash
python -m pip install requests==2.32.5
```

### 📋 List Installed Packages

```bash
python -m pip list
```

### 📋 List Outdated Packages

```bash
python -m pip list --outdated
```

### ℹ️ Display Package Information

```bash
python -m pip show requests
```

### 🔄 Upgrade a Package

```bash
python -m pip install --upgrade requests
```

### 🗑️ Uninstall a Package

```bash
python -m pip uninstall requests
```

### 📄 Export Installed Packages

```bash
python -m pip freeze > requirements.txt
```

### 📥 Install Packages from Requirements File

```bash
python -m pip install -r requirements.txt
```

### 🔍 Check Dependency Compatibility

```bash
python -m pip check
```

### 🧹 Clear pip Cache

```bash
python -m pip cache purge
```

### 📋 Display pip Configuration

```bash
python -m pip config list
```

---

# 🧪 11. Virtual Environment – venv

A virtual environment creates an isolated Python environment for a project.

It allows different projects to use different package versions without interfering with each other.

### 📂 Create Project Directory

```bash
mkdir PythonProject

cd PythonProject
```

### 🆕 Create Virtual Environment

```bash
python -m venv venv
```

Linux / macOS:

```bash
python3 -m venv venv
```

### ▶️ Activate Virtual Environment

**Linux / macOS – Bash**

```bash
source venv/bin/activate
```

**Windows – PowerShell**

```powershell
.\venv\Scripts\Activate.ps1
```

**Windows – CMD**

```cmd
venv\Scripts\activate.bat
```

### 🔍 Verify Active Environment

```bash
python --version

python -m pip --version
```

### 📦 Install Packages Inside Virtual Environment

```bash
python -m pip install requests flask
```

### 📋 List Environment Packages

```bash
python -m pip list
```

### ⏹️ Deactivate Virtual Environment

```bash
deactivate
```

### 🗑️ Delete Virtual Environment

Linux / macOS:

```bash
rm -rf venv
```

Windows PowerShell:

```powershell
Remove-Item -Recurse -Force .\venv
```

> **Best Practice:** Create a separate virtual environment for each Python project.

---

# 📋 12. requirements.txt Management

`requirements.txt` stores the Python dependencies required by a project.

### 📄 Create requirements.txt

```bash
touch requirements.txt
```

Windows:

```powershell
New-Item requirements.txt -ItemType File
```

### ✏️ Add Package Dependencies

Example:

```text
requests==2.32.5
flask==3.1.2
```

### 📦 Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### 📤 Export Dependencies

```bash
python -m pip freeze > requirements.txt
```

### 🔄 Upgrade Dependencies

```bash
python -m pip install --upgrade -r requirements.txt
```

### 🔍 Check Installed Dependencies

```bash
python -m pip check
```

---

# 🆕 13. Python Project Creation & Execution

### 📂 Create a Python File

```bash
touch app.py
```

Windows:

```powershell
New-Item app.py -ItemType File
```

### ✏️ Write Python Code

```python
print("Hello, World!")
```

### ▶️ Execute Python File

```bash
python app.py
```

Linux / macOS:

```bash
python3 app.py
```

Windows:

```powershell
py app.py
```

### 🐍 Open Python Interactive Shell

```bash
python
```

Or:

```bash
python3
```

### ⏹️ Exit Python Shell

```python
exit()
```

### 🧪 Run Python Code Directly

```bash
python -c "print('Hello from Python')"
```

### 📋 Compile Python Source File

```bash
python -m py_compile app.py
```

This creates a compiled `.pyc` file inside a `__pycache__` directory.

---

# 📚 14. Python Modules & Package Commands

A module is a Python file containing reusable code. A package is a collection of modules.

### 🔍 Display Python Module Information

```bash
python -c "import sys; print(sys.modules)"
```

### 📋 List Python Module Search Locations

```bash
python -c "import sys; print(sys.path)"
```

### 🔍 Check Whether a Module Is Installed

```bash
python -c "import requests; print(requests.__version__)"
```

### 📂 Display Installed Module Location

```bash
python -c "import requests; print(requests.__file__)"
```

### 📦 Install a Module

```bash
python -m pip install requests
```

### 🗑️ Uninstall a Module

```bash
python -m pip uninstall requests
```

### 📋 List Available Standard Library Modules

```bash
python -c "help('modules')"
```

---

# 🛠️ 15. Useful Python Commands

### 🔎 Display Python Help

```bash
python --help
```

### 🔎 Display pip Help

```bash
python -m pip --help
```

### 📋 Display Python Build Configuration

```bash
python -m sysconfig
```

### 🧠 Display Python Memory Information

```bash
python -c "import sys; print(sys.getsizeof([]))"
```

### 📊 Display Python Platform Information

```bash
python -c "import platform; print(platform.platform())"
```

### 🖥️ Display Processor Architecture

```bash
python -c "import platform; print(platform.architecture())"
```

### 🔍 Display Python Implementation

```bash
python -c "import platform; print(platform.python_implementation())"
```

---

# 🔄 16. Managing Multiple Python Versions

Multiple Python versions can be installed on the same machine.

For example:

- Python 3.11
- Python 3.12
- Python 3.13
- Python 3.14
- Python 3.15

### 🐧 Linux – List Installed Versions

```bash
python --version

python3 --version

python3.14 --version

python3.15 --version
```

The version-specific commands work only if those interpreters are installed.

### 🐧 Ubuntu – Check Available Alternatives

```bash
update-alternatives --list python3
```

> Ubuntu generally manages system Python through its distribution packages. Avoid changing the system Python default using `update-alternatives`, as OS utilities may depend on it.

### 🪟 Windows – Python Launcher

List installed Python versions:

```powershell
py -0p
```

Run Python 3.14:

```powershell
py -3.14
```

Run Python 3.15:

```powershell
py -3.15
```

Create a virtual environment using Python 3.15:

```powershell
py -3.15 -m venv venv
```

### 🍎 macOS – Homebrew

List installed Python formulas:

```bash
brew list --formula | grep python
```

Check a particular version:

```bash
python3.14 --version
```

### ⚙️ Use pyenv for Version Management

`pyenv` helps install and switch between multiple Python versions on supported Unix-like systems.

**macOS – Homebrew**

```bash
brew install pyenv
```

**Linux – pyenv installer**

```bash
curl -fsSL https://pyenv.run | bash
```

Configure Bash:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc

echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc

echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc

source ~/.bashrc
```

List available Python versions:

```bash
pyenv install --list
```

Install a specific version:

```bash
pyenv install 3.14.10
```

List installed versions:

```bash
pyenv versions
```

Set global Python version:

```bash
pyenv global 3.14.10
```

Set project-specific version:

```bash
pyenv local 3.14.10
```

Verify:

```bash
python --version
```

> **Note:** `pyenv` is a version manager, not a replacement for system Python. Windows users can use the Python Launcher or pyenv-win instead.

---

# 📦 17. pipx – Python CLI Application Management

pipx installs Python command-line applications in isolated environments.

It is useful for tools such as Black, Poetry and HTTPie.

### 🍎 macOS – Homebrew

```bash
brew install pipx

pipx ensurepath
```

### 🐧 Linux

```bash
python3 -m pip install --user pipx

python3 -m pipx ensurepath
```

### 🪟 Windows – PowerShell

```powershell
py -m pip install --user pipx

py -m pipx ensurepath
```

### 📦 Install a CLI Tool

```bash
pipx install httpie
```

### 📋 List Installed Tools

```bash
pipx list
```

### 🔄 Upgrade Tools

```bash
pipx upgrade-all
```

### 🗑️ Uninstall a Tool

```bash
pipx uninstall httpie
```

---

# 🐳 18. Python Docker Commands

Python applications can also run inside Docker containers.

### 📥 Pull Python Image

```bash
docker pull python:3.15
```

### 📥 Pull Python 3.14 Image

```bash
docker pull python:3.14
```

### 📋 List Python Images

```bash
docker images
```

### ▶️ Run Python Container

```bash
docker run --rm python:3.15 python --version
```

### 🐍 Run Interactive Python Shell

```bash
docker run --rm -it python:3.15 python
```

### 📂 Mount Local Project into Container

```bash
docker run --rm -it \
-v "$PWD":/app \
-w /app \
python:3.15 \
python app.py
```

---

# 🧹 19. Python Uninstallation

### 🐧 Amazon Linux 2

```bash
sudo yum remove python3-pip -y
```

### 🐧 Amazon Linux 2023

```bash
sudo dnf remove python3-pip -y
```

### 🟠 Ubuntu

```bash
sudo apt remove python3-pip -y
```

### 🔴 RHEL

```bash
sudo dnf remove python3-pip -y
```

### 🪟 Windows

```powershell
winget uninstall --id Python.Python.3.15 -e
```

### 🍎 macOS

```bash
brew uninstall python
```

> ⚠️ **Warning:** These examples remove pip, not necessarily the complete Python installation. Avoid removing the system Python from Linux distributions. For Windows and macOS, use the same installation method to uninstall the corresponding Python version.

---

# ⚠️ 20. Important Notes & Best Practices

- 🐍 Python 2 is obsolete and should not be selected for new development.
- 🚀 Prefer actively supported Python 3 versions.
- 📦 Use `pip` to install third-party Python libraries.
- 🧪 Use `venv` to isolate project dependencies.
- 🔒 Avoid installing project packages globally.
- ⚙️ Prefer `python -m pip` to avoid installing packages into the wrong Python environment.
- 📋 Use `requirements.txt` to document dependencies.
- 🏗️ Use compatible Python versions for frameworks such as Django, Flask and FastAPI.
- 🛡️ Never blindly replace or remove the system Python on Linux.
- 🔄 Keep Python, pip and project dependencies updated.
- 🐳 Use official Python Docker images for containerized applications.

---

# 📖 21. Official Documentation

| Resource | Official Link |
|---|---|
| 🐍 Python Official Website | https://www.python.org/ |
| 📥 Python Downloads | https://www.python.org/downloads/ |
| 📚 Python Documentation | https://docs.python.org/3/ |
| 📦 pip Documentation | https://pip.pypa.io/en/stable/ |
| 📋 PyPI | https://pypi.org/ |
| 🧪 Virtual Environments | https://docs.python.org/3/library/venv.html |
| 📦 Python Packaging Guide | https://packaging.python.org/ |
| 🔄 pyenv | https://github.com/pyenv/pyenv |
| 🪟 Python on Windows | https://docs.python.org/3/using/windows.html |
| 🍎 Python on macOS | https://docs.python.org/3/using/mac.html |
| 🐧 Python on Linux | https://docs.python.org/3/using/unix.html |

---

# 🎯 Happy Learning & Automating!

**Learn · Install · Configure · Code · Package · Automate** 🚀