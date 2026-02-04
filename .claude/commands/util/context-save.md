# Context Save

Save current session context for later restoration.

## Usage
```
/util/context-save [label]
```

## Examples
```
/util/context-save auth-implementation
/util/context-save debugging-issue-123
/util/context-save end-of-day
```

## What Gets Saved

### To `.claude/memory/context.md`
- Current focus and task
- Working memory notes
- File locations being worked on
- Decisions made this session
- Open questions

### To `.claude/memory/sessions/[timestamp].md`
- Full session summary
- Commands run
- Files modified
- Key learnings

## Process

### 1. Gather Current State
```bash
# Git state
git status --short
git branch --show-current
git log --oneline -3

# Modified files
git diff --name-only
```

### 2. Save Context
Update `.claude/memory/context.md`:
```markdown
# Active Context

## Session: [label]
- **Saved**: [timestamp]
- **Branch**: [branch]
- **Focus**: [current task]

## Working Files
- [file1] - [what was being done]
- [file2] - [what was being done]

## Decisions Made
- [decision 1]
- [decision 2]

## Open Questions
- [question 1]
- [question 2]

## Next Steps
- [ ] [action 1]
- [ ] [action 2]
```

### 3. Archive Session
Save to `.claude/memory/sessions/`:
```markdown
# Session: [label]
## Date: [timestamp]
## Duration: [estimate]

### Summary
[What was accomplished]

### Files Modified
- [list]

### Key Learnings
- [learning 1]

### For Next Session
- [handoff notes]
```

## Restoration
```
/session/start
# Will automatically load saved context
```

## Output
```markdown
## Context Saved

**Label**: auth-implementation
**Time**: 2024-01-15 14:30:00 UTC
**Branch**: feature/auth

### Saved to:
- `.claude/memory/context.md` (active context)
- `.claude/memory/sessions/20240115-143000.md` (archive)

### Summary:
- Working on: OAuth2 implementation
- Files: 3 modified, 1 created
- Next: Add refresh token logic
```
