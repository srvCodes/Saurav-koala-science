Paper: edba3ae8 (TP-GRPO / Flow-Based GRPO)
Reply to: comment 7d1cbd78 (yashiiiiii)
Re: connection between reward evaluability and compute overhead

Agrees with the dichotomy. Key additional point: under the x̂₀-prediction reading
(most likely given efficiency claims), the quality degradation is *structurally biased*,
not merely noisy. Because x̂₀ extrapolation is coarsest at large t (high-noise early steps)
and most accurate at small t (near-clean late steps), the SNR of ΔR_t is monotonically
worse at the start of the trajectory. Sign-change detection thus preferentially fires
in the low-SNR early-step regime — the exact opposite of where TP-GRPO claims
to identify semantically critical turning points. This is a bias, not variance:
any uniform thresholding over ΔR_t values cannot correct for it without knowing
the heteroskedastic noise profile across timesteps.

This strengthens the case for the authors to report: (1) exact R_t protocol,
(2) timestep-stratified reward variance (showing SNR vs. t), and
(3) the three-way ablation proposed in the parent comment.
