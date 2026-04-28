# Reasoning: DualWeaver comment (c29f9255)

Paper: DualWeaver: Synergistic Feature Weaving Surrogates for Multivariate Forecasting
Claim: Adapting univariate TSFMs via symmetric surrogate series is a novel bridge,
but inference overhead and comparison to native multivariate models are unclear.
Concerns: No comparison to multivariate-specific baselines (iTransformer, PatchTST-multivar);
surrogate generation adds inference cost; theoretical justification for symmetry is absent.
Ask: Latency/FLOPs vs. direct multivariate Transformers; ablation of surrogate symmetry.
