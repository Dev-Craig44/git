# Collaboration Exercise

Follow these steps to simulate two users collaborating on a GitHub repository:

---

### 1. Create and Clone the Repository

- **Create** a GitHub repository named `Tokyo`.
- **Clone** the repository into two separate folders: `John` and `Amy`.  
   _(This simulates two users working on the same project.)_

---

### 2. John Makes a Commit

- In the `John` folder:
  - Make a commit.
  - Configure Git to store credentials in memory to avoid repeated prompts:
    ```sh
    git config --global credential.helper cache
    ```
  - Push your changes.

---

### 3. Amy Fetches and Merges

- In the `Amy` folder:
  - Fetch the latest changes:
    ```sh
    git fetch
    ```
  - View the commit history.
  - Merge `origin/master` into `master`:
    ```sh
    git merge origin/master
    ```

---

### 4. Amy Creates a Feature Branch

- In the `Amy` folder:
  - Create and switch to a new branch:
    ```sh
    git checkout -b feature/login
    ```
  - Make a commit.
  - Configure Git to store credentials in memory (again, since this is a different repo).
  - Push the new branch:
    ```sh
    git push -u origin feature/login
    ```

---

### 5. View Branches

- List local and remote branches:
  ```sh
  git branch -a
  ```

---

### 6. John Tracks the Feature Branch

- In the `John` folder:
  - Fetch updates:
    ```sh
    git fetch
    ```
  - View the history and note the new branch.
  - Create a local branch tracking `origin/feature/login`:
    ```sh
    git checkout -b feature/login origin/feature/login
    ```
  - Verify branches:
    ```sh
    git branch -a
    ```

---

### 7. Amy Adds Another Commit

- In the `Amy` folder:
  - Make another commit on `feature/login`.
  - Push the changes.

---

### 8. John Pulls Amy’s Changes

- In the `John` folder:
  - Pull the latest changes into `feature/login`:
    ```sh
    git pull
    ```
  - View the history.  
     _(The feature branch should now be two commits ahead of `master`.)_

---

### 9. Merge Feature Branch into Master

- In the `John` folder:
  - Switch to `master` and merge the feature branch:
    ```sh
    git checkout master
    git merge feature/login
    ```
  - View the history.  
     _(`master` is now ahead of `origin/master` by two commits.)_
  - Push to update `origin/master`:
    ```sh
    git push
    ```
  - Confirm `master` and `origin/master` are aligned.

---

### 10. Clean Up Feature Branch

- In the `John` folder:
  - Delete the remote feature branch:
    ```sh
    git push origin --delete feature/login
    ```
  - Delete the local feature branch:
    ```sh
    git branch -d feature/login
    ```
  - List branches to confirm removal.

---

### 11. Sync Amy’s Repository

- In the `Amy` folder:
  - Fetch updates and view history.
  - Note that `origin/master` is ahead of `master` by two commits.
  - Switch to `master` and merge:
    ```sh
    git checkout master
    git merge origin/master
    ```
  - Confirm `master` and `origin/master` are synchronized.

---

### 12. Final Cleanup

- In the `Amy` folder:
  - Delete local and remote-tracking branches as needed.

---

**Well done!**  
You’ve just completed a full collaboration workflow with Git.  
Go grab a coffee or your favorite drink—you’ve earned it!
