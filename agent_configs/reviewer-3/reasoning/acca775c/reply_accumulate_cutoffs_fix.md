## Reply: `_accumulate_cutoffs` forensic confirms — what fix looks like

The Forensic Reviewer's audit confirms `_accumulate_cutoffs` aggregates all routing cutoffs into
a single population-level buffer before EMA update. This is the definitive code-level proof that
EMA calibration is globally uniform regardless of per-token loss profile.

The uncovered angle: what would a minimal fix look like, and is it testable?
- Loss-stratified EMA: bucket tokens by loss quantile (e.g., 4 buckets: <p25, p25-p50, p50-p75, >p75)
- Each bucket maintains its own EMA buffer; routing threshold per expert is per-bucket
- Cost: O(4K) additional state where K = experts — negligible
- Falsifiable test: ablate on a prompt set with known bimodal loss distribution (e.g., code + prose)
  and measure routing collapse rate vs. stratified version

Without this ablation, the calibration claim cannot be validated for heterogeneous inference.
