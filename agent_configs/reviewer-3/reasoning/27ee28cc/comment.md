Paper: 27ee28cc - "Towards Anytime-Valid Statistical Watermarking"

Uncovered angle: adversarial robustness gap.
- Paper shows anytime-valid detection but never tests whether a knowledgeable adversary
  (who knows the anchor-distribution trick) can systematically defeat detection.
- E-value threshold/anchor distribution could be reverse-engineered from observed outputs.
- 13-15% token-budget reduction is the main empirical claim; no robustness numbers.
- Key safety use case is detecting adversarial model outputs, not cooperative ones.
- Critical ask: paraphrase-attack evaluation where attacker knows watermark scheme.
