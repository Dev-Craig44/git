## Collaboration

<div align="left">

### Common Collaboration Workflows

- **Centralized Workflow**:  
   In a centralized version control system, all team members work from a single central repository. This setup makes everyone dependent on that central server—if it goes down, work halts for everyone.

- **Distributed Workflow (e.g., Git)**:  
   In distributed systems like Git, every developer has a full copy of the repository on their local machine. This allows for offline work and local commits. When ready, developers push their changes to a central repository, typically hosted on a server or a cloud service such as <a href="https://github.com/" target="_blank">GitHub</a>, <a href="https://gitlab.com/" target="_blank">GitLab</a>, or <a href="https://bitbucket.org/" target="_blank">Bitbucket</a>.

    <ul>
        <li>Developers can synchronize work directly, but this is often complex and error-prone.</li>
        <li>Most teams use a <strong>centralized workflow</strong> with a shared remote repository. This avoids a single point of failure—if the central repo is unavailable, local work can continue and be synchronized later.</li>
        <li>The central repository can be hosted on a private server or a cloud platform for accessibility.</li>
    </ul>

### Pushing, Fetching, and Pulling Changes

- <strong>Pushing</strong>: Upload your local commits to the central repository.
- <strong>Fetching</strong>: Download new data from the central repository without merging.
- <strong>Pulling</strong>: Fetch and merge changes from the central repository into your local branch.

### Working with Pull Requests, Issues, and Milestones

- <strong>Pull Requests</strong>: Propose changes to a repository. Other team members or maintainers can review, discuss, and merge these changes.
- <strong>Issues</strong>: Track bugs, enhancements, or tasks.
- <strong>Milestones</strong>: Group issues and pull requests to track progress toward a goal.

### Contributing to Open-Source Projects: The Integration-Manager Workflow

- In open-source projects, maintainers manage the official repository, while contributors fork the repository to their own accounts.
- <ol>
          <li><strong>Fork</strong> the repository to create your own copy in the cloud.</li>
          <li><strong>Clone</strong> your fork to your local machine and make commits.</li>
          <li><strong>Push</strong> your changes to your forked repository.</li>
          <li><strong>Send a pull request</strong> to the original repository.</li>
          <li>The maintainer reviews, pulls, and merges your changes into the official repository.</li>
  </ol>
- This is called the <strong>integration-manager workflow</strong> because maintainers are responsible for integrating contributions from others.

</div>

### Creating a New Repository on GitHub

1. Go to your GitHub account and click the **New** button to create a repository.
2. Fill in the repository name and description.
3. Select the option **"Add a README file"**—this initializes the repository with a README and makes the first commit for you.
4. Click **Create repository**.

This setup gives your project a starting point and allows collaborators to immediately see project details.

### Adding Collaborators to Your Repository

1. Navigate to your repository on GitHub.
2. Click on the **Settings** tab.
3. In the sidebar, select **Collaborators** or **Manage access** (depending on your GitHub interface).
4. Click **Add people** and enter the GitHub username or email address of the person you want to invite.
5. Choose the appropriate permission level (e.g., read, write, admin).
6. Click **Add** to send the invitation.

The invited collaborator will receive an email notification and must accept the invitation before they can access the repository.

### Cloning a Repository

To clone a repository from GitHub:

1. Go to the repository page on GitHub.
2. Click the **Code** button and copy the repository URL (choose HTTPS, SSH, or GitHub CLI as needed).
3. Open your terminal.
4. Type the following command, then paste the URL you copied:

   ```bash
   git clone <repository-url>
   ```

   For example:

   ```bash
   git clone https://github.com/username/repository.git
   ```

   This will create a new directory with the same name as the repository.

5. **Optional:** If you want the cloned directory to have a different name, add your desired name at the end of the command, separated by a space:

   ```bash
   git clone https://github.com/username/repository.git my-folder
   ```

   This will clone the repository into a directory called `my-folder` instead.

   ### Understanding `origin/master` and `origin/HEAD`

   When you clone a repository from GitHub, Git sets up a remote called `origin` that points to the original repository. The references like `origin/master` and `origin/HEAD` help you track the state of branches on the remote repository:

   - **`origin/master`**: This is a remote-tracking branch that tells you where the `master` branch is on the `origin` repository (the one on GitHub). It updates when you fetch or pull, but you can't check it out directly or commit to it—it's just a reference.
   - **`origin/HEAD`**: This is a symbolic reference that points to the default branch on the remote (`origin`). For most repositories, this is `origin/master` or `origin/main`. It helps Git know which branch to check out by default when you clone.

   These references allow you to see how your local branches compare to the remote ones. While you only have your local branches (like `master`), the `origin/*` references keep you informed about the state of the remote repository.

## Working with Remote Repositories

You can use `git remote` to list the remote repositories connected to your local repository.  
A remote repository is a repository that exists outside your local machine, or more specifically, outside your current directory.

To view detailed information about your remotes, run:

```sh
git remote -v
```

This command will display the URLs for each remote, both for fetching and pushing. For example:

```
origin  https://github.com/codewithmosh/Mars.git (fetch)
origin  https://github.com/codewithmosh/Mars.git (push)
```

A new line of code

Tey another line of code

- if commits were made to the remote repository, you can use `git fetch` to update your local repository with the latest changes
- so git is going to downlaod this new commit and then move origin/master forward.
- even though we downloaded this new commit, our working directory is not updated.

  - because currently master branch is "A" and origin/master is "B"
  - to bring in those changes we must switch to the master branch type `git merge origin/master`

- use `git branch -vv` this shows how our local and remote tracking branches are diverging

### How do I stash my changes before merging?

If you have uncommitted changes and want to temporarily save them before merging another branch, you can use `git stash`. This command stores your changes and reverts your working directory to the last commit.

To stash your changes:

```sh
git stash
```

After merging, you can reapply your stashed changes with:

```sh
git stash pop
```

### Pulling Changes from a Remote Repository

To update your local repository with changes from the remote, you typically need to **fetch** the latest commits and then **merge** them into your local branch. The `git pull` command combines these two steps:

```sh
git pull
```

This command fetches new commits from the remote repository and merges them into your current branch.

#### Using Rebase Instead of Merge

Rebasing provides a cleaner project history by replaying your local commits on top of the fetched changes, rather than creating a merge commit. To pull with rebase, use:

```sh
git pull --rebase
```

This fetches the latest changes and applies your local commits on top, resulting in a linear commit history.

## Pushing

When you want to upload your local commits to the remote repository, you typically use `git push`. However, there are some important considerations:

### Force Pushing (`git push -f`)

- Using `git push -f` (force push) tells Git to overwrite the remote branch with your local branch, discarding any commits on the remote that are not in your local history.
- For example, if the remote branch has commits `a ← b ← d` (where `d` is someone else's work), and your local branch has `a ← b ← c` (your work), force pushing will replace `d` with `c` on the remote.
- **Warning:** You should **never** use force push unless absolutely necessary (e.g., you made a serious mistake), as it can erase other people's work.

### The Correct Workflow

1. **Pull First:**  
   If the remote branch has new commits, always pull the latest changes before pushing.  
   For example:

   - Local: `a ← b ← c` (your branch)
   - Remote: `a ← b ← d` (origin/master)

   Run:

   ```sh
   git pull
   ```

2. **Merge or Rebase:**  
   After pulling, you may need to merge or rebase to integrate the remote changes (`d`) with your local commits (`c`). If there are conflicts, resolve them.

3. **Push Safely:**  
   Once your local branch is up to date and conflicts are resolved, push your changes to the remote repository:
   ```sh
   git push
   ```

This workflow ensures you do not overwrite others' work and keeps the repository history safe and consistent.

## Storing Credentials

When pushing to a remote repository, you typically don't want to enter your username and password every time. Git provides credential helpers to securely store your credentials, either in memory or on disk.

### Credential Helpers

- **In-Memory Cache:**  
   Store credentials in memory for a short period (default: 15 minutes).  
   Set up with:

  ```sh
  git config --global credential.helper cache
  ```

- **macOS (Keychain):**  
   Use the macOS Keychain to securely store credentials.

  1.  Check if the helper is available:
      ```sh
      git credential-osxkeychain
      ```
  2.  Set up the helper:
      ```sh
      git config --global credential.helper osxkeychain
      ```

- **Windows (Credential Manager):**  
   Use the Windows Credential Store to save credentials securely:
  ```sh
  git config --global credential.helper manager
  ```

These helpers store sensitive information like passwords and tokens in an encrypted format, keeping your data secure.

> **Tip:** Always use a credential helper appropriate for your operating system to avoid repeatedly entering your credentials.

## Sharing Tags

By default, the `git push` command does **not** push tags to the remote repository. Tags are useful for marking specific points in your project’s history (such as releases).

### Creating and Pushing Tags

1. **Create a tag:**  
   To attach a tag (e.g., `v1.0`) to your latest commit, run:

   ```sh
   git tag v1.0
   ```

   This tag exists only in your local repository.

2. **Share a tag:**  
   To share the tag with others, push it to the remote repository:
   ```sh
   git push origin v1.0
   ```

### Downloading Tags

You can fetch tags from the remote repository to your local repository. This is helpful for checking out specific releases or states of the project.

### Deleting Tags

- **Delete a tag from the remote:**  
  If you accidentally pushed a tag and want to remove it from the remote:

  ```sh
  git push origin --delete v1.0
  ```

  This deletes the tag from the remote repository, but it still exists locally.

- **Delete a tag locally:**  
  To remove the tag from your local repository:
  ```sh
  git tag -d v1.0
  ```

> **Note:** Deleting a tag from the remote does **not** remove it from your local repository, and vice versa.

## Releases

GitHub provides a **Releases** feature that works closely with tags to help you manage and distribute your software.

- **Create a Release:**  
   Navigate to the **Tags** section of your repository, then click on the **Releases** tab. Here, you can create a new release to package your software.

- **Attach Assets:**  
   You can include source code, binary files, and detailed release notes with each release. Uploaded binaries will appear in the **Assets** section after publishing.

- **Tagging:**  
   When you create a release, GitHub automatically creates a tag for the latest commit (if one doesn't already exist).

- **Pre-release Option:**  
   If your release is not production-ready, you can mark it as a **pre-release** by selecting the corresponding checkbox.

- **Note:**  
   Releases are a **GitHub feature**, not a core Git feature. They provide a convenient way to share packaged versions of your project with others.

This makes it easy for users to download specific versions of your project, complete with documentation and compiled assets.

# Sharing Branches

By default, branches you create in your local repository are private and not visible to others. To collaborate on a branch with your team, you need to explicitly push it to the remote repository.

## Pushing a New Branch

If you create a new branch (e.g., `feature/change-password`) and try to run `git push`, you may see an error like:

```
fatal: The current branch feature/change-password has no upstream branch.
```

This means your branch is not yet linked to a branch on the remote (`origin`).

To push your new branch and set the upstream (so future pushes are easier), use:

```sh
git push -u origin feature/change-password
```

- The `-u` flag sets up tracking between your local branch and the remote branch.

## Viewing Branches

- To see all local branches and their tracking status:
  ```sh
  git branch -vv
  ```
- To list all remote branches:
  ```sh
  git branch -r
  ```

## Deleting a Remote Branch

When you're done with a branch and want to remove it from the remote repository, run:

```sh
git push -d origin feature/change-password
```

- This deletes the branch from the remote (`origin`).

Note: After deleting the remote branch, it may still appear in the output of `git branch -r` until you fetch the latest updates:

```sh
git fetch -p
```

## Deleting a Local Branch

To delete the branch from your local repository (after switching to another branch, such as `main` or `master`):

```sh
git branch -d feature/change-password
```

This cleans up your local branches and keeps your repository organized.

# Collaboration Workflow Example

Suppose you and Amy are working together on a new feature. Here’s a step-by-step workflow for effective collaboration using Git and GitHub:

## 1. Creating and Sharing a Feature Branch

- One of you (e.g., you) creates a new feature branch locally and pushes it to GitHub:
  ```sh
  git checkout -b feature/change-password
  git push -u origin feature/change-password
  ```
- Alternatively, you can create the feature branch directly on GitHub and then fetch it locally.

- To see the new branch on your local machine:

  - Run `git fetch` to update your list of remote branches.
  - `git branch` will **not** show the new feature branch yet.
  - `git branch -r` will show it as `origin/feature/change-password`.

- To start working on the remote feature branch locally:
  ```sh
  git switch -C feature/change-password origin/feature/change-password
  ```
  > **Note:** If your Git version does not support `git switch`, use:
  >
  > ```sh
  > git checkout -b feature/change-password origin/feature/change-password
  > ```

## 2. Amy Joins the Collaboration

- Amy clones the repository from GitHub:
  ```sh
  git clone <repository-url>
  ```
- After cloning, she also won’t see the feature branch with `git branch`.
- She fetches the latest branches and creates a local branch tracking the remote:

  ```sh
  git fetch
  git switch -C feature/change-password origin/feature/change-password
  ```

  > **Note:** Or use `git checkout -b feature/change-password origin/feature/change-password` if needed.

- Amy makes changes, commits (e.g., "update file1"), and pushes to the shared feature branch:
  ```sh
  git add file1
  git commit -m "Update file1"
  git push
  ```

## 3. Ongoing Collaboration

- Both of you continue to push your changes to the shared feature branch.
- Regularly pull each other's changes to stay up to date:
  ```sh
  git pull
  ```
- If there are conflicts, resolve them locally before pushing again.

## 4. Closing the Feature Branch

- When the feature is complete, the person responsible (e.g., you) should:
  - Pull the latest changes to ensure everything is up to date:
    ```sh
    git pull
    ```
  - Review the commit history:
    ```sh
    git log
    ```
  - Merge the feature branch into the main branch (e.g., via a pull request on GitHub) and delete the feature branch if desired.

---

This workflow ensures smooth collaboration, minimizes conflicts, and keeps everyone in sync.

### Cleaning Up After Finishing a Feature Branch

Once you’re done with the feature branch, follow these steps to clean up both the remote and local references:

1. **Delete the branch from the remote repository:**

   ```sh
   git push -d origin feature/change-password
   ```

   This removes the branch from the remote (`origin`).

2. **Delete the local branch:**

   First, check your local branches:

   ```sh
   git branch
   ```

   Then, delete the feature branch locally:

   ```sh
   git branch -d feature/change-password
   ```

3. **Remove remote-tracking branches that no longer exist on the remote:**

   ```sh
   git remote prune origin
   ```

   This cleans up any stale references to branches that have been deleted from the remote.

---

By following these steps, multiple collaborators can efficiently work on a feature branch and keep their repositories tidy after the work is complete.

# Pull Request

- Quite often, as part of implementing a feature or fixing a bug, we would like other team members' feedback about our code. This is where we use a **pull request**.
- With a pull request, we open a discussion with the team before merging a branch into `master` (or `main`).

**Typical Pull Request Workflow:**

1. Go to the **Pull Requests** tab on GitHub and click **New pull request**.
2. Select the base branch (e.g., `master`) and the compare branch (e.g., your feature branch).
3. Click **Create pull request** and provide a descriptive title, such as `Feature: Social Login`.
4. Add a summary or description of the changes.

**Code Review Process:**

- A reviewer examines the pull request and may request changes. For example, they might comment:
  > "Please capitalize the 'h' in the heading."
- You (or Amy) make the requested changes in the feature branch, commit, and push them:
  ```sh
  git add .
  git commit -m "Capitalize 'h' in heading"
  git push
  ```
- The reviewer checks the updates and, if satisfied, approves the pull request.

**Merging and Cleaning Up:**

1. Once approved, merge the pull request on GitHub (choose **Squash and merge** or **Merge** as appropriate).
2. After merging, you can choose to **delete the feature branch** on GitHub.

**Syncing and Cleaning Up Locally (on Amy's workstation):**

1. Pull the latest changes from the remote:
   ```sh
   git pull
   ```
2. Prune deleted remote branches:
   ```sh
   git fetch -p
   ```
3. Delete the local feature branch (after switching to another branch, e.g., `main`):
   ```sh
   git branch -d feature/social-login
   ```

This process ensures that the code is reviewed, merged, and both remote and local repositories are kept clean and up to date.

## Resolving Conflicts

Suppose Amy, working on the `feature/logout` branch, adds the word "hello" to `file1`. Meanwhile, someone else makes conflicting changes to the same part of `file1` on the `main` branch.

When Amy tries to open a pull request from `feature/logout` to `main`, GitHub detects that both branches have modified the same section of `file1` and displays a message:  
**"This branch has conflicts that must be resolved."**

This means the conflicting changes must be reviewed and fixed manually before the pull request can be merged.

**Typical Conflict Resolution Workflow:**

1. **Pull the Latest Changes:**  
   The person responsible for merging (Amy or another team member) should first pull the latest changes from the `main` branch:

   ```sh
   git checkout feature/logout
   git pull origin main
   ```

2. **Resolve Conflicts:**  
   Git will pause and highlight the conflicting files. Open each file and look for conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`). Edit the file to keep the desired changes and remove the markers.

3. **Mark as Resolved and Commit:**  
   After resolving all conflicts, stage the changes and create a new commit:

   ```sh
   git add file1
   git commit -m "Resolve merge conflict in file1"
   ```

4. **Push the Updated Branch:**  
   Push the resolved branch to GitHub:

   ```sh
   git push
   ```

5. **Complete the Pull Request:**  
   Once the conflicts are resolved and pushed, the pull request can be merged as usual.

> **Tip:** Always communicate with your team when resolving conflicts to avoid overwriting important changes.

### Issues

Issue tracking goes hand-in-hand with pull requests and is a core part of collaborative development on GitHub.

- Click on the **Issues** tab in your repository to track bugs, request new features, suggest enhancements, or discuss ideas with your team.
- To create a new issue, click **New Issue** and provide a descriptive title (e.g., `Send email when someone signs up`).
- You can attach files, screenshots, or other resources to help clarify the issue.
- Assign issues to specific team members, or leave them unassigned so others can pick them up.
- Issues can be linked to pull requests. When a pull request that references an issue is merged and closed, the issue will be automatically closed as well.

> **Tip:** Use keywords like `Fixes #123` or `Closes #123` in your pull request description to automatically close the linked issue when the pull request is merged.

#### Labels

- Labels help categorize issues and pull requests, making it easier to organize and filter work.
- For example, if you assign the **enhancement** label to an issue, you'll see a count next to the label indicating how many open issues or pull requests are associated with it.
- Clicking a label shows all issues and pull requests tagged with that label, allowing you to quickly view related work in one place.

##### Milestones

Milestones are used to track progress toward specific goals or project phases. You can group related issues and pull requests under a milestone to monitor how much work has been completed and what remains. This provides a clear overview of your team's progress and helps with planning and prioritization.

- Add multiple issues or pull requests to a milestone.
- View milestone progress as a percentage of completed items.
- Use milestones to organize releases, sprints, or major features.

##### Contributing to Open-Source Projects

To contribute to an open-source project, follow these steps:

1. **Fork the Repository:**  
   Create a copy of the original repository under your own GitHub account by clicking the **Fork** button.

2. **Clone Your Fork:**  
   Download your forked repository to your local machine:

   ```sh
   git clone https://github.com/your-username/vidly-mvc-5.git
   ```

3. **Create a Feature Branch:**  
   Create a new branch for your changes (e.g., `bugfix`):

   ```sh
   git checkout -b bugfix
   ```

4. **Make Your Changes:**  
   For example, add `hello` to the `README.md` file.

5. **Commit and Push:**  
   Commit your changes and push the branch to your fork:

   ```sh
   git add README.md
   git commit -m "Add hello to README"
   git push origin bugfix
   ```

6. **Open a Pull Request:**  
   Go to the original repository on GitHub and click **New pull request**.  
   You'll see a comparison like:

   ```
   base repo: mosh-hamedani/vidly-mvc-5  base: master
   head repo: your-username/vidly-mvc-5  compare: bugfix
   ```

   This means you are proposing to merge your `bugfix` branch from your fork into the `master` branch of the original repository.

7. **Collaborate and Update:**  
   Discuss any requested changes with the maintainers, update your branch as needed, and once approved, your changes will be merged.

> **Tip:** Always use descriptive branch names and commit messages to make your contributions clear and easy to review.
