---
name: git-workflow
description: Git workflow conventions and best practices.
---

# Git Workflow Skill

Standard git workflow for consistent version control.

## Branch Naming

```
feature/description    # New features
fix/description        # Bug fixes
refactor/description   # Code refactoring
docs/description       # Documentation
test/description       # Test additions
chore/description      # Maintenance
```

Examples:
```
feature/user-authentication
fix/login-redirect-loop
refactor/extract-validation-service
```

## Commit Messages

### Format
```
type(scope): short description

[optional body]

[optional footer]
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Formatting
- `refactor`: Code restructure
- `test`: Tests
- `chore`: Maintenance

### Examples
```
feat(auth): add OAuth2 login flow

Implements Google and GitHub OAuth providers.
Includes token refresh and session management.

Closes #123
```

```
fix(api): handle null user in response

Prevents 500 error when user profile is incomplete.
```

## Workflow

### Feature Development
```bash
# 1. Create branch
git checkout -b feature/my-feature

# 2. Make changes with small commits
git add specific-files.py
git commit -m "feat(module): add initial structure"

# 3. Keep up to date
git fetch origin
git rebase origin/main

# 4. Push and create PR
git push -u origin feature/my-feature
gh pr create
```

### Hotfix
```bash
# 1. Branch from main
git checkout main
git pull
git checkout -b fix/critical-bug

# 2. Fix and commit
git commit -m "fix(auth): prevent session hijacking"

# 3. Push immediately
git push -u origin fix/critical-bug
gh pr create --label "priority:critical"
```

## Rules

### Do
- Commit early and often
- Write meaningful commit messages
- Keep commits focused (one change per commit)
- Rebase before merging
- Delete branches after merge

### Don't
- Commit directly to main
- Force push to shared branches
- Commit secrets or credentials
- Use generic messages ("fix", "update", "wip")
- Leave long-running branches
