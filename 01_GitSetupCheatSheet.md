## **Complete Git and GitHub Setup & Cheat Sheet**

This guide provides a detailed walkthrough for setting up Git and GitHub on a new machine, followed by a cheat sheet of common Git commands and their use cases. It's designed for both beginners and those who need a refresher.

---

### **1. Installing Git**

#### **Windows**:

1.  Download Git from [git-scm.com](https://git-scm.com/download/win).
2.  Run the installer. During installation, select the default options unless you have specific requirements.
    - Key options:
      - Adjust the PATH environment: Select "Use Git from the command line and also from 3rd-party software".
      - Choose a text editor: By default, it uses Vim, but you can choose another editor (e.g., VSCode).
      - Git branch naming: By default, it sets the branch name to `master`. You can change it later.

#### **macOS**:

1.  Install Git using Homebrew (recommended):
    ```bash
    brew install git
    ```
2.  Alternatively, install Git from [git-scm.com](https://git-scm.com/download/mac).

#### **Linux**:

- Use the package manager for your distribution:
  - **Ubuntu/Debian**:
    ```bash
    sudo apt update
    sudo apt install git
    ```
  - **Fedora**:
    ```bash
    sudo dnf install git
    ```
  - **Arch**:
    ```bash
    sudo pacman -S git
    ```

#### **Verify Installation**:

After installation, check the Git version:

```bash
git --version
```

This ensures Git is correctly installed.

---

### **2. Git Configuration**

Configure Git to associate your commits with your identity. This is a one-time setup per machine.

```bash
# Set your name (to be used in commits)
git config --global user.name "Your Name"

# Set your email (to be used in commits)
git config --global user.email "your-email@example.com"
```

#### **Other Optional Configurations**:

- Set your preferred text editor for writing commit messages (e.g., VSCode):
  ```bash
  git config --global core.editor "code --wait"
  ```
- Set the default branch name (e.g., `main`):
  ```bash
  git config --global init.defaultBranch main
  ```

---
