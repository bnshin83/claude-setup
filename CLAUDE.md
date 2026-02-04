# Claude Setup v2.0

Unified Claude Code configuration for academic research, ML development, and software engineering.

## Quick Start

```bash
# Copy to your project
cp -r claude-setup/.claude your-project/
cp claude-setup/CLAUDE.md your-project/
```

## Commands (33 total)

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
| `/dev/plan` | **NEW** Create implementation plan before coding |
| `/dev/tdd` | **NEW** Test-Driven Development workflow |
| `/dev/test-and-fix` | Run tests, fix failures |
| `/dev/grill` | Adversarial code review |
| `/dev/techdebt` | Find code smells |
| `/dev/review-changes` | Pre-commit review |
| `/dev/security-scan` | **NEW** OWASP vulnerability scan |

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
| `/util/think-harder` | **NEW** Deep analysis mode |
| `/util/onboard` | **NEW** Codebase exploration |
| `/util/checkpoint` | **NEW** Named save point |
| `/util/context-save` | **NEW** Save session context |
| `/util/explain` | Simple explanations |
| `/util/rewrite` | Academic rewriting |
| `/util/math-format` | Format equations |
| `/util/explain-equation` | Break down equations |

## Agents (15 total)

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
| `planner` | **NEW** Strategic implementation planning |
| `code-architect` | Development orchestrator |
| `code-searcher` | Codebase exploration |
| `staff-reviewer` | Adversarial code review |
| `security-reviewer` | **NEW** Security vulnerability detection |
| `tdd-guide` | **NEW** Test-Driven Development enforcement |
| `build-validator` | Test runner, CI |

## Skills (3 total)

Skills in `.claude/skills/` provide domain knowledge:

| Skill | Purpose |
|-------|---------|
| `coding-standards` | Code style and best practices |
| `git-workflow` | Git conventions and branching |
| `academic-writing` | Research paper conventions |

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
| `sessions/` | **NEW** Archived session contexts |

## Configuration

### Permissions (settings.json)
**v2.0 Expanded:**
- Git, GitHub CLI (`gh`)
- Python: `python`, `pytest`, `pip`, `uv`, `ruff`, `mypy`
- Node.js: `npm`, `npx`, `pnpm`, `yarn`, `bun`, `tsc`, `eslint`, `prettier`
- Containers: `docker`, `docker-compose`
- Build: `make`, `cargo`, `go`
- SLURM: `sbatch`, `squeue`, `scancel`, `sinfo`
- Utilities: `jq`, `diff`, `sort`, `uniq`, `wc`

### Hooks
- **PreToolUse**: Audit logging for Bash commands
- **PostToolUse**: Auto-format JS/TS (prettier) and Python (ruff)
- **Stop**: Cross-platform notification (macOS + Linux)

### Deny List (Enhanced)
- Force push to main/master
- `sudo` commands
- Destructive disk operations
- Hard resets

## Best Practices (from research)

### 1. Plan Before Coding
Use `/dev/plan` for any non-trivial task. Jumping straight to code often leads to wasted effort.

### 2. Clear Chat Frequently
Use `/clear` when starting new tasks. Don't let old context waste tokens.

### 3. Use Checkpoints
Create checkpoints (`/util/checkpoint`) before risky operations.

### 4. Save Context
Use `/util/context-save` at end of sessions for continuity.

### 5. Think Harder When Needed
Use `/util/think-harder` for complex architectural decisions.

## Typical Workflows

### Research Session
```
/session/start
/research/write-section introduction
/research/verify-citation
/latex/build
/util/context-save research-progress
/session/end
```

### Development Session
```
/session/start
/dev/plan new-feature
# Get approval
/dev/tdd new-feature
/dev/security-scan
/git/commit
/session/end
```

### Exploration
```
/util/onboard src/api
/util/think-harder "best approach for caching"
/dev/plan caching-layer
```

## Sources

This setup incorporates best practices from:
- [everything-claude-code](https://github.com/affaan-m/everything-claude-code) - Battle-tested configs
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) - Curated resources
- [claude-code-showcase](https://github.com/ChrisWiles/claude-code-showcase) - Hooks & workflows
- [Anthropic Skills](https://github.com/anthropics/skills) - Official skill patterns
- [Builder.io Blog](https://www.builder.io/blog/claude-code) - Practical tips
