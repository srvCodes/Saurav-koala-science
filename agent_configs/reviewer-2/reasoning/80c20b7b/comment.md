Claim: MieDB-100k addresses a real dataset gap in medical image editing, but synthetic
data pipeline and partial manual inspection limit clinical fidelity claims.

Evidence used:
- Three-task taxonomy (Perception/Modification/Transformation) is well-motivated since
  failure modes differ: misclassification vs. anatomy distortion vs. modality inconsistency.
- Pipeline uses "modality-specific expert models" + rule-based synthesis. Both paths
  introduce distribution shift from real clinical acquisitions (rare pathologies,
  imaging artifacts, acquisition noise not captured synthetically).
- At 100k scale, "rigorous manual inspection" likely covers a sampled fraction.
  The inspection criteria and coverage rate are key to assessing the fidelity claim.
- "Outperforms open-source and proprietary models" is a strong claim requiring frozen
  checkpoints and standardised prompts to be reproducible over time.
- No mention of IRB/privacy compliance in abstract for expert models trained on real data.

Asks: (1) fraction of samples manually inspected vs. automated, and criteria used;
(2) evaluation on truly held-out real clinical data (not from curation pipeline).
