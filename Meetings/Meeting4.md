# Git and GitHub: A Comprehensive Guide

## Brief History of Git

Git was created by Linus Torvalds in 2005 for the development of the Linux kernel. It was designed to be fast, efficient, and support distributed, non-linear workflows. Before Git, Torvalds used BitKeeper, but after a controversy regarding its license, he decided to create his own version control system.

## What is Git?

Git is a distributed version control system that tracks changes in any set of computer files. It is designed for coordinating work among programmers, but can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows.

## What is Version Control?

Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. It allows you to:

- Revert files back to a previous state
- Revert the entire project back to a previous state
- Compare changes over time
- See who last modified something that might be causing a problem
- Who introduced an issue and when

## Difference between Git and GitHub

- **Git** is a version control system that lets you manage and keep track of your source code history.
- **GitHub** is a cloud-based hosting service that lets you manage Git repositories. It provides a web-based graphical interface and adds many features including access control, collaboration features, bug tracking, feature requests, etc.

In simple terms, Git is the tool, GitHub is a service that hosts Git repositories.

## How to Set Up Git

### For Windows

1. Download Git from [Download git from here](https://git-scm.com/downloads)
2. Run the installer with default options or your best preference
3. Verify installation by opening a terminal/command prompt and typing:

```bash
git --version
```

### For Linux

1. For Debian/Ubuntu/Arch-based distributions:

   ```bash
   sudo apt-get update
   sudo apt-get install git
   ```

   For Fedora:

   ```bash
   sudo dnf install git
   ```

   For CentOS/RHEL:

   ```bash
   sudo yum install git
   ```

   For Arch/EndeavourOS/Manjaro

   ```bash
   Sudo pacman -S git
   ```

2. Verify installation:

```bash
git --version
```

### For Mac

1. Install using Homebrew (recommended):

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   brew install git
   ```

   Alternatively, download the installer from [git-scm.com](https://git-scm.com/downloads)

2. Verify installation:

```bash
git --version
```

## Git Configuration

Git configuration lets you customize how Git works. Configuration can be at three levels:

1. System level: affects all users on the system
2. Global level: affects all repositories for the current user
3. Local level: specific to the current repository

## What is --global?

The `--global` flag in Git configuration commands sets configurations for the current user across all repositories. For example:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Basic Git Commands

### git init

Initializes a new Git repository in the current directory:

```bash
git init
```

This creates a new `.git` subdirectory that contains all the metadata for the new repository.

### git add

Adds files to the staging area (prepares them for commit):

```bash
git add filename    # Add a specific file
git add .           # Add all modified files
```

### git commit

Records changes to the repository with a descriptive message:

```bash
git commit -m "Your descriptive message about the changes"
```

## Branches in Git

### What are Branches and Why Use Them?

Branches are separate lines of development that allow you to work on different features or fixes simultaneously without affecting the main codebase (usually the main branch). Benefits include:

- Work on features in isolation
- Multiple developers can work simultaneously on different features
- Experimentation without affecting the main codebase
- Easier to manage releases and hot fixes

### git branch

Used to list, create, or delete branches:

```bash
git branch                  # List all local branches
git branch branch-name      # Create a new branch
git branch -d branch-name   # Delete a branch
```

### git checkout and git switch

Both commands help you navigate between branches:

**git checkout:**

```bash
git checkout branch-name         # Switch to an existing branch
git checkout -b new-branch-name  # Create a new branch and switch to it
```

**git switch** (newer alternative):

```bash
git switch branch-name           # Switch to an existing branch
git switch -c new-branch-name    # Create a new branch and switch to it
```

### git merge

Combines changes from different branches:

```bash
git merge branch-name  # Merges branch-name into the current branch
```

## What is a Conflict?

A conflict occurs when Git can't automatically resolve differences in code between two commits. This typically happens when two branches have made changes to the same part of the same file. When a conflict occurs, Git will mark the file as conflicted and halt the merging process, requiring manual resolution.

## Remote Repositories

### What is a Remote Repository?

A remote repository is a version of your project hosted on the internet or network. It allows collaboration with other developers by providing a central location where everyone can push their changes and pull others' changes.

### Git Remote Commands

Git provides several commands to manage remote repositories:

#### git remote

Lists the remote connections you have to other repositories:

```bash
git remote            # Shows short names of remotes
git remote -v         # Shows URLs of remotes with their names
```

#### git remote add

Adds a new remote repository connection:

```bash
git remote add <name> <url>
# Example:
git remote add origin https://github.com/username/repository.git
```

"Origin" is the conventional name for the primary remote repository.

#### git remote remove

Removes a remote connection:

```bash
git remote remove <name>
# Example:
git remote remove origin
```

#### git remote rename

Renames a remote connection:

```bash
git remote rename <old-name> <new-name>
# Example:
git remote rename origin upstream
```

#### git remote set-url

Changes the URL of an existing remote:

```bash
git remote set-url <name> <new-url>
# Example:
git remote set-url origin https://github.com/username/new-repository.git
```

### Push to Your Remote Repository

Uploading your local commits to a remote repository:

```bash
git push origin branch-name
```

Additional push options:

```bash
git push -u origin branch-name  # Sets up tracking relationship
git push --force                # Forces push (use with caution!)
git push --all                  # Pushes all branches
```

### Pull from the Remote Repository

Downloading changes from the remote repository to your local repository:

```bash
git pull origin branch-name
```

Alternative approach using fetch and merge:

```bash
git fetch origin           # Downloads changes without merging
git merge origin/branch    # Merges downloaded changes
```

### git fetch vs git pull

- `git fetch` only downloads new data from the remote repository but doesn't integrate it into your working files
- `git pull` is essentially a `git fetch` followed by a `git merge` - it downloads AND integrates changes

---

## GitHub as a Remote Repository

GitHub is one of the most popular hosting services for Git repositories. It provides:

- Hosting for repositories
- Web interface for Git
- Issue tracking
- Pull requests for code review
- Actions for continuous integration
- Project management tools

### git clone

Creates a copy of a remote repository on your local machine:

```bash
git clone https://github.com/username/repository.git
```

## Advanced: GitHub Authentication with Personal Access Tokens

As of August 13, 2021, GitHub no longer accepts password authentication for Git operations. Instead, you need to use a Personal Access Token (PAT) when authenticating with GitHub from the command line.

### What is a Personal Access Token?

A Personal Access Token is an alternative to using passwords for authentication to GitHub when using the GitHub API or the command line. PATs are more secure than passwords because:

- They are specific to GitHub
- They can be scoped to allow specific access permissions
- They can be revoked at any time without needing to change your password

### How to Generate a Personal Access Token

1. Log in to your GitHub account
2. Click on your profile photo in the top-right corner and select "Settings"
3. In the left sidebar, click on "Developer settings"
4. In the left sidebar, click on "Personal access tokens" then "Tokens (classic)"
5. Click "Generate new token" and select "Generate new token (classic)"
6. Give your token a descriptive name
7. Select the scopes (permissions) you want to grant this token
   - For basic repository access, select "repo"
   - For public repositories only, select "public_repo"
8. Click "Generate token"
9. Copy your new personal access token immediately! GitHub will only show it once.

### Using Your Personal Access Token

When pushing to or pulling from GitHub using HTTPS, you'll be asked for your username and password:

```bash
git push origin main
```

Instead of your GitHub password, enter your personal access token when prompted.

#### Including PAT in URLs

You can also include your Personal Access Token directly in the Git URL to avoid being prompted for credentials:

```bash
# When cloning a repository
git clone https://TOKEN@github.com/username/repository.git

# When adding a remote
git remote add origin https://TOKEN@github.com/username/repository.git
```

Replace `TOKEN` with your actual Personal Access Token. For example:

> **Warning**: Using this method may expose your token in your shell history and is not recommended for shared environments. Be careful not to commit these URLs to your repository.

### Token Security Best Practices

1. Never share your tokens or check them into version control
2. Set an expiration date for your tokens
3. Use the minimum scopes necessary for your needs
4. Regularly review and revoke unused tokens
5. Consider using GitHub CLI or SSH keys for authentication as alternatives

---

## Tips for Front-End Developers

1. Use branches for features and bug fixes
2. Commit often with meaningful messages
3. Create a `.gitignore` file for node_modules and build files
4. Use pull requests for code review
5. Learn to resolve merge conflicts efficiently
6. Consider using Git hooks for linting before commits
7. Use semantic versioning for your projects

## GitHub Pages and How to Use Them

GitHub Pages is a free hosting service provided by GitHub that allows you to host static websites directly from your GitHub repository.

### How to Set Up GitHub Pages

1. Create a repository named `username.github.io` (replace "username" with your GitHub username)
2. Clone the repository to your local machine
3. Create a new repository
4. Add your web files (HTML, CSS, JS)
5. Scroll down to "GitHub Pages" section
6. Choose which branch to publish (usually `main` or `master`)
7. Save and visit the provided URL

---

## Task

Make your local repo that has a good structure with an index.html page and README file.

> **Hint:** A well-structured HTML page is a `semantic HTML` page that includes `comments`.

The index.html page must include a line that says "Welcome to my web page I am [your name]".

Use GitHub Pages to deploy your webpage.

### Steps to Complete the Task

1. Create a new repository locally using `git init`
2. Create a structured index.html with semantic HTML
3. Create a README.md file explaining your project
4. Commit your changes
5. Create a repository on GitHub
6. Connect your local repo to GitHub and push
7. Enable GitHub Pages in the repository settings
