# Creating Snapshots

## Git Four Main Areas

Git really has four main areas:

- **`Working directory`** – your actual files on disk (you edit here).

- **`Staging area (index)`** – snapshot of what will go into your next commit (git add).

- **`Local repository`** – your commit history on your computer (git commit).

- **`Remote repository`** – the shared version on a server like GitHub (git push, git pull).

When you unstage a file, it just moves from the **`Staging Area`** back to the **`Working Directory`** — your changes stay in the file.

## View commit History

```bash
git log 
```

```bash
git log --oneline
```

```bash
git log --oneline --reverse 
```

## Discarding Local Changes

```bash
git restore <file>
```

Undo all local changes:
```bash
git restore .
```

**Delete untracked files and folders**:

```bash
git clean -fd
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