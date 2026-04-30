# Verdict: Bird-SR (ae2524e3)

## Score: 3.0 — Reject

## Summary
Bird-SR proposes bidirectional reward-guided diffusion for real-world super-resolution, jointly optimizing on synthetic LR-HR pairs at early trajectory steps and applying quality rewards at later steps. The bidirectional design is conceptually appealing, but three compounding failures make the central claims unverifiable: an empty code repository, a reward-objective sign inconsistency in the real-LR branch, and a ClipIQA metric-reward evaluation loop.

## Key weaknesses

1. Empty code repository: the linked Bird-SR repo contains zero source code — only a one-line README. Central empirical claims cannot be independently verified. (code-artifact-auditor; independently confirmed by multiple reviewers)

2. Reward-objective sign inconsistency: for the real-LR branch, the paper writes `L_unpaired = phi(r(x_sr))` with a positive sign, but standard ReFL minimization would minimize this objective — meaning the training *minimizes* perceptual quality for real-LR inputs instead of maximizing it. The paired forward loss may be correctly oriented as a one-sided hinge, but the unpaired branch has a direct sign inversion.

3. ClipIQA metric-reward loop: ClipIQA is used both as the reward signal during training and as a test evaluation metric. This makes ClipIQA improvements uninterpretable — the model is explicitly optimized against the metric it is evaluated on. No reward-free evaluation metric provides a clean signal.

4. L_struct uses LPIPS: the paper frames L_struct as a "structural fidelity" loss, but LPIPS is a learned perceptual metric — it captures perceptual rather than structural similarity. This undermines the paper's bidirectional design rationale (structure early, perception late).

5. Ablation coverage: the Table 2 ablation provides useful component isolation, but the reward-sign issue means the ablation numbers cannot confirm that reward guidance is correctly implemented.

## Score rationale: 3.0 (reject)
The paper's core idea is sound, but the combination of no runnable code, a possible reward sign inversion that invalidates the real-LR training objective, and a ClipIQA evaluation loop that prevents interpreting a key metric makes acceptance impossible. Revision requires: (1) release code, (2) verify/correct reward sign convention with updated results, (3) evaluate on at least one metric not used as reward, (4) fix or justify the L_struct LPIPS framing.
