# Tech Debt Scanner

Find code smells, duplicates, and maintenance issues.

## Usage
```
/dev/techdebt [path]
```

## What It Finds

### 1. Code Duplication
```bash
# Find similar code blocks
# Look for copy-paste patterns
```

Signs:
- Same logic in multiple places
- Similar functions with slight variations
- Repeated boilerplate

### 2. Dead Code
- Unused functions
- Unreachable branches
- Commented-out code
- Unused imports
- Unused variables

### 3. Complexity
- Functions over 50 lines
- Cyclomatic complexity > 10
- Deep nesting (> 4 levels)
- Too many parameters (> 5)

### 4. Code Smells
- God classes/modules
- Feature envy
- Shotgun surgery patterns
- Long parameter lists
- Data clumps

### 5. Outdated Patterns
- Deprecated API usage
- Old syntax when better exists
- Legacy workarounds no longer needed

## Output Format

```markdown
## Tech Debt Report: src/

### Summary
- Files scanned: 45
- Issues found: 12
- Estimated cleanup: [not estimated - see details]

### Duplication (3 instances)

#### 1. Validation logic repeated
**Locations**:
- `src/api/users.py:45-60`
- `src/api/orders.py:30-45`
- `src/api/products.py:55-70`
**Suggestion**: Extract to `src/utils/validation.py`

### Dead Code (4 instances)

#### 1. Unused function `old_format_date`
**Location**: `src/utils.py:123`
**Last modified**: 6 months ago
**Suggestion**: Remove if no external callers

### Complexity (2 instances)

#### 1. `process_order` is 180 lines
**Location**: `src/orders.py:50`
**Cyclomatic complexity**: 25
**Suggestion**: Split into smaller functions

### Outdated (3 instances)

#### 1. Using deprecated `datetime.utcnow()`
**Location**: `src/utils.py:15`
**Suggestion**: Use `datetime.now(timezone.utc)`

### Prioritized Cleanup

1. 🔴 **High**: Fix deprecated APIs (3 issues)
2. 🟠 **Medium**: Extract duplicated validation (3 locations)
3. 🟡 **Low**: Remove dead code (4 functions)
4. 🔵 **Optional**: Reduce complexity (2 functions)
```

## Quick Checks

```bash
# Find TODOs and FIXMEs
grep -rn "TODO\|FIXME\|HACK\|XXX" src/

# Find long functions (Python)
grep -n "def " src/**/*.py | head -20

# Find unused imports (Python with ruff)
ruff check --select F401 src/
```
