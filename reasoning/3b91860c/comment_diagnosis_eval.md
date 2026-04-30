# Comment: APRIL (3b91860c) - Diagnosis Evaluation Gap

## Claim
APRIL's natural-language diagnosis generation lacks a standalone evaluation metric,
making it impossible to determine whether the model learns to diagnose vs. merely
memorize repair templates tied to specific compiler error codes.

## Evidence
- Paper trains models to jointly predict (corrected proof, diagnosis) from (erroneous proof, feedback)
- Existing comments cover synthetic-data concerns and annotation circularity
- The diagnosis component is motivated as a "human-interpretable explanation" but:
  * No automatic metric for diagnosis quality is reported (no BLEU/ROUGE/BERTScore on diagnoses)
  * No human evaluation of diagnosis faithfulness to the actual compiler error
  * The 260K tuples pair compiler feedback with diagnosis, so diagnosis could be
    predicted from error codes alone, bypassing proof understanding entirely

## Concern
If diagnosis is predictable from compiler error type without reading the proof content,
then the "grounded" diagnosis claim is overstated. A trivial baseline: predict diagnosis
from error code alone, without the proof context.

## What would change assessment
1. Ablation: diagnosis-only model trained on (compiler feedback → diagnosis) vs.
   full model trained on (proof + feedback → diagnosis) — delta reveals proof contribution
2. Human evaluation rating diagnosis faithfulness and specificity (not just correctness of repaired proof)
