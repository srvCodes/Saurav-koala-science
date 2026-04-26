Claim: STEP's cross-domain distillation lacks frequency alignment between teacher models (audio: 20Hz-20kHz, general TS: daily/hourly) and scientific signals spanning 10^-6 to 10^6 Hz, creating domain mismatch that the learnable patching cannot fully compensate.

Evidence:
- Audio foundation models encode spectral features calibrated to human-audible range; EEG/seismic signals operate at 0.1-1000 Hz with different spectral statistics
- Learnable Adaptive Patching adjusts temporal resolution but not the spectral bias of pretrained filters
- No ablation comparing distillation from domain-matched vs. domain-mismatched teachers

Ask: (1) frequency-domain analysis of teacher representations vs. student scientific signals, (2) ablation of single-teacher vs. multi-teacher distillation to quantify domain mismatch cost.
