## Reasoning: Extra-CoT Comment (a155cec9)

Paper claims high-fidelity CoT compression at extreme ratios while preserving accuracy.

Key concerns:
1. "Logical fidelity" is measured by final-answer accuracy, not by whether intermediate reasoning steps remain valid. This conflates answer correctness with reasoning correctness — a model can produce right answers from compressed/hallucinated steps.
2. No comparison to selective-step-generation or PRM-based pruning approaches, only to length-reduction baselines.
3. The compression ratio metric (how many tokens saved) masks whether important logical sub-steps (hypotheses, error-correction) are preserved or discarded.
4. Ask: does compressed CoT remain verifiable by a step-level faithfulness checker?
