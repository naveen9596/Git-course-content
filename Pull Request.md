In Git, collaboration features like creating pull requests and conducting code reviews are essential for team-based workflows. Here’s a breakdown of how these features work:

### 1. **Pull Requests (PRs)**

A **pull request** (often abbreviated as PR) is a Git feature provided by platforms like GitHub, GitLab, and Bitbucket, allowing team members to notify others about changes they have made and propose merging those changes into a target branch. Here’s how they work:

   - **Creating a Pull Request:**
      - After making changes in a feature branch, the developer pushes this branch to the remote repository.
      - They can then create a pull request (PR) from the feature branch into the target branch (usually the main branch).
      - A PR serves as a request for review and merging, presenting a summary of the changes and linking the modified code.

   - **Benefits of Pull Requests:**
      - PRs provide a **collaboration checkpoint**—they let others review changes before they’re merged.
      - PRs often include **comments, discussions, and suggestions** from other team members.
      - They keep a **record of changes** and why they were made.

### 2. **Code Review in Pull Requests**

Code review is an integral part of the pull request process, allowing team members to inspect code changes, identify bugs, and suggest improvements before changes are merged. This helps improve code quality and ensures consistency. Here’s how it works:

   - **Reviewing the Code:**
      - Reviewers are assigned to the pull request and examine the code.
      - They can **add inline comments** on specific lines to point out issues, suggest improvements, or ask questions.
      - Some platforms have options for **approving, requesting changes, or blocking the PR** based on the code review outcome.

   - **Resolving Comments and Making Changes:**
      - The author can **respond to comments** or **make changes** in response to feedback.
      - Changes can be pushed to the same branch, which automatically updates the pull request with the latest changes.
      - Once all reviewers are satisfied, they **approve the PR**, and it can then be merged.

### 3. **Merging a Pull Request**

After code review and approvals, the PR can be merged. Merging methods vary:

   - **Merge Commit**: This creates a merge commit and keeps the branch history intact.
   - **Squash and Merge**: This combines all commits from the PR into one, making the history cleaner.
   - **Rebase and Merge**: This replays commits from the PR on top of the target branch for a linear history.

### 4. **Additional Collaboration Features**

   - **Draft Pull Requests**: Allow developers to open pull requests for work-in-progress code and signal to others that it’s not ready for a full review.
   - **Approval Workflow**: Some repositories have settings requiring a minimum number of approvals before merging.
   - **Automated Checks**: PRs can trigger CI/CD checks to automatically validate code quality, passing builds, or running tests before merging.

Using pull requests and code reviews encourages better code practices, fosters knowledge sharing, and reduces the risk of bugs being introduced.
