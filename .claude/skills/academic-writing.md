---
name: academic-writing
description: Academic writing conventions for research papers.
---

# Academic Writing Skill

Guidelines for clear, precise academic prose.

## Core Principles

### Clarity
- One idea per paragraph
- Topic sentence first
- Active voice preferred
- Short sentences (20-25 words average)

### Precision
- Specific over vague ("17% improvement" not "significant improvement")
- Define all terms
- Quantify when possible
- Cite sources for all claims

### Flow
- Logical paragraph order
- Clear transitions
- Signpost structure ("First..., Second..., Finally...")
- Forward references for complex ideas

## Structure Guidelines

### Abstract (150-250 words)
1. Problem statement (1-2 sentences)
2. Method summary (2-3 sentences)
3. Key results (2-3 sentences)
4. Impact/significance (1 sentence)

### Introduction
1. Motivation and context
2. Gap in prior work
3. Our contributions (numbered)
4. Paper outline (optional)

### Related Work
- Organize thematically, not chronologically
- Position your work relative to others
- Acknowledge prior art honestly
- End with what's missing (your gap)

### Methods
- Problem formulation first
- Algorithm/approach description
- Theoretical analysis (if applicable)
- Complexity analysis

### Experiments
- Clear setup description
- Baselines and comparisons
- Results with error bars
- Ablation studies

### Discussion
- Interpret results
- Limitations (be honest)
- Broader impact
- Future work

## Common Fixes

| Bad | Good |
|-----|------|
| "It can be seen that" | [delete] |
| "In order to" | "To" |
| "A number of" | [specific number] |
| "Due to the fact that" | "Because" |
| "significantly better" | "17% improvement (p<0.01)" |
| "prior work shows" | "[@Smith2024] shows" |

## Citation Style

### Inline
```
[@Smith2024] showed that...
As shown by [@Smith2024]...
```

### Parenthetical
```
... as previously demonstrated \citep{Smith2024}.
```

### Multiple
```
Several works [@Smith2024; @Jones2023] have...
```

## Math Conventions

- Define before use
- Consistent notation throughout
- Bold for vectors (𝐱), capital for matrices (𝐀)
- Use standard symbols when available
