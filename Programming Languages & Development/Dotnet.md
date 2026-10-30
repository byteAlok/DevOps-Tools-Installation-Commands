# 💠 .NET – Installation & Commands Guide

A practical guide to installing, configuring and managing both legacy .NET Framework and modern .NET across different operating systems.

## 📌 1. Introduction

.NET is a developer platform created by Microsoft for building desktop applications, web applications, APIs, cloud services and enterprise software.

### 🕰️ .NET Generations

| Technology | Versions | Platform |
|---|---|---|
| 🏛️ .NET Framework | 1.0 – 4.8.1 | Primarily Windows |
| 🔄 .NET Core | 1.0 – 3.1 | Cross-platform |
| 🚀 Modern .NET | 5, 6, 7, 8, 9, 10 | Cross-platform |

**Important:** .NET Core was renamed to .NET starting with .NET 5. Modern .NET is the continuation of .NET Core.

### 🧩 .NET Components

| Component | Purpose |
|---|---|
| 💻 .NET SDK | Develop, build and publish applications |
| ⚙️ .NET Runtime | Run .NET applications |
| 🌐 ASP.NET Core Runtime | Run ASP.NET Core applications |
| 📦 NuGet | Package and dependency management |
| 🔧 C# Compiler | Compile C# source code |
| 🏗️ MSBuild | Build applications and projects |

---

# 🖥️ 2. Supported Operating Systems

| Operating System | .NET Framework | Modern .NET |
|---|---|---|
| 🐧 Amazon Linux 2 | ❌ | Not a recommended supported target |
| 🐧 Amazon Linux 2023 | ❌ | ✅ |
| 🟠 Ubuntu | ❌ | ✅ |
| 🔴 RHEL | ❌ | ✅ |
| 🪟 Windows | ✅ | ✅ |
| 🍎 macOS | ❌ | ✅ |

> **Important:** .NET Framework is Windows-specific. Modern .NET supports Linux, Windows and macOS, subject to the supported OS and architecture requirements for each release.

---

# 🏛️ 3. Old .NET – .NET Framework

.NET Framework is Microsoft's older development platform, primarily used for Windows-based applications.

### 📚 Common .NET Framework Versions

| Version | Release Year |
|---|---:|
| .NET Framework 2.0 | 2005 |
| .NET Framework 3.5 | 2007 |
| .NET Framework 4.0 | 2010 |
| .NET Framework 4.5 | 2012 |
| .NET Framework 4.6 | 2015 |
| .NET Framework 4.7 | 2017 |
| .NET Framework 4.8 | 2019 |
| .NET Framework 4.8.1 | 2022 |

## 🪟 3.1 Install .NET Framework on Windows

Official download page:

https://dotnet.microsoft.com/en-us/download/dotnet-framework

### 📦 Install .NET Framework 4.8.1 Developer Pack

The Developer Pack includes the reference assemblies and targeting pack required to develop applications targeting that framework version.

Download:

https://dotnet.microsoft.com/en-us/download/dotnet-framework/net481

Run the downloaded installer:

```powershell
# Install downloaded Developer Pack
Start-Process ".\ndp481-devpack-enu.exe" -Wait
```

### ⚙️ Install .NET Framework 3.5

.NET Framework 3.5 can be enabled as a Windows feature.

```powershell
# Enable .NET Framework 3.5
Enable-WindowsOptionalFeature `
-Online `
-FeatureName NetFx3 `
-All
```

Check whether the feature is enabled:

```powershell
Get-WindowsOptionalFeature `
-Online `
-FeatureName NetFx3
```

### 🔍 Check Installed .NET Framework Version

```powershell
# Check .NET Framework 4.x release information
Get-ItemProperty `
'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full' `
-Name Release
```

Check installed .NET Framework versions:

```powershell
Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP' -Recurse |
Get-ItemProperty -Name Version -ErrorAction SilentlyContinue |
Select-Object PSChildName, Version
```

### 🔎 Check .NET Framework Developer Packs

Open Visual Studio Installer and check installed components under:

```text
Individual Components
    → .NET Framework Targeting Packs
    → .NET Framework SDKs
```

### 🛠️ Build a Legacy .NET Framework Application

For legacy .NET Framework projects, Visual Studio with the appropriate Developer Pack is generally recommended.

Open the solution:

```powershell
devenv MyApplication.sln
```

Build using MSBuild:

```powershell
MSBuild.exe MyApplication.sln /p:Configuration=Release
```

> **Note:** `MSBuild.exe` must be available in PATH or executed from the Visual Studio Developer Command Prompt.

---

# 🚀 4. Modern .NET – Version Information

Modern .NET is the cross-platform development platform used for building web APIs, MVC applications, desktop applications, cloud services and more.

### 📚 Version History

| Version | Release Year | Support Type |
|---|---:|---|
| .NET Core 1.0 | 2016 | EOL |
| .NET Core 2.0 | 2017 | EOL |
| .NET Core 2.1 | 2018 | EOL |
| .NET Core 3.1 | 2019 | EOL |
| .NET 5 | 2020 | EOL |
| .NET 6 | 2021 | EOL |
| .NET 7 | 2022 | EOL |
| .NET 8 | 2023 | LTS |
| .NET 9 | 2024 | STS |
| .NET 10 | 2025 | LTS |

### ⭐ Current Recommended Version

| Version | Release Type | End of Support |
|---|---|---|
| .NET 10 | LTS | November 2028 |
| .NET 9 | STS | November 10, 2026 |
| .NET 8 | LTS | November 10, 2026 |

> **Recommendation:** Use .NET 10 for new development. Always check the official support policy before selecting a version for production.

---

# 📦 5. Modern .NET – Package Management Commands

These commands help search, list, inspect, install, update and remove .NET packages.

### 🔍 Search .NET Packages

```bash
# Amazon Linux 2023 / RHEL
dnf search dotnet

# Amazon Linux 2
yum search dotnet

# Ubuntu
apt search dotnet
```

### 📋 List Available .NET Packages

```bash
# Amazon Linux 2023 / RHEL
dnf list available 'dotnet*'

# Amazon Linux 2
yum list available 'dotnet*'

# Ubuntu
apt list 'dotnet*'
```

### 📋 List Installed .NET Packages

```bash
# Amazon Linux 2023 / RHEL
dnf list installed 'dotnet*'

# Amazon Linux 2
yum list installed 'dotnet*'

# Ubuntu
apt list --installed 'dotnet*'
```

### ℹ️ Get Package Information

```bash
# DNF
dnf info dotnet-sdk-10.0

# YUM
yum info dotnet-sdk-10.0

# Ubuntu
apt show dotnet-sdk-10.0
```

### 🗑️ Remove .NET SDK Package

```bash
# DNF
sudo dnf remove dotnet-sdk-10.0 -y

# YUM
sudo yum remove dotnet-sdk-10.0 -y

# Ubuntu
sudo apt remove dotnet-sdk-10.0 -y
```

> **Note:** Package availability depends on the operating system version and enabled repositories. Amazon Linux 2 does not have the same supported .NET package setup as Amazon Linux 2023.

---

# 🐧 6. Modern .NET Installation – Amazon Linux

## 🐧 6.1 Amazon Linux 2023

Amazon Linux 2023 provides .NET SDK and runtime packages through DNF.

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🔍 Search .NET Packages

```bash
dnf search dotnet
```

### 📋 List Available Packages

```bash
dnf list available 'dotnet*'
```

### 📋 List Installed Packages

```bash
dnf list installed 'dotnet*'
```

### 📦 Install .NET 10 SDK

```bash
sudo dnf install dotnet-sdk-10.0 -y
```

### ⚙️ Install Only .NET Runtime

```bash
sudo dnf install dotnet-runtime-10.0 -y
```

### 🌐 Install ASP.NET Core Runtime

```bash
sudo dnf install aspnetcore-runtime-10.0 -y
```

### 🔍 Verify Installation

```bash
dotnet --version
dotnet --info
dotnet --list-sdks
dotnet --list-runtimes
```

## 🐧 6.2 Amazon Linux 2

Amazon Linux 2 does not have the same current .NET package support as Amazon Linux 2023.

For learning or compatible environments, you can use Microsoft's installation script.

### 📥 Download Installation Script

```bash
curl -L https://dot.net/v1/dotnet-install.sh \
-o dotnet-install.sh
```

### 🔐 Give Execute Permission

```bash
chmod +x dotnet-install.sh
```

### 📦 Install .NET 10 SDK

```bash
./dotnet-install.sh --channel 10.0
```

### ⚙️ Configure PATH

```bash
echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc

echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc

source ~/.bashrc
```

### 🔍 Verify

```bash
dotnet --version
dotnet --info
```

> **Important:** The installation script does not guarantee that every Linux distribution is supported. Amazon Linux 2 is an older platform; check its dependencies and compatibility before using modern .NET in production. Prefer Amazon Linux 2023 for new deployments.

---

# 🟠 7. Modern .NET Installation – Ubuntu

### 🔄 Update Package Index

```bash
sudo apt update
```

### 🔍 Search .NET Packages

```bash
apt search dotnet
```

### 📋 List Available .NET Packages

```bash
apt list 'dotnet*'
```

### 📋 List Installed .NET Packages

```bash
apt list --installed 'dotnet*'
```

### 📦 Install .NET 10 SDK

```bash
sudo apt update

sudo apt install dotnet-sdk-10.0 -y
```

### ⚙️ Install .NET Runtime Only

```bash
sudo apt install dotnet-runtime-10.0 -y
```

### 🌐 Install ASP.NET Core Runtime

```bash
sudo apt install aspnetcore-runtime-10.0 -y
```

### 🔍 Get Package Information

```bash
apt show dotnet-sdk-10.0
```

### 🔍 Verify Installation

```bash
dotnet --version
dotnet --info
dotnet --list-sdks
dotnet --list-runtimes
```

> **Note:** These package commands apply to supported Ubuntu versions and repositories. On Ubuntu 24.04, .NET 10 is available through the Ubuntu package feed. Package availability differs across Ubuntu releases.

---

# 🔴 8. Modern .NET Installation – RHEL

RHEL 8, RHEL 9 and RHEL 10 provide .NET packages through their AppStream repositories.

### 🔄 Update System

```bash
sudo dnf update -y
```

### 🔍 Search .NET Packages

```bash
dnf search dotnet
```

### 📋 List Available Packages

```bash
dnf list available 'dotnet*'
```

### 📋 List Installed Packages

```bash
dnf list installed 'dotnet*'
```

### 📦 Install .NET 10 SDK

```bash
sudo dnf install dotnet-sdk-10.0 -y
```

### ⚙️ Install .NET Runtime

```bash
sudo dnf install dotnet-runtime-10.0 -y
```

### 🌐 Install ASP.NET Core Runtime

```bash
sudo dnf install aspnetcore-runtime-10.0 -y
```

### ℹ️ Package Information

```bash
dnf info dotnet-sdk-10.0
```

### 🔍 Verify Installation

```bash
dotnet --version
dotnet --info
dotnet --list-sdks
dotnet --list-runtimes
```

---

# 🪟 9. Modern .NET Installation – Windows

Windows supports both .NET Framework and modern .NET.

### 🔍 Search .NET SDK

```powershell
winget search Microsoft.DotNet.SDK
```

### 📦 Install .NET 10 SDK

```powershell
winget install --id Microsoft.DotNet.SDK.10 -e
```

### ⚙️ Install .NET Runtime

```powershell
winget search Microsoft.DotNet.Runtime
```

### 🌐 Install ASP.NET Core Runtime

```powershell
winget search Microsoft.DotNet.AspNetCore
```

Select the appropriate version from the search results.

### 🔍 Verify Installation

```powershell
dotnet --version

dotnet --info

dotnet --list-sdks

dotnet --list-runtimes
```

### 📂 Check Installation Path

```powershell
where.exe dotnet
```

### 📖 Official Download Page

https://dotnet.microsoft.com/en-us/download

---

# 🍎 10. Modern .NET Installation – macOS

### 🔄 Update Homebrew

```bash
brew update
```

### 🔍 Search .NET Packages

```bash
brew search dotnet
```

### 📦 Install .NET SDK

```bash
brew install --cask dotnet-sdk
```

### 🔍 Verify Installation

```bash
dotnet --version

dotnet --info

dotnet --list-sdks

dotnet --list-runtimes
```

### 📂 Check Installation Path

```bash
which dotnet
```

### 📖 Official Download Page

https://dotnet.microsoft.com/en-us/download

> **Note:** Select the correct SDK architecture for your Mac. Apple Silicon uses ARM64, while Intel Macs use x64.

---

# 🔍 11. .NET SDK & Runtime Verification Commands

These commands work on supported Windows, Linux and macOS installations.

### ☑️ Check .NET Version

```bash
dotnet --version
```

### ℹ️ Display Detailed .NET Information

```bash
dotnet --info
```

### 📋 List Installed SDKs

```bash
dotnet --list-sdks
```

### 📋 List Installed Runtimes

```bash
dotnet --list-runtimes
```

### 🔎 Display .NET Environment Information

```bash
dotnet --diagnostics
```

### 📂 Locate dotnet Executable

```bash
# Linux / macOS
which dotnet
```

Windows PowerShell:

```powershell
where.exe dotnet
```

---

# 🏗️ 12. Create a .NET Project

The .NET CLI is used to create, build, run and publish .NET applications.

### 📋 List Available Project Templates

```bash
dotnet new list
```

### 🆕 Create Console Application

```bash
dotnet new console -n MyConsoleApp
```

### 🆕 Create ASP.NET Core Web API

```bash
dotnet new webapi -n MyWebAPI
```

### 🆕 Create ASP.NET Core MVC Application

```bash
dotnet new mvc -n MyMVCApp
```

### 🆕 Create Razor Pages Application

```bash
dotnet new webapp -n MyWebApp
```

### 🆕 Create Class Library

```bash
dotnet new classlib -n MyLibrary
```

### 📂 Move into Project Directory

```bash
cd MyWebAPI
```

---

# ⚙️ 13. .NET Build & Execution Commands

### 📦 Restore Dependencies

```bash
dotnet restore
```

### 🏗️ Build Application

```bash
dotnet build
```

### 🚀 Build in Release Mode

```bash
dotnet build -c Release
```

### ▶️ Run Application

```bash
dotnet run
```

### 🧪 Run Tests

```bash
dotnet test
```

### 📦 Publish Application

```bash
dotnet publish -c Release
```

### 📂 Publish to a Specific Folder

```bash
dotnet publish -c Release -o ./publish
```

### 🧹 Clean Build Output

```bash
dotnet clean
```

### 🔄 Rebuild Application

```bash
dotnet build --no-incremental
```

---

# 📚 14. NuGet Package Management Commands

NuGet is the package manager used by the .NET ecosystem to manage libraries and dependencies.

### 🔍 Search NuGet Packages

```bash
dotnet package search Newtonsoft.Json
```

### 📦 Add a NuGet Package

```bash
dotnet add package Newtonsoft.Json
```

### 📋 List Project Packages

```bash
dotnet list package
```

### 📋 List Outdated Packages

```bash
dotnet list package --outdated
```

### 🔄 Update a Package

```bash
dotnet add package Newtonsoft.Json
```

The command adds the requested package version or updates the package reference to the version resolved by NuGet.

### 🗑️ Remove a Package

```bash
dotnet remove package Newtonsoft.Json
```

### 🔍 List NuGet Sources

```bash
dotnet nuget list source
```

### ➕ Add NuGet Source

```bash
dotnet nuget add source https://api.nuget.org/v3/index.json \
--name nuget.org
```

---

# 🧰 15. .NET Tool Management Commands

.NET tools are command-line utilities that extend the .NET CLI.

### 🔍 Search .NET Tools

```bash
dotnet tool search dotnet
```

### 📦 Install Global Tool

```bash
dotnet tool install --global dotnet-ef
```

### 📋 List Installed Global Tools

```bash
dotnet tool list --global
```

### 📦 Install Local Tool

```bash
dotnet tool install dotnet-ef
```

### 🔄 Update Global Tool

```bash
dotnet tool update --global dotnet-ef
```

### 🗑️ Uninstall Global Tool

```bash
dotnet tool uninstall --global dotnet-ef
```

### 🔍 Check EF Core CLI Version

```bash
dotnet ef --version
```

---

# 🔄 16. Multiple .NET SDK Versions

Multiple .NET SDK versions can be installed on the same system.

### 📋 List Installed SDKs

```bash
dotnet --list-sdks
```

### 📋 List Installed Runtimes

```bash
dotnet --list-runtimes
```

### ⚙️ Create global.json

A `global.json` file can specify which SDK version a project should use.

```bash
dotnet new globaljson --sdk-version 10.0.100
```

Example `global.json`:

```json
{
  "sdk": {
    "version": "10.0.100",
    "rollForward": "latestFeature"
  }
}
```

Check the SDK selected by the current directory:

```bash
dotnet --version
```

> **Note:** Replace `10.0.100` with an SDK version actually installed on your machine. `global.json` controls SDK selection; it does not install an SDK.

---

# 🐳 17. .NET Docker Commands

.NET applications can also be built and executed inside Docker containers.

### 📥 Pull .NET SDK Image

```bash
docker pull mcr.microsoft.com/dotnet/sdk:10.0
```

### 📥 Pull ASP.NET Core Runtime Image

```bash
docker pull mcr.microsoft.com/dotnet/aspnet:10.0
```

### 📥 Pull .NET Runtime Image

```bash
docker pull mcr.microsoft.com/dotnet/runtime:10.0
```

### 🔍 List .NET Images

```bash
docker images
```

### ▶️ Run .NET SDK Container

```bash
docker run --rm -it \
mcr.microsoft.com/dotnet/sdk:10.0 \
dotnet --info
```

---

# 🧹 18. Modern .NET Uninstallation

Remove the SDK or runtime using the same installation method and package manager.

### 🐧 Amazon Linux 2023

```bash
sudo dnf remove dotnet-sdk-10.0 -y
```

### 🟠 Ubuntu

```bash
sudo apt remove dotnet-sdk-10.0 -y

sudo apt autoremove -y
```

### 🔴 RHEL

```bash
sudo dnf remove dotnet-sdk-10.0 -y
```

### 🪟 Windows

```powershell
winget uninstall --id Microsoft.DotNet.SDK.10 -e
```

### 🍎 macOS

```bash
brew uninstall --cask dotnet-sdk
```

> **Note:** If multiple SDKs or runtimes are installed, remove only the version you no longer need. Shared host components and other applications may depend on them.

---

# ⚠️ 19. Important Notes

- 🏛️ .NET Framework is a legacy Windows-focused platform.
- 🚀 Modern .NET is cross-platform and is the recommended choice for new development.
- 🔄 .NET Core was renamed to .NET starting with version 5.
- 💻 SDK is required to develop and build applications.
- ⚙️ Runtime is sufficient when you only need to execute an application and the required runtime is not bundled with it.
- 🌐 ASP.NET Core Runtime is needed to run framework-dependent ASP.NET Core applications.
- 📦 NuGet is used to manage .NET libraries and dependencies.
- 🧩 Visual Studio is commonly used for .NET Framework development.
- 🛡️ Always use supported versions for production applications.
- 🔐 Keep the SDK and runtime updated with security patches.

---

# 📖 20. Official Documentation

| Resource | Official Link |
|---|---|
| 💠 .NET Official Website | https://dotnet.microsoft.com/ |
| 📥 .NET Downloads | https://dotnet.microsoft.com/en-us/download |
| 🏛️ .NET Framework Downloads | https://dotnet.microsoft.com/en-us/download/dotnet-framework |
| 📚 .NET Documentation | https://learn.microsoft.com/en-us/dotnet/ |
| 🔄 .NET Support Policy | https://dotnet.microsoft.com/en-us/platform/support/policy |
| 🐧 .NET on Linux | https://learn.microsoft.com/en-us/dotnet/core/install/linux |
| 🐧 .NET on Ubuntu | https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu-install |
| ☁️ .NET on Amazon Linux | https://docs.aws.amazon.com/linux/al2023/ug/dotnet.html |
| 🔴 .NET on RHEL | https://learn.microsoft.com/en-us/dotnet/core/install/linux-rhel |
| 🪟 .NET on Windows | https://learn.microsoft.com/en-us/dotnet/core/install/windows |
| 🍎 .NET on macOS | https://learn.microsoft.com/en-us/dotnet/core/install/macos |
| 📦 NuGet | https://www.nuget.org/ |
| 🔧 .NET CLI | https://learn.microsoft.com/en-us/dotnet/core/tools/ |

---

# 🎯 Happy Learning & Building!

**Learn · Install · Configure · Develop · Build · Deploy** 🚀