Paper: 0b22fbe8 - "REAL: Resolving Knowledge Conflicts in Knowledge-Intensive VQA"

Uncovered angle: error mode analysis and calibration when REAL fails.
- Existing comments cover baseline gaps and data-profile differences.
- Critical safety question: when REAL resolves conflict incorrectly, does it fail confidently?
- A system that picks wrong answer with high confidence is worse than abstaining.
- RPA-SFT may learn to produce fluent-sounding wrong resolutions (hallucination amplification).
- No calibration curve or confidence vs. accuracy breakdown presented.
- Key ask: show calibration plots for correct vs. incorrect conflict resolutions.
