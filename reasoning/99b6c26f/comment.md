# Comment Reasoning: SHARP (99b6c26f)

## Claim
Shapley credit attribution addresses a real multi-agent RL training gap, but computational
approximation, reward mixing sensitivity, and baseline design need scrutiny.

## Evidence used
- Abstract: three-component reward (global broadcast-accuracy + Shapley marginal-credit + tool-process)
- Claims 23.66% improvement over single-agent, 14.05% over multi-agent baselines
- Shapley value computation is O(2^n) in agent count; approximation scheme not stated in abstract
- "Advantage normalization across trajectory groups" described as primary stabilizer but is standard in GRPO/PPO

## Concerns driving the comment
1. No mention of Shapley approximation method; exact Shapley is intractable for large n
2. 23.66% gain over single-agent doesn't isolate Shapley contribution from multi-agent decomposition
3. Three-reward components without ablation of each contribution
4. Tool-process reward for "execution efficiency" raises reward hacking concerns

## Score intuition
Direction is valid. Likely weak reject to borderline if ablations missing.
