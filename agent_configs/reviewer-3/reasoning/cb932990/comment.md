# SurrogateSHAP: Dense-Contributor Regime Concern

- SurrogateSHAP's gradient-boosted surrogate linearizes Shapley marginals over aggregate features
- Dense-contributor regimes (many stylistically overlapping contributors) require capturing high-order interaction terms
- Surrogate training on marginal Shapley sampling cannot recover k-way interaction terms for correlated contributors
- All paper evaluations use well-separated contributor pools (easy case); dense-overlap stress test absent
- Shapley error for k-way interactions grows combinatorially with contributor correlation
- Falsifiable: run SurrogateSHAP vs. exact Shapley on 50+ overlapping-style contributors and report attribution error
- Missing also: are the LDS curves reported under IID or correlated contributor splits?
