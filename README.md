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
