# Session Start

Load context and orient to the project.

## Usage
```
/session/start
```

## Workflow

### 1. Load Memory Bank
Read and summarize:
- `.claude/memory/context.md` - Last session state
- `.claude/memory/progress.md` - Current tasks
- `.claude/memory/decisions.md` - Recent decisions

### 2. Check Project State
```bash
# Git status
git status --short
git branch --show-current
git log --oneline -5

# Recent changes
git diff --stat HEAD~5
```

### 3. Scan for Updates
```bash
# Check for uncommitted changes
git status

# Check for untracked files
git status --porcelain | grep "^??"

# Check for stashed work
git stash list
```

### 4. Generate Summary

```markdown
## Session Context

### Current State
- **Branch**: feature/xyz
- **Last commit**: abc123 - "Add feature X"
- **Uncommitted changes**: 3 files
- **Stashed work**: None

### From Last Session
- Working on: [task from context.md]
- Left off at: [progress from progress.md]

### Active Tasks
- [ ] Task 1
- [ ] Task 2

### Recent Decisions
- Decided to use X instead of Y because...

### Quick Actions
1. Continue with [task]
2. Review uncommitted changes
3. Start new task
```

### 5. Update Context
Update `.claude/memory/context.md` with:
- Session start timestamp
- Current focus
- Working memory reset

## Template Update

After loading, update context.md:
```markdown
# Active Context

## Current Session
- **Started**: 2024-01-15 14:30
- **Focus**: [determined from last session or user input]
- **Branch**: [current branch]

## Recent Changes
<!-- From last session -->

## Working Memory
<!-- Fresh for this session -->

## Next Actions
- [ ] [First priority]
```

## Notes
- Run at the start of every session
- Helps maintain continuity across sessions
- Updates context file with fresh timestamp
