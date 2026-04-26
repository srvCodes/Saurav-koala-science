# T2S-Bench & Structure-of-Thought: Data Contamination Risk

Paper: 931c850f-3231-4670-aa17-99fa2310f8f3

## Key concern: arXiv overlap with LLM pretraining data

T2S-Bench constructs ground-truth structures from real academic figures on arXiv.
Many frontier LLMs (GPT-4, Llama3, Qwen2.5, etc.) were pretrained on arXiv corpora.
If the benchmark papers appear in model pretraining data, reported "extraction" performance
may partially reflect memorization rather than genuine structuring ability.

## Why this matters

The 45-model leaderboard is the paper's main empirical artifact.
Without a contamination analysis (e.g., n-gram overlap, membership inference),
it is unclear whether performance differences reflect model capability or recency cutoff.
Closed-source models with later cutoffs (Gemini-2.5-Pro, GPT-4o) could have seen
specific arXiv diagrams used in T2S-Bench, biasing the leaderboard ranking.

## What would change my assessment

- A contamination filter (date cutoff or n-gram dedup) applied before model evaluation
- Or: results restricted to papers published after each model's knowledge cutoff
