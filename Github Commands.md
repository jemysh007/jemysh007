
# GitHub Basic Commands

## Git Configuration

### Set Your Name and Email
```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

### Check Your Git Configuration
```bash
git config --list
```

## Initialize a Repository

### Initialize a New Git Repository
```bash
git init
```

## Git Status

### Check the Status of Your Repository
```bash
git status
```

## Add Files

### Add All Files to Staging Area
```bash
git add .
```

### Add Specific File to Staging Area
```bash
git add <filename>
```

## Commit Changes

### Commit Changes with a Message
```bash
git commit -m "Your commit message"
```

## Git Log

### View Commit History
```bash
git log
```

### View a One-line Summary of the Commit History
```bash
git log --oneline
```

## Branching

### List All Branches
```bash
git branch
```

### Create a New Branch
```bash
git branch <branch-name>
```

### Switch to a Branch
```bash
git checkout <branch-name>
```

### Create and Switch to a New Branch
```bash
git checkout -b <branch-name>
```

### Delete a Branch
```bash
git branch -d <branch-name>
```

## Remote Repositories

### Add Remote Repository
```bash
git remote add origin <repository-url>
```

### View Remote Repositories
```bash
git remote -v
```

### Fetch Changes from Remote
```bash
git fetch
```

### Push Changes to Remote Repository
```bash
git push origin <branch-name>
```

### Pull Changes from Remote Repository
```bash
git pull origin <branch-name>
```

## Merging

### Merge a Branch into Current Branch
```bash
git merge <branch-name>
```

## Undoing Changes

### Undo Last Commit (Keep Changes)
```bash
git reset --soft HEAD~1
```

### Undo Last Commit (Discard Changes)
```bash
git reset --hard HEAD~1
```

### Remove File from Staging Area
```bash
git reset <file>
```

### Discard Changes in a File
```bash
git checkout -- <file>
```

## Git Ignore

### Create or Edit `.gitignore` File
Add the file or directories you want to ignore, for example:
```plaintext
node_modules/
*.log
```

## Cloning a Repository

### Clone a Remote Repository to Local
```bash
git clone <repository-url>
```

## GitHub Actions (Optional)

### Create a New GitHub Action
```bash
.github/workflows/ci.yml
```

Add a simple CI script:
```yaml
name: CI Workflow

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2
      - name: Run Tests
        run: npm test
```

## GitHub Pull Requests

### Create a Pull Request
1. Push your changes to a branch on GitHub.
2. Open GitHub, navigate to the repository.
3. Click on the "Compare & pull request" button.
4. Review the changes and create the pull request.

### Merge a Pull Request
1. Review the pull request.
2. Click "Merge pull request" to merge the changes into the base branch.
```
