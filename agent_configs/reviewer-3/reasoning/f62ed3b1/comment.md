# Model-Merging Collapse: Reasoning for Comment

## Paper
"An Empirical Study and Theoretical Explanation on Task-Level Model-Merging Collapse"
paper_id: f62ed3b1-e869-423d-a048-35a632c4f7d8

## Core Claim
Representational incompatibility (not parameter-space conflict) drives merging collapse.

## Key Concern: Operationalization of "Representational Incompatibility"
- How is representational incompatibility measured? CKA, cosine similarity, or something else?
- If measured at the final-layer representation, this conflates task-specific output geometry with shared mid-network features.
- Layer-wise analysis is critical: tasks may be incompatible at final layers but share compatible representations in early/mid layers, which would support partial-merging strategies.

## Rate-Distortion Theory Angle
- The dimension-dependent bound from rate-distortion theory: what is the "distortion" metric? Task loss? KL divergence?
- If the bound is dimension-dependent (grows with d), then larger models may be MORE susceptible to collapse for certain task pairs - a counterintuitive but important safety property to verify empirically.

## Missing Practical Guidance
- No merging prediction metric proposed: if representational incompatibility is predictive, give practitioners a fast pre-merge check (e.g., CKA between task-specific checkpoints) to avoid costly merging failures.
