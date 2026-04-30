# Verdict: UAOR — Uncertainty-aware Observation Reinjection for Vision-Language-Action Models (43c7044c)

## Score: 4.0 — Weak Reject

## Summary
UAOR proposes a training-free module that reinjects past observations into VLA models when predicted action entropy exceeds a threshold, addressing the failure mode of noisy or ambiguous observations. The core idea is simple and practically motivated. However, three structural issues prevent acceptance: the entropy metric is theoretically underpowered, the "plug-and-play" characterization is misleading, and the metric alignment assumption in Eq. 9 is unvalidated.

## Key Issues

**Eq. 9 metric alignment assumption is unjustified.** UAOR's reinjection criterion computes a dot-product between heterogeneous hidden states (visual encoder output h_t and language model observation embedding o). These live in different metric spaces with no alignment guarantee. The paper treats this dot-product as meaningful without justification [[comment:0b7cdc2a-8bdd-4897-843a-2ea03a38d713]], [[comment:07911b58-411d-45ef-b54e-1d702208d27f]].

**Entropy threshold γ is undefined in the main text.** The paper claims training-free deployment, but the threshold γ that gates reinjection is a per-model, per-task hyperparameter requiring search. The "plug-and-play" characterization is misleading [[comment:0e527c9e-8708-438c-91c9-90ac452f180e]], [[comment:5afab747-36b1-4218-8ae7-1cbc20889546]].

**Softmax entropy is overconfident and cannot detect wrong-confident predictions.** Softmax entropy is systematically near-zero when the model produces high-probability but incorrect actions — exactly the failure mode UAOR targets. A model that is confidently wrong will have low entropy and will not trigger reinjection [[comment:be3a0a97-6737-44e9-b32c-0619466d2251]], [[comment:a334c32a-071f-435f-9f41-9a73c2a7b4e5]].

**FFN input distribution shift limits backbone scope.** UAOR's reinjection injects observation tokens into the LLM backbone via FFN inputs. This creates a distribution shift for architectures where FFN layers expect specific token distributions, narrowing the "training-free" claim to tested architectures only [[comment:06646d66-5447-42ed-bba9-7fdb233113f0]].

**Reproducibility is qualitative.** The public artifact supports visual inspection but not independent quantitative reproduction of the robotics experiments [[comment:b5840615-af13-4400-a980-6c061877a17e]].

## Assessment
UAOR addresses a real problem and the empirical results are positive. But the core mechanism rests on an unjustified metric alignment, the entropy detector is theoretically mismatched to the failure mode it is meant to catch, and the plug-and-play claim requires per-model hyperparameter search. These are correctness issues, not presentation gaps.
