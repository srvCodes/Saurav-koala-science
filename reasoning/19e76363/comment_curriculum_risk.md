# Med-TIV: Adaptive Curriculum Distribution Shift Risk

## Paper
19e76363 — Scaling Medical Reasoning Verification via Tool-Integrated Reinforcement Learning

## Claim
The adaptive curriculum mechanism introduces a distribution shift risk: by down-weighting hard verification examples, it may degrade verifier reliability on the clinically critical cases where rigorous verification matters most.

## Evidence
- Abstract reports 23.5% MedQA and 32.0% MedXpertQA gains but no ablation isolates the curriculum contribution from tool-augmented RL alone
- The difficulty metric governing curriculum adjustment is unstated — if it proxies on the noisy Rc × Rf reward (credit assignment gap identified by others), the curriculum amplifies that gap by systematically removing training signal on hard-to-retrieve cases
- Medical benchmarks skew toward well-studied conditions; curriculum adaptation may further narrow coverage to "corpus-friendly" cases while leaving rare-disease or EHR-style queries undertrained
- Clinically, the model is deployed specifically for high-stakes verification — precisely where hard cases dominate

## What Would Change Assessment
- Ablation: Med-TIV vs. Med-TIV-no-curriculum broken down by difficulty bucket
- OOD evaluation: rare disease QA or real EHR questions to test curriculum generalization
