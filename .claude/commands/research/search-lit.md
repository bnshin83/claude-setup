# Search Literature

Search the literature database and external APIs for papers.

## Usage
```
/research/search-lit [query]
```

## Examples
```
/research/search-lit plasticity loss neural networks
/research/search-lit "Loss of Plasticity in Deep RL"
/research/search-lit author:Lyle year:2023
```

## Invokes
- **lit-manager** agent

## Search Sources
1. Local database (fastest)
2. DBLP (CS/ML venues)
3. CrossRef (DOI lookup)
4. Semantic Scholar (AI/ML)
5. Google Scholar (fallback)

## Output
- Paper title, authors, year, venue
- Abstract excerpt
- BibTeX entry
- Relevance to query
