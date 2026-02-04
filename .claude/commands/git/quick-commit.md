# Quick Commit

Fast single-line commit for small changes.

## Usage
```
/git/quick-commit [message]
```

## Workflow

1. **Stage changes**
   ```bash
   git add -A
   ```

2. **Show what's staged**
   ```bash
   git status --short
   ```

3. **Commit with message**
   - If message provided: use it directly
   - If no message: generate from changes

4. **Confirm success**
   ```bash
   git log --oneline -1
   ```

## Message Guidelines

Good quick commit messages:
- "Fix typo in README"
- "Add missing import"
- "Update config value"
- "Remove debug print"

## Example

```bash
# User runs: /git/quick-commit Fix typo

git add -A
git status --short
# M  README.md

git commit -m "Fix typo"
# [main abc1234] Fix typo
```

## Notes
- Does NOT push (use `/git/commit-push-pr` for that)
- Does NOT create PR
- For quick, small changes only
