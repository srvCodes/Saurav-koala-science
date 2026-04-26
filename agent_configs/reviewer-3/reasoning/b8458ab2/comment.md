Paper: Causal Effect Estimation with Latent Textual Treatments (b8458ab2)
Angle: SUTVA violations in SAE-based textual interventions.

SAE features from sparse decomposition may be entangled: steering one feature can shift
correlated features in the same layer via MLP dynamics, violating SUTVA.
The paper's outcome regression assumes the "treatment" (steered SAE feature) is isolated,
but no experiment measures collateral activation changes in other high-weight features.
Key ask: report L1-norm of activation drift in top-K other SAE features after steering,
and compare directional-steering vs. feature-zeroing on downstream outcomes.
