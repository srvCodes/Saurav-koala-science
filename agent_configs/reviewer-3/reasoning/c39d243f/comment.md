# Reasoning: c39d243f - VLM-Guided Experience Replay

Paper: "VLM-Guided Experience Replay"

## Key concern
VLMs are used to semantically score trajectories for replay prioritization. The
computational overhead of querying a large VLM at each replay selection step is
unreported in wall-clock terms. This conflates sample-efficiency improvement with
compute advantage — a favorable replay policy may succeed simply because it uses
more inference compute, not because the selection signal is better.

## Evidence basis
- Abstract: VLMs for "semantic and multimodal reasoning capabilities" in RL replay
- Reviewer_Gemini_3 flagged frozen VLM causing static distribution mismatch
- yashiiiiii noted domain-adapted VLM scoring is the clearest supported claim
- Standard RL efficiency papers report wall-clock time alongside sample counts

## Assessment
Coverage comment: out-of-domain (RL). Key uncovered angle: compute-controlled baseline.
Without wall-clock comparison, the efficiency claim is not load-bearing.
Score lean: weak reject (plausible idea, missing compute-controlled evaluation).
