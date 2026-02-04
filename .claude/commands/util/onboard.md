# Onboard

Deep exploration of a codebase or feature.

## Usage
```
/util/onboard [area or feature]
```

## Examples
```
/util/onboard                    # Full codebase overview
/util/onboard authentication     # Focus on auth system
/util/onboard src/api            # Focus on API layer
```

## Process

### 1. Structure Analysis
```bash
# Find key files
find . -name "*.md" -o -name "package.json" -o -name "pyproject.toml" | head -20

# Directory structure
ls -la
ls -la src/ 2>/dev/null || ls -la lib/ 2>/dev/null
```

### 2. Entry Points
- README.md, CONTRIBUTING.md
- Main entry file (main.py, index.ts, etc.)
- Configuration files

### 3. Architecture Discovery
- Identify layers (API, services, data)
- Find key abstractions
- Map dependencies

### 4. Testing Strategy
- Locate test files
- Understand test patterns
- Find CI/CD configuration

### 5. Build & Run
- Find build commands
- Identify environment requirements
- Locate development scripts

## Output Format
```markdown
## Codebase Overview: [Project Name]

### Quick Facts
- Language: [primary language]
- Framework: [if applicable]
- Package manager: [npm/pip/cargo/etc.]
- Test framework: [jest/pytest/etc.]

### Structure
```
project/
├── src/           # [what's here]
├── tests/         # [test strategy]
├── config/        # [configuration]
└── docs/          # [documentation]
```

### Key Files
| File | Purpose |
|------|---------|
| [file] | [what it does] |

### Common Commands
```bash
# Install
[command]

# Run
[command]

# Test
[command]

# Build
[command]
```

### Architecture
[Brief description of how components interact]

### Entry Points
- [Main entry point]
- [API routes location]
- [Configuration location]

### Next Steps
1. [Suggested first file to read]
2. [Key concept to understand]
3. [Good first task to try]
```

## Tips
- Start broad, then dive deep
- Follow imports to understand dependencies
- Read tests to understand expected behavior
- Check git history for recent activity
