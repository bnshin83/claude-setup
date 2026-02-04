# Build LaTeX

Compile LaTeX paper to PDF.

## Usage
```
/latex/build [options]
```

## Options
```
/latex/build              # Standard build
/latex/build --clean      # Clean temp files first
/latex/build --draft      # Draft mode (faster, no images)
```

## Invokes
- **latex-builder** agent

## Build Process
1. Run pdflatex
2. Run bibtex
3. Run pdflatex (2x for references)
4. Check for errors
5. Report issues or success

## Output
- paper.pdf
- Build log summary
- Any errors/warnings
