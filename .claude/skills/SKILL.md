---
name: coding-standards
description: Enforce coding standards and best practices across the project.
---

# Coding Standards Skill

Apply these standards to all code written or reviewed.

## General Principles

### Clarity Over Cleverness
- Write code that's easy to read
- Avoid "clever" one-liners that obscure meaning
- Comment WHY, not WHAT

### Single Responsibility
- Functions do one thing
- Classes have one reason to change
- Modules have clear boundaries

### Fail Fast
- Validate inputs early
- Throw/raise on invalid state
- Don't continue with bad data

## Language-Specific

### Python
```python
# Use type hints
def process(items: list[str]) -> dict[str, int]:

# Use dataclasses for data containers
@dataclass
class User:
    name: str
    email: str

# Prefer pathlib over os.path
from pathlib import Path
config_path = Path("config") / "settings.yaml"

# Use context managers
with open(path) as f:
    data = f.read()

# Avoid mutable default arguments
def func(items: list | None = None):
    items = items or []
```

### TypeScript
```typescript
// Use strict mode
"strict": true

// Prefer interfaces for objects
interface User {
  name: string;
  email: string;
}

// Use const assertions
const ROLES = ['admin', 'user'] as const;

// Avoid any
function process(data: unknown): void

// Use optional chaining
const name = user?.profile?.name;
```

## Error Handling

### Do
- Catch specific exceptions
- Add context when re-raising
- Log errors with stack traces
- Return meaningful error messages

### Don't
- Catch and ignore silently
- Use bare `except:` in Python
- Use `catch(e) {}` in JS
- Expose internal errors to users

## Testing

### Test Names
```
test_[unit]_[scenario]_[expected]()
```

### Test Structure (AAA)
```
# Arrange - set up
# Act - perform action
# Assert - verify
```

### Coverage Goals
- Aim for 80%+ coverage
- 100% on critical paths
- Don't test implementation details
