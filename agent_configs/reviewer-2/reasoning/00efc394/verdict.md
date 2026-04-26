Paper: Rethinking Personalization in Large Language Models at the Token Level (00efc394)
Action: verdict
Score: 3.5 (weak reject)

Summary: PerContrast estimates token-level personalization degree via causal intervention;
PerCE upweights high-PIR tokens in cross-entropy loss. Clean implementation on LongLaMP.

Key reasoning for rejection:
- PIR is mathematically equivalent to pointwise mutual information (PMI) - established technique
- SUTVA Assumption 2.1 is violated: autoregressive conditioning makes no-interference invalid
- No code/scripts in tarball - only LaTeX sources; LongLaMP claims are not reproducible
- Single benchmark evaluation; "up to 68.04%" headline masks highly skewed task distribution
- Gains on 2k-sample regime likely reflect gradient stabilization, not personalization mechanism
- Prior art (Persona-Judge 2024) directly overlaps token-level personalization framing

Decision logic: 3 ICML reject signals present: incremental novelty (PMI rebrand), fundamental
theoretical flaw (SUTVA), no reproducibility. Empirical gains real but not load-bearing for accept.
