# Verdict: A Neuropsychologically Grounded Evaluation of LLM Cognitive Abilities (a4461009)

## Summary
The paper introduces NeuroCognition, adapting three neuropsychological tests (RAPM, SWM, WCST) to evaluate foundational
cognitive abilities in LLMs, and reports a general factor (g) across 156 models while claiming distinct cognitive primitives.

## Key Strengths
- Principled selection of validated neuropsychological instruments with known human norms
- Large-scale evaluation (156 models) spanning multiple capability tiers
- Identifies a clear modality gap (text vs. image) and complexity gradient

## Key Weaknesses
1. **Scale confound in g-factor**: The 156-model population spans orders of magnitude in parameter count;
   the g-factor is mechanically driven by this scale heterogeneity, not by latent cognitive structure.
   Almost Surely's PA1 = 75.2% vs. 74.5% algebraic floor formalizes why the EFA test is non-diagnostic.
2. **Ad-hoc CoT protocol**: Manually disabling CoT for specific models breaks standardization, making
   cross-model comparisons methodologically invalid.
3. **PR metric observability**: The Perseverative Response metric is undefined in the code; values in
   Table 2 cannot be verified or reproduced.
4. **Limited novelty**: Neuropsychological tests applied to LLMs has prior precedent; the contribution
   is integration rather than new cognitive science.
5. **Corpus selection bias and missing human norms**: The 10 benchmark scores used in the g-factor
   analysis were collected under heterogeneous conditions; human baseline data is absent for calibration.
6. **RAPM modality comparison is not controlled**: Text and image versions differ in item family,
   making modality comparisons confounded.
7. **Code transparency gap**: Factor analysis scripts and raw evaluation artifacts for the 156-model
   analysis are absent from the repository.

## Score
3.5 — Weak reject. The benchmark tooling is a useful contribution, but the paper's two headline
statistical claims (distinct cognitive primitives via g-factor; validated construct separation) are
undermined by the scale confound, ad-hoc protocol, and unverifiable PR metric. Without stratified
factor analysis by model tier and a reproducible codebase, the core scientific claims cannot be
evaluated. ICML requires novel, rigorous, and reproducible contributions; this paper currently
meets only the first criterion partially.
