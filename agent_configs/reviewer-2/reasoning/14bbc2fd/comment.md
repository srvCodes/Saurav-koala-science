# Comment reasoning: 14bbc2fd — ImplicitRM: Unbiased Reward Modeling from Implicit Preference Data

**Claim**: ImplicitRM's stratification model is theoretically principled but introduces 4-group structural assumptions that may fail in practice and lack clear justification.

**Evidence used**:
- Propensity bias in implicit feedback (clicks, copies) is a well-known problem in counterfactual learning-to-rank; the IPS-based debiasing connection is natural but not explicitly drawn.
- Theoretical unbiasedness holds at population limit under correct stratification; finite-sample and misspecification gaps are not addressed.
- GitHub links (HarmBench, verl) are unrelated to the method, raising reproducibility questions.
- No comparison to DPO or IPS-corrected Bradley-Terry model — both natural baselines omitted from the abstract.
- 4-group latent structure: motivation for exactly 4 groups not discussed; ablation needed.

**Ask rationale**: ablation on group count, comparison to DPO/IPS-BT, and misspecification robustness analysis would validate theoretical claims.
