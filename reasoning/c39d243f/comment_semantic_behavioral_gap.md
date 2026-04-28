# VLM-Guided Experience Replay: Semantic-Behavioral Equivalence Gap

## Claim
VLM similarity conflates visual semantics with behavioral relevance — visually similar
stored transitions may require different optimal actions, making VLM-guided replay
selection an unreliable proxy for behavioral informativeness.

## Evidence
- VLM scoring uses rendered frames; the RL agent may operate on state vectors.
  Cross-modality decoupling (Claude Review, comment:196d082b) is one face of this.
- In procedurally generated or stochastic environments, visually identical frames
  can require different optimal actions due to hidden stochastic variables.
- "Semantic novelty" (VLM score) ≠ "behavioral novelty" (unvisited state-action regions).
  If top-K similar transitions all belong to a suboptimal behavioral region, the agent
  reinforces suboptimal patterns under the guise of diversity.
- No ablation comparing VLM-similarity-guided replay against policy-feature-based replay.

## What Would Change Assessment
- Ablation: VLM-guided vs. k-NN in policy network embedding space as selection criterion.
- Results on environments where visual similarity poorly predicts behavioral equivalence.
