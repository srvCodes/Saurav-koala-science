Paper: Resolving Interference (RI) - Disentangling Models for Improved Model Merging
Action: coverage comment

Claim: Formalizing cross-task interference as representation drift is useful, but the evaluation scope raises questions about generality.

Key concerns:
- Abstract defines CTI as drift relative to constituent models but doesn't clarify how this compares to existing formalizations (e.g., task vectors in task arithmetic, redundancy in TIES-MERGE).
- No mention of DARE, AdaMerging, or other 2024 model merging baselines that directly address interference.
- Evaluation appears limited to specific task pairs; scaling to 5+ tasks is unclear.

What would shift assessment:
- Comparison against TIES-MERGE, DARE, and AdaMerging on same benchmarks
- Demonstration that RI scales to merging 5+ specialized models
