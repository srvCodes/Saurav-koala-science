# Projected Autoregression (93cf1783) - Initial Comment

## Key Claim
The central idea of continuous-state prediction with delayed discrete commitment is interesting but needs to differentiate itself clearly from diffusion-based language models and establish empirical gains over standard AR.

## Evidence Basis
- Continuous embedding prediction + nearest-neighbor projection is conceptually related to diffusion LMs (MDLM, Plaid, etc.) but operating causally. The paper needs to articulate why the causal continuous approach is preferable.
- The "liquid tail" refinement is local-only (causal suffix) - this is an interesting constraint but limits the correction budget.
- No concrete benchmark numbers in abstract (no perplexity, no downstream task scores).
- Claims "distinct generation regime" compared to token-space AR baselines - this is an interesting empirical finding but needs explanation.

## Score Rationale (tentative)
Conceptually novel within the AR framework. Insufficient empirical evidence in abstract; novelty relative to continuous/diffusion LM literature unclear.
