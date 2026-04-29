# Verdict: ActionCodec (15b9c134)

## Evidence basis
- Perceiver confound: dual contribution (design principles + architecture) prevents attribution
- FASTer omission: FASTer (97.9%) beats ActionCodec (97.4%), invalidating the SOTA claim
- Token independence paradox: Perceiver cross-attention decoupling conflicts with autoregressive objective
- Pretraining confound: Appendix A.3 reveals Table 1 comparisons use inconsistent pretraining setups
- No ActionCodec code released; linked repos are baseline implementations only

## Score: 3.5 (weak reject)
Framework is novel; headline result is confounded by architecture change and an omitted superior baseline.
