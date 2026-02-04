# Review Changes

Pre-commit review of current changes.

## Usage
```
/dev/review-changes
```

## Purpose
Quick sanity check before committing. Catches common mistakes without full grill mode intensity.

## Workflow

### 1. See What Changed
```bash
git status
git diff --stat
```

### 2. Review Each File
```bash
git diff [file]  # or git diff --staged [file]
```

### 3. Check List

For each change:
- [ ] Change is intentional (not debug code left in)
- [ ] No console.log/print statements for debugging
- [ ] No commented-out code
- [ ] No hardcoded values that should be config
- [ ] No secrets or credentials
- [ ] Tests updated if needed
- [ ] No unrelated changes mixed in

### 4. Quick Validation
```bash
# Lint check
ruff check . || npm run lint

# Type check
mypy . || npx tsc --noEmit

# Quick test
pytest -x || npm test
```

## Output Format

```markdown
## Pre-Commit Review

### Changes
- `src/auth.py` - Modified (25 lines)
- `tests/test_auth.py` - Modified (15 lines)
- `config.py` - Modified (3 lines)

### Review

#### src/auth.py
✅ Logic looks correct
✅ Error handling present
⚠️ Line 45: Debug print statement - remove before commit
⚠️ Line 67: Magic number 3600 - consider using constant

#### tests/test_auth.py
✅ Tests cover the new code
✅ Assertions are meaningful

#### config.py
✅ Just config changes, looks fine

### Pre-commit Checks
- Lint: ✅ Pass
- Types: ✅ Pass
- Tests: ✅ Pass

### Verdict
⚠️ Two minor issues to address:
1. Remove debug print at auth.py:45
2. Consider constant for 3600 at auth.py:67

Ready to commit after fixes.
```

## Quick Fixes

Common pre-commit cleanups:

```bash
# Remove debug prints (Python)
grep -rn "print(" src/ --include="*.py"

# Remove console.logs (JS)
grep -rn "console.log" src/ --include="*.js" --include="*.ts"

# Find TODOs in changed files
git diff --name-only | xargs grep -n "TODO\|FIXME"

# Auto-format
ruff format . || prettier --write .
```
