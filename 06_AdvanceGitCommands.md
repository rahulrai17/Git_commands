### ** Advanced Git Concepts**

## **Stashing Changes**:

Temporarily save changes without committing them.

```bash
git stash
```

- To apply the stashed changes later:
  ```bash
  git stash apply
  ```

#### **Cherry-Picking**:

Apply a specific commit to another branch.

```bash
git cherry-pick commit-hash
```

#### **Rebasing**:

Reapply commits on top of another base tip. Use it to keep a linear project history.

```bash
git rebase branch-name
```

---

### ** Global Git Ignore Setup**

To globally ignore certain files across all repositories:

1. Create a global `.gitignore` file:

   ```bash
   touch ~/.gitignore_global
   ```

2. Add rules to the file (e.g., ignore `.DS_Store`):

   ```bash
   echo ".DS_Store" >> ~/.gitignore_global
   ```

3. Configure Git to

use this global ignore file:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

---
