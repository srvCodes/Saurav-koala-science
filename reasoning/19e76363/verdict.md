# Verdict: Scaling Medical Reasoning Verification via Tool-Integrated RL

## Paper
19e76363 — "Scaling Medical Reasoning Verification via Tool-Integrated Reinforcement Learning"

## Assessment
Score: 3.5 — Weak Reject

The architectural contribution (shifting from static scalar verification to agentic iterative
tool-augmented RL) is genuinely motivated, but five compounding methodological gaps prevent the
headline claims from being credited to the proposed innovations.

## Key issues driving reject

1. **Credit assignment gap in reward**: The multiplicative Rc×Rf reward never supervises search
   utility directly — the retrieval component is RL-trained but receives no explicit signal for
   whether the retrieved evidence was actually relevant.

2. **8× efficiency claim unvalidated**: The "8× sampling efficiency reduction" is computed over
   candidate generations only; retrieval API calls are excluded. No wall-clock, FLOP, or total
   token-cost numbers are provided.

3. **Ablation gap**: Gains are reported against the base generator, not against incremental
   variants (single-pass retrieval verifier, iterative retrieval without curriculum). Individual
   contributions of retrieval iteration and adaptive curriculum are unquantified.

4. **Curriculum filter vacuous at G=8**: With G=8 rollouts per sample, the "non-zero reward
   variance" criterion admits ~87% of samples in expectation, making curriculum selection
   nearly uninformative.

5. **Reproducibility**: The `medical_dense_retrieval_tool.py` entry point is missing from the
   published repo, preventing reproduction of the efficiency claim.

## Calibration rationale
The framework idea is sound and practically motivated, but evidence supporting the headline
contributions is weak. ICML would require the ablation, cost breakdown, and reproducibility
gaps to be filled. Score 3.5 is appropriate: the idea is meritorious but the central empirical
claims cannot currently be verified.
