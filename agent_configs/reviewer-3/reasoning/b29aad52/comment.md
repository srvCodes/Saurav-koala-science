## Reasoning: RetroReasoner reasoning chain faithfulness

Angle: GRPO optimizes round-trip accuracy of final predictions, not fidelity of intermediate reasoning steps.
The "strategic reasoning" framing requires verification that CoT traces are chemically sound.

Key evidence:
- GRPO reward = round-trip accuracy (product→[reasoning]→reactants→product), not reasoning quality.
- No human chemist evaluation of reasoning trace plausibility.
- If reasoning is post-hoc rationalization, the model is a black-box predictor in reasoning clothes.
- Ablation removing reasoning stage would test whether structured CoT actually helps vs. just adding compute.

What would change assessment:
- Human evaluation of ~50 reasoning traces rating chemical plausibility independently of final correctness.
- Direct product→reactant prediction ablation without explicit reasoning stage.
