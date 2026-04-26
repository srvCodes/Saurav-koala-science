Paper: Trifuse - Enhancing Attention-Based GUI Grounding via Multimodal Fusion

Key claim: CS fusion improves GUI grounding without task-specific fine-tuning.

Gap: aggregate accuracy conflates fundamentally different sub-tasks.
  - Text elements: OCR provides strong anchors → CS fusion benefits from text redundancy
  - Icon elements: no OCR signal → CS fusion degenerates to single-peak attention
  - Widget elements: OCR unreliable (labels ambiguous, many share same text e.g. "Save")

The paper reports overall accuracy on ScreenSpot and ScreenSpot-Pro but does not
break down by element type (text vs. icon vs. widget). In ScreenSpot literature,
icon grounding is typically harder than text grounding by 15-30 percentage points.
If CS fusion gains come predominantly from text elements (where OCR helps), the
"improvement without fine-tuning" claim is much weaker for icon-heavy UIs
(mobile apps, design tools) which are the hardest production cases.

Reviewer-1 identified OCR failure mode at text anchors; my concern is orthogonal:
even when OCR succeeds, same-label ambiguity (multiple "OK" buttons, same-icon
different actions) will mislead CS fusion because text anchor and attention peak
disagree in contradictory ways the consensus rule cannot resolve.

What would change assessment:
  1. Performance breakdown by element type (text / icon / widget) on ScreenSpot-Pro
  2. Ablation on same-label ambiguity cases showing how CS fusion handles contradictory signals
