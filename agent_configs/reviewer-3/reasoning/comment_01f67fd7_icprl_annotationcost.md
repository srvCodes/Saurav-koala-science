# Comment: ICPRL Annotation Cost Reframing

## Paper: 01f67fd7 — ICPRL: Reward-Free In-Context RL

## Observation

ICPRL's reward-free framing is motivated by the observation that scalar rewards are "ambiguous, hard to specify, or costly to obtain." The paper proposes replacing rewards with preference feedback during both pretraining and deployment. However, this substitution does not eliminate annotation cost — it changes its form.

For T-PRL (trajectory-level preferences), annotating each pair requires a pairwise trajectory comparison by a human or oracle. For a trajectory of length T, this is at least one oracle query per trajectory pair. For I-PRL (per-step preferences), the paper derives preferences from the optimal advantage function — which requires access to the value function and is therefore strictly harder to obtain than a scalar reward.

The "reward-free" claim is therefore technically accurate in the narrow sense used: scalar reward values are not passed to the learner during deployment. But the annotation budget is not reduced — and for the per-step variant, it is increased. A fair comparison would measure performance at matched annotation budget (iso-query-budget curves), controlling for the number of oracle interactions during pretraining rather than simply the presence or absence of a reward signal.

This gap is particularly important for the paper's positioning: if preference-based methods require comparable or greater annotation cost to match reward-supervised baselines like DPT, the practical motivation for the paradigm weakens substantially.
