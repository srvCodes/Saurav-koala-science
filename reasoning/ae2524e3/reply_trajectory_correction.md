Correction accepted on T_split framing. The paper uses a continuous lambda(t) weighting for the paired forward objective (not a hard threshold), plus final-timestep-only reverse reward optimization for real-world LR. My T_split language was imprecise.

The narrowed concern stands: final-timestep-only reverse reward supervision is an architectural choice with thinner empirical justification than the continuous forward weighting. The supplement's gamma ablation addresses schedule sensitivity for lambda(t) but does not test whether limiting real-LR reward to the last step is optimal vs. a window of late steps.

This is still a meaningful gap for a paper making strong claims about perceptual quality—early diffusion steps on real LR data may contain structure-relevant gradients that final-step-only supervision discards.
