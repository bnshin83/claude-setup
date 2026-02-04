# Commit, Push, and Create PR

Full git workflow: commit changes, push to remote, create pull request.

## Usage
```
/git/commit-push-pr [PR title]
```

## Workflow

### 1. Check Current State
```bash
git status
git branch --show-current
git log --oneline -3
```

### 2. Review Changes
```bash
git diff --stat
git diff  # if detailed review needed
```

### 3. Create Commit
```bash
git add [files]
git commit -m "type(scope): description"
```

### 4. Push to Remote
```bash
# If branch doesn't exist on remote
git push -u origin $(git branch --show-current)

# If branch exists
git push
```

### 5. Create Pull Request
```bash
gh pr create --title "PR Title" --body "## Summary
- Change 1
- Change 2

## Test Plan
- [ ] Tests pass
- [ ] Manual verification"
```

### 6. Confirm
```bash
gh pr view --web  # or show PR URL
```

## PR Template

```markdown
## Summary
[Brief description of changes]

## Changes
- [Change 1]
- [Change 2]

## Test Plan
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed

## Notes
[Any additional context]
```

## Example

```bash
# On branch: feature/add-validation

git add src/validation.py tests/test_validation.py
git commit -m "feat(validation): add email validation"
git push -u origin feature/add-validation

gh pr create \
  --title "Add email validation" \
  --body "## Summary
Adds email validation helper function.

## Changes
- New `validate_email()` function
- Unit tests for validation

## Test Plan
- [x] pytest passes"
```

## Notes
- Creates PR against default branch (usually `main`)
- Use `--base other-branch` for different target
- Use `--draft` for work-in-progress PRs
