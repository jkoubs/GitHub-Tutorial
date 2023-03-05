# GitHub Tutorial 

# Initialize a repo locally and push it to a remote location (GitHub):

Open a terminal:

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
# add --oneline flag for a condensed version
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

# Git branches

   ## Create a new branch with changes

Suppose our main branch is called <strong>main</strong>, and now we want to create a new branch <strong>b1</strong>.

```bash
# Check out and create new branch
git checkout -b b1

# Then do the modifications inside new branch
# Once done editing, need to stage and commit:
git commit -am "new_commit"

# Finally push into remote repo
git push
```
We now have 2 different branches <strong>main</strong> and <strong>b1</strong>. From here there is 2 options: 

- <strong>Merge branches</strong>
- <strong>Create a Pul Request</strong>

## Merge branches


What if we want to merge <strong>b1</strong> into the <strong>main</strong> branch. We can do that by first going back into the <strong>main</strong> branch:

```bash
git checkout main
git merge b1
git push
```

## Pull Request (PR)

A PR is a request to apply your changes to a repo that you do not own, or do not have access rights, or need other people to review.

In general, a PR can be created once you created a new branch, edited it, staged, commited and pushed it. You create the PR through GitHub to request a person (that has the access rights) to merge your created branch into the main branch. In that way, people can review your branch, leave some comments and then if they consider it can be merged, they will merge it.
## Resolving merge conflicts

When working with a team you and teammates yoy will create branches and merge them regularly. It could happen that 2 developers changes the same line of code creating a <strong>merge conflict</strong>.

Git can't tell which version to keep, and you'll have to decide. Git modifies the file with conflicting changes so that you can identify your changes and the changes applied to the destination branch by someone else.

The beginning of a conflict message is marked by "<strong><<<<<<<<</strong>".
After this, the line(s) of code are the changes applied to the destination branch but that you do NOT have locally.

Next, to divide the changes in the destination branch from your local changes, Git addds a marker "<strong>========</strong>". The line(s) of code afterward contain your work and what you are trying to merge.

Finally, Git adds a marker "<strong>>>>>>>>></strong>" to indicate the end of the lines in conflict.

To resolve a merge conflict, you'll have to open the file in conflict in a code editor. Next, edit or remove the line(s) of code that should not stay and remove all Git markers. <strong>You'll have to create the intended code version and save the file</strong>.

To finish, add or stage your changes and commits with a log msg, then do the merge again and it will work.


# Remove Git Cache

In some cases we would like to clear the cache. 
For example when .gitignore does not work properly, a cache clearing is necessary.

```bash
git rm -rf --cache .
git add --all
git commit -m "Cleared Caches"
```

# How to undo a git pull ?

If by accident you git pulled and modified/overwritten your local files incorrectly, you can revert your code back to its old state and <strong>undo the git pull</strong>:


<strong><em>Note 1:</strong></em> First do a backup of your project in case you cause things to get worse.

<strong><em>Note 2:</strong></em> The following commands will cause you to lose all <strong>uncommitted</strong> changes. So the backup will help you restore that.

### Reset using commit ID

First, get a list of the commit history:

```bash
git reflog
```

Then choose the commit you want to revert to by selecting the <strong>appropriate commit ID</strong>.
For example, if we want to revert from the ID <strong>4bd983d</strong>, then the following command will revert your repository to that version:

```bash
git reset --hard 4bd983d
```



