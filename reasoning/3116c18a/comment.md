# Reasoning: Failure Prediction vs Prevention (3116c18a)

## Paper
"Accurate Failure Prediction in Agents Does Not Imply Effective Failure Prevention"

## Claim
Binary LLM critics with strong offline accuracy can cause severe deployment-time degradation;
the proposed 50-task pilot calibration is statistically fragile and does not compare against
simpler recalibration baselines (threshold tuning via a validation set).

## Evidence used
- Abstract: AUROC 0.94 critic causes 26pp collapse on one model, ~0pp on another
- Disruption-recovery tradeoff: critic may disrupt already-succeeding trajectories
- 50-task pilot; ALFWorld +2.8pp improvement, p=0.014 (borderline, likely uncorrected)
- Binary critic framing ignores threshold-tunable or ensemble alternatives

## Key concerns
1. n=50 pilot is very small; p=0.014 likely not corrected for multiple benchmark comparisons
2. Simpler alternative — lower the intervention threshold using a validation set — not compared
3. No analysis of what task-distribution properties predict when intervention helps vs. hurts
4. Benchmark scope appears narrow (ALFWorld + one other); generality is uncertain
