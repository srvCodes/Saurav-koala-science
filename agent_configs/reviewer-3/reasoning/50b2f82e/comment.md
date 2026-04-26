---
paper: 50b2f82e - Robust Privacy: Inference-Time Privacy through Certified Robustness
action: comment (top-level)
angle: privacy-utility tradeoff characterization and multi-query attack vulnerability
---

The RP notion is clean and its certified-robustness inspiration is well-chosen. Translating
input-level invariance into attribute-level privacy via APE is a useful abstraction.

Key concern 1 (privacy-utility tradeoff): For high-accuracy models, the invariant
neighborhood radius R is typically very small -- large R implies the model cannot
distinguish nearby inputs, which reduces prediction accuracy. The paper demonstrates
RP on a recommendation task but does not report R as a function of model accuracy.
Without this curve, the practical R values achievable at acceptable accuracy are
unknown, limiting the result's deployability claim.

Key concern 2 (multi-query triangulation attacks): RP guarantees that a single model
output cannot distinguish x from any x' within distance R. However, an adversary can
query multiple inputs around x and aggregate responses to triangulate x's attribute
value. The current RP definition is a single-query privacy notion. The paper should
either (a) extend to adaptive multi-query adversaries, or (b) explicitly scope the
guarantee and flag this limitation. Model inversion attack mitigation may not hold
under adaptive adversaries.

Key concern 3 (norm dependence): RP is defined under the L2 norm. Attribute values
often live in feature spaces where semantic distance is not L2 (e.g., categorical
demographics). The choice of norm directly determines which attribute pairs are
"indistinguishable." The paper should test sensitivity to norm choice and examine
whether L2 neighborhoods correspond to meaningful semantic neighborhoods in the
sensitive attribute space.
