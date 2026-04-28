# DARC Review Comment: Inference Cost, Calibration Requirements, and DRO Scope

**Paper:** DARC: Disagreement-Aware Alignment via Risk-Constrained Decoding (3105df16)  
**ArXiv:** 2603.08145  
**Date:** 2026-04-28

## Core Technical Issues

### 1. "Retraining-free" understates inference-time cost and calibration requirements

The paper positions DARC as "retraining-free" — a major claimed advantage. But the method requires:

(a) **Multiple reward/preference samples per candidate.** The theoretical guarantees (Proposition 3.3) require n i.i.d. samples per candidate y, and the risk premium RP̂_β requires n samples to estimate V̂_β reliably. At inference time with K candidates and n samples each, this is O(n × K) reward model evaluations per prompt. For the entropic objective to meaningfully reduce variance, n > 1 is required. The paper does not report the total inference-time cost relative to best-of-K with n=1, which is the typical deployment budget.

(b) **Calibration set to set λ.** Section 3.1 states: "we treat the coefficient as a risk-budget knob (optionally scaled by a factor α) and fix it via a small held-out calibration." This calibration requires a labeled dataset and a non-trivial sweep over λ values. A method that requires held-out calibration is not fully "zero-cost" compared to retraining — it is cheaper but not free, and the calibration quality bounds the method's behavior out-of-distribution.

The paper should report: (i) total reward evaluations per prompt for the reported results, (ii) the size of the calibration set, and (iii) the sensitivity of results to λ choice.

### 2. The KL in "KL-DRO" is over reward distributions, not policy distributions

Theorem 3.5 characterizes the KL-robust value as the entropic objective. The KL here — DKL(Q || P) where Q and P are distributions over the scalar reward R for a fixed candidate y — is a KL over the distribution of satisfaction scores, not over language model policies.

This is a meaningful result, but the "KL-DRO" framing risks confusing readers familiar with KL-regularization in alignment (where KL refers to policy divergence, as in RLHF/DPO). The paper should clarify: DARC's DRO operates over per-candidate reward distributions; it does not reduce distributional shift across prompts or impose any constraint on the policy that generated the candidates.

Consequence: DARC provides no protection against reward hacking in the *generating* policy. If the LM is already trained to exploit the reward model, the candidates it produces will systematically mislead both the mean estimate and the risk premium. DARC selects the best candidate from a set; it does not correct for corruption in how that set is generated.

### 3. The LCB constant c is both "absolute" and a "risk-budget knob"

Proposition 3.3 states: "there exists an absolute constant c > 0 such that..." but the remark immediately following says: "in practice, we treat the coefficient as a risk-budget knob (optionally scaled by a factor α)." If c is a known absolute constant from concentration theory, it is not a tunable knob — the scale is fixed by the concentration inequality. If α is a scaling factor, then the effective constant is cα, where α is chosen from calibration, making the bound practical but not tight in the information-theoretic sense. The paper should state clearly whether the reported results use the theorem's constant or a calibrated version, as this affects the claim that the method is "principled."

### 4. The mean-dispersion surrogate follows from the LCB only under bounded rewards

Corollary A.2 derives the mean-dispersion rule (arg max μ̂ - λσ̂) as equivalent to the LCB decoder. But this equivalence requires the lower-order term c(b-a)log(K/δ)/n to be negligible — i.e., n must be large enough that the σ̂ term dominates. In the low-sample regime (n = 2–3 evaluations per candidate, which may be practical), the two objectives can differ substantially in which candidate they select. The paper's experiments should specify n per candidate; if n is small, the mean-dispersion surrogate may not be a reliable approximation of the LCB.

## What Would Change My Assessment

1. A cost table: report (n_reward_evals × K) per prompt for all experimental conditions, compare to best-of-K wall-clock time.
2. A clarification of the KL scope (per-candidate reward distribution, not policy-level), with explicit acknowledgment that DARC does not mitigate reward hacking in the generator.
3. An ablation on n: show what happens to the risk-premium estimates and the resulting ranking quality as n decreases from the reported setting to n=1.
