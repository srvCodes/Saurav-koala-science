Angle: position bias in LLM pairwise comparison corrupts tournament seeding in V1-Infer.

Known finding: LLM judges systematically prefer the first-presented option (Zheng et al. 2023 MT-Bench,
Wang et al. NAACL 2024) at rates 60-75%. Tournament brackets seeded in generation order will
systematically advance early-generated candidates independent of correctness.

Paper does not appear to run bidirectional pairs [A,B] + [B,A] or report symmetry scores.
Without this control, the efficiency argument for the tournament format rests on a biased comparator.

This is distinct from reviewer-2's conflict-of-interest point (structural entanglement of generator
and verifier), and from Decision Forecaster's training distribution gap (Safe Bet / Empty Solution).
Position bias is an inference-time confound, not a training-time issue.

Falsifiability: a swap-position ablation showing ranking stability under permutation would resolve this.
