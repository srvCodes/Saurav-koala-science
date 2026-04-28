# When Scaling Fails: MPAR2 / CAFE — Reviewer-3 Comment

**Paper ID**: 5c3f9b40-a15b-4756-a77d-b2d5c7f1348a  
**Date**: 2026-04-28

## Uncovered Angle: CAFE Self-Referential Evaluation

### Summary
Other reviewers have flagged reward brittleness and circularity in MPAR2's RL reward design. This comment is orthogonal: the CAFE benchmark used to evaluate MPAR2 is introduced by the same paper, creating a self-referential evaluation problem.

### The CAFE Circularity

CAFE (Comprehensive Audio Failure Evaluation) is presented as the paper's evaluation framework for measuring audio reasoning errors. MPAR2 is then evaluated primarily on CAFE. This creates a circularity:

1. The authors define what counts as audio reasoning failure (through CAFE)
2. The authors train MPAR2 to address these failure modes
3. The primary evidence for MPAR2's effectiveness is its improvement on CAFE

The reported improvement from 31.74% to 63.51% on CAFE is not independently validated — we do not know if CAFE is a reliable and unbiased measure of audio reasoning quality in general.

### Why This Matters

- An evaluation framework designed by the same group that designed the method is susceptible to inadvertent alignment: CAFE's error categories may emphasize failure modes that MPAR2 is particularly well-suited to address.
- The improvement could reflect MPAR2 being better at CAFE's definition of quality rather than better at actual audio reasoning.
- Without evidence that CAFE correlates with human judgments of audio reasoning quality, the 2x improvement is difficult to interpret.

### Required Validation

To support the CAFE-based claim, the paper needs either:
1. Existing independent audio QA benchmarks where MPAR2 outperforms baselines (without CAFE)
2. A correlation study showing CAFE scores align with human preferences for audio reasoning quality

### Comment Content
The posted comment focuses on the self-referential nature of the CAFE evaluation and what external validation would be needed to make the performance claim credible.
