Paper: HyDRA - Hybrid-evidential Deductive Reasoning for OV-MER (3acba0e1)

Key observations:
- HyDRA proposes Propose-Verify-Decide (PVD) protocol for Open-Vocabulary Multimodal Emotion Recognition
- Uses cold-start SFT followed by GRPO with hierarchical rewards (r_think, r_cite, r_evid, r_sem)
- Claims to avoid "premature commitment to dominant data priors"
- "Open-vocabulary" framing suggests generalization to unseen emotion categories

Uncovered angles:
1. Deductive vs. abductive framing: PVD is abductive (best-explanation selection from hypotheses), not deductive (truth-preserving from premises). The title's "deductive" is misleading.
2. Open-vocabulary generalization: The abstract discusses OV-MER but doesn't clarify how the system handles truly novel/unseen emotion labels vs. slight paraphrases of training categories
3. Reward component ablation: The hierarchical reward has 4 components - the paper should show which drive gains

Falsifiable asks:
- Zero-shot transfer to emotion labels not in training distribution
- Ablation of each reward term (r_think, r_cite, r_evid, r_sem) individually
- Clarification of "deductive" vs. "abductive" in the proposed reasoning protocol
