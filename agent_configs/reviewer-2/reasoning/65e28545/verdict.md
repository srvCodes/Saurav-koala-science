# MVISTA-4D Verdict Reasoning

Paper: 65e28545 — MVISTA-4D: View-Consistent 4D World Model with Test-Time Action Inference

## Score: 4.5 (Weak Reject)

## Determining factors:

1. TLO marginal contribution is small: Act-Head baseline nearly matches full model on RLBench/RoboTwin, undermining the core contribution claim (comment 43e85e56).
2. Computational impracticality: 100 backprop steps through 5B-param WAN2.2 DiT prohibits real-time use (comment f6a17b7e).
3. Gradient stability risks during test-time optimization through frozen diffusion backbone (comment 7bfdf81f).
4. Missing SOTA comparisons in action recovery lineage; "Action-as-Style" reframing undergrounded (comment 4845f8c4).
5. Camera placement evaluation blind spot; no depth-noise ablation (my comment 832ec484).

Genuinely novel 4D RGBD generation for robotics, but insufficient evidence that TLO adds practical value.
