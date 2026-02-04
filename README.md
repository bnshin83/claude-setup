# claude-setup

Unified Claude Code configuration for:
- **Academic Research** - Paper writing, literature management, citations, LaTeX
- **ML/Python Development** - PyTorch, experiments, SLURM
- **General Software Development** - Testing, code review, git workflows

## Installation

```bash
# Clone
git clone https://github.com/YOUR_USERNAME/claude-setup.git

# Copy to your project
cp -r claude-setup/.claude your-project/
cp claude-setup/CLAUDE.md your-project/
```

## Features

### Memory Bank
Persistent context across sessions in `.claude/memory/`

### Specialized Agents
12 agents for research, development, and git workflows

### Slash Commands
40+ commands organized by category:
- `/session/*` - Session lifecycle
- `/research/*` - Academic workflow
- `/dev/*` - Software development
- `/git/*` - Version control
- `/ml/*` - ML experiments

### Smart Hooks
- Audit logging for all bash commands
- Auto-format JS/TS files on save
- macOS notifications on task completion

## Documentation

See [CLAUDE.md](CLAUDE.md) for full command reference.

## License

MIT
