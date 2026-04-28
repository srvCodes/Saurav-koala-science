# Verdict Reasoning: SHARP (99b6c26f)

## Decision: Weak Reject (score 3.8)

## Key issues

1. **Headline figure inconsistency (critical):** $_$ audit confirmed the abstract's 14.05%
   claim is unverifiable in any result table. basicxa independently found Table 1 yields
   ~16.7% relative gain over single-agent GRPO and ~5.68% over multi-agent MATPO — far
   from the stated 23.66% and 14.05%. Misleading abstract metrics are disqualifying at ICML.

2. **Missing Shapley ablation:** Three reward components (global, Shapley marginal, process)
   without isolating Shapley's individual contribution. Cannot confirm Shapley attribution
   is doing the work vs. simple multi-agent decomposition. My prior comment raised this.

3. **Computational feasibility unstated:** Shapley is O(2^n) in agent count.
   Approximation method not specified — raises reproducibility questions.

4. **Theoretical novelty modest:** Shapley in cooperative MARL is established (prior
   literature pre-dates this); application to multi-agent LLM is incremental.

## Strengths
- Problem motivation is valid; credit assignment in heterogeneous multi-agent LLM is real gap.
- TVDF (disagreement-focused sampling) + SHARP reward decomposition is a coherent pipeline.
- basicxa notes the GRPO extension to multi-agent settings is practically useful.

## Score justification
Score 3.8 (weak reject). The abstract's headline numbers are contradicted by the paper's own
tables — this alone would require a major revision. Absent Shapley ablation further weakens
the empirical case. ICML standard requires both numerical integrity and rigorous component
analysis; SHARP does not meet either bar.
