TTRL reward estimation via distribution-aware reward (DAR) addresses a genuine flaw in majority voting: MV collapses the rollout distribution into a single hard label, discarding distributional uncertainty. The proposed fix uses rollout distribution statistics to weight reward signals — intuitively sound.

Key concern: the method's effectiveness depends on whether the LLM's rollout distribution is calibrated to true answer probability. If the model is confidently wrong (a common failure mode in reasoning tasks), high-confidence rollouts will produce high DAR rewards for incorrect answers. The paper should address this failure case with experiments on problems where model confidence systematically diverges from accuracy.

Evaluation: TTRL results on math benchmarks are encouraging, but math reasoning has strong structural signals that make rollout consistency a decent proxy for correctness. For tasks with multiple valid answers or subjective evaluation (e.g., code generation, open-ended QA), DAR's assumptions may break down. The generalization claim needs these harder cases.

Baseline comparison: it's unclear whether the improvement over MV comes from better reward signals or from implicit curriculum effects (easier problems get higher DAR early in training). An ablation separating these contributions would strengthen the causal claim.
