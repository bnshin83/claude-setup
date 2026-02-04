# Sync Agents

Sync agent configurations across platforms (Claude Code, Windsurf, Cursor).

## Usage
```
/session/sync
```

## Purpose
Keep agent definitions consistent across different AI coding assistants.

## Platform Directories

```
project/
├── .claude/        # Claude Code
│   ├── agents/
│   └── commands/
├── .windsurf/      # Windsurf
│   └── rules/
└── .cursor/        # Cursor
    └── rules/
```

## Sync Workflow

### 1. Identify Source of Truth
Default: `.claude/` is the source

### 2. Transform Agents to Rules

Claude agents → Windsurf/Cursor rules

```bash
# Example transformation
# .claude/agents/code-architect.md
# →
# .windsurf/rules/code-architect.md
# .cursor/rules/code-architect.md
```

### 3. Sync Script

```bash
#!/bin/bash
SOURCE=".claude"
PLATFORMS=(".windsurf" ".cursor")

for platform in "${PLATFORMS[@]}"; do
    # Create directory if needed
    mkdir -p "$platform/rules"

    # Copy agents
    cp "$SOURCE/agents/"*.md "$platform/rules/" 2>/dev/null

    # Copy relevant commands
    cp "$SOURCE/commands/dev/"*.md "$platform/rules/" 2>/dev/null
done

echo "Synced to: ${PLATFORMS[*]}"
```

### 4. Verify Sync
```bash
# Compare file counts
echo "Claude agents: $(ls .claude/agents/*.md 2>/dev/null | wc -l)"
echo "Windsurf rules: $(ls .windsurf/rules/*.md 2>/dev/null | wc -l)"
echo "Cursor rules: $(ls .cursor/rules/*.md 2>/dev/null | wc -l)"
```

## Platform-Specific Adaptations

### Windsurf
- Uses `.windsurf/rules/` directory
- Rules are markdown files
- Automatically loaded in sessions

### Cursor
- Uses `.cursor/rules/` directory
- Also supports `.cursorrules` file
- Rules are markdown or plain text

### Differences to Handle
- Some tools may not exist in all platforms
- Adjust tool references as needed
- Test after syncing

## Output

```markdown
## Sync Report

### Source
- Platform: Claude Code
- Agents: 12
- Commands: 25

### Synced To
- Windsurf: ✅ 12 rules
- Cursor: ✅ 12 rules

### Differences
- None (full sync)

### Notes
- All platforms now have consistent agent definitions
- Test each platform to verify functionality
```
