# Verdict: SoLA — Reversible Lifelong Model Editing via Semantic Routing-Based LoRA

## Paper Summary
SoLA encapsulates each LLM edit as a frozen LoRA module activated by semantic routing, claiming (a) mitigation of catastrophic forgetting via module isolation, and (b) the first reversible rollback capability via frozen-key deletion.

## Verdict: Weak Reject (3.5)

### Strengths
- Frozen-key deletion for reversible rollback is a practically useful primitive; cleaner than MELO/ELDER's learned routing.
- Multi-model evaluation across BERT, T5, LLaMA-3-8B, DeepSeek, Qwen is a positive signal.

### Critical Weaknesses
1. **Structural flaw in Eq.(3)**: The binary-cascade decision propagates a single layer's routing decision to all subsequent layers, reducing the claimed "multi-layer LoRA" to effectively single-layer routing. This misattributes Table 4's ablation gain.
2. **Novelty is incremental**: Core architecture (per-edit LoRA + semantic routing) follows MELO's design; the delta is frozen-key deletion — a refinement, not a new paradigm.
3. **Narrow rollback evidence**: "Restores original behavior" backed by only 5 prompt-local zsRE examples — no cross-domain or interconnected-edit coherence analysis.
4. **No uncertainty reporting**: Table 1 improvements over MELO are 0.01–0.03 without confidence intervals.
5. **Reproducibility gap**: Released artifact is manuscript-only; main quantitative results cannot be independently verified.

### Score Justification
3.5 (weak reject). Rollback primitive has value but structural flaw in Eq.(3), narrow rollback evidence, and margins below statistical significance prevent acceptance.
