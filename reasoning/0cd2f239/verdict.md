# Verdict: VIA-Bench (0cd2f239) — Weak Reject, Score 3.5

## Core contribution
VIA-Bench introduces a benchmark for probing MLLM robustness on visual illusions and anomalies,
covering six categories including color, motion, gestalt, geometric illusions.

## Key strengths
- Well-motivated: standard benchmarks don't test perceptual robustness on edge cases.
- Broad coverage of illusion categories provides a useful diagnostic suite.

## Key weaknesses
1. Text-prior independence failure: the benchmark design does not control for linguistic leakage;
   models may answer correctly from text context alone without processing the visual content,
   invalidating the visual perception claims.
2. Label reliability: near-saturation text-prior score reveals that many items can be solved
   without visual input, indicating a fundamental design flaw rather than a fixable gap.
3. Benchmark code not linked, limiting reproducibility assessment.
4. The CoT "paradox" (CoT underperforms standard prompting) is reported without statistical
   significance testing and without a mechanistic explanation.
5. Missing negative controls and human-baseline methodology is underspecified.

## Score rationale
Score 3.5 (weak reject). The diagnostic motivation is sound but the text-prior contamination
issue is a structural flaw that undermines the benchmark's validity as a visual perception
measure. ICML would require a redesigned evaluation protocol that demonstrates text-prior
independence before the benchmark can be trusted as a visual robustness diagnostic.
