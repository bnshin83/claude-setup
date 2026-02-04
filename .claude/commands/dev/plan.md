# Plan

Create a detailed implementation plan before coding.

## Usage
```
/dev/plan [feature or task]
```

## Purpose
Force thorough planning before execution. Reduces wasted effort from wrong approaches.

## Process

### 1. Understand Requirements
- What problem are we solving?
- Who is the user?
- What are the acceptance criteria?
- What are the constraints?

### 2. Explore Existing Code
- What already exists that's relevant?
- What patterns are used?
- What can we reuse?
- What might we break?

### 3. Design Approach
- High-level architecture
- Data flow
- API design
- State management

### 4. Break Into Tasks
- Ordered list of implementation steps
- Dependencies between tasks
- Estimated complexity (S/M/L)

### 5. Identify Risks
- What could go wrong?
- What are we uncertain about?
- What needs clarification?

## Output Format
```markdown
## Implementation Plan: [Feature Name]

### Requirements
- [Requirement 1]
- [Requirement 2]

### Existing Code
| File | Relevance |
|------|-----------|
| [file] | [how it relates] |

### Approach
[High-level description]

### Data Flow
```
[User] → [Component] → [Service] → [Database]
```

### Tasks
| # | Task | Complexity | Depends On |
|---|------|------------|------------|
| 1 | [Task 1] | S | - |
| 2 | [Task 2] | M | 1 |
| 3 | [Task 3] | M | 1, 2 |

### Files to Modify
- `src/api/auth.py` - Add endpoint
- `src/services/user.py` - Add validation

### Files to Create
- `src/services/oauth.py` - OAuth logic
- `tests/test_oauth.py` - Tests

### Risks
| Risk | Likelihood | Mitigation |
|------|------------|------------|
| [Risk 1] | Medium | [How to address] |

### Questions
- [ ] [Question needing clarification]

### Definition of Done
- [ ] All tasks completed
- [ ] Tests passing
- [ ] Code reviewed
- [ ] Documentation updated
```

## Tips
- Don't skip this for non-trivial features
- Get plan approved before coding
- Update plan if requirements change
- Reference plan during implementation
