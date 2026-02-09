# GitHub Account Setup Guide

## 📖 Overview

GitHub is the world's largest code hosting platform, essential for version control, collaboration, and showcasing your projects. This guide covers account creation, authentication setup, and SSH configuration for Windows, Linux, and macOS.

## ⚡ Why GitHub?

- ✅ Version control and collaboration
- ✅ Host unlimited public repositories
- ✅ Portfolio for your coding projects
- ✅ Contribute to open-source projects
- ✅ GitHub Actions for CI/CD
- ✅ GitHub Copilot for AI-assisted coding
- ✅ GitHub Pages for free website hosting

## 📋 Prerequisites

- Valid email address
- Internet connection
- Web browser
- Terminal/Command Prompt access (for SSH setup)

## 🗂️ Guide Structure

1. **[Creating a GitHub Account](#part-1-creating-a-github-account)** - Universal (web-based)
2. **[Two-Factor Authentication](#part-2-two-factor-authentication-2fa)** - Universal (web-based)
3. **[SSH Key Setup](#part-3-ssh-key-setup-os-specific)** - OS-specific instructions
   - [Windows SSH Setup](#windows-ssh-setup)
   - [Linux SSH Setup](#linux-ssh-setup)
   - [macOS SSH Setup](#macos-ssh-setup)
4. **[Email Settings](#part-4-configure-github-email-settings)** - Universal
5. **[Profile Completion](#part-5-complete-your-profile)** - Universal

---

## Part 1: Creating a GitHub Account

This process is the same for all operating systems (web-based).

### Step 1: Visit GitHub

1. Open your web browser
2. Go to [https://github.com/](https://github.com/)
3. Click **"Sign up"** in the top-right corner

### Step 2: Enter Your Information

1. **Email Address**: Enter your email address
2. Click **"Continue"**
3. **Create Password**: Choose a strong password
   - At least 15 characters, or
   - 8+ characters with numbers and special characters
4. Click **"Continue"**
5. **Username**: Choose a unique username
   - This will be your GitHub identity (e.g., `github.com/yourusername`)
   - Use lowercase, hyphens, or numbers
   - Choose something professional
6. Click **"Continue"**

### Step 3: Verify Your Account

1. **Email Preferences**: Choose whether to receive updates (optional)
2. Click **"Continue"**
3. **Verify you're human**: Complete the puzzle/CAPTCHA
4. Click **"Create account"**

### Step 4: Email Verification

1. GitHub will send a verification code to your email
2. Check your inbox for "GitHub: Verify your email address"
3. Copy the 6-digit code
4. Paste it in the GitHub verification page
5. Click **"Verify"**

### Step 5: Personalization (Optional)

GitHub will ask questions to personalize your experience:
- What is your level of programming experience?
- What do you plan to use GitHub for?

Answer these or click **"Skip personalization"**

### Step 6: Choose Your Plan

1. Select **"Free"** plan (recommended for beginners)
2. The free plan includes:
   - Unlimited public repositories
   - Unlimited private repositories
   - 2,000 CI/CD minutes/month
   - 500MB of package storage

Click **"Continue for free"**

---

## Part 2: Two-Factor Authentication (2FA)

**Highly Recommended for Security**

This process is the same for all operating systems (web-based).

### Step 1: Access Security Settings

1. Click your profile picture in the top-right corner
2. Select **"Settings"**
3. In the left sidebar, click **"Password and authentication"**
4. Scroll to **"Two-factor authentication"**
5. Click **"Enable two-factor authentication"**

### Step 2: Configure 2FA

**Option A: Using an Authenticator App (Recommended)**

1. Download an authenticator app on your phone:
   - **Microsoft Authenticator** (Recommended - works on Android & iOS)
   - **Google Authenticator** (Android & iOS)
   - **Authy** (Android & iOS)
2. Click **"Set up using an app"**
3. Scan the QR code with your authenticator app
4. Enter the 6-digit code from the app
5. Click **"Enable"**

**Option B: Using SMS**

1. Click **"Set up using SMS"**
2. Enter your phone number
3. Enter the verification code received via SMS

### Step 3: Save Recovery Codes

1. GitHub will display recovery codes
2. **IMPORTANT**: Download and save these codes securely
3. Store them in a safe place:
   - Password manager (1Password, Bitwarden, LastPass)
   - Printed copy in a safe location
   - Secure note on your device
4. Click **"I have saved my recovery codes"**

**⚠️ Warning**: Without these codes, you may lose access to your account if you lose your 2FA device!

---

## Part 3: SSH Key Setup (OS-Specific)

SSH keys provide secure, password-free authentication with GitHub. Choose your operating system:

- **[Windows SSH Setup](#windows-ssh-setup)**
- **[Linux SSH Setup](#linux-ssh-setup)**
- **[macOS SSH Setup](#macos-ssh-setup)**

After setup, proceed to **[Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms)** (same for all platforms).

---

### Windows SSH Setup

#### Step 1: Check for Existing SSH Keys

Open **Command Prompt** or **PowerShell**:

```bash
dir %USERPROFILE%\.ssh
```

Or in PowerShell:

```powershell
ls ~/.ssh
```

If you see `id_rsa.pub` or `id_ed25519.pub`, you already have SSH keys. Skip to [Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms).

#### Step 2: Generate New SSH Key

In Command Prompt or PowerShell, run (replace with your GitHub email):

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**If you get an error about ed25519**, use RSA instead:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**Prompts:**
1. **"Enter file in which to save the key"**: Press **Enter** (uses default location)
2. **"Enter passphrase"**:
   - Press **Enter** for no passphrase (convenient but less secure)
   - Or type a passphrase for extra security
3. **"Enter same passphrase again"**: Press **Enter** or retype passphrase

**Expected output:**
```
Your identification has been saved in C:\Users\YourName/.ssh/id_ed25519
Your public key has been saved in C:\Users\YourName/.ssh/id_ed25519.pub
```

#### Step 3: Start SSH Agent

**Command Prompt:**

```bash
# Start SSH agent
start-ssh-agent

# If that doesn't work, try:
ssh-agent
```

**PowerShell:**

```powershell
# Start SSH agent
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent
```

**Git Bash (if installed):**

```bash
eval "$(ssh-agent -s)"
```

#### Step 4: Add SSH Key to Agent

```bash
ssh-add ~/.ssh/id_ed25519
```

Or if you used RSA:

```bash
ssh-add ~/.ssh/id_rsa
```

#### Step 5: Copy SSH Public Key

**Method 1: Copy to Clipboard (Easiest)**

**PowerShell:**
```powershell
Get-Content ~/.ssh/id_ed25519.pub | Set-Clipboard
```

**Command Prompt:**
```bash
type %USERPROFILE%\.ssh\id_ed25519.pub | clip
```

**Git Bash:**
```bash
clip < ~/.ssh/id_ed25519.pub
```

**Method 2: Display and Copy Manually**

```bash
type %USERPROFILE%\.ssh\id_ed25519.pub
```

Copy the entire output (starts with `ssh-ed25519`).

Now proceed to [Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms).

---

### Linux SSH Setup

#### Step 1: Check for Existing SSH Keys

Open Terminal:

```bash
ls -la ~/.ssh
```

If you see `id_rsa.pub` or `id_ed25519.pub`, you already have SSH keys. Skip to [Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms).

#### Step 2: Generate New SSH Key

Run (replace with your GitHub email):

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**If your system doesn't support ed25519**, use RSA:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**Prompts:**
1. **"Enter file in which to save the key"**: Press **Enter** (default location)
2. **"Enter passphrase"**:
   - Press **Enter** for no passphrase
   - Or enter a passphrase for extra security
3. **"Enter same passphrase again"**: Press **Enter** or retype

**Expected output:**
```
Your identification has been saved in /home/yourusername/.ssh/id_ed25519
Your public key has been saved in /home/yourusername/.ssh/id_ed25519.pub
```

#### Step 3: Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

Expected output: `Agent pid 12345`

#### Step 4: Add SSH Key to Agent

```bash
ssh-add ~/.ssh/id_ed25519
```

Or if you used RSA:

```bash
ssh-add ~/.ssh/id_rsa
```

#### Step 5: Copy SSH Public Key

**Ubuntu/Debian (with xclip):**

```bash
# Install xclip if not installed
sudo apt install xclip

# Copy to clipboard
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

**Fedora/RHEL (with xclip):**

```bash
# Install xclip
sudo dnf install xclip

# Copy to clipboard
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

**Without xclip (any distro):**

```bash
cat ~/.ssh/id_ed25519.pub
```

Select and copy the entire output (starts with `ssh-ed25519`).

Now proceed to [Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms).

---

### macOS SSH Setup

#### Step 1: Check for Existing SSH Keys

Open Terminal (Applications > Utilities > Terminal):

```bash
ls -la ~/.ssh
```

If you see `id_rsa.pub` or `id_ed25519.pub`, you already have SSH keys. Skip to [Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms).

#### Step 2: Generate New SSH Key

Run (replace with your GitHub email):

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**For older Macs**, if ed25519 doesn't work:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**Prompts:**
1. **"Enter file in which to save the key"**: Press **Enter** (default location)
2. **"Enter passphrase"**:
   - Press **Enter** for no passphrase
   - Or enter a passphrase for extra security
3. **"Enter same passphrase again"**: Press **Enter** or retype

**Expected output:**
```
Your identification has been saved in /Users/yourusername/.ssh/id_ed25519
Your public key has been saved in /Users/yourusername/.ssh/id_ed25519.pub
```

#### Step 3: Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

Expected output: `Agent pid 12345`

#### Step 4: Add SSH Key to Agent and Keychain

**macOS Sierra 10.12.2 or later:**

First, check if `~/.ssh/config` exists:

```bash
touch ~/.ssh/config
```

Add this configuration:

```bash
cat >> ~/.ssh/config << EOF
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
EOF
```

Then add the key:

```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

**Older macOS versions:**

```bash
ssh-add -K ~/.ssh/id_ed25519
```

#### Step 5: Copy SSH Public Key

**Method 1: Copy to Clipboard (Easiest)**

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

**Method 2: Display and Copy Manually**

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output (starts with `ssh-ed25519`).

Now proceed to [Add SSH Key to GitHub](#add-ssh-key-to-github-all-platforms).

---

### Add SSH Key to GitHub (All Platforms)

This process is the same for all operating systems:

1. Go to [GitHub](https://github.com/) and sign in
2. Click your profile picture > **"Settings"**
3. In the left sidebar, click **"SSH and GPG keys"**
4. Click **"New SSH key"** (green button)
5. Fill in the details:
   - **Title**: Enter a descriptive name
     - Examples: "Personal Windows Laptop", "MacBook Pro", "Linux Desktop"
   - **Key type**: Select **"Authentication Key"**
   - **Key**: Paste your public key (starts with `ssh-ed25519` or `ssh-rsa`)
6. Click **"Add SSH key"**
7. If prompted, confirm with your GitHub password or 2FA code

---

### Test SSH Connection (All Platforms)

Run this command in Terminal/Command Prompt:

```bash
ssh -T git@github.com
```

**First time:**
```
The authenticity of host 'github.com (140.82.121.3)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Type **"yes"** and press Enter.

**Expected success message:**
```
Hi YourUsername! You've successfully authenticated, but GitHub does not provide shell access.
```

✅ **Success!** Your SSH key is working correctly.

---

## Part 4: Configure GitHub Email Settings

This process is the same for all operating systems (web-based).

### Step 1: Email Privacy

1. Go to **Settings** > **Emails**
2. Check the following options:
   - ✅ **"Keep my email addresses private"**
   - ✅ **"Block command line pushes that expose my email"**

3. **Note your private email**: `123456+username@users.noreply.github.com`
   - You'll use this for Git configuration (see [Git Installation Guide](git-installation.md))
   - This prevents your personal email from appearing in public commits

---

## Part 5: Complete Your Profile

This process is the same for all operating systems (web-based).

### Step 1: Add Profile Information

1. Go to your profile (click your picture > **"Your profile"**)
2. Click **"Edit profile"**
3. Add information:
   - **Name**: Your full name
   - **Bio**: Short description (e.g., "Python Developer | Student | Open Source Enthusiast")
   - **Company**: Your company or school (optional)
   - **Location**: Your city/country (optional)
   - **Website**: Personal website or portfolio (optional)
   - **Twitter**: Your Twitter handle (optional)
   - **Profile Picture**: Click "Edit" to upload a photo

4. Click **"Save"**

### Step 2: Create Your First Repository (Optional)

1. Click the **"+"** icon in top-right > **"New repository"**
2. Fill in details:
   - **Repository name**: `hello-world`
   - **Description**: "My first GitHub repository"
   - **Visibility**: Select **"Public"**
   - ✅ Check **"Add a README file"**
3. Click **"Create repository"**

🎉 Congratulations! You've created your first repository.

---

## ✅ Verification Checklist

- [ ] GitHub account created and email verified
- [ ] Two-factor authentication enabled (highly recommended)
- [ ] SSH key generated for your operating system
- [ ] SSH key added to GitHub account
- [ ] SSH connection tested successfully (`ssh -T git@github.com`)
- [ ] Email privacy settings configured
- [ ] Profile information completed
- [ ] First repository created (optional)

---

## 🚨 Troubleshooting

### Universal Issues

#### Issue: Not Receiving Verification Email

**Solution:**
1. Check spam/junk folder
2. Wait a few minutes and try again
3. Click "Resend verification email"
4. Try a different email address
5. Check email filters/rules

#### Issue: SSH Key Not Accepted

**Solution:**
1. Ensure you copied the **PUBLIC** key (`.pub` file)
2. Copy the entire key including `ssh-ed25519` or `ssh-rsa` at the beginning
3. Check for extra spaces or line breaks when pasting
4. Make sure the key type matches (Authentication Key)
5. Try generating a new key

#### Issue: "Permission denied (publickey)"

**Solution:**
1. Verify SSH agent is running
2. Check that key is added to agent:
   ```bash
   ssh-add -l
   ```
3. If not listed, add it:
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```
4. Verify the key is added to your GitHub account
5. Test connection: `ssh -T git@github.com`

### Windows-Specific Issues

#### Issue: ssh-keygen not found

**Solution:**
1. Ensure Git is installed (includes OpenSSH)
2. Use PowerShell or Git Bash instead of Command Prompt
3. Or install OpenSSH:
   - Settings > Apps > Optional Features
   - Add "OpenSSH Client"

#### Issue: ssh-agent not running

**Solution:**
```powershell
# Set ssh-agent to start automatically
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent
```

### Linux-Specific Issues

#### Issue: Permission denied on .ssh directory

**Solution:**
```bash
# Fix permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
```

#### Issue: ssh-agent not persisting

**Solution:**
Add to `~/.bashrc` or `~/.zshrc`:
```bash
# Start SSH agent automatically
if [ -z "$SSH_AUTH_SOCK" ]; then
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
fi
```

### macOS-Specific Issues

#### Issue: Keychain not saving SSH passphrase

**Solution:**
1. Ensure you used `--apple-use-keychain` flag
2. Update `~/.ssh/config`:
```bash
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

#### Issue: "ssh-add: illegal option -- K"

**Solution:**
- For macOS Monterey and later, use:
```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

---

## 🎓 GitHub Student Benefits

If you're a student, get free access to:
- **GitHub Copilot** (AI pair programmer)
- **GitHub Pro** (advanced features)
- **Azure credits** ($100/year)
- **Domain name** (1 year free)
- **JetBrains IDEs** (free licenses)
- And many more tools!

**Apply at:** [https://education.github.com/pack](https://education.github.com/pack)

**Requirements:**
- Valid student email address or school ID
- Proof of enrollment

---

## 📚 Additional Resources

- [GitHub Docs](https://docs.github.com/)
- [GitHub Learning Lab](https://lab.github.com/)
- [GitHub Skills](https://skills.github.com/)
- [SSH Key Guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [2FA Guide](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa)

---

## ➡️ Next Steps

Once your GitHub account is set up, proceed to:
- [Git Installation and Configuration Guide](git-installation.md) - Configure Git to work with your GitHub account

---

**Last Updated:** February 2026
