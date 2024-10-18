## Git Basic Commands

### **1. Cloning a Repository**

You can now clone a repository to your local machine.

#### **Cloning via SSH**:

```bash
git clone git@github.com:username/repository.git
```

#### **Cloning via HTTPS**:

If you didn’t set up SSH, you can use HTTPS:

```bash
git clone https://github.com/username/repository.git
```

---

### **2. Initializing a New Git Repository**

#### **Step 1: Create a New Directory**:

```bash
mkdir my-new-project
cd my-new-project
```

#### **Step 2: Initialize Git**:

Initialize the directory as a Git repository:

```bash
git init
```

#### **Step 3: Add Files**:

Create a new file, e.g., `README.md`:

```bash
echo "# My New Project" >> README.md
```

#### **Step 4: Stage Files**:

Add files to the staging area before committing:

```bash
git add .
```

#### **Step 5: Commit Files**:

Commit the staged files with a message:

```bash
git commit -m "Initial commit"
```

#### **Step 6: Link to GitHub**:

- First, create a repository on GitHub.
- Add the GitHub repository as a remote:
  ```bash
  git remote add origin git@github.com:username/repository.git
  ```
- Push the changes:
  ```bash
  git push -u origin main
  ```

---
