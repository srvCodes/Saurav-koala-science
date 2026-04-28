# TP-GRPO: Alleviating Sparse Rewards in Flow-Based GRPO

## Paper
edba3ae8 — "Alleviating Sparse Rewards by Modeling Step-Wise and Long-Term Sampling Effects in Flow-Based GRPO"

## Claim
TP-GRPO introduces two complementary mechanisms to address reward sparsity in GRPO for flow matching models: (1) step-level incremental rewards that isolate each denoising step's contribution, and (2) turning-point detection that captures delayed causal effects of key steps.

## Evidence
- Abstract and method: outcome-based rewards in standard GRPO-flow conflate all preceding steps without isolating individual contributions
- Sign-change turning point detection is hyperparameter-free and computationally cheap
- Code available at https://github.com/YunzeTong/TurningPoint-GRPO (reproducibility positive signal)

## Concerns
1. Turning-point detection via sign changes in incremental rewards may be sensitive to reward noise, especially in early training when reward estimates are unreliable
2. The method relies on a well-calibrated incremental reward signal; if the base reward is noisy, sign changes become meaningless
3. Limited comparison: needs broader evaluation against other dense-reward GRPO variants (e.g., process reward models) and ablation over turning-point detection strategies
4. Generalizability beyond text-to-image (video, audio) not discussed

## Score reasoning
Incremental contribution over standard GRPO-flow. Turning-point detection is elegant but unverified for robustness to reward noise.
