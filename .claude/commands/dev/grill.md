# Grill Mode

Adversarial code review - find every possible issue.

## Usage
```
/dev/grill [file or diff]
```

## Purpose
Channel your inner skeptical senior engineer. Assume bugs exist until proven otherwise. Question everything.

## Invokes
- **staff-reviewer** agent in adversarial mode

## Review Targets

```bash
# Review specific file
/dev/grill src/auth.py

# Review recent changes
/dev/grill HEAD~1..HEAD

# Review staged changes
/dev/grill --staged

# Review PR
/dev/grill pr:123
```

## What Gets Grilled

### Correctness
- Logic errors
- Edge cases
- Off-by-one errors
- Null handling
- Race conditions
- Resource leaks

### Security
- Input validation
- Injection vulnerabilities
- Auth/authz issues
- Data exposure
- Hardcoded secrets

### Performance
- Hidden O(n²)
- Memory leaks
- N+1 queries
- Unnecessary work
- Missing indexes

### Maintainability
- God functions
- Deep nesting
- Magic values
- Copy-paste code
- Unclear names

## Output

Issues categorized by severity:

```markdown
## Grill Report: src/auth.py

### 🔴 Critical (1)
1. **SQL Injection at line 45**
   - `query = f"SELECT * FROM users WHERE id = {user_id}"`
   - Any user input goes directly into query
   - Fix: Use parameterized queries

### 🟠 Major (2)
1. **Missing rate limiting on login (line 23)**
   - Brute force attacks possible
   - Fix: Add rate limiting middleware

2. **Password logged in plaintext (line 67)**
   - `logger.debug(f"Login attempt: {username}, {password}")`
   - Fix: Remove password from log

### 🟡 Minor (3)
1. **Function `check_auth` is 150 lines (line 12)**
   - Hard to test and maintain
   - Consider: Split into smaller functions

### Verdict: ❌ REQUEST CHANGES
Critical security issues must be fixed.
```

## Mindset

Ask yourself:
- What if this input is malicious?
- What if this fails halfway through?
- What if two requests hit this simultaneously?
- What if this data is 10x larger than expected?
- Would I bet $1000 this code is bug-free?
