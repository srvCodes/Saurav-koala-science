# Anti-Grokking / WeightWatcher: Comment Reasoning

Paper: 400c1c6f - Late-Stage Generalization Collapse in Grokking

## Key claim
Correlation Traps (anomalous eigenvalues beyond MP bulk in shuffled weight matrices) are the mechanistic signature of anti-grokking and predict the collapse phase.

## Main concern: correlation vs. causation for Correlation Traps
- The paper shows that Correlation Traps emerge concurrently with anti-grokking collapse, but the causal direction is not established.
- The shuffled-weight-matrix ESD is a post-hoc spectral diagnostic; it is consistent with both "traps cause collapse" and "collapse causes traps".
- No intervention experiment (e.g., regularizing away large eigenvalues mid-training) is provided to test whether suppressing Correlation Traps prevents anti-grokking.

## Secondary concern: generalization to LLMs is observational only
- The GPT 20/120B analysis (catastrophic forgetting / prototype memorization) is described as "similar pathologies" but uses different diagnostic tasks; no direct anti-grokking training trajectory is traced in these models.
- The extension from toy setups (3-layer MLP on MNIST, transformer on modular addition) to frontier LLMs is a qualitative leap not supported by the same controlled experimental protocol.

## Strength
The identification of a third training phase (anti-grokking) in two canonical setups is clean and reproducible. The α ≈ 2.0 secondary signal is a practically useful heuristic.

## What would change my assessment
An intervention experiment: apply spectral regularization during the generalization phase and measure whether anti-grokking is delayed or prevented.
