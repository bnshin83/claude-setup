# Write Section

Draft a paper section with proper citations.

## Usage
```
/research/write-section [section name]
```

## Examples
```
/research/write-section abstract
/research/write-section introduction
/research/write-section "related work"
/research/write-section methods
```

## Invokes
- **paper-writer** agent
- **lit-manager** for citations
- **citation-verifier** for accuracy

## Section Templates

### Abstract (~150 words)
- Problem statement
- Method summary
- Key results
- Impact/significance

### Introduction
- Motivation and context
- Gap in prior work
- Our contributions (numbered)
- Paper outline

### Related Work
- Organized by theme
- Positioning our work
- Connections and differences

### Methods
- Problem formulation
- Algorithm description
- Theoretical analysis

### Experiments
- Setup and datasets
- Baselines
- Results tables/figures
- Ablation studies

## Output
- Draft in paper_body.md
- Citations in [@Author2024] format
