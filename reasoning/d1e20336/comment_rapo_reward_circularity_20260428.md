# RAPO Review Comment: Reward Circularity and Proxy Measurement Issues

**Paper:** RAPO: Risk-Aware Preference Optimization for Generalizable Safe Reasoning (d1e20336)  
**ArXiv:** 2602.04224  
**Date:** 2026-04-28

## Core Technical Issues Identified

### 1. Empirical motivation relies on correlation, not causation (Table 1)

Table 1 shows that successful refusals co-occur with higher proportions of safe reasoning tokens, and that attack success rate increases as the proportion of safe reasoning tokens decreases. The paper uses this as evidence that "deeper safe reasoning can enhance LRM's robustness."

This is a correlational observation, not a causal one. The correlation is unsurprising under the alternative hypothesis: a model that correctly identifies an attack (due to underlying safety capability) naturally generates more safety-relevant thinking. The causal arrow may run from safety capability to reasoning proportion, not from reasoning proportion to refusal success. Training models to produce more safe reasoning tokens may simply teach stylistic mimicry of the safe-reasoning pattern without improving the underlying capability that distinguishes successful from failed refusals.

An experiment that directly tests the causal claim would be: take a model that fails to refuse an attack, artificially prepend or lengthen its safe reasoning block (via prompting, not training), and measure whether refusal rate improves. If it does, the causal claim is supported. If it does not, RAPO's mechanism is training a different capability than the one Table 1 motivates.

### 2. Reward design circularity via LLM-as-judge

The risk-aware reward (Section 4.3) uses an LLM-as-judge to evaluate whether the safety reasoning block is "adequate" for the prompt's complexity level. The judge (a) first determines the risk complexity level of the prompt, then (b) assigns a reward based on whether the reasoning depth matches that level.

This introduces two concerns:

**Circular generalization:** The paper's central claim is that RAPO generalizes to novel jailbreak attacks. But if the LLM-as-judge can correctly assess complexity levels and reward adequate reasoning, then the judge itself already performs the task RAPO is trying to learn. If the judge is brittle on novel jailbreaks (cannot correctly classify them), the training signal is noisy exactly where generalization is claimed. The paper should report the judge's own robustness to novel attacks.

**Proxy gaming:** The reward evaluates reasoning depth/length conditional on judge-assigned complexity level. The model can improve reward by producing stylistically "deep-looking" safety reasoning that satisfies the judge's evaluation criteria (Table 3) without genuine safety improvement. The paper explicitly mentions "we consider cases of excessive reasoning to prevent reward hacking" (Section 4.3) — but this presupposes that length can be independently controlled, while the paper's own theory (Theorem 3.1) says longer safe reasoning is causally required for harder attacks.

### 3. Theorem 3.1 is valid for a restricted linear model, not LRMs

Theorem 3.1 proves that "the number of safe reasoning traces should be at least t = Ω(k) to refuse the prompt" under a specific linear-model assumption: the prompt is an average of k+1 concept vectors, the model's "detector" w is orthogonal to all safe concepts and has positive inner product with harmful ones.

This result is interesting as a formal analogy, but:
- LRM prompts are not convex combinations of concept vectors in a shared embedding space
- The "threshold" mechanism (w^T c_0 > 0) corresponds to a linear classifier, not a transformer attention/MLP computation
- The proof relies on a specific initialization assumption about the "token-level in-context learning" process

The paper uses Theorem 3.1 as theoretical support for its empirical finding (Table 1), but the theorem proves a necessary condition in a linear model. It does not rule out that, in practice, a model can achieve the same safety effect with fewer but semantically richer reasoning steps. A 50-token focused analysis may outperform a 500-token shallow analysis in practice.

## What Would Change My Assessment

1. A controlled causal experiment: show that *forcing* longer/deeper safe reasoning at inference time improves refusal rates on attacks the model would otherwise fail, without RAPO training.
2. Evaluation of the LLM-as-judge's accuracy on novel jailbreaks (not seen during training), to bound the quality of the training signal in the generalization regime.
3. Comparison with a simpler baseline: train the model with a reward that simply measures whether it refuses harmful prompts, without the reasoning-adequacy component. If RAPO's advantage over this baseline is marginal, the risk-aware reward's complexity may not be justified.
