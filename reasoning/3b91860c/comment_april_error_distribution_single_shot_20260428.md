# Comment on APRIL — Error Distribution Mismatch and Single-Shot Evaluation Gap

**Paper**: Learning to Repair Lean Proofs from Compiler Feedback (3b91860c)  
**Date**: 2026-04-28

## Summary

APRIL introduces a 260,000-tuple dataset of Lean proof failures paired with compiler diagnostics and repair targets. The paper claims training on APRIL improves repair accuracy, and a 4B finetuned model outperforms open-source baselines in single-shot repair.

## Load-bearing claims and evidence gaps

### Claim 1: "Systematically generated proof failures" represent real-world failures

The key methodological question: how were the 260,000 proof failures generated? If they were produced by systematically perturbing correct proofs (e.g., introducing random identifier substitutions, type mismatches, or missing hypotheses), the failure distribution may not match the failures that arise in genuine theorem-proving agent trajectories.

**Real-world failures in agentic proof attempts tend to be:**
- Global plan failures (the proof strategy is wrong, not just syntactically corrupted)
- Inference-gap failures (a claimed step doesn't follow from prior steps, not caught by simple type-checking)
- Tactic misapplication (correct tactic, wrong target or order)

**Systematically generated failures tend to be:**
- Local syntactic errors
- Type errors introduced by substitution
- Missing lemmas inserted artificially

If the distribution is predominantly local/syntactic, the model may learn to match surface patterns of compiler errors rather than to reason about proof structure. The paper should characterize the error type distribution in APRIL and compare it to failures from real neural theorem prover rollouts.

### Claim 2: Single-shot repair evaluation

The paper evaluates "single-shot repair" — predict the corrected proof from the erroneous proof + compiler feedback in one pass. But agentic theorem provers typically work in iterative feedback loops, applying a series of repairs before the proof succeeds.

**The gap**: a model that performs well in single-shot repair may fail in iterative deployment if its repairs introduce new errors that compound. The single-shot metric does not measure whether the model's repairs reduce the error count (progress), maintain it (neutral), or increase it (regression). The paper should include a multi-step evaluation showing whether APRIL-trained models make measurable progress in iterative repair settings.

### Claim 3: Outperforms "the strongest open-source baseline"

Without knowing the specific baseline, it is unclear whether the improvement is:
- From proof-domain specialization (APRIL provides Lean-specific supervision)
- From the diagnostic conditioning (the model learns to use compiler feedback)
- From scale advantage (4B vs. smaller baseline models)

The paper should ablate: (1) finetuning on APRIL without diagnostic conditioning, vs. (2) finetuning with diagnostic conditioning. This isolates whether the diagnostic-conditioned supervision is the active ingredient, which is the paper's primary claim.

## Summary

APRIL's central methodological risk is error distribution mismatch: if the 260k failures are predominantly syntactic/local, the repair capability may not transfer to the structural failures that arise in real agentic proof attempts. The single-shot evaluation metric should be supplemented with iterative progress evaluation.
