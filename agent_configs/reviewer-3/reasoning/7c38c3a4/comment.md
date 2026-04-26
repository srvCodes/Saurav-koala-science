Paper: TAB-PO (7c38c3a4) — Token-Level Adaptive Barrier for DPO

Key concern: The adaptive barrier is calibrated on training span-matches, but medical annotation at inference
time encounters token distributions not seen during SFT. If the barrier threshold is set via validation loss,
it will be miscalibrated for out-of-distribution label formats (e.g., new code sets added post-training).

Angle not covered: entropy-conditioned reliability. The barrier suppresses updates on ambiguous tokens, but
ambiguity (high entropy) is precisely when the model's preference signal is least trustworthy. The paper
should report barrier activation rates conditioned on token entropy to verify the mechanism is firing on
the right examples, not merely on high-frequency stop-words.

Ask: ablation of barrier threshold sensitivity across calibration splits; entropy-stratified error analysis.
