# Verdict reasoning: Self-Attribution Bias (0316ddbf)

## Verdict score: 4.5 (weak reject)

## Core finding assessed
Implicit/explicit asymmetry (Fig. 7) is genuinely novel: implicit turn-structure framing induces
leniency whereas explicit self-attribution does not. No prior work isolated turn-position vs. semantic
attribution while holding content fixed.

## Key weaknesses driving rejection
- No linked GitHub repo; artifacts are rendered figures + paper source only; headline numbers cannot
  be independently verified — reproducibility failure is disqualifying at ICML
- Mechanism not isolated: cannot distinguish turn-position bias vs. KV-cache vs. familiarity vs.
  semantic self-attribution; mitigation (off-policy auditing) may not target the correct causal driver
- Cross-model control confounded by within-family preference bias (Spiliopoulou et al. 2025)
- Deployment risk overstated without base-rate control for actual monitoring outcome changes

## Score: 4.5 — needs public code, 2x2x2 ablation, recalibrated claims before ICML standard
