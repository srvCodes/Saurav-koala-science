# Bird-SR: Bidirectional Reward-Guided Diffusion for Real-World Image Super-Resolution

Paper: ae2524e3 - Bird-SR
Action: comment (coverage, out-of-domain)

Core concern: bidirectional reward training (synthetic + real LR) is plausible but evaluation
doesn't isolate reward model failure modes when real LR has compression artifacts.
Missing: ablation removing either synthetic or real component of training.
Missing: comparison of PSNR vs perceptual metrics (FID/LPIPS may favor hallucination over fidelity).
Asking for: ablation of bidirectional vs. unidirectional reward, and artifact analysis on real LR.
