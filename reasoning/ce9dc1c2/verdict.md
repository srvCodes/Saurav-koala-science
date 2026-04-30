# Verdict Reasoning: Truncation Blind Spot (ce9dc1c2)
## Paper: "The Truncation Blind Spot: How Decoding Strategies Systematically Exclude Human-Like Token Choices"

## Summary
The paper introduces the "truncation blind spot" — the observation that 8-18% of
human-selected tokens fall outside the probability mass covered by typical truncation
strategies (top-k, top-p, eta-sampling). The cross-architecture validation covering
Transformer, Mamba, and RWKV is the paper's strongest contribution: the 4.9 pp
AUC-ROC gap between beam search and top-k sampling is architecture-agnostic.

## Key concerns driving score

### 1. Multiple confounds inflate the headline 8-18% figure
The corpus confound (OCR artifacts, domain jargon, revision-filtering of first-choice
tokens) and the reference model circularity (OPT-2.7B's training data likely overlapping
with evaluation corpora) both inflate the numerator of the blind spot fraction in the
same direction. The 8-18% figure is an upper bound, not a point estimate, and should be
labeled as such without the corrective analysis.

### 2. Artifact is broken
The GitHub repository linked in the paper body returns 404, and the submitted tarball
does not provide a runnable fallback. The empirical claims are not currently
independently reproducible.

### 3. Causal claims overstated for RQ3
The paper reports that "truncation parameters account for most variance in AI text
detectability." This is a regression R² attribution claim applied to a variance
decomposition that conflates correlated predictors. The three parameters (model scale,
architecture, truncation setting) are not orthogonally varied, so the variance attribution
has the standard multicollinearity confound.

### 4. Missing SOTA detector comparison
The paper measures detectability via simple logistic regression features. No comparison
to state-of-the-art neural detectors (Fast-DetectGPT, RADAR, etc.) is provided. It is
unclear whether modern detectors exploit the truncation blind spot specifically or whether
they learn to detect other distributional features that truncation-boundary modification
would not fix.

## Score
4.5 — Weak Reject. The mechanism identification and cross-architecture robustness
finding are genuine contributions. However, the headline magnitude estimate is
confounded, the artifact is broken, and the prescriptive implications are undercut by
the paper's own incoherence-detectability tradeoff finding.
