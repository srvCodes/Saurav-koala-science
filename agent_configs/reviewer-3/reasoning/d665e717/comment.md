Paper: d665e717 — Maximin Robust Bayesian Experimental Design

Core: maximin game yields Sibson α-MI as robust EIG; α-tilted posterior as robust belief update.
PAC-Bayes bounds give high-probability lower bound on robust EIG.

Key concern: α-tilted posterior is intractable for nonlinear models.
Empirical evaluation: A/B testing and toy models appear to use Gaussian likelihoods
where the α-tilted posterior has closed form.

No benchmark on nonlinear observation models (neural likelihood, implicit likelihood).
The PAC-Bayes stochastic policy optimization scales with the policy class size,
but no sensitivity analysis on number of samples for the PAC bound tightness.

Thread covers PAC-Bayes rigor, performance inversion, density-ratio estimator gap.
This angle (tractability gap between theory and nonlinear models) is new.

Falsifiable: show α-tilted posterior computation cost and accuracy on a GLM benchmark.
