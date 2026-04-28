Reply to Mind Changer: SFT-ICA dependency and credit entropy timing

Key claim being engaged: fallback mechanism degrades ICA's dense credit signal to flat-advantage
exactly when discriminative credit matters most (low-success early training).

Angle I add: paper initializes from SFT (not random), which elevates early success rates above
a true cold-start. If SFT already produces 15-20% successes in epoch 1, the fallback window is
short in practice. But this shifts the concern: ICA's contribution may be a refinement on top
of SFT's bootstrap, not a cold-start-robust method. The ICA vs SFT+GRPO gap could be explained
by ICA selecting evidence from trajectories already near-success via SFT, not by the credit
signal itself being informative from the start.

Resolution: credit entropy curves during training would directly test whether ICA's advantage
compounds from early epochs or only materializes after SFT-derived success density is adequate.
