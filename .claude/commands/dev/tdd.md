# TDD Cycle

Test-Driven Development workflow.

## Usage
```
/dev/tdd [feature]
```

## The TDD Cycle

```
┌─────────────────────────────────────────┐
│                                         │
│    ┌─────────┐                          │
│    │  RED    │  Write failing test      │
│    └────┬────┘                          │
│         │                               │
│         ▼                               │
│    ┌─────────┐                          │
│    │  GREEN  │  Make test pass          │
│    └────┬────┘                          │
│         │                               │
│         ▼                               │
│    ┌─────────┐                          │
│    │REFACTOR │  Clean up code           │
│    └────┬────┘                          │
│         │                               │
│         └───────────────────────────────┘
```

## Process

### 1. RED: Write Failing Test
```python
def test_validate_email_accepts_valid():
    """Test that valid emails pass validation."""
    assert validate_email("user@example.com") is True

def test_validate_email_rejects_invalid():
    """Test that invalid emails fail validation."""
    assert validate_email("not-an-email") is False
```

Run test → Should FAIL (function doesn't exist)

### 2. GREEN: Minimal Implementation
```python
def validate_email(email: str) -> bool:
    """Validate email format."""
    return "@" in email and "." in email
```

Run test → Should PASS

### 3. REFACTOR: Improve Code
```python
import re

EMAIL_PATTERN = re.compile(r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$')

def validate_email(email: str) -> bool:
    """Validate email format using regex."""
    return bool(EMAIL_PATTERN.match(email))
```

Run test → Should still PASS

### 4. Repeat
Add more test cases, repeat cycle.

## Commands

```bash
# Run specific test
pytest tests/test_feature.py -v

# Run and stop on first failure
pytest -x

# Run with coverage
pytest --cov=src

# Watch mode (if available)
ptw -- tests/
```

## Test Structure
```python
class TestFeature:
    """Tests for feature X."""

    def test_happy_path(self):
        """Test normal expected usage."""
        pass

    def test_edge_case_empty(self):
        """Test with empty input."""
        pass

    def test_edge_case_large(self):
        """Test with large input."""
        pass

    def test_error_invalid_type(self):
        """Test with wrong type raises error."""
        pass
```

## Tips
- Write the test FIRST, always
- Keep tests small and focused
- One assertion per test (usually)
- Test behavior, not implementation
- Name tests descriptively
- Don't refactor until green
