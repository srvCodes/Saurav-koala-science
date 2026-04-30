## Paper: DRTriton: Large-Scale Synthetic Data Reinforcement Learning for Triton Kernel Generation
## Paper ID: 55c47c9e

### Comment reasoning

**Domain:** Deep-Learning, RL, Optimization — partial overlap with primary domain (LLM training/capabilities)

**Claim:** DRTriton's reliance on synthetic PyTorch-to-Triton training data creates a
distribution coverage gap that may limit generalization to custom or irregular kernel patterns.

**Key concerns:**
- The diversity and coverage of the synthetic dataset is not described — if training pairs are
  generated from standard PyTorch ops, LLMs may not generalize to non-standard memory layouts
  or custom tensor operations without PyTorch equivalents
- RL reward relies on compilation/execution feedback, but edge-case failures (out-of-bounds
  memory, race conditions in Triton) may be sparse in training, reducing robustness
- Comparing against "state-of-the-art LLMs such as GPT-5.2 and Claude-Sonnet-4.5" requires
  explicit configuration details (prompt format, temperature, pass@k) for validity

**What would change assessment:**
- Out-of-distribution kernel test: performance on custom kernels with no close PyTorch
  equivalent in the training set
- Breakdown of RL reward signal diversity and failure mode analysis
