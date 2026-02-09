# IDE Setup Guide - Table of Contents

Welcome to the comprehensive IDE Setup Guide! This guide will walk you through setting up a complete development environment for modern software development on **Windows, Linux, and macOS**.

## 🖥️ Multi-Platform Support

All guides in this collection support **three major operating systems**:
- 🪟 **Windows** (10/11)
- 🐧 **Linux** (Ubuntu, Debian, Fedora, Arch, openSUSE)
- 🍎 **macOS** (Catalina and later)

Each guide includes OS-specific instructions with jump links for quick navigation.

---

## 📋 Installation Guides

### 1. **[Python Installation Guide](python-installation.md)**
   **Platforms:** Windows | Linux | macOS

   - **Windows**: Microsoft Store or Python.org installer
   - **Linux**: apt, dnf, pacman, zypper (multiple distros)
   - **macOS**: Homebrew or Python.org installer
   - Verifying installation across all platforms
   - Platform-specific troubleshooting

### 2. **[Visual Studio Code Installation Guide](vscode-installation.md)**
   **Platforms:** Windows | Linux | macOS

   - **Windows**: Direct download installer
   - **Linux**: apt, snap, dnf, AUR, zypper
   - **macOS**: Direct download or Homebrew
   - Essential AI extensions (GitHub Copilot, Codeium, Tabnine)
   - Python development extensions
   - Productivity extensions and configuration

### 3. **[GitHub Account Setup Guide](github-login.md)**
   **Platforms:** Universal (Web-based) + OS-specific SSH setup

   - Creating a GitHub account (all platforms)
   - Two-factor authentication setup
   - **Windows**: SSH key generation (CMD, PowerShell, Git Bash)
   - **Linux**: SSH key generation and configuration
   - **macOS**: SSH key with Keychain integration
   - Email privacy settings

### 4. **[Git Installation and Configuration Guide](git-installation.md)**
   **Platforms:** Windows | Linux | macOS

   - **Windows**: Git for Windows installer (detailed walkthrough)
   - **Linux**: apt, dnf, pacman, zypper installation
   - **macOS**: Homebrew, Xcode Command Line Tools, or binary installer
   - Global configuration for all platforms
   - Connecting to GitHub (HTTPS, SSH, GitHub CLI)
   - Platform-specific credential helpers

### 5. **[Python Virtual Environment (venv) Guide](python-venv-guide.md)**
   **Platforms:** Windows | Linux | macOS

   - Understanding virtual environments
   - Creating venv (same across all platforms)
   - **Windows**: Activation in CMD, PowerShell, Git Bash
   - **Linux/macOS**: Activation in Bash, Zsh, Fish shells
   - Basic usage and examples
   - VS Code integration

---

## 🚀 Quick Start

Follow the guides in the order listed above for the smoothest setup experience:

1. **Install Python** for your operating system
2. **Install VS Code** and essential extensions
3. **Create GitHub account** and set up SSH keys
4. **Install and configure Git** to work with GitHub
5. **Learn virtual environments** for Python projects

Each guide is designed to be comprehensive yet easy to follow, with clear OS-specific sections.

---

## 📦 Project Dependencies (Optional)

After completing the setup guides, you can install all necessary packages for advanced Python development:

### Installing from requirements.txt

The included `requirements.txt` contains packages for:
- 🤖 Building transformers from scratch (PyTorch)
- 🔗 Working with LangChain framework
- 🌐 Integrating OpenAI, Anthropic (Claude), and Google Gemini APIs
- 📊 Data processing and visualization
- 📓 Jupyter notebooks for interactive development

**Installation:**

1. **Create and activate virtual environment** (see [venv guide](python-venv-guide.md))

   **Windows:**
   ```bash
   python -m venv venv
   venv\Scripts\activate
   ```

   **Linux/macOS:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

2. **Install all packages:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up API keys** (if using LLM providers):
   - Copy `.env.example` to `.env`
   - Add your API keys (OpenAI, Anthropic, Google)
   - See [PROJECT_SETUP.md](PROJECT_SETUP.md) for details

**What's Included:**
- PyTorch, NumPy, SciPy (ML/DL)
- Transformers, Tokenizers (Hugging Face)
- LangChain + OpenAI/Anthropic/Gemini integrations
- Pandas, Matplotlib, Seaborn (data & viz)
- ChromaDB, FAISS (vector stores)
- Jupyter notebooks
- Development tools (pytest, black, flake8)

---

## 💡 Prerequisites

### All Operating Systems
- Administrator/sudo privileges
- Stable internet connection
- Basic command line/terminal knowledge

### Platform-Specific
- **Windows**: Windows 10 (version 1903+) or Windows 11
- **Linux**: Modern distribution (Ubuntu 20.04+, Fedora 35+, etc.)
- **macOS**: macOS 10.15 (Catalina) or later

---

## 🎯 What You'll Have After Completion

- ✅ Python development environment
- ✅ Visual Studio Code with AI-powered extensions
- ✅ GitHub account with SSH authentication
- ✅ Git version control configured
- ✅ Virtual environment management skills

---

## 📊 Platform Support Matrix

| Guide | Windows | Linux | macOS | Universal |
|-------|---------|-------|-------|-----------|
| Python Installation | ✅ | ✅ | ✅ | ✅ Verification |
| VS Code Installation | ✅ | ✅ | ✅ | ✅ Extensions |
| GitHub Setup | ✅ SSH | ✅ SSH | ✅ SSH | ✅ Account |
| Git Installation | ✅ | ✅ | ✅ | ✅ Config |
| Python venv | ✅ | ✅ | ✅ | ✅ Usage |

---

## 📞 Support

If you encounter any issues during the installation process:
- Refer to the **troubleshooting section** in each individual guide
- Each guide has OS-specific troubleshooting for common issues
- Check the **verification checklists** to ensure proper installation

---

## 📚 Additional Features

- **Jump Links**: Quick navigation to your operating system section
- **Command Reference Tables**: Compare commands across platforms
- **Verification Steps**: Ensure successful installation
- **Best Practices**: Industry-standard setup recommendations
- **Troubleshooting**: Platform-specific solutions

---

**Last Updated:** February 2026

**Version:** 2.0 - Multi-Platform Support
