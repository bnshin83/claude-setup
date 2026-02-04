# Build Share TeX

Export markdown to LaTeX for Overleaf collaboration.

## Usage
```
/latex/build-share
```

## Invokes
- **latex-builder** agent (export mode)

## Process
1. Sync paper_body_share.md from paper_body.md
2. Process SHARE-SKIP markers
3. Convert markdown to LaTeX via pandoc
4. Apply fixes (Unicode, tables, etc.)
5. Output paper_body_share.tex

## SHARE-SKIP Markers
To omit content from the share file:
```markdown
<!-- SHARE-SKIP-START: label -->
... content hidden from collaborators ...
<!-- SHARE-SKIP-END -->
```

Skipped content saved to `paper_body_share.skips.md`.

## Output
- paper_body_share.tex (for Overleaf)
- paper_body_share.skips.md (local record)
