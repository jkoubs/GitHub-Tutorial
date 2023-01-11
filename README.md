# GitHub Tutorial b1

# Initialize a repo locally and push it to a remote location (GitHUb):

```bash
git init
```

Next, go to GitHub and create a new repository.
Here we will name it: GitHub-Tutorial.
Once created, follow the Quick setup instructions from GitHub

```bash
echo "# GitHub-Tutorial" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:jkoubs/GitHub-Tutorial.git
git push -u origin main
```

# Git commands

## Basics
```bash
# Create empty git repo in specified directory
git init

# Clone repo from remote machine such via HTTP or SSH
git clone <url>

# Stage all changes in <directory> for the next commit
# Replace <directory> with a <file> to change a specific file
git add <directory>

# Stage all changes
git add .

# Commit the staged snapshot, but instead of launching a text editor, use "commit_name" as the commit message
git commit -m "commit_name"

# List which files are staged, unstaged, and untracked
git status

# Display entire commit history using the default format
# For customization see additional options
git log

# Show unstaged changes between your index and working directory
# View changes before staging
git diff
```
## Undoing changes

```bash
# Create new commit that undoes all of the changes made in <commit>, then,apply it to the current branch
git revert <commit>

# Remove <file> from the staging area, but leave the working directory unchanged. 
# This unstages a file without overwriting any changes
git reset <file>

# Shows which files would be removed from working directory
# Use the -f flag in place of the -n flag to execute the clean
git clean -n
```

## Branches

```bash
# List all of the branches in your repo
git branch

# Check out a new branch named <branch> Drop the -b flag to checkout an existing branch
git checkout -b <branch>

# Merge <branch> into the current branch
git merge <branch>

# Deleting a branch only if it has been merged
# Replace with -D flag to force branch to be deleted
git branch -d <branch_merged>

# Display commits contained in one branch b2 with respect to the other one b1.
git log <b1> <b2>

# Compares latests commits on both branches
git diff <b1> <b2>

# Rename a branch
git branch -m <old_branch> <new_branch>
```

## Remote repos

```bash
# List all of the branches in your repo
git remote add <name> <url>

# Fetches a specific <branch>, from the repo. 
# Leave off <branch> to fetch all remote refs.
git fetch <remote> <branch>

# Fetch the specified remote’s copy of current branch and immediately merge it into the local copy.
git pull <remote>

# Push the branch to <remote>, along with necessary commits and objects. 
# Creates named branch in the remote repo if it doesn’t exist.
git push <remote> <branch>
```

