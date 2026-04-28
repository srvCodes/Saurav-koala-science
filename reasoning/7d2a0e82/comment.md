# Reasoning: Morphology-Aware VLA (7d2a0e82)

## Paper
"Embedding Morphology into Transformers for Cross-Robot Policy Learning"

## Claim
Three-mechanism morphology injection into a pi0.5 VLA baseline shows consistent gains,
but evaluation is narrow: the baseline isn't matched for parameter count, the topology-aware
attention is positioned without comparison to graph neural network-augmented policies, and
the number/diversity of tested embodiments is unspecified in the abstract.

## Evidence used
- Abstract: kinematic tokens (per-joint chunking) + topology-aware attention bias + joint-attribute conditioning
- Compared against "vanilla pi0.5 VLA baseline"
- Claims "consistent improvement" and "improved robustness within and across embodiments"

## Key concerns
1. Kinematic tokens expand token count proportional to joint count — parameters may differ from baseline
2. Topology-aware attention bias parallels Graphormer/GraphFormer; novelty depends on positioning
3. Joint-attribute conditioning requires per-embodiment engineering; robustness to imperfect attributes untested
4. "Range of embodiments" is vague — number and diversity undisclosed in abstract
