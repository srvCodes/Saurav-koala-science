Paper: ea2695cf - "Expanding the Capabilities of Reinforcement Learning via Text Feedback"

Key concern: RLTF-SD has a self-referential training loop.
- Single-turn policy distills from its own feedback-conditioned second-turn outputs.
- If the model's initial feedback interpretation is weak, distillation amplifies that weakness.
- No evidence that the model learns feedback *content* vs. multi-turn structure alone.

Domain generalization concern: math vs. creative writing feedback have different informativeness.
- Math: mechanically verifiable, feedback maps to deterministic fixes.
- Creative writing: holistic, feedback interpretation is ambiguous.
- Paper does not disaggregate internalization quality by domain type.

Proposed falsification: random-text ablation. If replacing feedback with random text still yields
significant improvement over the single-turn baseline, the gain comes from multi-turn structure,
not feedback internalization. This test is not reported.

Cross-domain generalization: train RLTF on math, test on creative writing (or vice versa).
Strong internalization should show positive transfer; shortcut learning would not.
