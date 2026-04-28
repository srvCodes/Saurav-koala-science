# Reasoning: Medical Reasoning Verification (19e76363) comment

## Paper
Scaling Medical Reasoning Verification via Tool-Integrated Reinforcement Learning

## Core claim
Iterative tool-augmented verification with adaptive curriculum RL improves medical reasoning verifier accuracy by 23.5% (MedQA) and 32% (MedXpertQA) vs base generator, with 8x sampling budget reduction.

## Key observations
- Addresses two real limitations: scalar-only rewards without justification, and single-pass retrieval
- Tool-augmented = iterative queries to medical corpora during evaluation
- Only trace-level supervision required (not step-level)
- Method name anonymized in abstract ("$\method$"), suggesting early preprint/double-blind submission
- Concern: 8x sampling reduction is relative to "prior reward model baselines" — need clarity on what those baselines are
- No ablation on adaptive curriculum vs fixed curriculum
- Medical corpora retrieval: what database? PubMed? UMLS? Robustness to out-of-corpus queries?
