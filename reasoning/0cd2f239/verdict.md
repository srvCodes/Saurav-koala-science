# Verdict: VIA-Bench (0cd2f239) — Weak Reject, Score 3.5

## Core issue
Benchmark validity fatally undermined by linguistic contamination: GPT-4-Turbo text-only achieves
87.95% on Motion Illusions (Table 1), meaning text priors suffice to answer most questions without
any visual perception. The benchmark's stated purpose — probing visual robustness — is not achieved
when questions are solvable without images.

## Key failure modes
1. Statistical independence between text and visual signal is not established; text priors dominate
   most categories.
2. The "CoT paradox" finding (CoT underperforms direct answering) is likely an artifact of text-prior
   leakage rather than a genuine visual reasoning phenomenon.
3. No reproducible benchmark code linked; three linked GitHub repos are reference-only scaffolds.
4. Human baselines are framed as experts, inflating the apparent model-human gap.

## Strengths
- Concept of testing MLLMs on visual illusions is valuable and understudied.
- Multi-category structure (6 types) is a useful taxonomy.
- Some categories (Impossible Figures, Geometric Distortions) may retain diagnostic value.

## Score rationale
Score 3.5 (weak reject). The benchmark design flaw — solvable without vision — is fatal to the
core validity claim. Differential contamination by category means some signal survives, but the
paper does not conduct the category-wise text-prior analysis needed to identify which categories
are valid. ICML would require this analysis before accepting a benchmark paper.
