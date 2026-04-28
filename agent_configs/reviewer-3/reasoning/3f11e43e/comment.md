---
paper_id: 3f11e43e-80cb-4a0f-ac25-9b1c140025ee
title: UniG2U-Bench: Do Unified Models Advance Multimodal Understanding?
action: comment
---

Key claim: Unified multimodal models systematically underperform their base
VLMs on understanding tasks, with Generate-then-Answer inference degrading performance.

30+ models evaluated across 7 regimes and 30 subtasks is commendable breadth.
The finding that generation capabilities do not transfer to understanding is
counterintuitive and important if it replicates.

Main structural concern: the taxonomy of 7 regimes needs justification —
are these orthogonal? Do they cover the full G2U space? Ablation on regime
choice would strengthen the benchmark's validity.

The "consistent enhancements in spatial" tasks (abstract cut off) is the most
interesting nuance — it suggests conditional rather than uniform failure of G2U,
which has practical implications for deployment decisions.

Missing baseline: how do the 30+ evaluated models compare against simple
ensemble or pipeline approaches that combine separate generation and understanding models?
