# Test and Fix

Run tests and automatically fix failures.

## Usage
```
/dev/test-and-fix [test pattern]
```

## Workflow

### 1. Detect Test Framework
```bash
# Check for test configuration
ls pytest.ini pyproject.toml setup.cfg package.json go.mod Cargo.toml
```

### 2. Run Tests
```bash
# Python
pytest -v --tb=short

# With pattern
pytest -v -k "test_pattern"

# JavaScript
npm test

# Go
go test ./...
```

### 3. Parse Failures
Extract from output:
- Test name
- File and line number
- Error message
- Expected vs actual

### 4. Analyze Each Failure
For each failing test:
1. Read the test code
2. Read the code under test
3. Determine if bug is in:
   - Test (wrong expectation)
   - Code (actual bug)
   - Both

### 5. Fix and Verify
1. Make the fix
2. Re-run the specific test
3. Run full suite to check for regressions

## Output Format

```markdown
## Test Results

### Initial Run
- Total: 50 tests
- Passed: 48
- Failed: 2

### Failures

#### 1. test_validation.py::test_email_valid
**Error**: AssertionError
**Expected**: True
**Actual**: False
**Analysis**: Bug in code - regex missing '+' handling
**Fix**: Updated regex in `src/validation.py:15`

#### 2. test_utils.py::test_format_date
**Error**: ValueError
**Expected**: "2024-01-15"
**Actual**: Exception raised
**Analysis**: Test bug - wrong date format in fixture
**Fix**: Updated test fixture

### Final Run
- Total: 50 tests
- Passed: 50
- Failed: 0

✅ All tests passing
```

## Quick Commands

```bash
# Run all tests
pytest -v

# Run specific test file
pytest test_module.py -v

# Run tests matching pattern
pytest -k "validation" -v

# Run last failed tests
pytest --lf -v

# Run with coverage
pytest --cov=src -v

# Stop on first failure
pytest -x -v
```

## Tips

- Fix one test at a time
- Run related tests after each fix
- Check for cascading failures
- Don't change tests unless they're wrong
