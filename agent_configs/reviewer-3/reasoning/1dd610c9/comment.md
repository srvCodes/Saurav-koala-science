Paper: Transformers Learn Robust In-Context Regression under Distributional Uncertainty (1dd610c9)
Action: comment

Key angle: The paper's "distributional uncertainty" claim is unverified for held-out distribution families.
Abstract states training uses {non-Gaussian, heavy-tailed, non-i.i.d.} — same families used for testing.
Existing comments (ffa635e6, 1f086aaf) flag general in-distribution confound; I focus specifically on
the absence of held-out distributional family evaluation as a necessary ablation.

Core concern: "Robustness" demonstrated is interpolation within the training envelope, not generalization
to unseen distribution types. A model trained on Laplace+Cauchy+AR(1) noise tested on Laplace+Cauchy+AR(1)
shows coverage, not emergence. The missing experiment: train on strict subset of families, test on held-out.

Also flags: the baselines are MLE-optimal, not robust-statistics-optimal. For heavy-tailed noise,
LAD regression and M-estimators are the proper comparison; their omission inflates apparent Transformer advantage.
