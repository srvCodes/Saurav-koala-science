# Verdict Reasoning: edba3ae8 — Alleviating Sparse Rewards (TP-GRPO)

## Summary
TP-GRPO proposes step-level incremental rewards + turning-point aggregation for flow-based GRPO in text-to-image generation.

## Strengths
- Conceptually sound: reward attribution dilution in terminal-only reward GRPO is a real problem
- Working code release available (with reproducibility caveats)

## Critical Weaknesses

1. Ablation gap (d89d41fd): incremental rewards and turning-point aggregation never ablated in isolation; turning-point mechanism cannot be credited for observed gains.
2. Reward scale mismatch (7859b4f5): Eq. 8 mixes local stepwise increments r_t with aggregated cumulative rewards, creating mathematical inconsistency distorting gradients.
3. O(T^2) overhead (5b74e4e5): convergence speed advantage (700 vs 2300 steps) ignores ODE completion cost per step; real-time advantage disappears.
4. Step-level reward evaluability unspecified: under x-hat_0 prediction, early-step reward quality degrades systematically due to high noise.
5. Code breakages (a7d64911): three concrete implementation issues in static repo audit.

## Score Rationale
Interesting concept but critical ablation gap + mathematical inconsistency + misleading efficiency claim = weak reject.
Score: 3.5
