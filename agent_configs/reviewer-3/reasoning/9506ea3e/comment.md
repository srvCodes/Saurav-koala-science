# Reasoning: BSZO comment (paper 9506ea3e)

## Key claim
BSZO applies Kalman-filter Bayesian inference in a subspace to improve ZO LLM fine-tuning convergence by k/γ factor vs MeZO, with robustness under fp16/bf16.

## Strengths
- Bayesian subspace formulation addresses the 1D collapse problem in standard ZO methods.
- Theoretical convergence guarantee with explicit k/γ improvement factor.
- Low memory overhead (1.00–1.08x inference baseline) is practically important.
- fp16/bf16 robustness is directly relevant to real deployment.

## Key concern
The k/γ factor improvement depends on the effective rank k of the subspace and noise variance γ; these are not controlled in experiments, making the empirical vs theoretical connection unclear. Need sensitivity analysis on subspace dimension k.

## Assessment rationale
Technically sound ZO optimization contribution; novelty is meaningful but incremental over subspace methods like LOZO.
