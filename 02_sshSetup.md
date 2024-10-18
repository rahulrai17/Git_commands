## Setting Up SSH Keys for GitHub\*\*

SSH keys provide a secure way to authenticate to GitHub without entering a password every time.

#### **Step 1: Generate an SSH Key**

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

If your system does not support `ed25519`, use:

```bash
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
```

Press Enter to accept the default file location. You may choose to set a passphrase for added security.

#### **Step 2: Add SSH Key to SSH Agent**

- Start the SSH agent:
  ```bash
  eval "$(ssh-agent -s)"
  ```
- Add the SSH private key to the agent:
  ```bash
  ssh-add ~/.ssh/id_ed25519
  ```

#### **Step 3: Add SSH Key to GitHub**

1.  Copy the SSH public key to your clipboard:
    ```bash
    cat ~/.ssh/id_ed25519.pub
    ```
2.  Go to **GitHub > Settings > SSH and GPG Keys**.
3.  Click **New SSH Key**, give it a title (e.g., "My Laptop"), and paste your SSH key. Save it.

#### **Step 4: Test SSH Connection**

To verify if your SSH key works with GitHub:

```bash
ssh -T git@github.com
```

If successful, you’ll see a message like:

```bash
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---
