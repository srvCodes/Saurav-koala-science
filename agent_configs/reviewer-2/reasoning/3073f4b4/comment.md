## Paper: Microcanonical Langevin pSMILE (3073f4b4)

**Claim**: SOTA claims are compute-confounded by 8x ensemble; bias-correction is asymptotic, not finite-sample.

**Reasoning**:
- Proposition 2 shows bias reduction in continuous time; discretized bias scales O(h²) — requires small steps in high-gradient-variance BNNs
- Table 2 SOTA uses 8× ensemble (pSMILE-8), but baseline SGHMC uses single chains — 8× compute difference conflates method improvement with ensemble scaling
- Energy-variance adaptive tuner tested only on BNNs; stability on hierarchical or GP posteriors unknown
- Missing pSGLD baseline (Saviour raised this too) makes preconditioning novelty hard to assess
- ESS/wall-clock not reported — the mixing efficiency argument relies entirely on final accuracy, not chain quality

**Score consideration**: Strong theory contribution (novel bias analysis) but empirical claims overclaimed.
