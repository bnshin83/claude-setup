# claude-setup

> Unified Claude Code configuration for academic research, ML development, and software engineering.

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)]()

## Features

- **15 Specialized Agents** - Research, development, security, TDD
- **33 Slash Commands** - Organized by domain
- **3 Skills** - Coding standards, git workflow, academic writing
- **Smart Hooks** - Auto-format, audit logging, notifications
- **Memory Bank** - Persistent context across sessions

## Installation

```bash
# Clone
git clone https://github.com/bnshin83/claude-setup.git

# Copy to your project
cp -r claude-setup/.claude your-project/
cp claude-setup/CLAUDE.md your-project/
```

## What's Included

### Agents (15)
| Category | Agents |
|----------|--------|
| Research | scholar, lit-manager, paper-writer, citation-verifier, draft-reviewer |
| Technical | latex-builder, memory-bank, git-guardian |
| Development | planner, code-architect, code-searcher, staff-reviewer, security-reviewer, tdd-guide, build-validator |

### Commands (33)
```
/session/*     (3)  - Session lifecycle
/research/*    (6)  - Academic workflow
/latex/*       (2)  - Document building
/dev/*         (7)  - Development (includes /plan, /tdd, /security-scan)
/git/*         (4)  - Version control
/ml/*          (3)  - ML experiments
/util/*        (8)  - Utilities (includes /think-harder, /onboard, /checkpoint)
```

### Skills (3)
- `coding-standards` - Code style and best practices
- `git-workflow` - Git conventions and branching
- `academic-writing` - Research paper conventions

### Memory Bank
```
.claude/memory/
├── context.md          # Active session
├── patterns.md         # Code/writing patterns
├── decisions.md        # Architecture decisions
├── troubleshooting.md  # Issues & solutions
├── progress.md         # Task tracking
├── reference.md        # Project references
└── sessions/           # Archived contexts
```

## Key Workflows

### Research
```
/session/start
/research/write-section introduction
/latex/build
/session/end
```

### Development
```
/session/start
/dev/plan feature-name      # Plan first!
/dev/tdd feature-name       # Test-driven
/dev/security-scan          # Security check
/git/commit
/session/end
```

### Exploration
```
/util/onboard               # Understand codebase
/util/think-harder problem  # Deep analysis
/dev/plan solution          # Plan approach
```

## Best Practices

1. **Plan Before Coding** - Use `/dev/plan` for non-trivial tasks
2. **Clear Chat Often** - Use `/clear` when switching tasks
3. **Use Checkpoints** - `/util/checkpoint` before risky operations
4. **Save Context** - `/util/context-save` preserves session state
5. **Think Harder** - `/util/think-harder` for complex decisions

## Configuration

### Permissions
Expanded permissions for common development tools:
- Python: `pytest`, `pip`, `uv`, `ruff`, `mypy`
- Node.js: `npm`, `pnpm`, `yarn`, `bun`, `tsc`, `eslint`
- Containers: `docker`, `docker-compose`
- SLURM: `sbatch`, `squeue`, `scancel`

### Hooks
- **PreToolUse**: Audit logging
- **PostToolUse**: Auto-format Python (ruff) and JS/TS (prettier)
- **Stop**: Cross-platform notifications

### Safety
Denied by default:
- Force push to main/master
- `sudo` commands
- `git reset --hard`
- Destructive disk operations

## Structure

```
.claude/
├── agents/           # 15 specialized agents
├── commands/
│   ├── session/      # Session management
│   ├── research/     # Academic workflow
│   ├── latex/        # Document building
│   ├── dev/          # Development
│   ├── git/          # Version control
│   ├── ml/           # ML experiments
│   └── util/         # Utilities
├── skills/           # Domain knowledge
├── memory/           # Persistent context
└── settings.json     # Configuration
```

## Inspiration

This setup incorporates best practices from:
- [everything-claude-code](https://github.com/affaan-m/everything-claude-code)
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)
- [claude-code-showcase](https://github.com/ChrisWiles/claude-code-showcase)
- [Anthropic Skills](https://github.com/anthropics/skills)
- [Builder.io Blog](https://www.builder.io/blog/claude-code)

## License

MIT
