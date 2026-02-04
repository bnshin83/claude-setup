# Checkpoint

Create a named save point for easy recovery.

## Usage
```
/util/checkpoint [name]
```

## Examples
```
/util/checkpoint before-refactor
/util/checkpoint working-auth
/util/checkpoint pre-upgrade
```

## What It Does

### 1. Create Git Tag
```bash
# Generate checkpoint name
CHECKPOINT="checkpoint-$(date +%Y%m%d-%H%M%S)"
# Or use provided name
CHECKPOINT="checkpoint-$NAME"

# Create tag
git tag "$CHECKPOINT"
```

### 2. Log to Audit
```bash
echo "$(date -u +%FT%TZ) CHECKPOINT: $CHECKPOINT" >> .claude/audit/checkpoints.log
```

### 3. Stash Uncommitted Changes (Optional)
```bash
# If there are uncommitted changes
git stash push -m "checkpoint: $CHECKPOINT"
```

## Recovery

### List Checkpoints
```bash
git tag -l "checkpoint-*" | sort -r | head -10
```

### Restore to Checkpoint
```bash
# Hard reset (discard changes)
git reset --hard checkpoint-name

# Soft reset (keep changes staged)
git reset --soft checkpoint-name
```

### View Checkpoint
```bash
# See what was at checkpoint
git show checkpoint-name --stat
```

## Output
```markdown
## Checkpoint Created

**Name**: checkpoint-before-refactor
**Time**: 2024-01-15 14:30:00 UTC
**Commit**: abc1234
**Branch**: feature/auth

### To restore:
```bash
git reset --hard checkpoint-before-refactor
```

### Recent checkpoints:
1. checkpoint-before-refactor (now)
2. checkpoint-20240115-120000
3. checkpoint-working-state
```

## Best Practices
- Create checkpoints before risky operations
- Use descriptive names
- Don't create too many (clean up old ones)
- Combine with git stash for uncommitted work
