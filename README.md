# claude-setup

Unified Claude Code configuration for:
- **Academic Research** - Paper writing, literature management, citations, LaTeX
- **ML/Python Development** - PyTorch, experiments, SLURM clusters
- **General Software Development** - Testing, code review, git workflows

## Installation

```bash
# Clone
git clone https://github.com/YOUR_USERNAME/claude-setup.git

# Copy to your project
cp -r claude-setup/.claude your-project/
cp claude-setup/CLAUDE.md your-project/
```

## What's Included

### 12 Specialized Agents
- **Research**: scholar, lit-manager, paper-writer, citation-verifier, draft-reviewer
- **Technical**: latex-builder, memory-bank, git-guardian
- **Development**: code-architect, code-searcher, staff-reviewer, build-validator

### 25+ Slash Commands
Organized by category:
- `/session/*` - Session lifecycle
- `/research/*` - Academic workflow
- `/latex/*` - Document building
- `/dev/*` - Software development
- `/git/*` - Version control
- `/ml/*` - ML experiments
- `/util/*` - Utilities

### Memory Bank
Persistent context across sessions:
- `context.md` - Active session state
- `patterns.md` - Code/writing patterns
- `decisions.md` - Architecture decisions
- `troubleshooting.md` - Issues & solutions
- `progress.md` - Task tracking

### Smart Configuration
- **Permissions**: Safe defaults with common commands allowed
- **Hooks**: Audit logging, auto-formatting, notifications
- **Deny list**: Protection against dangerous operations

## Quick Start

### Research Workflow
```
/session/start
/research/search-lit "plasticity loss"
/research/write-section introduction
/latex/build
/session/end
```

### Development Workflow
```
/session/start
/dev/test-and-fix
/dev/grill src/module.py
/git/commit
/session/end
```

### ML Workflow
```
/ml/run-experiment config.yaml
/ml/analyze-results outputs/
/git/quick-commit "Add results"
```

## Customization

Edit `.claude/settings.json` to customize permissions and hooks.

See [CLAUDE.md](CLAUDE.md) for full documentation.

## Structure

```
.claude/
├── agents/           # 12 specialized agents
├── commands/
│   ├── session/      # Session management
│   ├── research/     # Academic workflow
│   ├── latex/        # Document building
│   ├── dev/          # Development
│   ├── git/          # Version control
│   ├── ml/           # ML experiments
│   └── util/         # Utilities
├── memory/           # Persistent context
└── settings.json     # Configuration
```

## License

MIT
