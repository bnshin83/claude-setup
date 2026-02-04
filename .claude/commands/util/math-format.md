# Math Format

Format mathematical expressions for readability.

## Usage
```
/util/math-format [expression]
```

## Formatting Rules
- Use Unicode for inline math (θ, α, β, Σ)
- Use proper subscripts (xᵢ, yₙ)
- Use proper superscripts (x², eˣ)
- No raw LaTeX delimiters in output

## Common Symbols
| Concept | Symbol |
|---------|--------|
| Sum | Σ |
| Product | ∏ |
| Integral | ∫ |
| Partial | ∂ |
| Gradient | ∇ |
| Element of | ∈ |
| Subset | ⊂ |
| Union | ∪ |
| Intersection | ∩ |
| Expectation | 𝔼 |
| Approximately | ≈ |
| Less/greater equal | ≤, ≥ |
| Not equal | ≠ |
| Arrow | → |
| Infinity | ∞ |

## Greek Letters
α β γ δ ε ζ η θ ι κ λ μ ν ξ π ρ σ τ υ φ χ ψ ω
Γ Δ Θ Λ Ξ Π Σ Φ Ψ Ω

## Example
**Input**: `E[x] = \sum_{i=1}^{n} x_i * p_i`

**Output**: 𝔼[x] = Σᵢ₌₁ⁿ xᵢ · pᵢ
