# Vibe Matcher – Mini Fashion Recommendation Prototype

A lightweight recommendation system that takes a vibe-style query (e.g., “energetic urban chic”) and finds the top-matching fashion items using embeddings and cosine similarity. Built with OpenRouter embeddings, weighted product representations, and boosted similarity scoring.

## Project Overview

The system:
- Converts product metadata (name, description, vibes) into embeddings
- Converts user vibe queries into embeddings
- Computes cosine similarity between query and products
- Returns the best-matched products with interpretable scores
- Works even without an API key using a deterministic fallback

## Features

- Small mock fashion dataset 
- OpenRouter-powered embeddings
- Weighted embeddings (name + description + vibes)
- Query expansion for better semantic understanding
- Cosine similarity ranking (Top-3 results)
- Score breakdown (raw, scaled, boosted)
- Deterministic fallback mode (no API? no problem)
- Latency measurement and evaluation loop

## How It Works

- User enters a vibe query → system expands it for richer semantics.
- Each product is represented by weighted embeddings (name, desc, vibe tags).
- Query and product vectors are compared using cosine similarity.
- Scores are scaled + boosted for better interpretability.
- Top-3 matches are returned with full score breakdown.

## Project Structure

```bash
Vibe-Matcher/
├── file.ipynb           # Main notebook (end-to-end prototype)
├── README.md            # You're reading it
└── .env                 # Contains OPENROUTER_API_KEY (not included)
```

## Tech Stack

- Python
- NumPy, Pandas, Scikit-Learn
- Matplotlib
- Requests
- OpenRouter Embeddings

## Product Catalog
Each product is defined using:
- name
- description
- vibes (style tags)
```
Example-
{
  "name": "Urban Pulse Jacket",
  "desc": "Sleek cropped bomber with reflective trim—designed for energetic city nights.",
  "vibes": ["urban", "chic", "energetic"]
}

```

## Embedding Strategy
```
Final Vector = 0.3·Name + 0.5·Description + 0.2·Vibes
```

## Similarity & Scoring
- Similarity metric: Cosine Similarity
- Raw cosine score ∈ [-1, 1]
- Scores are transformed into a user-friendly range:

| Stage   | Formula       |
| ------- | ------------- |
| Scaled  | (raw + 1) / 2 |
| Boosted | scaled ^ 0.6  |

Boosted scores make strong matches more distinguishable.

## Performance Evaluation

Metrics Collected:
  - Raw similarity score
  - Scaled score
  - Boosted score
  - Match quality flag
  - Latency per query (ms)

Latency Test:
  - Multiple runs of the same query
  - Results plotted using Matplotlib
  - Confirms low and stable inference time

## Limitations:
- Small in-memory catalog
- No database or vector store
- No learning or feedback loop
- Single-query matching only
- No keyword + semantic hybrid search

## Future Improvements:
- Pinecone / FAISS vector store
- Batch embedding & caching
- Hybrid keyword + semantic search
- Larger product catalog
- API or frontend integration

