# Git Installation and Configuration Guide

## 📖 Overview

Git is a distributed version control system that tracks changes in your code. This guide covers installing Git on Windows, Linux, and macOS, and configuring it to work with your GitHub account.

## ⚡ Why Git?

- ✅ Track code changes and history
- ✅ Collaborate with other developers
- ✅ Create branches for new features
- ✅ Revert to previous versions
- ✅ Required for GitHub, GitLab, Bitbucket
- ✅ Industry-standard version control

## 🖥️ Choose Your Operating System

Click on your operating system to jump directly to the installation instructions:

- **[Windows Installation](#windows-installation)** - Git for Windows installer
- **[Linux Installation](#linux-installation)** - Package managers for various distributions
- **[macOS Installation](#macos-installation)** - Homebrew or binary installer

After installation, proceed to **[Global Configuration](#global-git-configuration)** (same for all platforms).

## 📋 Prerequisites

- Administrator/sudo privileges
- GitHub account (see [GitHub Login Guide](github-login.md))
- Internet connection
- Basic command line knowledge

---

## Windows Installation

### 📋 Windows Prerequisites

- Windows 10/11
- Administrator privileges
- At least 300 MB of free disk space

### Step 1: Download Git

1. Open your web browser
2. Go to [https://git-scm.com/download/win](https://git-scm.com/download/win)
3. The download should start automatically
4. If not, click **"Click here to download manually"**
5. Download the **64-bit Git for Windows Setup** (e.g., `Git-2.43.0-64-bit.exe`)

### Step 2: Run the Installer

1. Locate the downloaded file (usually in Downloads folder)
2. Double-click **Git-2.xx.x-64-bit.exe**
3. Click **"Yes"** if prompted by User Account Control

### Step 3: Installation Wizard

Follow these settings for the best experience:

1. **License Agreement**: Click **"Next"**

2. **Select Destination Location**: Keep default `C:\Program Files\Git`, click **"Next"**

3. **Select Components**: Keep default selections, ensure these are checked:
   - ✅ Windows Explorer integration
   - ✅ Git Bash Here
   - ✅ Git GUI Here
   - ✅ Associate .git* configuration files with the default text editor
   - ✅ Associate .sh files to be run with Bash

   Click **"Next"**

4. **Select Start Menu Folder**: Keep default "Git", click **"Next"**

5. **Choosing the default editor**:
   - Select **"Use Visual Studio Code as Git's default editor"** (if VS Code is installed)
   - Or keep **"Use Vim"** if comfortable with it
   - Click **"Next"**

6. **Adjusting the name of the initial branch**:
   - Select **"Override the default branch name for new repositories"**
   - Keep it as **"main"** (modern standard)
   - Click **"Next"**

7. **Adjusting your PATH environment**:
   - Select **"Git from the command line and also from 3rd-party software"** (Recommended)
   - Click **"Next"**

8. **Choosing HTTPS transport backend**:
   - Select **"Use the OpenSSL library"**
   - Click **"Next"**

9. **Configuring line ending conversions**:
   - Select **"Checkout Windows-style, commit Unix-style line endings"** (Recommended)
   - Click **"Next"**

10. **Configuring the terminal emulator**:
    - Select **"Use MinTTY (the default terminal of MSYS2)"**
    - Click **"Next"**

11. **Default behavior of `git pull`**:
    - Select **"Default (fast-forward or merge)"**
    - Click **"Next"**

12. **Credential helper**:
    - Select **"Git Credential Manager"** (Recommended)
    - Click **"Next"**

13. **Configuring extra options**:
    - ✅ Enable file system caching
    - ✅ Enable symbolic links
    - Click **"Next"**

14. **Configuring experimental options**:
    - Leave unchecked (not needed for beginners)
    - Click **"Install"**

15. Wait for installation to complete (2-3 minutes)

16. Uncheck **"View Release Notes"** and click **"Finish"**

### Step 4: Verify Installation

Open Command Prompt (`Windows Key + R`, type `cmd`, press Enter):

```bash
git --version
```

Expected output:
```
git version 2.43.x.windows.1
```

✅ **Success!** Git is installed.

### Windows Post-Installation

Git Bash is now available:
- Right-click in any folder → **"Git Bash Here"**
- Use Git Bash for Unix-style commands

---

## Linux Installation

### 📋 Linux Prerequisites

- Linux distribution (Ubuntu, Debian, Fedora, Arch, etc.)
- Terminal access
- sudo privileges

### 🐧 Ubuntu / Debian / Linux Mint

**Check if Git is already installed:**

```bash
git --version
```

If not installed or outdated:

```bash
# Update package list
sudo apt update

# Install Git
sudo apt install git

# Verify installation
git --version
```

Expected output:
```
git version 2.34.x
```

**Install latest version from PPA (optional):**

```bash
# Add Git PPA
sudo add-apt-repository ppa:git-core/ppa
sudo apt update

# Install latest Git
sudo apt install git

# Verify
git --version
```

### 🎩 Fedora / RHEL / CentOS

```bash
# Install Git
sudo dnf install git

# Or for older systems
sudo yum install git

# Verify installation
git --version
```

Expected output:
```
git version 2.39.x
```

### 🏔️ Arch Linux / Manjaro

```bash
# Update system and install Git
sudo pacman -Syu git

# Verify installation
git --version
```

Expected output:
```
git version 2.43.x
```

### 🦎 openSUSE

```bash
# Install Git
sudo zypper install git

# Verify installation
git --version
```

### Linux Post-Installation

Git is now available system-wide. You can use it from any terminal.

**Install additional tools (optional):**

```bash
# Ubuntu/Debian
sudo apt install git-gui gitk git-doc

# Fedora/RHEL
sudo dnf install git-gui gitk git-doc

# Arch
sudo pacman -S git-gui tk
```

---

## macOS Installation

### 📋 macOS Prerequisites

- macOS 10.15 (Catalina) or later
- Administrator privileges
- Internet connection

### 🍎 Method 1: Homebrew (Recommended)

**Step 1: Install Homebrew (if not already installed)**

Open Terminal (Applications > Utilities > Terminal):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions.

**Step 2: Install Git**

```bash
# Install Git via Homebrew
brew install git

# Verify installation
git --version
```

Expected output:
```
git version 2.43.x
```

**Step 3: Update Git (when needed)**

```bash
brew update
brew upgrade git
```

### 🍎 Method 2: Xcode Command Line Tools

Git comes with Xcode Command Line Tools:

```bash
# Trigger installation
git --version
```

If Git is not installed, macOS will prompt you to install Command Line Tools. Click **"Install"**.

Or install manually:

```bash
xcode-select --install
```

Click **"Install"** → **"Agree"** → Wait for download and installation.

**Verify:**

```bash
git --version
```

Expected output:
```
git version 2.39.x (Apple Git-xxx)
```

**Note**: Apple's Git version may be older than Homebrew's.

### 🍎 Method 3: Binary Installer

1. Visit [https://git-scm.com/download/mac](https://git-scm.com/download/mac)
2. Download the **macOS installer** (.dmg file)
3. Open the downloaded file
4. Double-click the **.pkg** file
5. Follow the installation wizard
6. Click **"Continue"** → **"Install"** → Enter password
7. Click **"Close"** when finished

**Verify:**

```bash
git --version
```

### macOS Post-Installation

**Add Git to PATH (if needed):**

If using Homebrew, it usually handles this automatically. If not, add to `~/.zshrc`:

```bash
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

---

## Global Git Configuration

These commands work the same on all operating systems. Run them in Terminal (Linux/macOS) or Command Prompt/Git Bash (Windows).

### Step 1: Configure User Name and Email

```bash
git config --global user.name "Your Name"
```

```bash
git config --global user.email "your_email@example.com"
```

**Important:**
- Use the SAME email associated with your GitHub account
- If you enabled email privacy on GitHub, use your GitHub no-reply email:
  ```bash
  git config --global user.email "123456+username@users.noreply.github.com"
  ```
  (Find this in GitHub Settings > Emails)

---

## Connecting Git to GitHub

This process is the same for all operating systems.

### Method 1: Using HTTPS (Simpler for Beginners)

When you push/pull for the first time, Git will prompt for credentials:

1. **Username**: Your GitHub username
2. **Password**: Your GitHub **Personal Access Token** (NOT your password)

#### Creating a Personal Access Token

1. Go to [GitHub](https://github.com/) and sign in
2. Click profile picture > **"Settings"**
3. Scroll to **"Developer settings"** (bottom of left sidebar)
4. Click **"Personal access tokens"** > **"Tokens (classic)"**
5. Click **"Generate new token"** > **"Generate new token (classic)"**
6. Fill in details:
   - **Note**: "Git access from command line"
   - **Expiration**: Choose 90 days or longer
   - **Select scopes**: Check **"repo"** (full control of repositories)
7. Scroll down and click **"Generate token"**
8. **IMPORTANT**: Copy the token immediately (you won't see it again!)
9. Save it securely (password manager or secure note)

When Git prompts for password, paste this token.

### Method 2: Using SSH (More Secure, Recommended)

If you've set up SSH keys (see [GitHub Login Guide](github-login.md)), Git will automatically use them.

#### Test SSH Connection

```bash
ssh -T git@github.com
```

Expected output:
```
Hi YourUsername! You've successfully authenticated, but GitHub does not provide shell access.
```

#### Clone with SSH

```bash
git clone git@github.com:username/repository.git
```

### Method 3: GitHub CLI (Advanced)

```bash
# Install GitHub CLI (gh)
# Windows: winget install GitHub.cli
# macOS: brew install gh
# Linux: See https://cli.github.com/manual/installation

# Authenticate
gh auth login

# Clone repositories
gh repo clone username/repository
```

---

## First Git Commands

These commands work the same on all operating systems.

### Initialize a Repository

```bash
mkdir my-project
cd my-project
git init
```

This creates a new Git repository in the current directory.

### Clone an Existing Repository

**HTTPS:**
```bash
git clone https://github.com/username/repository.git
```

**SSH:**
```bash
git clone git@github.com:username/repository.git
```

### Basic Git Workflow

```bash
# 1. Check status
git status

# 2. Add files to staging
git add filename.txt
# Or add all files
git add .

# 3. Commit changes
git commit -m "Your commit message"

# 4. Push to GitHub
git push origin main

# 5. Pull latest changes
git pull origin main
```

---

## Essential Git Configuration Summary

Here's a complete configuration script for quick setup:

### Windows

```bash
# Identity
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"

# Default branch
git config --global init.defaultBranch main

# Line endings (Windows)
git config --global core.autocrlf true

# Editor (VS Code)
git config --global core.editor "code --wait"

# Colors
git config --global color.ui auto

# Pull strategy
git config --global pull.rebase false

# Credential helper (Windows)
git config --global credential.helper manager

# Aliases (optional shortcuts)
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
git config --global alias.last "log -1 HEAD"
```

### Linux/macOS

```bash
# Identity
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"

# Default branch
git config --global init.defaultBranch main

# Line endings (Linux/macOS)
git config --global core.autocrlf input

# Editor (VS Code)
git config --global core.editor "code --wait"

# Colors
git config --global color.ui auto

# Pull strategy
git config --global pull.rebase false

# Credential helper
# macOS
git config --global credential.helper osxkeychain
# Linux
git config --global credential.helper cache

# Aliases (optional shortcuts)
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
git config --global alias.last "log -1 HEAD"
```

---

## ✅ Universal Checklist

- [ ] Git is installed (`git --version` works)
- [ ] User name configured (`git config user.name`)
- [ ] User email configured (`git config user.email`)
- [ ] Default branch set to "main"
- [ ] Line endings configured for your OS
- [ ] Default editor configured
- [ ] Can initialize a repository (`git init`)
- [ ] Can clone a repository from GitHub
- [ ] Authentication method set up (SSH or Personal Access Token)

---

## 🚨 Troubleshooting

### Universal Issues

#### Issue: "git is not recognized" or "command not found"

**Solution:**
1. Restart your terminal/command prompt
2. Verify installation: Check if Git is in your PATH
3. Reinstall Git if necessary

#### Issue: Permission Denied When Pushing

**Solution:**
1. Verify GitHub credentials are correct
2. Check authentication method (SSH vs HTTPS)
3. For HTTPS: Ensure using Personal Access Token, NOT password
4. For SSH: Test connection with `ssh -T git@github.com`
5. Check repository permissions on GitHub

#### Issue: Wrong User Name/Email in Commits

**Solution:**
1. Check current config:
   ```bash
   git config user.name
   git config user.email
   ```
2. Update if wrong:
   ```bash
   git config --global user.name "Correct Name"
   git config --global user.email "correct_email@example.com"
   ```
3. For existing commits, you need to amend or rebase

#### Issue: Line Ending Warnings

**Solution:**

**Windows:**
```bash
git config --global core.autocrlf true
```

**Linux/macOS:**
```bash
git config --global core.autocrlf input
```

### Windows-Specific Issues

#### Issue: "git is not recognized" after installation

**Solution:**
1. Restart Command Prompt/PowerShell
2. If still not working, add Git to PATH manually:
   - Search **"Environment Variables"** in Windows
   - Click **"Environment Variables"** → Edit **"Path"**
   - Add: `C:\Program Files\Git\cmd`
   - Click **"OK"** and restart terminal

#### Issue: Git Bash not opening

**Solution:**
1. Verify installation completed successfully
2. Check if Git Bash is in Start Menu
3. Try running from: `C:\Program Files\Git\git-bash.exe`
4. Reinstall Git if necessary

#### Issue: Credential Manager not working

**Solution:**
```bash
# Reset credential helper
git config --global --unset credential.helper
git config --global credential.helper manager

# Or use Git Credential Manager Core
git config --global credential.helper manager-core
```

### Linux-Specific Issues

#### Issue: Git not found after installation

**Solution:**
```bash
# Check if Git is installed
which git

# If not found, check package manager
# Ubuntu/Debian
dpkg -l | grep git

# Fedora/RHEL
rpm -qa | grep git

# Reinstall if necessary
sudo apt install git  # Ubuntu/Debian
sudo dnf install git  # Fedora/RHEL
```

#### Issue: Permission denied (file system)

**Solution:**
```bash
# Fix repository ownership
sudo chown -R $USER:$USER /path/to/repository

# Fix .git directory permissions
chmod -R 755 .git
```

#### Issue: Credential helper not persisting

**Solution:**
```bash
# Use cache with longer timeout
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=7200'

# Or use store (less secure but persistent)
git config --global credential.helper store
```

### macOS-Specific Issues

#### Issue: xcrun error after macOS update

**Solution:**
```bash
# Reinstall Xcode Command Line Tools
xcode-select --install

# Or reset Xcode Command Line Tools
sudo xcode-select --reset
```

#### Issue: Git version is old (Apple Git)

**Solution:**
```bash
# Install latest Git via Homebrew
brew install git

# Make sure Homebrew Git is used
which git
# Should show: /usr/local/bin/git or /opt/homebrew/bin/git

# If not, update PATH in ~/.zshrc
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

#### Issue: Keychain keeps prompting for password

**Solution:**
```bash
# Configure credential helper
git config --global credential.helper osxkeychain

# If still prompting, reset keychain
git credential-osxkeychain erase
```

---

## 🎓 Quick Git Command Reference

### Basic Commands

```bash
git init                          # Initialize repository
git clone <url>                   # Clone repository
git status                        # Check status
git add <file>                    # Stage file
git add .                         # Stage all changes
git commit -m "message"           # Commit changes
git push origin main              # Push to remote
git pull origin main              # Pull from remote
```

### Branch Commands

```bash
git branch                        # List branches
git branch <name>                 # Create branch
git checkout <name>               # Switch branch
git checkout -b <name>            # Create and switch
git merge <branch>                # Merge branch
git branch -d <name>              # Delete branch
git branch -m <old> <new>         # Rename branch
```

### Information Commands

```bash
git log                           # View commit history
git log --oneline                 # Compact log
git log --graph --all             # Visual graph
git diff                          # View changes
git diff --staged                 # View staged changes
git show <commit>                 # Show commit details
git remote -v                     # Show remotes
```

### Undo Commands

```bash
git restore <file>                # Discard changes
git restore --staged <file>       # Unstage file
git reset HEAD~1                  # Undo last commit
git revert <commit>               # Revert commit
git clean -fd                     # Remove untracked files
```

---

## 📚 Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Learn Git Branching (Interactive)](https://learngitbranching.js.org/)
- [Pro Git Book (Free)](https://git-scm.com/book/en/v2)
- [GitHub Git Guides](https://github.com/git-guides)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)

---

## 🏆 Best Practices

1. **Commit Often**: Make small, frequent commits with clear messages
2. **Write Clear Messages**: Describe what and why, not how
   - Good: "Add user authentication with JWT"
   - Bad: "Changed some files"
3. **Use Branches**: Keep main branch stable, develop features in branches
4. **Pull Before Push**: Stay updated with remote changes
5. **Review Before Commit**: Use `git status` and `git diff`
6. **Don't Commit Secrets**: Never commit passwords, API keys, or sensitive data
7. **Use .gitignore**: Exclude unnecessary files (logs, temp files, dependencies)
8. **Tag Releases**: Use `git tag` for version releases
9. **Squash Small Commits**: Keep history clean before merging
10. **Document Workflow**: Maintain a CONTRIBUTING.md for team projects

---

## ➡️ Next Steps

Once Git is installed and configured, proceed to:
- [Python Virtual Environment Guide](python-venv-guide.md)
- Start creating your own projects and repositories!
- Learn advanced Git workflows (branching strategies, rebasing, etc.)

---

**Last Updated:** February 2026
