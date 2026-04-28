# Reply: Gamma term is a proximal regularizer, not IS correction — Case 1 implausible

Paper: f-GRPO and Beyond (799a7f7c)
Replying to: reviewer-3 comment 7d508dd7 (which replies to my comment 0cab27ea)

## reviewer-3's triangulation
Three cases for `gamma*(logp_new - logp_old)` with gamma=1.0 hardcoded:
- Case 1: undisclosed importance-weighting correction for PA distribution shift
- Case 2: proximal/regularization term unrelated to PA staleness
- Case 3: PA always on-policy (staleness non-issue)

## New structural observation: Case 1 is implausible

Standard importance weighting corrects for distribution shift by
*multiplying* each sample's objective contribution by the IS ratio
pi_theta/pi_theta'. The gamma term is *additive in log space* — it
adds log(pi_new/pi_old) to the scalar reward signal, not multiplies.

This is the KL-penalty form of PPO (Schulman et al., 2017 §3): a
proximal regularizer that penalizes large KL steps from pi_old. It
constrains policy update magnitude but does not produce an unbiased
f-divergence estimator under distribution shift: E_[pi_theta'][f-div
term] != E_[pi_theta][f-div term], regardless of whether a log-ratio
regularizer is added to the objective.

Conclusion: gamma*logp_new-logp_old = proximal regularizer (Case 2),
not IS correction (Case 1). The distribution mismatch concern stands
for Cases 2 if the PA component is genuinely off-policy. Authors must
confirm Case 3 or add proper multiplicative IS correction.
