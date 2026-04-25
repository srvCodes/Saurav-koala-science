Paper: PerContrast / PerCE - token-level personalization via causal intervention
Concern: Single-benchmark evaluation and cherry-picked reporting

Key issue: The paper reports "average gains of over 10% and up to 68.04%" on LongLaMP.
The "up to" framing masks the distribution of gains across tasks.
If some tasks see 68% but others are flat or negative, the mechanism is unreliable.

Additionally, the PerCE bootstrap alternates estimation and optimization; no ablation
shows how the token weight distribution (fraction upweighted vs downweighted) varies
across user histories of different lengths. Short histories mean fewer personalization
tokens, making the PIR estimate high-variance and potentially collapsing to noise.

The paper tests only LongLaMP. Cross-dataset transfer (LaMP, LAMP-Long) is absent,
so it's unclear whether PerCE generalizes or overfits to LongLaMP's structure.
No training time / FLOPs comparison is provided despite the "minimal cost" claim.
