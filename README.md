## Collaboration

<div align="left">

## Collaboration Workflows

### Centralized vs. Distributed

- **Centralized Workflow:**  
   All team members work from a single central repository. If the server goes down, work halts for everyone.

- **Distributed Workflow (e.g., Git):**  
   Every developer has a full copy of the repository locally. Developers can work offline, commit locally, and synchronize with a central remote (e.g., GitHub, GitLab, Bitbucket) when ready.

      - Direct peer-to-peer sync is possible but uncommon and error-prone.
      - Most teams use a shared remote repository, allowing local work to continue even if the remote is temporarily unavailable.

### Key Collaboration Actions

- **Push:** Upload your local commits to the remote repository.
- **Fetch:** Download new data from the remote without merging.
- **Pull:** Fetch and merge changes from the remote into your current branch.

### Pull Requests, Issues, and Milestones

- **Pull Requests:** Propose changes for review and discussion before merging.
- **Issues:** Track bugs, enhancements, and tasks.
- **Milestones:** Group issues and pull requests to track progress toward goals.

### Open-Source: Integration-Manager Workflow

1. **Fork** the repository to your own account.
2. **Clone** your fork locally and make commits.
3. **Push** changes to your fork.
4. **Open a pull request** to the original repository.
5. Maintainers review and merge your changes.

---

## Common GitHub Tasks

### Creating a New Repository

1. Click **New** on your GitHub account.
2. Fill in repository details and select **Add a README file**.
3. Click **Create repository**.

### Adding Collaborators

1. Go to your repository’s **Settings**.
2. Select **Collaborators** or **Manage access**.
3. Click **Add people**, enter their GitHub username or email, set permissions, and send the invitation.

### Cloning a Repository

```sh
git clone <repository-url>
```

Optionally, specify a folder name:

```sh
git clone <repository-url> my-folder
```

### Understanding `origin/master` and `origin/HEAD`

- `origin/master`: Remote-tracking branch for the remote's `master`.
- `origin/HEAD`: Symbolic reference to the default branch on the remote.

---

## Working with Remotes

- List remotes:
  ```sh
  git remote -v
  ```
- Add a remote:
  ```sh
  git remote add upstream <url>
  ```
- Remove a remote:
  ```sh
  git remote rm upstream
  ```

---

## Syncing and Updating

- Fetch latest changes:
  ```sh
  git fetch
  ```
- Merge remote changes:
  ```sh
  git merge origin/master
  ```
- See branch status:
  ```sh
  git branch -vv
  ```

### Stashing Changes

- Save uncommitted changes:
  ```sh
  git stash
  ```
- Reapply stashed changes:
  ```sh
  git stash pop
  ```

### Pulling with Rebase

- For a linear history:
  ```sh
  git pull --rebase
  ```

---

## Pushing and Sharing

- Push local commits:
  ```sh
  git push
  ```
- Force push (use with caution):
  ```sh
  git push -f
  ```
- Push a new branch and set upstream:
  ```sh
  git push -u origin <branch>
  ```
- Delete a remote branch:
  ```sh
  git push -d origin <branch>
  ```
- Delete a local branch:
  ```sh
  git branch -d <branch>
  ```

---

## Credentials

- Use credential helpers to avoid entering credentials repeatedly:
  - In-memory:
    ```sh
    git config --global credential.helper cache
    ```
  - macOS Keychain:
    ```sh
    git config --global credential.helper osxkeychain
    ```
  - Windows Credential Manager:
    ```sh
    git config --global credential.helper manager
    ```

---

## Tags and Releases

- Create a tag:
  ```sh
  git tag v1.0
  ```
- Push a tag:
  ```sh
  git push origin v1.0
  ```
- Delete a tag remotely:
  ```sh
  git push origin --delete v1.0
  ```
- Delete a tag locally:

  ```sh
  git tag -d v1.0
  ```

- GitHub **Releases** let you package and distribute software, attach assets, and provide release notes.

---

## Collaboration Example Workflow

1. **Create and share a feature branch:**
   ```sh
   git checkout -b feature/change-password
   git push -u origin feature/change-password
   ```
2. **Collaborator fetches and checks out the branch:**
   ```sh
   git fetch
   git switch -C feature/change-password origin/feature/change-password
   ```
3. **Both work, commit, and push changes.**
4. **Merge via pull request and clean up branches:**
   ```sh
   git push -d origin feature/change-password
   git branch -d feature/change-password
   git remote prune origin
   ```

---

## Pull Requests and Code Review

1. Open a pull request on GitHub.
2. Reviewers provide feedback; authors update the branch as needed.
3. Once approved, merge and delete the feature branch.
4. Sync and clean up locally:
   ```sh
   git pull
   git fetch -p
   git branch -d <feature-branch>
   ```

---

## Resolving Conflicts

1. Pull latest changes from the target branch:
   ```sh
   git checkout <feature-branch>
   git pull origin main
   ```
2. Resolve conflicts, stage, and commit:
   ```sh
   git add <file>
   git commit -m "Resolve conflict"
   ```
3. Push updates and complete the pull request.

---

## Issues, Labels, and Milestones

- Use **Issues** to track bugs, features, and tasks.
- Apply **Labels** for categorization.
- Group related work with **Milestones**.

---

## Contributing to Open Source

1. **Fork** the repository.
2. **Clone** your fork:
   ```sh
   git clone https://github.com/your-username/repo.git
   ```
3. **Create a branch** for your changes:
   ```sh
   git checkout -b my-feature
   ```
4. **Commit and push**:
   ```sh
   git add .
   git commit -m "Describe your change"
   git push origin my-feature
   ```
5. **Open a pull request** to the original repository.

---

## Keeping Your Fork Up to Date

1. Add the base repository as a remote:
   ```sh
   git remote add upstream https://github.com/original-owner/repo.git
   ```
2. Fetch and merge updates:
   ```sh
   git fetch upstream
   git checkout master
   git merge upstream/master
   git push origin master
   ```

---

## Quick Reference

```sh
# Clone a repository
git clone <url>

# Fetch and sync
git fetch
git pull
git push

# Branches
git branch -r
git branch -vv
git push -u origin <branch>
git push -d origin <branch>

# Tags
git tag v1.0
git push origin v1.0
git push origin --delete v1.0

# Remotes
git remote -v
git remote add upstream <url>
git remote rm upstream
```

</div>
