# ☕ Java – Installation & Commands Guide

A practical guide to installing, configuring and managing Java across different operating systems.

## 📌 1. Introduction

Java is a high-level, object-oriented programming language and platform used to develop web applications, enterprise software, backend services and distributed systems.

**Key Components:**

- ☕ JDK – Java Development Kit
- ⚙️ JRE – Java Runtime Environment
- 🚀 JVM – Java Virtual Machine
- 📦 JAR – Java Archive
- 🔧 javac – Java Compiler
- ▶️ java – Java Application Launcher

## 🖥️ 2. Supported Operating Systems

| Operating System | Package Manager |
|---|---|
| 🐧 Amazon Linux 2 | YUM |
| 🐧 Amazon Linux 2023 | DNF |
| 🟠 Ubuntu | APT |
| 🔴 RHEL 7 | YUM |
| 🔴 RHEL 8 / 9 / 10 | DNF |
| 🪟 Windows | winget / Chocolatey |
| 🍎 macOS | Homebrew |

## 📦 3. Package Management Commands

### 🔍 Search Java Packages

```bash
# Amazon Linux 2 / RHEL 7
yum search java

# Amazon Linux 2023 / RHEL 8+
dnf search java

# Ubuntu
apt search openjdk
```

### 📋 List Available Java Packages

```bash
# YUM
yum list java*

# DNF
dnf list java*

# Ubuntu
apt list 'openjdk*'
```

### 📋 List Installed Java Packages

```bash
# YUM
yum list installed java*

# DNF
dnf list installed java*

# Ubuntu
apt list --installed 'openjdk*'
```

### ℹ️ Get Java Package Information

```bash
# YUM
yum info java-21-amazon-corretto-devel

# DNF
dnf info java-21-amazon-corretto-devel

# Ubuntu
apt show openjdk-21-jdk
```

### 🔎 Search Java 21 Packages

```bash
# YUM
yum search java-21

# DNF
dnf search java-21

# Ubuntu
apt search openjdk-21
```

### 📦 List Available Java Versions

```bash
# Amazon Linux 2 / RHEL 7
yum list available '*java*'

# Amazon Linux 2023 / RHEL 8+
dnf list available '*java*'

# Ubuntu
apt search openjdk
```

### 🗑️ Remove Java Packages

```bash
# YUM
sudo yum remove java-21-amazon-corretto-devel -y

# DNF
sudo dnf remove java-21-amazon-corretto-devel -y

# Ubuntu
sudo apt remove openjdk-21-jdk -y
```

> **Note:** Package names depend on the distribution and enabled repositories. Use the search and list commands to confirm the exact package name before installing.

---

## ☕ 4. Java Installation – Amazon Corretto 21 / OpenJDK 21

### 🐧 Amazon Linux 2

```bash
# Update system
sudo yum update -y

# Search Java packages
yum search java-21

# List available Java packages
yum list java*

# Install Amazon Corretto 21 JDK
sudo yum install java-21-amazon-corretto-devel -y

# Verify Java
java -version
javac -version
```

### 🐧 Amazon Linux 2023

```bash
# Update system
sudo dnf update -y

# Search Java packages
dnf search java-21

# List available Java packages
dnf list java*

# Install Amazon Corretto 21 JDK
sudo dnf install java-21-amazon-corretto-devel -y

# Verify Java
java -version
javac -version
```

### 🟠 Ubuntu

```bash
# Update package index
sudo apt update

# Search Java packages
apt search openjdk-21

# List available Java packages
apt list 'openjdk*'

# Install OpenJDK 21
sudo apt install openjdk-21-jdk -y

# Verify Java
java -version
javac -version
```

### 🔴 RHEL 8 / 9 / 10

```bash
# Update system
sudo dnf update -y

# Search Java packages
dnf search java-21

# List available Java packages
dnf list java*

# Install OpenJDK 21
sudo dnf install java-21-openjdk-devel -y

# Verify Java
java -version
javac -version
```

### 🔴 RHEL 7

```bash
# Update system
sudo yum update -y

# Search Java packages
yum search java

# List available Java packages
yum list java*

# Install an available OpenJDK development package
sudo yum install java-11-openjdk-devel -y

# Verify Java
java -version
javac -version
```

> **Note:** RHEL 7 repositories generally do not provide the same Java 21 package availability as modern distributions. The Java 11 example depends on the enabled repositories. RHEL 7 is also an older platform; use a supported OS for new environments.

### 🪟 Windows – PowerShell

**Using winget:**

```powershell
# Search Java packages
winget search EclipseAdoptium.Temurin.21.JDK

# Install Java 21 JDK
winget install --id EclipseAdoptium.Temurin.21.JDK -e

# Verify Java
java -version
javac -version
```

**Using Chocolatey:**

```powershell
# Search Java packages
choco search temurin

# Install Java 21
choco install temurin21 -y

# Verify
java -version
javac -version
```

### 🍎 macOS – Homebrew

```bash
# Update Homebrew
brew update

# Search Java packages
brew search openjdk

# Install OpenJDK 21
brew install openjdk@21

# Verify
java -version
javac -version
```

---

## 🔍 5. Java Verification Commands

### ☕ Check Java Version

```bash
java -version
```

### 🔧 Check Java Compiler Version

```bash
javac -version
```

### 📍 Locate Java Executable

```bash
# Linux
which java

# macOS
which java

# Windows PowerShell
where.exe java
```

### 📂 Find Java Installation Path

```bash
# Linux
readlink -f $(which java)

# macOS
/usr/libexec/java_home -V

# Windows PowerShell
(Get-Command java).Source
```

### 🔎 Check Java Environment Variable

```bash
echo $JAVA_HOME
```

Windows PowerShell:

```powershell
$env:JAVA_HOME
```

---

## ⚙️ 6. JAVA_HOME Configuration

`JAVA_HOME` is an environment variable that points to the Java installation directory.

Many tools, including Maven, Jenkins and Java-based applications, use this variable to locate Java.

### 🐧 Amazon Linux / Ubuntu / RHEL

Find the Java installation path:

```bash
readlink -f $(which java)
```

Example output:

```text
/usr/lib/jvm/java-21-amazon-corretto/bin/java
```

Set JAVA_HOME:

```bash
export JAVA_HOME=/usr/lib/jvm/java-21-amazon-corretto

export PATH=$JAVA_HOME/bin:$PATH
```

Verify:

```bash
echo $JAVA_HOME
java -version
javac -version
```

To make the configuration persistent for Bash:

```bash
echo 'export JAVA_HOME=/usr/lib/jvm/java-21-amazon-corretto' >> ~/.bashrc

echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc

source ~/.bashrc
```

> **Important:** The example path is for illustration. Use the actual installation directory returned by your system.

### 🪟 Windows – PowerShell

Find Java installation path:

```powershell
(Get-Command java).Source
```

Set JAVA_HOME for the current session:

```powershell
$env:JAVA_HOME = "C:\Program Files\Eclipse Adoptium\jdk-21"

$env:Path = "$env:JAVA_HOME\bin;$env:Path"
```

Verify:

```powershell
$env:JAVA_HOME

java -version
javac -version
```

To permanently set JAVA_HOME:

```powershell
[Environment]::SetEnvironmentVariable(
    "JAVA_HOME",
    "C:\Program Files\Eclipse Adoptium\jdk-21",
    "Machine"
)
```

Open a new terminal after changing the permanent environment variable.

### 🍎 macOS

Find installed Java versions:

```bash
/usr/libexec/java_home -V
```

Set Java 21 for the current terminal:

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 21)

export PATH=$JAVA_HOME/bin:$PATH
```

Verify:

```bash
echo $JAVA_HOME
java -version
```

---

## 🔄 7. Managing Multiple Java Versions

Sometimes multiple Java versions are installed on the same machine.

For example:

- Java 17
- Java 21
- Java 25

You can switch between installed versions using the available system tools.

### 🐧 Amazon Linux / RHEL

List installed Java versions:

```bash
sudo alternatives --config java
```

Switch Java version:

```bash
sudo alternatives --config javac
```

Check active version:

```bash
java -version
javac -version
```

### 🟠 Ubuntu

List available Java alternatives:

```bash
sudo update-alternatives --list java
```

Switch Java version:

```bash
sudo update-alternatives --config java
```

Switch compiler:

```bash
sudo update-alternatives --config javac
```

Verify:

```bash
java -version
javac -version
```

### 🪟 Windows – PowerShell

Change Java version for the current terminal:

```powershell
$env:JAVA_HOME = "C:\Program Files\Eclipse Adoptium\jdk-21"

$env:Path = "$env:JAVA_HOME\bin;" + (($env:Path -split ';' | Where-Object { $_ -notmatch 'Java|jdk' }) -join ';')

java -version
```

For permanent configuration, update `JAVA_HOME` and the system PATH through Windows Environment Variables.

### 🍎 macOS

List installed Java versions:

```bash
/usr/libexec/java_home -V
```

Select Java 21:

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 21)
```

Select Java 17:

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 17)
```

Verify:

```bash
java -version
```

---

## 🧪 8. Java Program Execution

### 📝 Create a Java File

```bash
nano HelloWorld.java
```

Add the following code:

```java
public class HelloWorld {

    public static void main(String[] args) {

        System.out.println("Hello, World!");

    }

}
```

### 🔧 Compile Java Program

```bash
javac HelloWorld.java
```

This generates:

```text
HelloWorld.class
```

### ▶️ Execute Java Program

```bash
java HelloWorld
```

Output:

```text
Hello, World!
```

### ⚡ Execute a Single Java Source File

Java 11 and later support source-file execution:

```bash
java HelloWorld.java
```

---

## 📦 9. JAR File Commands

JAR stands for Java Archive. It packages Java classes and resources into a single archive.

### 📦 Create JAR File

```bash
jar cf application.jar HelloWorld.class
```

### 📋 List JAR Contents

```bash
jar tf application.jar
```

### 🔍 Extract JAR File

```bash
jar xf application.jar
```

### ▶️ Run Executable JAR

```bash
java -jar application.jar
```

---

## 🛠️ 10. Useful Java Commands

### 🔍 Display Java Properties

```bash
java -XshowSettings:properties -version
```

### 🧠 Display JVM Memory Information

```bash
java -XshowSettings:vm -version
```

### 📋 List Java Processes

```bash
jps -l
```

### 🔎 Display Java Process Details

```bash
jcmd
```

### 📊 Display JVM Version Details

```bash
java -Xinternalversion
```

### 📖 Display Java Help

```bash
java --help
javac --help
jar --help
```

---

## 🧹 11. Java Uninstallation

### 🐧 Amazon Linux 2

```bash
sudo yum remove java-21-amazon-corretto-devel -y
```

### 🐧 Amazon Linux 2023

```bash
sudo dnf remove java-21-amazon-corretto-devel -y
```

### 🟠 Ubuntu

```bash
sudo apt remove openjdk-21-jdk -y

sudo apt autoremove -y
```

### 🔴 RHEL

```bash
sudo dnf remove java-21-openjdk-devel -y
```

### 🪟 Windows

Uninstall through Windows Settings → Apps → Installed Apps, or use:

```powershell
winget uninstall --id EclipseAdoptium.Temurin.21.JDK -e
```

### 🍎 macOS – Homebrew

```bash
brew uninstall openjdk@21
```

---

## ⚠️ 12. Important Notes

- ☕ JDK includes development tools such as `javac`; a JRE-only installation may not include the compiler.
- 🔧 `java` executes Java applications, while `javac` compiles Java source files.
- ⚙️ `JAVA_HOME` should point to the JDK installation directory, not its `bin` directory.
- 🔄 Multiple Java versions can coexist on a system.
- 🧩 Always verify Java compatibility before installing Jenkins, Maven or other Java-based tools.
- 🔐 Download Java from trusted sources such as Eclipse Temurin, OpenJDK or Amazon Corretto.
- 📦 Package availability depends on OS version and enabled repositories.

---

## 📖 13. Official Documentation

| Resource | Official Link |
|---|---|
| ☕ OpenJDK | https://openjdk.org/ |
| ☁️ Amazon Corretto | https://docs.aws.amazon.com/corretto/ |
| 📚 Java Documentation | https://docs.oracle.com/en/java/ |
| 🔧 Java Downloads | https://adoptium.net/ |
| 📦 Maven | https://maven.apache.org/ |
| 🔨 Jenkins Java Requirements | https://www.jenkins.io/doc/book/platform-information/support-policy-java/ |

---

## 🎯 Happy Learning!

**Learn · Install · Configure · Compile · Execute** 🚀