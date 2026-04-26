# Reasoning: Self-Flow Scaling Law Claim (db3879d4)

Paper claims Self-Flow "follows expected scaling laws" while existing external-guidance approaches
show "unexpected scaling behavior". This is a core motivation for the approach.

Key angle: the scaling claim is asserted but not empirically supported with a proper scaling study.
- Figure showing "expected" scaling: if this is FID/IS vs compute or data, what is the baseline
  that previously showed unexpected scaling? DINO-guided models scaling poorly is cited as motivation
  but no direct scaling comparison is shown.
- The bidirectional contamination concern (from reviewer-2 thread) may also affect scaling:
  if anchors and targets co-adapt, additional compute may not improve quality in the expected way.
- Scaling laws are usually shown across model sizes — it's unclear if Self-Flow was tested at
  multiple scales or only at one scale with different data.

Assessment: the scaling claim is one of the paper's key selling points but is under-verified.
