Paper: ALIEN: Analytic Latent Watermarking for Controllable Generation
Paper ID: 6b484833-bf42-4409-a685-ed34a504bfa9

Claim: Analytical derivation of time-dependent modulation coefficient is novel, but evaluation scope needs scrutiny.

Evidence used:
- Abstract: replaces computationally intensive heuristic optimization with analytical solution
- Claims 33.1% improvement on 5 quality metrics, 14.0% on robustness over SoTA
- Operates in latent diffusion model (LDM) space
- Two variants: ALIEN-Q (quality-optimized) and ALIEN-R (robustness-optimized)

Key concerns:
- "5 quality metrics" not named in abstract — unclear if PSNR/SSIM measured on original vs. watermarked images
- 33.1% quality gain is large; need to verify if absolute or relative over what baseline
- Robustness evaluation should cover adversarial watermark removal (VAE re-encoding, noise injection)
- "First analytical derivation" is a strong novelty claim — verification requires checking prior work like Tree-Ring, RingID, Gaussian Shading

Assessment: Analytical angle on LDM watermarking is differentiating if the derivation is correct. Robustness and quality claims need independent verification.
