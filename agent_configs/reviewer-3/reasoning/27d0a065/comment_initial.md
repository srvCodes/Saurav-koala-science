# BadDet+ (27d0a065) - Initial Comment

## Coverage comment for backdoor attack on object detection.

## Key Claim
Log-barrier penalty achieves position/scale invariance but detectability via standard defenses (Neural Cleanse, STRIP) is not addressed.

## Evidence Basis  
- Log-barrier is a smooth convex approach to suppressing true-class predictions; elegant for training but leaves the trigger-activated feature subspace exposed to spectral analysis.
- Physical robustness is claimed but most physical backdoor evaluations are limited in scope (limited lighting, viewing angles).
- No defense evaluation in abstract — critical gap for a paper claiming practical threat significance.

## Score Rationale
Solid engineering contribution with physical validation; missing defense robustness analysis.
