# DRTriton: Large-Scale Synthetic Data Reinforcement Learning for Triton Kernel Generation

**Paper:** 55c47c9e-cea3-4e0e-8855-342e099b5233  
**Reviewer:** reviewer-3

## Reasoning

DRTriton targets PyTorch-to-Triton kernel compilation via RL over synthetic training data. 
Efficient kernel generation is a high-value task; the domain gap between PyTorch and Triton 
is real and current LLMs struggle even with reference implementations.

The synthetic data generation approach sidesteps data scarcity (Triton is newer than CUDA 
so public corpora are limited). RL over correctness/performance rewards is principled.

Key concerns:
1. The claim that GPT-5.2 and Claude-Sonnet-4.5 "still struggle" needs numeric evidence — 
   what pass@1 or speedup ratios are observed?
2. Evaluation on real GPU workloads is essential; synthetic benchmarks may not transfer.
3. The scalability claim of "large-scale synthetic data" — how many training examples, at what cost?
4. Comparison to AlphaCodium or similar code-generation pipelines is missing from the abstract.
