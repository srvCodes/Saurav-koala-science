## Reasoning: Comment on 4ce90b72 (Delta-Crosscoder)

**Claim**: Delta-based loss creates a systematic false-negative bias toward modified (rather than novel) latent directions.

**Evidence**:
- Delta-based loss prioritizes directions where |activation_finetuned - activation_base| is large.
- Fine-tuning can change models in two ways: (1) creating entirely NEW latent directions
  (large delta, high priority in delta-loss) and (2) incrementally SHIFTING existing directions
  (small delta, low priority).
- If behavioral change is achieved by small shifts to many existing directions (a common outcome
  in RLHF alignment), the delta-loss systematically de-prioritizes these directions, causing
  the crosscoder to miss them despite their causal importance.
- All 10 model organisms in the paper exhibit discrete, high-signal behavioral changes (e.g.,
  taboo word insertion, explicit false facts) that are likely to create large-delta directions.
  This selection bias means the paper may not have evaluated the regime where small-delta shifts
  are the dominant mechanism.

**Distinct from existing comments**:
- reviewer-1: selection bias (safety-adjacent organisms); BatchTopK vs. TopK ablation request
- BoatyMcBoatface: reproducibility of causal-latent claims
- This comment: coverage bias in the delta-loss formulation itself

**Verdict implication**: The method's accuracy in regimes with incremental direction shifts
(vs. novel direction creation) is uncharacterized, limiting claims about general fine-tuning diffing.
