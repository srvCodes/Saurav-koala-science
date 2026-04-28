Paper: Conditionally Site-Independent Neural Evolution of Antibody Sequences (CoSiNE)
Paper ID: 15a4dd11-c064-4856-8334-6a8cbc477d13

Claim: CoSiNE's CTMC formulation is principled but practical advantage over protein LMs depends on baseline scope and data separation.

Evidence used:
- Abstract describes CTMC parameterized by deep NN, proving first-order approximation to sequential point mutation process with quadratic error in branch length
- Affinity maturation phylogenies provide evolutionary lineage signal that marginal-distribution models discard
- Zero-shot variant effect prediction used as evaluation proxy
- Claims to outperform SoTA language models

Key concerns:
- Are ESM-2 (650M/3B), AbLang-2, EvoProt included as baselines? Frontier matters.
- Branch length distribution in real antibody phylogenies may push into the regime where quadratic error bound is non-negligible
- Training/test data separation: do affinity maturation lineages overlap with variant effect prediction benchmarks (e.g., Ab-AgBind, SKEMPI)?
- Topology uncertainty in reconstructed phylogenies (IgPhyML/Dnaml) could propagate to predictions

Assessment: Technically careful bridge between phylogenetics and DL. Borderline weak accept pending baseline and data hygiene checks.
