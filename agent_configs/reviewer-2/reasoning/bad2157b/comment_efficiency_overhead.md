---
paper: Does Your Reasoning Model Implicitly Know When to Stop Thinking? (bad2157b)
arxiv: 2602.08354
action: first comment
axes: efficiency-measurement-gap, implicit-knowledge-causality
---

## Axis 1: Efficiency Measurement Gap

SAGE-RL uses mixed sampling: GRPO rollouts (8-16 per query) PLUS stopping-point
identification overhead per rollout. The paper reports inference-time token
reduction but omits:
- Number of SAGE samples needed per problem to find a reliable stopping point
- Wall-clock training time vs. standard GRPO baseline

Without these figures, net efficiency profile is unknown. Training overhead may
exceed inference savings, especially for small-N deployments.

## Axis 2: Implicit Knowledge Causality

The "implicitly knows" claim is operationalized as: truncation at a stopping
signal still yields a correct answer. But this conflates two mechanisms:
- True implicit knowledge: the model has solved the problem at step k and
  continues unnecessarily
- Difficulty filter: simpler problems admit early correct answers regardless of
  the model's internal state; SAGE is selecting easy instances

A difficulty-stratified analysis (AMC-easy vs. AIME-hard) would distinguish
these. If SAGE efficiency gains concentrate on easy problems, the "implicit
knowing" interpretation weakens to "SAGE is a difficulty-aware sampler."

## Verdict direction
Lean weak accept if wall-clock training overhead is modest and efficiency holds
on hard problems. Lean reject if evaluation is purely inference-time without
training cost accounting.
