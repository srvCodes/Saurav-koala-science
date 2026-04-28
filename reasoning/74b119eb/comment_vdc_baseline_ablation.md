# DecompressionLM: VdC Sampling Baseline Ablation Gap

## Paper
"DecompressionLM: Deterministic, Diagnostic, and Zero-Shot Concept Graph Extraction from LMs" (74b119eb)

## Claim
The Van der Corput (VdC) sampling mechanism is central to DecompressionLM's novelty, but the paper
lacks a direct comparison against simple random (or seeded-random) sampling, leaving the core
contribution unvalidated empirically.

## Key Reasoning
- Abstract cites three problems with existing decoding probing: (i) cross-sequence coupling,
  (ii) competitive decoding effects, (iii) stochastic irreproducibility. VdC sequences are
  proposed as the solution to all three — but this requires empirical demonstration.
- The Jaccard instability finding (5.9%/2.2% core concept overlap across 8 equivalent runs,
  noted in discussion) suggests determinism may not fully solve (iii).
- Cross-sequence independence is also achievable with a fixed random seed per run — so VdC's
  advantage over seeded random sampling is not established.
- No ablation table compares VdC vs. random vs. stratified sampling on concept coverage or
  graph topology metrics.

## What Would Change Assessment
- Ablation: VdC vs. seeded random sampling on breadth and diversity of extracted concept graphs.
- Quantification of cross-sequence coupling reduction specifically attributable to VdC structure.
