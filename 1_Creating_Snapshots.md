# Creating Snapshots

## Git Four Main Areas

Git really has four main areas:

- **`Working directory`** – your actual files on disk (you edit here).

- **`Staging area (index)`** – snapshot of what will go into your next commit (git add).

- **`Local repository`** – your commit history on your computer (git commit).

- **`Remote repository`** – the shared version on a server like GitHub (git push, git pull).

When you unstage a file, it just moves from the **`Staging Area`** back to the **`Working Directory`** — your changes stay in the file.

## Initializing a Repository

```bash
git init
```
## Staging Files 

```bash
git add file1.js # Stages a single file 
git add file1.js file2.js # Stages multiple files
git add *.js # Stages with a pattern
git add . # Stages the current directory and all its content  
```
## Viewing the Status 

```bash
git status # Full status 
git status -s # Short status
```

## Committing the Staged Files 

```bash
git commit -m “Message” # Commits with a one-line message  
git commit # Opens the default editor to type a long message  
```

## Skipping the Staging Area 

```bash
git commit -am “Message"
```

## Removing Files

```bash
git rm file1.js # Removes from working directory and staging area
git rm --cached file1.js # Removes from staging area only  
```

## Renaming or Moving Files

```bash
git mv file1.js file1.txt
```

## Viewing the Staged/Unstaged Changes

```bash
git diff # Shows unstaged changes
git diff --staged # Shows staged changes 
git diff --cached # Same as the above
```
## View History

```bash
git log # Full history 
git log --oneline # Summary  
git log --reverse # Lists the commits from the oldest to the newest 
```


## Viewing a commit 

```bash
git show 921a2ff # Shows the given commit 
git show HEAD # Shows the last commit  
git show HEAD~2 # Two steps before the last commit  
git show HEAD:file.js # Shows the version of file.js stored in the last commit
```
## Unstaging files (undoing git add)

```bash
git restore --staged file.js # Copies the last version of file.js from repo to index
```
## Discarding Local Changes

```bash
git restore file.js # Copies file.js from index to working directory  
git restore file1.js file2.js # Restores multiple files in working directory 
git restore . # Discards all local changes (except untracked files) 
git clean -fd # Removes all untracked clean -fd
```

## Restoring a File to an Earlier Version

Remove file from **both the `Working Directory` and `Staging Area`**:

```bash
git rm <file>
git commit -m "Delete file"
```

Restore a File from Previous Commit:

```bash
git restore --source=HEAD~1 <file> 
```