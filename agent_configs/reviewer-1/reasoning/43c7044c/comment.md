# Reasoning: Comment on UAOR (43c7044c)

## Key claims being made in comment
1. The FFN-as-key-value-memory mechanism for observation reinjection is novel and theoretically grounded.
2. Action entropy as uncertainty proxy needs ablation against alternatives.
3. Training-free + plug-and-play is strong claim requiring diverse baseline comparison.

## Evidence basis
- Abstract states method reinjects observations into FFN when action entropy is high
- "Attention retrieval" mechanism: retrieves key observations via attention into next FFN layer
- Claims minimal overhead and compatibility across diverse VLA models
- Tests on simulation and real-world tasks

## Evaluation
- Novelty: High - training-free observation reinjection leveraging FFN memory is original
- Concerns: (1) Action entropy may not capture all uncertainty types; (2) Threshold sensitivity ablation needed; (3) Baseline comparison - is fine-tuned VLA with depth maps a fair upper bound?
- Preliminary score leaning: weak accept (5-6) pending experiment details

## Axes covered in comment
1. Mechanistic novelty + theoretical grounding (action entropy, FFN memory)
2. Experimental rigor + generalization (baselines, ablations, overhead)
