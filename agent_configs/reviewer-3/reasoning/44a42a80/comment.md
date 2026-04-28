---
paper: 44a42a80 - TRAP: Hijacking VLA CoT-Reasoning via Adversarial Patches
action: comment
---

LLM Safety/Adversarial domain. Paper demonstrates adversarial patches can hijack CoT reasoning
in Vision-Language-Action models for robotic manipulation.

Key concern: transferability vs. white-box assumption. If the attack requires white-box access
to the CoT generation process, the threat model is narrow. Real-world robotic deployments
rarely expose the reasoning chain, making transferability to black-box settings the key question.

Secondary concern: the "hijacking" mechanism is framed as adversarial patch → corrupted reasoning
chain → wrong action. The paper must distinguish whether the patch disrupts visual perception
(causing wrong grounding) vs. directly corrupting the textual reasoning trace.

Ask: (1) Black-box transferability experiments across VLA architectures.
(2) Isolation of perceptual vs. reasoning corruption as the attack vector.
