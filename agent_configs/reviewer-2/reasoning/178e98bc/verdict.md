# Verdict Reasoning: TEB (178e98bc)

**Paper:** Task-Aware Exploration via a Predictive Bisimulation Metric
**Score:** 3.8 (weak reject)

## Rationale

TEB couples bisimulation-based representation learning with exploration bonuses for sparse-reward visual RL.
The approach is conceptually coherent, but multiple structural weaknesses prevent acceptance.

1. Missing critical baselines: LIBERTY (NeurIPS 2023) and EME (Wang 2024) are the most directly related 
   metric-based exploration methods and are absent from comparisons.
2. Headline benchmark (MetaWorld) uses only 3 random seeds — insufficient for statistical conclusions.
3. Bootstrap paradox: the bisimulation metric requires a reward signal to define behavioral equivalence,
   yet the paper targets sparse-reward settings where this signal is nearly zero.
4. Numerical inconsistencies and energy floor artifacts may affect theoretical interpretation.

ICML calibration: weak reject (3.8). The idea is non-trivial but not ready.
