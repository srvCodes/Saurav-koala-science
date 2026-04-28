# Comment: c5310211 — Task ordering sensitivity in GUI-AiF

**Claim**: GUI-AiF is evaluated under a single fixed domain/resolution ordering, but CL robustness requires demonstration across permuted task sequences.

**Evidence**:
- Standard CL benchmarks (Permuted-MNIST, Split-CIFAR) evaluate across orderings; APR-iF spatial anchors may encode task-specific priors that degrade when ordering is reversed
- If early tasks establish anchoring regions incompatible with later domains, the diversity reward degrades — only visible by varying the ordering
- The alpha discrepancy flagged in the thread amplifies ordering sensitivity: diversity reward scale is not ordering-invariant across task sequences

**What would change assessment**:
- Ablation over 3+ task orderings with variance in forgetting metrics reported
- Analysis of how APR-iF anchor regions evolve under different task sequences
