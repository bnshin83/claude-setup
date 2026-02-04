# Claude Setup

Unified Claude Code configuration for academic research, ML development, and software engineering.

## Quick Start

```bash
# Copy to your project
cp -r claude-setup/.claude your-project/
cp claude-setup/CLAUDE.md your-project/
```

## Commands

### Session Management
- `/session/start` - Load context and orient to project
- `/session/end` - Save progress and update memory
- `/session/sync` - Sync agents across platforms

### Research & Writing
- `/research/scholar` - Master research orchestrator
- `/research/search-lit` - Search literature database
- `/research/add-paper` - Add paper to database
- `/research/write-section` - Draft paper section
- `/research/review-draft` - Review draft quality
- `/research/verify-citation` - Verify citations

### LaTeX
- `/latex/build` - Compile LaTeX paper
- `/latex/build-share` - Export for Overleaf

### Development
- `/dev/test-and-fix` - Run tests, fix failures
- `/dev/grill` - Adversarial code review
- `/dev/techdebt` - Find code smells
- `/dev/review-changes` - Pre-commit review

### Git
- `/git/commit` - Standard commit
- `/git/commit-push-pr` - Full PR workflow
- `/git/quick-commit` - Fast single-line commit
- `/git/worktree` - Parallel branch sessions

### ML Experiments
- `/ml/run-experiment` - Execute training
- `/ml/slurm-submit` - Submit SLURM job
- `/ml/analyze-results` - Parse results

### Utilities
- `/util/explain` - Simple explanations
- `/util/rewrite` - Academic rewriting
- `/util/math-format` - Format equations
- `/util/explain-equation` - Break down equations

## Memory Bank

Files in `.claude/memory/` persist context across sessions:
- `context.md` - Active session state
- `patterns.md` - Code/writing patterns
- `decisions.md` - Architecture decisions
- `troubleshooting.md` - Common issues & fixes
- `progress.md` - Task tracking
- `reference.md` - Project-specific references

## Agents

Specialized agents in `.claude/agents/`:
- `scholar.md` - Research orchestrator
- `lit-manager.md` - Literature management
- `paper-writer.md` - Academic prose
- `citation-verifier.md` - Verify claims
- `draft-reviewer.md` - Quality review
- `latex-builder.md` - LaTeX compilation
- `memory-bank.md` - Context persistence
- `git-guardian.md` - Safe git operations
- `code-architect.md` - Dev orchestrator
- `code-searcher.md` - Codebase exploration
- `staff-reviewer.md` - Adversarial review
- `build-validator.md` - Test runner

## Configuration

Edit `.claude/settings.json` to customize:
- Allowed/denied commands
- Pre/post tool hooks
- Environment variables
