## Common Git Commands Cheat Sheet

#### **Basic Commands**:

1. **Check Repository Status**:

   ```bash
   git status
   ```

   - Shows the current status of your working directory and staging area (e.g., modified files, untracked files).

2. **Stage Changes**:

   - Stage a single file:
     ```bash
     git add filename
     ```
   - Stage all changes:
     ```bash
     git add .
     ```

3. **Commit Changes**:

   - Commit staged changes with a message:
     ```bash
     git commit -m "Your message here"
     ```

4. **Push Changes**:
   Push your commits to the remote repository:

   ```bash
   git push
   ```

5. **Pull Changes**:
   Fetch and merge changes from the remote repository:
   ```bash
   git pull
   ```

#### **Undoing Changes**:

1. **Unstage a File** (keep changes, remove from staging):

   ```bash
   git reset filename
   ```

2. **Discard Changes** (revert to last commit):

   ```bash
   git checkout -- filename
   ```

3. **Amend the Last Commit**:

   - Modify the last commit (useful if you forgot to include a file):
     ```bash
     git commit --amend
     ```

4. **Revert a Commit** (undo a specific commit):
   ```bash
   git revert commit-hash
   ```

#### **Remote Repositories**:

1. **List Remote Repositories**:

   ```bash
   git remote -v
   ```

2. **Add a Remote Repository**:

   ```bash
   git remote add origin git@github.com:username/repository.git
   ```

3. **Remove a Remote Repository**:
   ```bash
   git remote remove origin
   ```

#### **Viewing Commit History**:

1. **View Commit History**:

   ```bash
   git log
   ```

2. **View a Shorter Log** (one line per commit):
   ```bash
   git log --oneline
   ```

---
