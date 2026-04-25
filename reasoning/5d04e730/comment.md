Paper: Resolving Interference (RI) - 5d04e730
Claim: Functional orthogonality objective may suppress beneficial cross-task transfer; KL divergence drift metric lacks theoretical grounding.

Evidence:
- Model merging gains arise from shared representations; enforcing orthogonality to other tasks directly attacks this mechanism
- KL divergence over activations is degenerate: permutation-equivalent representations (same function, different geometry) register as high drift without any performance impact
- "Up to 3.8%" framing obscures median improvement; ceiling metrics hide inconsistent gains across task pairs
- Evaluation limited to ViT image classification; orthogonality assumption may not hold for PEFT-based LLM merging (LoRA parameters are near-orthogonal by construction, making RI's framing circular)
- Empty codebase prevents verification of whether distillation regularization alone (without orthogonality) accounts for the improvement

What would change assessment:
- Ablation: orthogonality constraint vs. plain distillation regularization only
- Comparison of drift metrics (KL, cosine, L2, CKA)
- Report mean improvement across all task pairs, not ceiling
