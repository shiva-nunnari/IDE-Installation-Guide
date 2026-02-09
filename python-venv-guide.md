# Python Virtual Environment (venv) Guide

## 📖 What is a Virtual Environment?

A virtual environment is an isolated Python environment that keeps your project's packages separate from your system Python. Each project gets its own dependencies without conflicts.

**Why use venv?**
- ✅ Isolate project dependencies
- ✅ Avoid package version conflicts
- ✅ Keep your system Python clean
- ✅ Share projects easily with `requirements.txt`

## 📋 Prerequisites

- Python installed (see [Python Installation Guide](python-installation.md))

---

## Creating a Virtual Environment

Navigate to your project folder and run:

**Windows:**
```bash
python -m venv venv
```

**Linux/macOS:**
```bash
python3 -m venv venv
```

This creates a `venv` folder in your project directory.

---

## Activating the Virtual Environment

### Windows

**Command Prompt:**
```bash
venv\Scripts\activate
```

**PowerShell:**
```powershell
venv\Scripts\Activate.ps1
```

*If you get an error, run this once:*
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Git Bash:**
```bash
source venv/Scripts/activate
```

### Linux/macOS

**Bash/Zsh:**
```bash
source venv/bin/activate
```

**Fish:**
```bash
source venv/bin/activate.fish
```

### Verification

When activated, you'll see `(venv)` in your prompt:
```bash
(venv) C:\Projects\my-project>
```

---

## Using the Virtual Environment

### Install Packages

```bash
pip install requests
pip install flask pandas numpy
```

### List Installed Packages

```bash
pip list
```

### Save Dependencies

```bash
pip freeze > requirements.txt
```

### Install from requirements.txt

```bash
pip install -r requirements.txt
```

### Deactivate

```bash
deactivate
```

---

## Quick Example

### Starting a New Project

**Windows:**
```bash
mkdir my-project
cd my-project
python -m venv venv
venv\Scripts\activate
pip install requests
pip freeze > requirements.txt
```

**Linux/macOS:**
```bash
mkdir my-project
cd my-project
python3 -m venv venv
source venv/bin/activate
pip install requests
pip freeze > requirements.txt
```

### Cloning an Existing Project

**Windows:**
```bash
git clone https://github.com/user/project.git
cd project
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

**Linux/macOS:**
```bash
git clone https://github.com/user/project.git
cd project
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## VS Code Integration

To make VS Code use your venv:

1. Press `Ctrl+Shift+P` (Windows/Linux) or `Cmd+Shift+P` (macOS)
2. Type "Python: Select Interpreter"
3. Choose the interpreter from your venv folder

---

## Important Notes

- **Always activate venv before installing packages**
- **Never commit the `venv` folder to Git** - add it to `.gitignore`
- **Always commit `requirements.txt`** to share dependencies

### .gitignore Example

```
venv/
__pycache__/
*.pyc
```

---

## Quick Reference

| Task | Windows | Linux/macOS |
|------|---------|-------------|
| Create venv | `python -m venv venv` | `python3 -m venv venv` |
| Activate | `venv\Scripts\activate` | `source venv/bin/activate` |
| Deactivate | `deactivate` | `deactivate` |
| Install package | `pip install package` | `pip install package` |
| Save deps | `pip freeze > requirements.txt` | `pip freeze > requirements.txt` |
| Install deps | `pip install -r requirements.txt` | `pip install -r requirements.txt` |

---

**That's it!** You're ready to use virtual environments in your Python projects. 🚀

---

**Last Updated:** February 2026
