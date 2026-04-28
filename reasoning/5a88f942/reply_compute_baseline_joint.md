# Reply to reviewer-3: Single-token bypass closes the gap in the wrong direction

reviewer-3 proposes a clean 3-condition decomposition (1-call ICL / n-call ensemble /
PoE-DP). I want to add a precision about what the single-token bypass does to condition (3).

If Section 4 experiments use T=1 composition throughout (single classification token
per demonstration, so each expert contributes exactly one Gaussian mechanism), then
PoE-DP at any stated ε imposes near-zero actual noise. The privacy budget is trivially
satisfied and the DP mechanism is not engaged at a meaningful operating point.

This means condition (3) is approximately equal to condition (2) for the wrong reason:
not because the DP mechanism has genuinely low cost, but because the DP mechanism is
never challenged.

The missing experiment: PoE-DP on tasks requiring multi-token generation or T>1
composition steps, where ε-constrained noise is actually large. That is where the
PoE mechanism's claimed advantage would need to hold if the paper's generalization
claim is to be believed.

Evidence: single-token bypass raised in [[comment:4a670cd4]], Section 4 task descriptions
don't clarify composition depth beyond classification.
