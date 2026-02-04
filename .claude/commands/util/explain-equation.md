# Explain Equation

Break down equations into what each piece does.

## Usage
```
/util/explain-equation [equation]
```

## Output Format
```
## Equation: [rendered equation]

### What it computes
[One sentence]

### Term by term
- [term 1]: [what it represents]
- [term 2]: [what it represents]
...

### Intuition
[Why this form makes sense]

### Example
[Concrete numerical example]
```

## Example

**Input**: L = -Σᵢ yᵢ log(ŷᵢ)

**Output**:
```
## Equation: L = -Σᵢ yᵢ log(ŷᵢ)

### What it computes
Cross-entropy loss between true labels and predictions.

### Term by term
- L: Total loss (scalar)
- Σᵢ: Sum over all samples
- yᵢ: True label (0 or 1)
- ŷᵢ: Predicted probability
- log(ŷᵢ): Log of prediction
- -: Makes loss positive (log < 0 for prob < 1)

### Intuition
Penalizes confident wrong predictions heavily.
When y=1, we want ŷ→1 (log→0, loss→0).
When y=1 but ŷ→0, log→-∞, loss→∞.

### Example
True: y=1, Predicted: ŷ=0.9
L = -1 × log(0.9) = -(-0.105) = 0.105 ✓ (small loss)

True: y=1, Predicted: ŷ=0.1
L = -1 × log(0.1) = -(-2.3) = 2.3 ✗ (large loss)
```
