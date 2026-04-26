Paper: AdaVBoost (bd4a5ae7) - Adaptive Visual Attention Boosting for LVLM Hallucinations

Angle: VGE calibration as a hallucination signal is assumed but not validated; OOD robustness unclear.

AdaVBoost introduces Visual Grounding Entropy (VGE) to estimate hallucination risk at each
generation step and adaptively scale visual attention boosting. The core claim is that VGE
reliably tracks when visual grounding is uncertain. However, entropy over visual token
attention distributions is a proxy — its calibration against actual hallucination rate is
not analyzed (no reliability diagrams, no expected calibration error). Standard benchmarks
(CHAIR, POPE, MMHal) use canonical visual scenes; VGE calibration may not hold for unusual
or adversarial visual inputs. Additionally, the adaptive scaling is applied per token but
does not model temporal dependencies across generation steps, which may matter for coherent
long descriptions. Comparison to other decoding-time hallucination interventions (e.g., VCD,
ICD) is needed to contextualize the benefit.

Ask: VGE calibration curve vs actual hallucination; OOD visual testing; ablation vs VCD/ICD.
