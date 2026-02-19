# Git & GitHub: Very Basic Tutorial

This short guide covers common Git and GitHub tasks: creating/cloning repositories, making commits, pushing, branching, and using GitHub Desktop.

Prerequisites:
- Git installed locally (https://git-scm.com)
- A GitHub account

1. Creating a repository

- On GitHub (recommended):
  1. Sign in to [GitHub](https://github.com), and on the top-right, press the **+** icon, then select **New repository**.
![GitHub SS](./images/ss01.png)
  2. Enter a name, choose public/private, scroll down to the bottom and click **Create repository**.
![GitHub SS](./images/ss02.png)
  3. Cloning a repository
    - From GitHub copy the repository URL
![GitHub SS](./images/ss03.png)
    - In your [terminal](a "Git Bash or PowerShell on Windows"), navigate to the folder where you want to clone the repo and run:
```bash
cd C:/Projects # create this folder if it doesn't exist
git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
# Sign in with GitHub if prompted
cd REPO_NAME
# Check the status of your repo
$ git status
code . # Open in VS Code (optional)
```
![Terminal SS](./images/ss04.png)
![VS Code SS](./images/ss05.png)
> This is an empty [repository](a "A repository is a storage location for your project files"), so there are no files yet. You can add files and commit them to start building your project.

3. Creating updates

- Try to add or modify files with your editor.
- You may open VSCode's Terminal (Ctrl+`) to run Git commands without leaving the editor.
- Also ensure that `bash` or similar shell is selected instead of PowerShell for a more consistent experience with Git commands.
!["VS Code SS - Empty Repository"](./images/ss06.png)
- Check status with the following command.
```bash
$ git status
```
![VS Code SS - Unstaged](./images/ss07.png)
- You should see the new file from the red text. We will need to stage it.

4. Committing updates

- [Stage](a "Staging files is the process of adding changes to the staging area before committing") and commit your changes:
```bash
$ git add newfile1.txt
# Check that the file is staged (green text) and ready to be committed
$ git status
$ git commit -m "Add newfile1.txt with initial content"
# Check that there are no changes to commit
$ git status
```
![VS Code SS - Staged](./images/ss08.png)

5. Pushing updates

- Push your commits to the remote branch:
  ```bash
  git push origin main
  ```
![Terminal SS - Push](./images/ss09.png)
- Refresh the GitHub repository page to see your new commit and file.
![GitHub SS - New Commit](./images/ss10.png)

6. Creating a different branch

> This is the most important part of Git — using branches to manage different changes without affecting the main codebase until you're ready to merge.

- Create and switch to a feature branch:
```bash
# Checks current branches
$ git branch
# Creates and switches to 'feature-xyz' branch
$ git checkout -B feature-xyz
# Check that you're on the new branch
$ git status
```
![Terminal SS - Branch](./images/ss11.png)

- Create a new file, and modify existing file:
![VS Code SS - Branch Changes](./images/ss12.png)
- Stage files, commit, and push to the new branch:
```bash
# Check changes and take note of the modified and new files
$ git status
# Stage both the new and modified files
$ git add newfile2.txt modifiedfile1.txt
## OR!!! You can also stage all changes with:
# Stages all changes.
$ git add .
$ git status # Check that all changes are staged
$ git commit -m "Add changes to feature-xyz"
```
![VS Code SS - Staged Branch Changes](./images/ss13.png)

- Push the new branch to GitHub:
```bash
# Check that you're still on 'feature-xyz' branch, you should see an asterisk (*) next to it and green text
$ git branch
# Pushes the 'feature-xyz' branch to GitHub, creating it if it doesn't exist:
$ git push origin feature-xyz
```
![Terminal SS - Push Branch](./images/ss14.png)

7. Creating a pull request on GitHub

- Go to `https://github.com/YOUR_USERNAME/REPO_NAME/pulls` and click **New pull request** to compare and create a pull request for your branch.
![GitHub SS - Pull Request](./images/ss15.png)
- On the `compare: ` selection box, choose your branch (`feature-xyz`) and click **Create pull request**.
![GitHub SS - Create Pull Request](./images/ss16.png)
![GitHub SS - Pull Request Details](./images/ss17.png)
- Set a title and description for your pull request, then click **Create pull request**.
![GitHub SS - Pull Request Created](./images/ss18.png)
- Explore the page, especially the `Files changed` tab to see the differences between your branch and the main branch.
![GitHub SS - PR Page](./images/ss19.png)
![GitHub SS - Files Changed](./images/ss20.png)
- You can switch back to the `Conversation` tab to see comments and discussions related to your pull request, and you can press the **Merge pull request** button to merge your changes into the main branch once you're ready.
![GitHub SS - Merge Pull Request](./images/ss21.png)
- When merging, it will ask you to confirm the merge and optionally edit the commit message for the merge commit. After confirming, your changes from `feature-xyz` will be merged into `main`.
![GitHub SS - Confirm Merge](./images/ss22.png)
![GitHub SS - Merge Completed](./images/ss23.png)
- After merging, you can go back to the `Code` tab (https://github.com/YOUR_USERNAME/REPO_NAME) to see the updated main branch.
![GitHub SS - Updated Main Branch](./images/ss24.png)


8. On your Visual Studio Code, you can pull the latest changes from the main branch to keep your local repository up to date.
- First, make sure you're on the main branch:
```bash
# You should still be on 'feature-xyz' branch
$ git branch
# Switch to main branch
$ git checkout main 
# NOTE: This will be the OUTDATED main branch without the latest changes we merged from Github. To update it, we need to pull the latest changes from GitHub:
```
![Terminal SS - Pull Main](./images/ss25.png)
- Pull the latest changes from the main branch on GitHub:
```bash
# Fetches the latest changes from the remote main branch
$ git fetch origin main 
# Merges the fetched changes into your local main branch
$ git pull origin main
```
![Terminal SS - Pull Main](./images/ss26.png)
- After pulling, your local main branch will now have the latest changes that were merged from the

# CHALLENGE
- Create a new branch and make some changes to your files. Then push the branch to GitHub and create a pull request. Finally, merge the pull request on GitHub and pull the latest changes to your local main branch.

# Important Things to observe:
- Main commits: https://github.com/YOUR_USERNAME/REPO_NAME/commits/main/
  - This page shows the commit history of the main branch, including all commits that have been merged into it. You can see details of each commit, such as the author, date, and commit message.
- Similarly, for branch commits: https://github.com/YOUR_USERNAME/REPO_NAME/commits/BRANCH_NAME/
  - This page shows the commit history of the specific branch you created, including all commits made to that branch. You can compare this with the main branch to see which commits are unique to your branch and which have been merged into main.