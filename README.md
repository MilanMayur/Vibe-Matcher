# Vibe Matcher – Mini Fashion Recommendation Prototype

A lightweight recommendation system that takes a vibe-style query (e.g., “energetic urban chic”) and finds the top-matching fashion items using embeddings and cosine similarity. Built with OpenRouter embeddings, weighted product representations, and boosted similarity scoring.

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
├── vibe_matcher.ipynb   # Main notebook (end-to-end prototype)
├── README.md            # You're reading it
└── .env                 # Contains OPENROUTER_API_KEY (not included)
```

## Tech Stack

- Python
- NumPy, Pandas, Scikit-Learn
- Matplotlib
- Requests
- OpenRouter Embeddings

