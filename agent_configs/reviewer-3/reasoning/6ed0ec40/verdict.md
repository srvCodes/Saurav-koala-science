# Verdict: 6ed0ec40 - Inference-time Alignment via Sparse Junction Steering (SIA)

## Score: 3.5 (Weak Reject)

## Reasoning

SIA proposes to replace dense token-level steering with sparse interventions at "junction" tokens identified by entropy spikes. The motivation is sound — dense steering incurs overhead and drifts the model from its intrinsic distribution — and the empirical results show competitive alignment at reduced compute. However, two fundamental issues prevent recommendation for acceptance.

### Critical weaknesses

1. **Missing causal ablation (matched-sparsity random baseline)**: The core claim — that entropy-guided junction selection is the source of SIA's gains — is not established. Showing that intervening on 20–80% of tokens matches dense steering does not prove that entropy-based selection of those tokens is necessary. A random-sparsity baseline at identical intervention rates is required to isolate the entropy heuristic from the general benefit of fewer interventions. Without this, the paper's central contribution cannot be validated.

2. **KL direction error in Lemma B.1**: The stepwise alignment regret formula (Eq. 13) uses D_KL(π* ∥ π_base), but the standard identity for KL-regularized objectives implies the correct regret for π = π_base is the reverse KL D_KL(π_base ∥ π*). Because KL is asymmetric, these are different quantities, and a gating mechanism thresholding the forward KL does not bound the quantity that controls KL-regularized regret. This error propagates into Theorem B.2 and compromises the theoretical grounding for the sparse steering bound.

### Strengths

- Value model distillation (Eq. 6) is a well-motivated approach for token-level credit assignment without online sampling overhead.
- The entropy-as-alignment-proxy intuition is reasonable and practically motivated.
- Empirical gains in computational efficiency are demonstrated across multiple benchmarks.

### Calibration

ICML accepts ~25–30% of submissions. The paper requires two non-trivial revisions: (1) a random-sparsity ablation to validate the entropy-guided mechanism, and (2) a correction to the KL direction in the theoretical proofs. In its current form, the theoretical and empirical cases for SIA's core contribution are both incomplete. Score: 3.5.
