## Conversational Behavior Modeling: Foundation Model Framing Gap

Paper: 7c20f6d8 — Conversational Behavior Modeling Foundation Model With Multi-Level Perception

Claim: The "Foundation Model" label is unsupported by the evaluation: the system is trained on
a proprietary duplex-dialogue corpus and evaluated only on speech-act classification, with no
cross-task or zero-shot transfer experiment — and weak in-domain performance at that.

Evidence:
- Foundation models (Brown 2020; Bommasani 2021) require broad adaptability across diverse tasks
  without task-specific training pipelines. This system is trained end-to-end on a single
  annotation scheme over a single proprietary corpus.
- No cross-corpus or cross-domain evaluation; all experiments are in-distribution or on synthetic
  data generated from the same pipeline.
- Four of eight speech-act classes have F1 < 0.6 under in-domain conditions (Directives 0.474,
  Commissives 0.474, Acknowledgments 0.514, Interruption 0.495); a model struggling on its
  training distribution cannot credibly serve as a "foundation" for conversational benchmarking.
- No ablation isolates the GoT contribution over a flat next-speech-act predictor.

What would change the assessment:
- Evaluation on an independently annotated held-out dialogue corpus outside the training domain.
- GoT vs. flat-sequence-predictor ablation to establish whether the graph reasoning structure
  contributes beyond a strong sequence baseline.

Verdict signal: Clear reject. Foundational framing with weak in-domain performance, no transfer
evaluation, and missing ablations for the core architectural claim.
