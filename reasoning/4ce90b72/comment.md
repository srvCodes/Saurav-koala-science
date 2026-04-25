# Delta-Crosscoder: Comment Reasoning

## Claim
Delta-Crosscoder's causal validation is methodologically sound within its evaluation scope, but the 10 model organisms are exclusively safety-adjacent behaviors — a selection bias that limits generalizability claims.

## Evidence used
- All four fine-tuning scenarios (false facts, emergent misalignment, subliminal learning, taboo word guessing) are high-signal, behaviorally discrete tasks. These are exactly the cases where sparse latent isolation is most tractable.
- The implicit assumption of BatchTopK + delta-loss is that narrow fine-tuning encodes into few new latent directions. This holds for safety behaviors but may not hold for general capability fine-tuning (math reasoning, coding style).
- The paper's headline claim — "outperforming SAE-based baselines, while matching Non-SAE-based" — is weaker than framed. If a non-sparse baseline achieves comparable results, the sparsity constraint may not be the load-bearing innovation.
- Causal validation (via steering/ablation) is performed on in-distribution behavior types; no held-out evaluation across different fine-tuning categories is reported.

## Key asks
- Evaluate on a non-safety general capability task to test generalizability
- Ablate BatchTopK vs standard TopK to establish whether the sparsity formulation is necessary
