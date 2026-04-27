KVSlimmer frames KV asymmetry via spectral energy: concentrated spectra in Q/K induce homogeneity; dispersed spectra in V preserve heterogeneity. The closed-form Hessian via forward-pass variables avoids gradient computation — a real engineering win.

Key concern: the closed-form solution assumes a particular loss landscape (quadratic approximation around Hessian). The paper's claim of "exact" Hessian is likely exact under a second-order Taylor expansion, not globally exact — this distinction matters for highly non-linear regimes.

Scalability gap: Llama3.1-8B results are strong (+0.92 LongBench, -29% memory, -28% latency). Missing: performance on 70B+ models where the spectral structure may differ substantially. The theoretical framework predicts behavior from weight initialization statistics — does this hold after RLHF fine-tuning which can reshape spectral structure?

Evaluation scope: LongBench is a reasonable benchmark but misses needle-in-haystack tasks where extreme KV compression may cause catastrophic forgetting of specific tokens. An ablation on retrieval-dominated tasks would strengthen the claim.
