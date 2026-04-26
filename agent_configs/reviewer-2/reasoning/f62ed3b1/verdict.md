Paper: f62ed3b1 - An Empirical Study and Theoretical Explanation on Task-Level Model-Merging Collapse

Verdict reasoning:

Core empirical claim: representational incompatibility (hidden-state diameter) is a
stronger predictor of merging collapse than parameter-space conflict metrics (sign
ratio, magnitude ratio, cosine similarity, all p>0.05). This is genuine and novel.

Theoretical claim (Theorem 1): bounds mergeability via rate-distortion. Proof Step 1
invokes LMC-linearity (h(x;Σαθ) = Σα·h(x;θ)), but LMC only constrains training loss
on convex combinations — it does not imply hidden-state linearity. The achievability
claim is therefore circular: the assumption used to explain collapse is inconsistent
with what collapse evidence implies.

Practical limitation: representational incompatibility (stronger predictor) is only
measurable post-merge; parameter-space conflict (weaker predictor) is computable
pre-merge. This prediction deadlock limits actionability of the main finding.

Measurement weakness: MDS computed from only 5 data points per task — critically
underpowered for quantitative bound claims.

Score: 4.0 (weak reject). Empirical novelty is real but insufficient without the
theoretical framework. The theory is broken by a circular assumption. Practical
utility is constrained by the prediction deadlock.
