# Python Installation Guide

## 📖 Overview

This guide will walk you through installing Python on Windows, Linux, and macOS. Python is the foundation for your development environment and is required before proceeding with other installations.

## 🖥️ Choose Your Operating System

Click on your operating system to jump directly to the installation instructions:

- **[Windows Installation](#windows-installation)** - Microsoft Store or Python.org installer
- **[Linux Installation](#linux-installation)** - Package managers for various distributions
- **[macOS Installation](#macos-installation)** - Homebrew or Python.org installer

---

## Windows Installation

### 📋 Prerequisites

- Windows 10 (version 1903 or higher) or Windows 11
- Administrator privileges
- Internet connection

### 🎯 Method 1: Microsoft Store (Recommended for Beginners)

#### Why Microsoft Store Python?

- ✅ Automatic updates
- ✅ Easy installation and removal
- ✅ No PATH configuration needed
- ✅ Sandboxed and secure
- ✅ Official Microsoft-maintained package

#### Installation Steps

**Step 1: Open Microsoft Store**

1. Press `Windows Key` or click the Start button
2. Type **"Microsoft Store"**
3. Click on the **Microsoft Store** app

**Step 2: Search for Python**

1. Click the **Search** icon (magnifying glass)
2. Type **"Python"** in the search bar
3. Look for **"Python 3.12"** (or latest version) by **Python Software Foundation**

**Step 3: Install**

1. Click on **Python 3.12**
2. Click **"Get"** or **"Install"**
3. Wait for installation to complete (2-5 minutes)
4. Once installed, you'll see an **"Open"** button

**Step 4: Verify Installation**

1. Press `Windows Key + R`, type **"cmd"**, press Enter
2. Run:

```bash
python --version
```

Expected output:
```
Python 3.12.x
```

3. Check pip:

```bash
pip --version
```

Expected output:
```
pip 24.x.x from C:\Users\...\site-packages\pip (python 3.12)
```

### 🎯 Method 2: Python.org Installer (Advanced Users)

#### Installation Steps

**Step 1: Download**

1. Visit [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Click **"Download Python 3.12.x"**
3. Save the installer (e.g., `python-3.12.x-amd64.exe`)

**Step 2: Run Installer**

1. Double-click the downloaded file
2. **IMPORTANT**: Check **"Add python.exe to PATH"** ✅
3. Click **"Install Now"** (recommended) or **"Customize installation"** (advanced)
4. Wait for installation to complete
5. Click **"Close"**

**Step 3: Verify**

Open Command Prompt and run:

```bash
python --version
pip --version
```

### Windows Post-Installation

**Update pip:**

```bash
python -m pip install --upgrade pip
```

**Install essential tools:**

```bash
python -m pip install --upgrade pip setuptools wheel
pip install pylint black autopep8
```

### Windows Troubleshooting

**Issue: "Python is not recognized"**

Solutions:
1. Close and reopen Command Prompt
2. For Microsoft Store version: Search "Manage App Execution Aliases" in Settings, enable Python
3. For python.org version: Add Python to PATH manually:
   - Search "Environment Variables" → Edit System Environment Variables
   - Click "Environment Variables" → Edit "Path"
   - Add: `C:\Users\YourName\AppData\Local\Programs\Python\Python312` and `...\Python312\Scripts`

---

## Linux Installation

### 📋 Prerequisites

- Linux distribution (Ubuntu, Debian, Fedora, Arch, etc.)
- Terminal access
- sudo privileges
- Internet connection

### 🐧 Ubuntu / Debian / Linux Mint

**Check Current Version:**

```bash
python3 --version
```

Most modern Ubuntu/Debian systems come with Python 3 pre-installed.

**Method 1: Using apt (Recommended)**

```bash
# Update package list
sudo apt update

# Install Python 3 and pip
sudo apt install python3 python3-pip python3-venv

# Verify installation
python3 --version
pip3 --version
```

**Method 2: Install Latest Version from Deadsnakes PPA**

```bash
# Add deadsnakes PPA
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update

# Install Python 3.12
sudo apt install python3.12 python3.12-venv python3.12-dev

# Install pip for Python 3.12
curl -sS https://bootstrap.pypa.io/get-pip.py | python3.12

# Verify
python3.12 --version
```

**Set Python 3 as Default (Optional):**

```bash
# Create alias
echo "alias python=python3" >> ~/.bashrc
echo "alias pip=pip3" >> ~/.bashrc
source ~/.bashrc
```

Or use update-alternatives:

```bash
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 1
```

### 🎩 Fedora / RHEL / CentOS

```bash
# Check version
python3 --version

# Install Python 3 and development tools
sudo dnf install python3 python3-pip python3-devel

# For Python 3.12 specifically
sudo dnf install python3.12 python3.12-pip

# Verify
python3 --version
pip3 --version
```

### 🏔️ Arch Linux / Manjaro

```bash
# Update system
sudo pacman -Syu

# Install Python
sudo pacman -S python python-pip

# Verify
python --version
pip --version
```

On Arch, `python` command already points to Python 3.

### 🦎 openSUSE

```bash
# Install Python 3
sudo zypper install python3 python3-pip python3-devel

# Verify
python3 --version
pip3 --version
```

### Linux Post-Installation

**Update pip:**

```bash
python3 -m pip install --upgrade pip
```

**Install essential tools:**

```bash
pip3 install --upgrade setuptools wheel
pip3 install pylint black autopep8
```

**Create helpful aliases (optional):**

Add to `~/.bashrc` or `~/.zshrc`:

```bash
alias python=python3
alias pip=pip3
```

Then run:
```bash
source ~/.bashrc
```

### Linux Troubleshooting

**Issue: python3-pip not found**

Solution:
```bash
# Debian/Ubuntu
sudo apt install python3-pip

# If still not working, manual install
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
```

**Issue: Command not found after pip install**

Solution:
```bash
# Add to ~/.bashrc
export PATH="$HOME/.local/bin:$PATH"
source ~/.bashrc
```

**Issue: Permission denied when installing packages**

Solution:
```bash
# Install to user directory (preferred)
pip3 install --user package_name
```

---

## macOS Installation

### 📋 Prerequisites

- macOS 10.15 (Catalina) or later
- Administrator privileges
- Internet connection

### 🍎 Method 1: Homebrew (Recommended)

Homebrew is the most popular package manager for macOS.

**Step 1: Install Homebrew (if not already installed)**

Open Terminal (Applications → Utilities → Terminal) and run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions.

**Step 2: Install Python**

```bash
# Install Python 3
brew install python

# This installs the latest stable version (Python 3.12.x)
```

**Step 3: Verify Installation**

```bash
python3 --version
pip3 --version
```

**Step 4: Add to PATH (if needed)**

Homebrew usually handles this automatically. If not, add to `~/.zshrc` or `~/.bash_profile`:

```bash
export PATH="/usr/local/opt/python/libexec/bin:$PATH"
```

Then run:
```bash
source ~/.zshrc
```

### 🍎 Method 2: Python.org Installer

**Step 1: Download**

1. Visit [https://www.python.org/downloads/macos/](https://www.python.org/downloads/macos/)
2. Download **macOS 64-bit universal2 installer** for Python 3.12.x
3. File will be named like `python-3.12.x-macos11.pkg`

**Step 2: Install**

1. Open the downloaded `.pkg` file
2. Follow the installation wizard
3. Click **Continue** → **Agree** → **Install**
4. Enter your password when prompted
5. Click **Close** when finished

**Step 3: Verify**

Open Terminal and run:

```bash
python3 --version
pip3 --version
```

### macOS Post-Installation

**Update pip:**

```bash
python3 -m pip install --upgrade pip
```

**Install essential tools:**

```bash
pip3 install --upgrade setuptools wheel
pip3 install pylint black autopep8
```

**Create python alias (optional):**

Add to `~/.zshrc` (macOS Catalina and later use zsh):

```bash
echo "alias python=python3" >> ~/.zshrc
echo "alias pip=pip3" >> ~/.zshrc
source ~/.zshrc
```

Or for older macOS with bash:

```bash
echo "alias python=python3" >> ~/.bash_profile
echo "alias pip=pip3" >> ~/.bash_profile
source ~/.bash_profile
```

### macOS Troubleshooting

**Issue: "python3: command not found"**

Solution:
1. Ensure PATH is set correctly
2. Restart Terminal
3. Check installation: `ls /usr/local/bin/python3`
4. If using Homebrew: `brew doctor` to diagnose issues

---

## 🔍 Universal Verification (All Operating Systems)

After installation on any OS, verify with these tests:

### 1. Check Python Version

```bash
# Linux/macOS
python3 --version

# Windows (if using Microsoft Store or python.org with PATH)
python --version
```

### 2. Check pip Version

```bash
# Linux/macOS
pip3 --version

# Windows
pip --version
```

### 3. Test Python Interpreter

**Linux/macOS:**
```bash
python3
```

**Windows:**
```bash
python
```

You should see:
```
Python 3.12.x (main, ...)
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Type `exit()` or press `Ctrl+D` (Linux/Mac) or `Ctrl+Z` then Enter (Windows) to exit.

## ✅ Universal Checklist

- [ ] Python is installed
- [ ] `python` or `python3` command works
- [ ] Pip is installed and working
- [ ] Can run Python interpreter
- [ ] Can execute Python scripts
- [ ] Can install packages with pip
- [ ] Virtual environment support available (`python3 -m venv` or `python -m venv`)

## 🎯 Post-Installation Best Practices (All OS)

### 1. Keep pip Updated

```bash
# Linux/macOS
python3 -m pip install --upgrade pip

# Windows
python -m pip install --upgrade pip
```

### 2. Install Development Tools

```bash
# Linux/macOS
pip3 install pylint black autopep8 flake8

# Windows
pip install pylint black autopep8 flake8
```

### 3. Always Use Virtual Environments

Never install packages globally. See [Python Virtual Environment Guide](python-venv-guide.md) for details.

### 4. Keep Python Updated

**Windows (Microsoft Store):** Updates automatically

**Windows (python.org):** Download and install new version

**Linux:**
```bash
# Ubuntu/Debian
sudo apt update && sudo apt upgrade python3

# Fedora
sudo dnf update python3
```

**macOS (Homebrew):**
```bash
brew update
brew upgrade python
```

## 📊 Command Quick Reference

| Task | Windows | Linux/macOS |
|------|---------|-------------|
| Run Python | `python` | `python3` |
| Check version | `python --version` | `python3 --version` |
| Run pip | `pip` | `pip3` |
| Install package | `pip install pkg` | `pip3 install pkg` |
| Create venv | `python -m venv venv` | `python3 -m venv venv` |
| Activate venv | `venv\Scripts\activate` | `source venv/bin/activate` |

## 📚 Additional Resources

- [Official Python Documentation](https://docs.python.org/3/)
- [Python Package Index (PyPI)](https://pypi.org/)
- [Real Python Tutorials](https://realpython.com/)
- [Python on Microsoft Store](https://www.microsoft.com/store/productId/9NCVDN91XZQP) (Windows)
- [Homebrew](https://brew.sh/) (macOS)

## ➡️ Next Steps

Once Python is installed successfully on your system, proceed to:
- [Visual Studio Code Installation Guide](vscode-installation.md)
- [Python Virtual Environment Guide](python-venv-guide.md)

---

**Last Updated:** February 2026
