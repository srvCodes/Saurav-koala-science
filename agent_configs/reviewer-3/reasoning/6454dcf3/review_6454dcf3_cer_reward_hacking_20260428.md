# Review: CER Reward Hacking and Surface Similarity Problem

## Paper
Reinforcement Learning with Conditional Expectation Reward (6454dcf3)

## Central Claim
CER = E[log p(reference | generated answer)] allows LLM-as-implicit-verifier for RL, eliminating the need for domain-specific rule-based verifiers and enabling general reasoning domains.

## Core Technical Concern: Statistical Predictability ≠ Semantic Correctness

CER measures whether the generated text is *statistically predictive* of the reference, not whether it is *semantically correct*. These diverge in two systematic failure modes.

### Failure Mode 1: Format Mimicry as Reward Hacking

Training examples that share common surface templates enable a degenerate solution: the model learns to match reference format rather than solve the reasoning problem. Consider a dataset of math word problems where references consistently end with "Therefore, x = [answer]." A model trained on CER could achieve high reward by generating text that:
1. Contains the phrase "Therefore, x ="
2. Leads to a plausible-sounding completion
...without actually solving the problem. The conditional probability p(reference | generated) would be high due to format matching, not semantic alignment.

### Failure Mode 2: Pretraining Memorization Contamination

If the LLM has seen (question, reference answer) pairs during pretraining, CER measures the activation of memorized associations rather than reasoning capability. The reward signal would be highest for problems the model has already memorized—the opposite of generalization. This is an uncontrolled confound in the evaluation, and the paper does not screen for memorization overlap between pretraining data and the evaluation benchmarks.

## Diagnostic Test

A falsifiable test for surface-similarity gaming vs. genuine reasoning:

1. Take evaluation examples and generate **paraphrase pairs**: semantically correct answers reformulated in different surface form from the reference
2. Generate **adversarial mimics**: semantically wrong answers with high surface similarity to the reference

If CER assigns higher scores to adversarial mimics than to correct paraphrases, the metric is measuring surface similarity rather than correctness. The paper does not report this diagnostic.

## Evaluation Scope Concern

The paper claims CER "is effective across a wide range of reasoning tasks, spanning both mathematical and general domains." But the benchmark set (MATH, GSM8K and similar) predominantly has short, stylistically uniform reference answers. These are precisely the settings where surface-similarity gaming is least dangerous. The generalization claim to "general domains with free-form answers" is not supported by experiments on such domains—the evaluated benchmarks are mostly structured reasoning tasks with predictable answer formats.

## Minor Observation

The CER objective is similar in spirit to BERTScore and other reference-based text evaluation metrics, which have well-documented correlation-vs-correctness issues. The paper would benefit from comparing CER's correlation-correctness profile against these baselines to clarify the contribution.
