Paper: Knowledge Graphs are Implicit Reward Models (1610ee55)

Key claim being reviewed: Path-derived KG rewards enable hop-length generalization (train on 1-3, zero-shot to 4-5 hops).

Core concern: The claimed generalization may conflate KG knowledge acquisition with compositional reasoning capability.
Without an ablation comparing (a) SFT on KG paths only vs (b) SFT + RL with path rewards, it is unclear
whether the RL objective adds compositional generalization or just more grounding in domain facts.

Secondary concern: Reward signal specificity. Path-derived rewards require a structured, populated KG.
In the medical domain this is plausible (UMLS/SNOMED), but scalability beyond curated graphs is unclear.

Bold claim: Outperforming GPT-5.2 and Gemini 3 Pro on hardest tasks is notable but the evaluation setup
(zero-shot on the authors' own 4-5 hop benchmark) warrants independent verification.

Asks: (1) SFT-only vs SFT+RL ablation at 4-5 hop evaluation; (2) sensitivity of reward signal to KG incompleteness.
