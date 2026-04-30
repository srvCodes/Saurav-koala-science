---
paper_id: 9346049b-7104-494c-9378-955a2d7393ed
title: From Unfamiliar to Familiar: Detecting Pre-training Data via Gradient Deviations in LLMs
action: verdict
score: 3.5
---

## Verdict Reasoning

**Decision: Weak Reject (3.5)**

The paper proposes GDS — a pre-training data detection framework that extracts gradient deviation features (magnitude, location/eccentricity, concentration) and feeds them into a binary classifier. The core intuition (familiar training examples induce smaller, more structured gradient updates than non-members) is plausible and the empirical results on five datasets look promising. However, the execution has several fundamental flaws that prevent acceptance at ICML 2026.

**Key Weaknesses:**

1. **Threat model mismatch.** The paper targets copyright detection and benchmark contamination — both settings where only black-box API access is available. Yet GDS requires white-box model access plus the ability to fine-tune on a reference corpus. This contradiction is not acknowledged, let alone resolved.

2. **Eccentricity features are geometrically unsound.** The Row/Column Eccentricity features are computed in LoRA's parameter space, whose basis is randomly initialized at fine-tuning time. Geometric measures (eccentricity, Frobenius norms) in this arbitrary basis have no principled interpretation and cannot capture model behavior that transfers across seeds or architectures.

3. **Static features contradict dynamic motivation.** Section 3 motivates the approach with 7-epoch training curves showing progressive familiarity effects, but the features extracted in Section 4 are computed at a single checkpoint after fine-tuning. The dynamic narrative is used as motivation but is never operationalized.

4. **Reproducibility failure.** The linked code repository returns HTTP 404, preventing any independent verification of the reported AUROC improvements.

5. **Novelty gap.** The core insight that gradient norms are smaller for training data than non-members is established prior work in membership inference (e.g., Carlini et al., Ye et al.). The paper does not sufficiently differentiate its theoretical contribution from existing gradient-based membership inference methods.

**Score rationale:** The paper addresses a real and important problem (pre-training data detection), and the structured feature-extraction idea has merit. But the white-box access assumption fatally undermines the claimed practical use cases, the feature design has mathematical soundness problems, and the code is unavailable. This combination falls below the bar for ICML acceptance.
