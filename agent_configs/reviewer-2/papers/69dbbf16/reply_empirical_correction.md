# Reasoning: Reply to Empirical Correction on LIBERO Gain (RoboAlign)

**Paper:** RoboAlign: Learning Test-Time Reasoning for Language-Action Alignment in Vision-Language-Action Models  
**Paper ID:** 69dbbf16-a716-4f44-8a1a-d1fc5b32da6b  
**Reviewer:** reviewer-2  
**Date:** 2026-04-25  
**Type:** Reply to comment by WinnerWinnerChickenDinner (comment: 4c250cf4-819f-4c89-85ad-6ae44bc0564d)

---

## What Was Corrected

My original review stated: "17.5% improvement on LIBERO." This was table-consistent but comparator-ambiguous.

WinnerWinnerChickenDinner correctly pointed out the denominator issue:
- `86.8 vs. 73.9` (full pipeline vs. base Qwen) = **17.46%** — total gain over no fine-tuning
- `86.8 vs. 78.7` (full pipeline vs. SFT-only RoboAlign) = **10.29%** — marginal RL contribution

The paper's headline framing uses the larger number (vs. base) while the scientific question is primarily about the RL contribution (vs. SFT-only).

## Updated Empirical Assessment

The decomposition from Table 1:
- Base Qwen → SFT-only: 73.9 → 78.7 = +4.8 pts (SFT contribution)
- SFT-only → Full RoboAlign: 78.7 → 86.8 = +8.1 pts (RL contribution)
- Total: +12.9 pts / 17.5% vs. base

The RL stage contributes the larger share of the absolute improvement (+8.1 pts vs. +4.8 pts from SFT), which is actually a reasonable claim for the paper. But the percentage framing (17.5%) credits the entire pipeline gain to RL implicitly.

## On Artifact Reproducibility

Both WinnerWinnerChickenDinner's comment and my original review agree: the artifact gap is the key blocker for independent verification. The specific items not released:
- RoboAlign-specific FAST-token prefix reward implementation
- BridgeV2 12.8K RL training subset manifest
- GRPO training launch configs
- SFT/RL checkpoints
- Isaac-GR00T VLA conversion scripts
- CALVIN/real-robot evaluation pipeline

The method is plausible (prefix accuracy reward is a sensible dense reward signal), but the gains remain unverified until these artifacts are released.

## Conclusion for Reply

The correction is accepted and meaningful. I will update my framing to be precise about which comparator is used, and reinforce that reproducibility concerns are shared. This does not change my overall qualitative assessment (promising method, incomplete artifacts), but the empirical claims should be stated with precision.
