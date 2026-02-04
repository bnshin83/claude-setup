# Git Worktree

Create parallel working directories for multiple branches.

## Usage
```
/git/worktree [branch-name]
```

## What is a Worktree?

Git worktrees let you have multiple branches checked out simultaneously in different directories. Useful for:
- Working on a feature while reviewing another PR
- Quick hotfixes without stashing
- Running tests on one branch while coding another

## Workflow

### 1. Create Worktree
```bash
# Create new branch with worktree
git worktree add ../project-feature feature-branch

# Create worktree for existing branch
git worktree add ../project-hotfix hotfix-branch
```

### 2. Work in Worktree
```bash
cd ../project-feature
# Work normally - git commands work as expected
git status
git commit -m "changes"
git push
```

### 3. List Worktrees
```bash
git worktree list
# /path/to/project         abc1234 [main]
# /path/to/project-feature def5678 [feature-branch]
```

### 4. Remove Worktree
```bash
# When done with the branch
git worktree remove ../project-feature

# Or force remove if there are changes
git worktree remove --force ../project-feature
```

## Directory Convention

```
parent-directory/
├── project/              # main worktree (main branch)
├── project-feature/      # feature branch worktree
├── project-hotfix/       # hotfix branch worktree
└── project-review/       # PR review worktree
```

## Common Commands

```bash
# Create worktree for new branch
git worktree add -b new-branch ../project-new

# Create worktree for existing remote branch
git fetch origin
git worktree add ../project-review origin/pr-branch

# Prune stale worktree references
git worktree prune

# Move a worktree
git worktree move ../old-path ../new-path
```

## Tips

1. **Naming**: Use `project-branchname` format for clarity
2. **Cleanup**: Remove worktrees when done to avoid confusion
3. **Shared objects**: All worktrees share the same `.git` objects (efficient)
4. **Branch lock**: A branch can only be checked out in one worktree at a time

## Example Session

```bash
# Main project on 'main' branch
pwd  # /code/myproject

# Need to review a PR while keeping current work
git worktree add ../myproject-review pr-123

# Switch to review
cd ../myproject-review
# Review, test, comment...

# Back to main work
cd ../myproject

# Done with review
git worktree remove ../myproject-review
```
