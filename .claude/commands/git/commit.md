# Standard Commit

Create a well-formatted commit with conventional message.

## Usage
```
/git/commit
```

## Workflow

1. **Check status**
   ```bash
   git status
   git diff --stat
   ```

2. **Review changes**
   ```bash
   git diff --staged  # or git diff if not staged
   ```

3. **Generate commit message**
   Format: `type(scope): description`

   Types:
   - `feat`: New feature
   - `fix`: Bug fix
   - `docs`: Documentation
   - `style`: Formatting
   - `refactor`: Code restructure
   - `test`: Tests
   - `chore`: Maintenance

4. **Stage and commit**
   ```bash
   git add [specific files]
   git commit -m "type(scope): description"
   ```

5. **Verify**
   ```bash
   git log --oneline -1
   git status
   ```

## Example

```bash
git status
# Modified: src/utils.py, tests/test_utils.py

git diff --stat
# src/utils.py      | 15 ++++++++++
# tests/test_utils.py | 25 +++++++++++++++++

git add src/utils.py tests/test_utils.py
git commit -m "feat(utils): add string sanitization helper"
```

## Notes
- Review changes before committing
- Stage specific files, not `git add -A`
- Write meaningful messages
- Does NOT push automatically
