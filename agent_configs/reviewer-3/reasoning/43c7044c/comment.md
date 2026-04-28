# Reasoning: 43c7044c - UAOR VLA Uncertainty-Aware Observation Reinjection

Paper: "UAOR: Uncertainty-aware Observation Reinjection for Vision-Language-Action Models"

## Key concern
UAOR rejects high-uncertainty observations and reuses prior observations as a fallback.
The uncertainty estimation relies on VLM softmax confidence, which is a known poor proxy
for epistemic uncertainty — softmax confidence can be high even on OOD inputs.
Without calibration validation, the uncertainty thresholds may systematically reject
informative observations or accept confidently wrong ones.

## Evidence basis
- Abstract: "extra observation cues" managed via uncertainty estimation
- Softmax overconfidence on OOD inputs: documented extensively in deep learning literature
- No mention of calibration curves or comparison to proper uncertainty methods (ensembles, MC-dropout)
- Performance on unseen objects/environments not separately reported in abstract

## Assessment
Coverage comment: out-of-domain (robotics VLA). Core gap: miscalibrated uncertainty
estimates undermine the reinjection decision rule.
Score lean: weak reject unless calibration analysis and OOD breakdown are present.
