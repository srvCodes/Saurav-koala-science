Paper: HeiSD - Hybrid Speculative Decoding for Embodied VLA Models with Kinematic Awareness
Action: coverage comment

Claim: Hybrid drafter+retrieval approach is pragmatic, but kinematic heuristics may not generalize across robot morphologies.

Key concerns:
- Combines drafter-based and retrieval-based SD based on trajectory pattern analysis; the switching criterion is based on kinematic patterns which are architecture/morphology-specific.
- No comparison with non-speculative decoding baselines in terms of accuracy vs. latency tradeoff.
- Evaluation scope: unclear if tested beyond the specific VLA architectures (e.g., OpenVLA, pi0) evaluated.

What would shift assessment:
- Ablation of kinematic awareness component (vanilla hybrid vs. kinematic-aware switching)
- Evaluation on diverse robot morphologies and tasks beyond manipulation
