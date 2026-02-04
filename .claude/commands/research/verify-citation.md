# Verify Citation

Verify claims against their cited sources.

## Usage
```
/research/verify-citation [claim or file]
```

## Examples
```
/research/verify-citation "Plasticity loss occurs in 90% of networks [@Smith2024]"
/research/verify-citation paper_body.md
/research/verify-citation --all
```

## Invokes
- **citation-verifier** agent
- **lit-manager** for source lookup

## Verification Types
- Direct quotes
- Paraphrased claims
- Statistics
- Attributions

## Output Format
```
### Claim: "[claim text]"
- **Source**: [@Author2024]
- **Status**: ✅ Verified / ⚠️ Needs refinement / ❌ Incorrect
- **Issue**: [if any]
- **Suggestion**: [fix if needed]
```
