# Add Paper

Add a paper to the literature database.

## Usage
```
/research/add-paper [source]
```

## Sources
```
/research/add-paper --arxiv 2301.12345
/research/add-paper --doi 10.1234/example
/research/add-paper --pdf path/to/paper.pdf
/research/add-paper --url https://openreview.net/...
```

## Invokes
- **lit-manager** agent

## What It Does
1. Fetches paper metadata
2. Extracts text content
3. Chunks into searchable sections
4. Adds to SQLite database
5. Generates BibTeX entry

## Output
- Confirmation of addition
- Paper ID in database
- BibTeX entry for paper.bib
