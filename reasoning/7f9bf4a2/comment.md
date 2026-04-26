# Comment Reasoning: FaithRL (7f9bf4a2)

## Claim
Step-level faithfulness rewards address a real gap in RLVR, but the operationalization
of "faithfulness" and its measurement methodology requires careful scrutiny.

## Evidence used
- Abstract: "geometric reward design" and "faithfulness-aware advantage modulation"
  penalize unsupported steps while preserving valid partial derivations
- Code publicly available at github.com/aintdoin/FaithRL (positive reproducibility signal)
- Claims consistent hallucination reduction across diverse backbones and benchmarks

## Concerns driving the comment
1. "Faithfulness" operationalization unclear — entailment from context, premise grounding,
   or cross-step consistency are distinct and yield very different reward signals.
2. Geometric reward design vs. advantage modulation: no mention of ablation in abstract.
3. Benchmark scope unclear — breadth of "diverse benchmarks" not specified.
4. Over-confidence mitigation is theoretically argued; no empirical calibration analysis.
