## Git Branching Stratergy Step by Step

### Project Lifecycle and Branching Workflow

In the **Gitflow** strategy, developers work through different branches (like `develop`, `feature`, `release`, and `main`) based on the phase of the project they are in. Let’s go step by step, starting from project initiation to making production releases.

---

### 1. **Starting the Project**

#### Step 1: **Initialize the Repository**

When you start a new project, the first step is to create a Git repository and initialize your **main** branch. This is where the first version of your project will live.

**Commands:**

```bash
git init
git checkout -b main
git commit -m "Initial commit"
git push origin main
```

- **`main`**: The `main` branch (sometimes called `master`) is considered the **stable, production-ready branch**. When you make releases, your production code lives here.

#### Step 2: **Create a `develop` Branch**

After initializing the `main` branch, the next step is to create the `develop` branch. This is where all the ongoing development happens before it gets merged into `main` for production.

**Commands:**

```bash
git checkout -b develop
git push origin develop
```

- **`develop`**: This is your primary working branch where all feature branches merge. Developers branch off from `develop` to work on features and bug fixes.

### 2. **Working on Features**

#### Step 3: **Create Feature Branches**

When you start working on a new feature, you create a feature branch from the `develop` branch. Each feature is isolated to its own branch, allowing multiple developers to work on separate features without causing conflicts.

- **Feature Branch**: Named `feature/feature-name`, this is where all work related to a specific feature happens.

**Commands:**

```bash
git checkout develop
git checkout -b feature/feature-name
```

Now, you work on the feature in this branch:

```bash
git add .
git commit -m "feat: add user authentication"
```

- **Why Use Feature Branches?**:
  - They allow parallel development of different features.
  - They keep the `develop` branch clean and stable until features are complete.

#### Step 4: **Complete the Feature and Merge into `develop`**

Once the feature is complete, you need to merge it back into `develop`. To do this:

- Push your feature branch to the remote repository.
- Create a **Pull Request (PR)** from `feature/feature-name` to `develop`. This allows code review, testing, and conflict resolution before merging.

**Commands:**

```bash
git push origin feature/feature-name
# Open a PR on GitHub/GitLab/Bitbucket to merge into develop
git checkout develop
git merge feature/feature-name
git push origin develop
```

---

### 3. **Preparing for a Release**

Once you have developed multiple features in the `develop` branch, and it’s time to prepare for a production release, you initiate a **release branch**. This branch helps you stabilize the code, make minor bug fixes, and perform final testing before pushing it to production.

#### Step 5: **Create a Release Branch**

- When your `develop` branch is stable and ready to be pushed to production, you create a **release branch**.
- The release branch allows developers to fix minor bugs and polish the code without affecting new feature development in `develop`.
- Release branches are usually named with version numbers (`release/v1.0`, `release/v2.0`, etc.).

**Commands:**

```bash
git checkout develop
git checkout -b release/v1.0
git push origin release/v1.0
```

- **When to Create a Release Branch**:
  - When you are confident that your `develop` branch is in a stable state and you are ready for production.
  - All new features for this release should be merged into `develop` before you create the release branch.

#### Step 6: **Stabilize the Release Branch**

- In the release branch, you **do not add new features**. Only bug fixes, documentation updates, and release-related tasks (like updating the version number) are allowed.
- Conduct final testing on the release branch. If you find any bugs, fix them directly in this branch.

**Commands for Bug Fixing:**

```bash
git add .
git commit -m "fix: resolve minor bug in user authentication"
git push origin release/v1.0
```

- **Why a Release Branch?**:
  - It allows for thorough testing and stabilization before moving to production.
  - New features can continue to be developed in the `develop` branch without affecting the release.

---

### 4. **Releasing to Production**

Once you’re confident that the release branch is stable and ready to go live, you merge it into both the `main` and `develop` branches.

#### Step 7: **Merge Release into `main` and `develop`**

- First, you merge the release branch into `main`. This is your production branch, so it now holds the stable version of your app.
- Then, you merge the release branch back into `develop` so that any final fixes made in the release branch are incorporated back into the main development line.

**Commands:**

```bash
# Merge into main for production release
git checkout main
git merge release/v1.0
git push origin main

# Merge back into develop to sync the changes
git checkout develop
git merge release/v1.0
git push origin develop
```

- **Important**: Once the release is merged, delete the release branch to keep your Git history clean:
  ```bash
  git branch -d release/v1.0
  git push origin --delete release/v1.0
  ```

#### Step 8: **Tag the Release**

- After merging into `main`, tag the release with a version number so you can easily track it later.
- Tags mark important points in the history of the repository, such as the release of a new version.

**Commands:**

```bash
git tag -a v1.0 -m "Release version 1.0"
git push origin v1.0
```

- **Why Tag Releases?**:
  - It’s a way of marking significant milestones in the project’s lifecycle (such as a stable release).
  - Tags make it easier to roll back to a previous release if needed.

---

### 5. **Handling Hotfixes in Production**

Sometimes, after releasing to production, critical bugs are found that need to be fixed immediately. In this case, you use a **hotfix branch**.

#### Step 9: **Create a Hotfix Branch**

- Hotfix branches are created directly from the `main` branch. The goal is to apply a quick fix to production without waiting for the `develop` branch to stabilize.
- After the fix is complete, the hotfix branch is merged into both `main` (to fix the live version) and `develop` (to ensure the fix is incorporated into ongoing development).

**Commands:**

```bash
git checkout main
git checkout -b hotfix/urgent-fix
```

- Fix the issue and commit your changes:

```bash
git add .
git commit -m "fix: urgent production bug"
```

#### Step 10: **Merge Hotfix into `main` and `develop`**

- After fixing the bug, merge the hotfix branch into `main` to update the production code, and into `develop` to incorporate the fix into ongoing development.

**Commands:**

```bash
# Merge into main to update production
git checkout main
git merge hotfix/urgent-fix
git push origin main

# Merge into develop to sync the fix
git checkout develop
git merge hotfix/urgent-fix
git push origin develop
```

- After merging, delete the hotfix branch:

```bash
git branch -d hotfix/urgent-fix
git push origin --delete hotfix/urgent-fix
```

---

### **Summary of Branches and When to Use Them**

1. **`main`**: This is the production-ready branch. Only stable code is merged here. Releases are tagged here.
2. **`develop`**: The main working branch for ongoing development. New features are merged here.
3. **`feature/*`**: Feature branches are used to develop new features. They are created from `develop` and merged back into `develop`.
4. **`release/*`**: Created from `develop` when the code is ready to be prepared for a new production release. Bug fixes are done here, and it is eventually merged into both `main` and `develop`.
5. **`hotfix/*`**: Created from `main` to quickly patch production

bugs. It is merged into both `main` and `develop`.

By following this branching strategy, you ensure a smooth transition from development to production, minimize conflicts, and handle production bugs efficiently. This workflow supports parallel development, frequent releases, and efficient bug fixing.
