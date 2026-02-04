# Session End

Save progress and context for next session.

## Usage
```
/session/end
```

## Workflow

### 1. Summarize Session
Review what was accomplished:
- Changes made
- Decisions taken
- Problems solved
- New questions raised

### 2. Update Memory Bank

#### context.md
```markdown
## Recent Changes
- [Change 1]
- [Change 2]

## Working Memory
- [Important context for next session]

## Next Actions
- [ ] [What to do next]
```

#### progress.md
```markdown
## Completed
- [x] Task completed this session

## In Progress
- [ ] Task started but not finished

## Blocked
- [ ] Task blocked by [reason]
```

#### decisions.md (if applicable)
```markdown
### [Date] Decision Title
**Context**: Why needed
**Decision**: What was chosen
**Rationale**: Why
```

#### troubleshooting.md (if applicable)
```markdown
### Issue: [Problem encountered]
**Solution**: [How it was fixed]
```

### 3. Git Status Check
```bash
git status
git stash list
git log --oneline -3
```

### 4. Generate Handoff

```markdown
## Session Summary

### Accomplished
- [x] Completed task 1
- [x] Fixed bug in module X
- [x] Added tests for feature Y

### Changes
- Modified: `src/module.py`, `tests/test_module.py`
- Created: `src/new_feature.py`
- Commits: 2

### State
- Branch: feature/xyz
- Uncommitted: None
- Stashed: None

### For Next Session
- Continue with [task]
- Review PR #123
- Consider [open question]

### Notes
- [Important context]
- [Decision made]
- [Question to revisit]
```

### 5. Optional: Commit Progress
```bash
# If there are uncommitted changes worth saving
git add -A
git commit -m "WIP: [description]"
```

## Notes
- Run at the end of every session
- Ensures continuity for next session
- Captures decisions and context that might be forgotten
