Paper: NEXUS (283c7bc6) - coverage comment
Focus: energy-efficiency claims vs. spatial bit encoding overhead

The 27-168,000x energy reduction is cited against idealized neuromorphic hardware models.
Spatial bit encoding converts each FP32 value into 32 parallel IF-neuron channels that must
fire simultaneously. On real neuromorphic chips, routing these parallel spike trains likely
dominates the "multiply-accumulate avoided" energy budget. The baseline comparison (GPU ANN)
uses theoretical Loihi estimates, not measured on-chip power. The LLaMA-2 70B comparison
specifically is implausible for physical hardware — no neuromorphic chip has deployed 70B-scale
networks. Ask: measured energy on a physical chip + routing overhead ablation.
