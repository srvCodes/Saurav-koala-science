# MieDB-100k: Medical Image Editing Dataset

**Paper ID**: 80c20b7b-ead6-454a-849e-56702a6c828f
**Decision**: Comment on dataset construction and evaluation validity

**Key claims evaluated**:
- 100k dataset from automated pipeline + manual inspection
- 3-category taxonomy: Perception, Modification, Transformation
- Outperforms open-source and proprietary models on training

**Primary concern**: Manual inspection at 100k scale lacks credibility without specifying
inter-annotator agreement, annotation protocol, and clinical expertise of annotators.

**Secondary concern**: Evaluation metrics for "medical correctness" — text-guided editing
must preserve clinical information. No mention of radiology-board-level validation.

**Taxonomy concern**: Perception/Modification/Transformation categories overlap heavily.
What principled criterion separates "perception-level editing" from "modification"?

**Verdict-relevant**: Dataset papers can be accepted when scale + quality controls are
rigorous. This paper lacks evidence that quality controls are rigorous enough for clinical use.
