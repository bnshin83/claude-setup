# Claude Setup

Unified Claude Code configuration for academic research, ML development, and software engineering.

## Quick Start

```bash
# Copy to your project
cp -r claude-setup/.claude your-project/
cp claude-setup/CLAUDE.md your-project/

# Or symlink for updates
ln -s /path/to/claude-setup/.claude your-project/.claude
```

## Commands

### Session (`/session/*`)
| Command | Description |
|---------|-------------|
| `/session/start` | Load context, orient to project |
| `/session/end` | Save progress, update memory |
| `/session/sync` | Sync agents across platforms |

### Research (`/research/*`)
| Command | Description |
|---------|-------------|
| `/research/scholar` | Master research orchestrator |
| `/research/search-lit` | Search literature database |
| `/research/add-paper` | Add paper to database |
| `/research/write-section` | Draft paper section |
| `/research/review-draft` | Review draft quality |
| `/research/verify-citation` | Verify citations |

### LaTeX (`/latex/*`)
| Command | Description |
|---------|-------------|
| `/latex/build` | Compile paper to PDF |
| `/latex/build-share` | Export for Overleaf |

### Development (`/dev/*`)
| Command | Description |
|---------|-------------|
| `/dev/test-and-fix` | Run tests, fix failures |
| `/dev/grill` | Adversarial code review |
| `/dev/techdebt` | Find code smells |
| `/dev/review-changes` | Pre-commit review |

### Git (`/git/*`)
| Command | Description |
|---------|-------------|
| `/git/commit` | Standard commit |
| `/git/quick-commit` | Fast single-line commit |
| `/git/commit-push-pr` | Full PR workflow |
| `/git/worktree` | Parallel branch sessions |

### ML (`/ml/*`)
| Command | Description |
|---------|-------------|
| `/ml/run-experiment` | Execute training |
| `/ml/slurm-submit` | Submit SLURM job |
| `/ml/analyze-results` | Parse results |

### Utilities (`/util/*`)
| Command | Description |
|---------|-------------|
| `/util/explain` | Simple explanations |
| `/util/rewrite` | Academic rewriting |
| `/util/math-format` | Format equations |
| `/util/explain-equation` | Break down equations |

## Agents (12 total)

### Research & Writing
| Agent | Purpose |
|-------|---------|
| `scholar` | Master research orchestrator |
| `lit-manager` | Literature database + reference search |
| `paper-writer` | Academic prose drafting |
| `citation-verifier` | Verify claims against sources |
| `draft-reviewer` | Quality review |
| `latex-builder` | LaTeX compilation + Overleaf export |
| `memory-bank` | Cross-session context |
| `git-guardian` | Safe version control |

### Development
| Agent | Purpose |
|-------|---------|
| `code-architect` | Development orchestrator |
| `code-searcher` | Codebase exploration |
| `staff-reviewer` | Adversarial code review |
| `build-validator` | Test runner, CI |

## Memory Bank

Files in `.claude/memory/` persist context:

| File | Purpose |
|------|---------|
| `context.md` | Active session state |
| `patterns.md` | Code/writing patterns |
| `decisions.md` | Architecture decisions |
| `troubleshooting.md` | Issues & solutions |
| `progress.md` | Task tracking |
| `reference.md` | Project references |

## Configuration

### Permissions (settings.json)
- Git, Python, Node.js, LaTeX commands allowed
- SLURM cluster commands allowed
- Dangerous operations denied (force push, rm -rf /)

### Hooks
- **PreToolUse**: Audit logging for Bash commands
- **PostToolUse**: Auto-format JS/TS files
- **Stop**: macOS notification on completion

### Customization
Edit `.claude/settings.json` to:
- Add/remove allowed commands
- Modify hooks
- Set environment variables

## Typical Workflows

### Research Session
```
/session/start
/research/write-section introduction
/research/verify-citation
/latex/build
/session/end
```

### Development Session
```
/session/start
/dev/review-changes
/dev/test-and-fix
/git/commit
/session/end
```

### ML Experiment
```
/ml/run-experiment config.yaml
/ml/analyze-results outputs/
/git/quick-commit "Add experiment results"
```
