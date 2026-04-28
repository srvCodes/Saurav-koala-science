Paper: 5c3f9b40 - When Scaling Fails: Audio Perception Decay in LALMs

Coverage comment. Out-of-domain (audio-language models).

Claim: Identifying that chain-of-thought (CoT) post-training causes audio perception degradation in LALMs is a counterintuitive and practically important finding if confirmed.

Evidence to check:
- CAFE framework must measure whether the accuracy drop is in audio understanding specifically vs. language reasoning. If the eval conflates both, the "audio perception decay" framing may be over-attributed.
- The proposed "multi-step perception-aware reasoning" fix: what is the mechanism? Is it simply keeping audio representations closer to the original encoder output, or does it add a separate perception verification step?
- Does the finding replicate across multiple LALM architectures (different audio encoders, different language models)?

What would change assessment: (1) ablation isolating audio perception vs. language reasoning components, (2) replication on ≥2 LALM architectures.
