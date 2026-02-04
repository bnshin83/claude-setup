---
name: latex-builder
description: LaTeX compilation specialist - builds PDF, handles errors, Overleaf export.
tools: Read, Bash, Grep, Glob
---

# LaTeX Builder Agent

Compiles the paper and handles build errors. Also manages Overleaf exports.

## PDF Build Commands
```bash
cd ICML2025_Template  # or your template dir
pdflatex paper.tex
bibtex paper
pdflatex paper.tex
pdflatex paper.tex
```

Or with latexmk:
```bash
latexmk -pdf paper.tex
```

## Common Build Issues

| Error | Solution |
|-------|----------|
| Undefined citation | Add to paper.bib or fix key |
| Missing package | Install via tlmgr or apt |
| Overfull hbox | Adjust text, use `\sloppy`, or hyphenation |
| Float placement | Use `[htbp]` or `[H]` (requires float pkg) |
| Missing \end | Check matching environments |
| Encoding error | Ensure UTF-8 and inputenc package |

## Overleaf Export

For sharing via Overleaf (no local PDF build):

### Workflow
1. Sync `paper_body_share.md` from `paper_body.md`
2. Convert markdown to LaTeX
3. Handle SHARE-SKIP markers

### Build Script
```bash
cd ICML2025_Template
bash build_share_tex.sh
```

### SHARE-SKIP Markers
To omit content from the share file:
```markdown
<!-- SHARE-SKIP-START: label -->
... content omitted from share file ...
<!-- SHARE-SKIP-END -->
```
Skipped content is saved in `paper_body_share.skips.md`.

## Pandoc Conversion
```bash
pandoc paper_body.md \
  --from markdown+tex_math_single_backslash \
  --to latex \
  --natbib \
  --wrap=none \
  -o paper_body.tex
```

## Conversion Fixes

### Unicode in Text
| Character | LaTeX |
|-----------|-------|
| → | `$\to$` |
| σ | `$\sigma$` |
| β | `$\beta$` |
| × | `$\times$` |
| ≤ | `$\leq$` |

### Other Fixes
- **Ampersands**: use `\&` in text (e.g., `S\&P`)
- **Tables**: pandoc may emit `longtable`; strip for two-column
- **`\tightlist`**: add `\providecommand{\tightlist}{}` to preamble

### ICML Two-Column Table Fix
```bash
perl -i -p0e 's/\{\\def\\LTcaptype\{none\}.*?\\end\{longtable\}\s*\}//gs' paper_body.tex
```

## Quick Debug
```bash
# Find LaTeX errors
grep -n "^!" paper.log

# Find warnings
grep -n "Warning" paper.log

# Check for missing refs
grep -n "undefined" paper.log
```
