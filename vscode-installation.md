# Visual Studio Code Installation Guide

## 📖 Overview

Visual Studio Code (VS Code) is a powerful, free, and open-source code editor developed by Microsoft. This guide covers installation on Windows, Linux, and macOS, plus essential extensions including AI-powered tools.

## ⚡ Why VS Code?

- ✅ Free and open-source
- ✅ Lightweight yet powerful
- ✅ Extensive extension marketplace
- ✅ Integrated terminal
- ✅ Git integration
- ✅ IntelliSense and debugging support
- ✅ Cross-platform (Windows, Mac, Linux)

## 🖥️ Choose Your Operating System

Click on your operating system to jump directly to the installation instructions:

- **[Windows Installation](#windows-installation)** - Download and install VS Code on Windows
- **[Linux Installation](#linux-installation)** - Package managers and manual installation
- **[macOS Installation](#macos-installation)** - Homebrew or direct download

After installation, proceed to **[Essential Extensions](#essential-extensions)** (same for all platforms).

---

## Windows Installation

### 📋 Prerequisites

- Windows 10/11
- Administrator privileges
- At least 500 MB of free disk space
- Internet connection

### 🔧 Installation Steps

**Step 1: Download VS Code**

1. Open your web browser
2. Go to [https://code.visualstudio.com/](https://code.visualstudio.com/)
3. Click **"Download for Windows"**
4. Download starts automatically (`VSCodeUserSetup-x64-x.xx.x.exe`)

**Step 2: Run the Installer**

1. Locate the downloaded file (usually in Downloads folder)
2. Double-click **VSCodeUserSetup-x64-x.xx.x.exe**
3. Click **"Yes"** if prompted by User Account Control

**Step 3: Installation Wizard**

1. **License Agreement**: Click **"I accept the agreement"** → **"Next"**
2. **Destination Location**: Keep default → **"Next"**
3. **Start Menu Folder**: Keep default → **"Next"**
4. **Additional Tasks**: Check these options:
   - ✅ Create a desktop icon
   - ✅ Add "Open with Code" action to Windows Explorer file context menu
   - ✅ Add "Open with Code" action to Windows Explorer directory context menu
   - ✅ Register Code as an editor for supported file types
   - ✅ Add to PATH (requires shell restart)
5. Click **"Next"** → **"Install"**
6. Wait 1-3 minutes for installation
7. Check **"Launch Visual Studio Code"** → **"Finish"**

**Step 4: First Launch**

1. VS Code opens automatically
2. You'll see a welcome screen with tutorials
3. Familiarize yourself with the interface

### Windows Verification

Open Command Prompt and verify:

```bash
code --version
```

Expected output:
```
1.85.x
abc123def456
x64
```

### Windows Troubleshooting

**Issue: "code is not recognized as a command"**

Solution:
1. Restart Command Prompt/PowerShell
2. If still not working, ensure "Add to PATH" was checked during installation
3. Manually add to PATH:
   - Search "Environment Variables" → Edit System Environment Variables
   - Click "Environment Variables" → Edit "Path"
   - Add: `C:\Users\YourName\AppData\Local\Programs\Microsoft VS Code\bin`

**Issue: Installer Won't Run**

Solution:
1. Download the **System Installer** instead of User Installer from [VS Code downloads page](https://code.visualstudio.com/Download)
2. Right-click installer → "Run as administrator"

---

## Linux Installation

### 📋 Prerequisites

- Linux distribution (Ubuntu, Debian, Fedora, Arch, etc.)
- Terminal access
- sudo privileges
- Internet connection

### 🐧 Ubuntu / Debian / Linux Mint

**Method 1: Using APT (Recommended)**

```bash
# Update package index and install dependencies
sudo apt update
sudo apt install wget gpg

# Import Microsoft GPG key
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg

# Add VS Code repository
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'

# Install VS Code
sudo apt update
sudo apt install code

# Verify installation
code --version
```

**Method 2: Using Snap**

```bash
# Install via Snap
sudo snap install --classic code

# Verify
code --version
```

**Method 3: Download .deb Package**

1. Visit [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download)
2. Download **.deb** package
3. Install:

```bash
cd ~/Downloads
sudo dpkg -i code_*.deb
sudo apt install -f  # Fix any dependency issues
```

### 🎩 Fedora / RHEL / CentOS

**Using DNF/YUM:**

```bash
# Import Microsoft GPG key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add VS Code repository
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

# Update cache and install
sudo dnf check-update
sudo dnf install code

# Verify
code --version
```

**Or download .rpm:**

1. Download **.rpm** from [VS Code downloads](https://code.visualstudio.com/Download)
2. Install:

```bash
sudo dnf install code-*.rpm
```

### 🏔️ Arch Linux / Manjaro

**Using AUR:**

```bash
# Install from AUR (using yay or paru)
yay -S visual-studio-code-bin

# Or manually
git clone https://aur.archlinux.org/visual-studio-code-bin.git
cd visual-studio-code-bin
makepkg -si

# Verify
code --version
```

**Using Snap:**

```bash
sudo pacman -S snapd
sudo systemctl enable --now snapd.socket
sudo snap install --classic code
```

### 🦎 openSUSE

```bash
# Import Microsoft GPG key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add repository
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/vscode.repo'

# Install
sudo zypper refresh
sudo zypper install code

# Verify
code --version
```

### Linux Post-Installation

**Launch VS Code:**

```bash
# From terminal
code

# Or from applications menu
# Search for "Visual Studio Code"
```

**Create Desktop Entry (if not automatic):**

```bash
code --install-extension ms-vscode.references-view
```

### Linux Troubleshooting

**Issue: "code: command not found"**

Solution:
```bash
# Add to PATH (add to ~/.bashrc or ~/.zshrc)
export PATH="$PATH:/usr/share/code/bin"
source ~/.bashrc

# Or create symlink
sudo ln -s /usr/share/code/bin/code /usr/local/bin/code
```

**Issue: Cannot Open Files from Terminal**

Solution:
```bash
# Try with full path
/usr/bin/code filename.py

# Or reinstall
sudo apt remove code
sudo apt install code
```

**Issue: Snap Version Limitations**

The Snap version runs in a sandbox with limited system access.

Solution:
- Use .deb or repository installation instead
- Or grant additional permissions:
```bash
sudo snap connect code:home
sudo snap connect code:removable-media
```

---

## macOS Installation

### 📋 Prerequisites

- macOS 10.15 (Catalina) or later
- Administrator privileges
- At least 500 MB of free disk space
- Internet connection

### 🍎 Method 1: Direct Download (Recommended)

**Step 1: Download**

1. Visit [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Click **"Download Mac Universal"**
3. Downloads as `VSCode-darwin-universal.zip`

**Step 2: Install**

1. Open the downloaded **zip** file (usually extracts automatically)
2. Drag **Visual Studio Code.app** to **Applications** folder
3. Open Applications folder
4. Right-click **Visual Studio Code** → **"Open"**
5. Click **"Open"** in the security dialog (first launch only)

**Step 3: Add to PATH**

To use `code` command in Terminal:

1. Open VS Code
2. Press `Cmd+Shift+P` to open Command Palette
3. Type **"shell command"**
4. Select **"Shell Command: Install 'code' command in PATH"**
5. Restart Terminal

**Step 4: Verify**

```bash
code --version
```

### 🍎 Method 2: Homebrew

**Step 1: Install Homebrew (if not installed)**

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Step 2: Install VS Code**

```bash
# Install via Homebrew Cask
brew install --cask visual-studio-code

# Verify
code --version
```

**Step 3: Launch**

```bash
# From terminal
code

# Or from Applications folder
open -a "Visual Studio Code"
```

### macOS Post-Installation

**Grant Permissions:**

macOS may prompt for permissions:
- **Files and Folders**: Grant access for VS Code to read/write files
- **Developer Tools**: Grant access for debugging

### macOS Troubleshooting

**Issue: "Visual Studio Code is damaged and can't be opened"**

Solution:
```bash
# Remove quarantine attribute
xattr -cr /Applications/Visual\ Studio\ Code.app
```

**Issue: "code command not found"**

Solution:
1. Method 1: Install via Command Palette (see Method 1, Step 3 above)
2. Method 2: Manual symlink:
```bash
sudo ln -s "/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code" /usr/local/bin/code
```

**Issue: Permission Denied**

Solution:
```bash
# Reset permissions
sudo chown -R $(whoami) /Applications/Visual\ Studio\ Code.app
```

---

## Essential Extensions

These extensions work the same on all operating systems.

### 🤖 AI Extensions

#### 1. GitHub Copilot Chat

**Conversational AI for Coding**

1. Search for **"GitHub Copilot Chat"**
2. Click **"Install"**
3. Works with GitHub Copilot
4. Access via chat icon or `Ctrl+Shift+I` / `Cmd+Shift+I`

**Features:**
- Ask coding questions
- Refactoring suggestions
- Bug fixing help
- Code explanations

### 🐍 Python Extensions

#### 1. Python (by Microsoft)

**Must-have for Python development**

1. Search for **"Python"**
2. Install by **Microsoft**

**Features:**
- IntelliSense
- Linting
- Debugging
- Code formatting
- Jupyter Notebook support

#### 2. Pylance

**Fast Python language server**

1. Search for **"Pylance"**
2. Install by **Microsoft**

**Features:**
- Type checking
- Auto-imports
- Better IntelliSense

### 🛠️ Productivity Extensions

#### 1. GitLens

**Supercharge Git capabilities**

1. Search for **"GitLens"**
2. Install by **GitKraken**

---

## Initial Configuration

### 1. Configure Auto Save

1. Open Settings: `Ctrl+,` (Windows/Linux) or `Cmd+,` (macOS)
2. Search for **"auto save"**
3. Set **"Files: Auto Save"** to **"afterDelay"**

### 2. Configure Terminal

**Windows:**
1. Press `Ctrl+` ` to open terminal
2. Click dropdown → **"Select Default Profile"**
3. Choose **"Command Prompt"** or **"PowerShell"**

**Linux:**
1. Press `Ctrl+` ` to open terminal
2. Should default to your system shell (bash/zsh)

**macOS:**
1. Press `Cmd+` ` to open terminal
2. Defaults to zsh (macOS Catalina+)

### 3. Configure Python Interpreter

1. Open a `.py` file or create one
2. Press `Ctrl+Shift+P` (Windows/Linux) or `Cmd+Shift+P` (macOS)
3. Type **"Python: Select Interpreter"**
4. Select your Python installation

### 4. Font and Theme (Optional)

Press `Ctrl+Shift+P` / `Cmd+Shift+P` → Type **"Preferences: Open Settings (JSON)"**

```json
{
    "editor.fontSize": 14,
    "editor.fontFamily": "Consolas, 'Courier New', monospace",
    "workbench.colorTheme": "Dark+ (default dark)",
    "editor.minimap.enabled": true,
    "editor.wordWrap": "on",
    "editor.formatOnSave": true
}
```

**macOS Font Recommendation:**
```json
{
    "editor.fontFamily": "Menlo, Monaco, 'Courier New', monospace"
}
```

**Linux Font Recommendation:**
```json
{
    "editor.fontFamily": "Droid Sans Mono, monospace, Droid Sans Fallback"
}
```

---

## Keyboard Shortcuts

### Windows / Linux Shortcuts

| Action | Shortcut |
|--------|----------|
| Command Palette | `Ctrl+Shift+P` |
| Quick Open File | `Ctrl+P` |
| Toggle Terminal | `Ctrl+` ` |
| Toggle Sidebar | `Ctrl+B` |
| Extensions | `Ctrl+Shift+X` |
| Search in Files | `Ctrl+Shift+F` |
| New File | `Ctrl+N` |
| Save | `Ctrl+S` |
| Settings | `Ctrl+,` |
| Comment Line | `Ctrl+/` |
| Split Editor | `Ctrl+\` |
| Close Editor | `Ctrl+W` |

### macOS Shortcuts

| Action | Shortcut |
|--------|----------|
| Command Palette | `Cmd+Shift+P` |
| Quick Open File | `Cmd+P` |
| Toggle Terminal | `Cmd+` ` |
| Toggle Sidebar | `Cmd+B` |
| Extensions | `Cmd+Shift+X` |
| Search in Files | `Cmd+Shift+F` |
| New File | `Cmd+N` |
| Save | `Cmd+S` |
| Settings | `Cmd+,` |
| Comment Line | `Cmd+/` |
| Split Editor | `Cmd+\` |
| Close Editor | `Cmd+W` |

---

## Universal Troubleshooting

### Issue: Extensions Not Installing

**Solution:**
1. Check internet connection
2. Restart VS Code
3. Try installing from [VS Code Marketplace](https://marketplace.visualstudio.com/)
4. Check firewall/proxy settings

### Issue: Python Not Detected

**Solution:**
1. Install Python extension
2. Restart VS Code
3. Select interpreter: `Ctrl+Shift+P` / `Cmd+Shift+P` → "Python: Select Interpreter"
4. Ensure Python is in PATH

### Issue: GitHub Copilot Not Working

**Solution:**
1. Ensure active subscription
2. Sign in to GitHub account
3. Check Copilot status in bottom-right corner
4. Restart VS Code

### Issue: High CPU/Memory Usage

**Solution:**
1. Disable unused extensions
2. Exclude large folders in settings:
```json
{
    "files.watcherExclude": {
        "**/.git/objects/**": true,
        "**/node_modules/**": true
    }
}
```

### Issue: Terminal Not Working

**Solution:**
1. Check default shell configuration
2. Restart VS Code
3. Try different terminal profile
4. Check terminal path in settings

---

## ✅ Universal Checklist

- [ ] VS Code is installed
- [ ] Can launch from terminal (`code` command works)
- [ ] Extensions panel accessible
- [ ] At least one AI extension installed
- [ ] Python extension installed (if using Python)
- [ ] Integrated terminal works
- [ ] Can open files and folders
- [ ] Settings are customized to preference

---

## 📚 Additional Resources

- [VS Code Documentation](https://code.visualstudio.com/docs)
- [VS Code Tips and Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)
- [Extension Marketplace](https://marketplace.visualstudio.com/vscode)
- [GitHub Copilot Docs](https://docs.github.com/en/copilot)
- [Keyboard Shortcuts PDF](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

---

## ➡️ Next Steps

Once VS Code is set up, proceed to:
- [GitHub Account Setup Guide](github-login.md)
- [Git Installation Guide](git-installation.md)

---

**Last Updated:** February 2026
