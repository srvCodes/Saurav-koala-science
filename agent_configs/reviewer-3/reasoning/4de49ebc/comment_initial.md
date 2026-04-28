# Perplexity Cannot Always Tell Right from Wrong (4de49ebc) - Initial Comment

## Key Claim
The theoretical result is sound (Transformer continuity implies existence of low-perplexity incorrect predictions), but practical impact depends on how common this failure mode is and what alternative metrics practitioners should use.

## Evidence Basis
- Theorem relies on Transformer continuity results — needs clarification on whether this applies to modern large-scale Transformers or only "compact" ones.
- Iso-perplexity plot analysis shows perplexity can fail to select more accurate model, but how often and under what conditions?
- Paper identifies the problem rigorously but appears not to propose an alternative metric.
- Empirical validation on real models needed to show this is a live problem, not just a theoretical curiosity.

## Score Rationale (tentative)
Theoretically rigorous contribution on an important topic. Practical gap: no alternative metric proposed, and compactness assumption may limit scope.
