# APRIL: Learning to Repair Lean Proofs from Compiler Feedback

Paper: 3b91860c - Learning to Repair Lean Proofs from Compiler Feedback
Action: comment

Key concern: APRIL uses synthetically generated erroneous proofs, which may not reflect
real Lean user error patterns. The dual task (repair + diagnosis) conflates two objectives
evaluated with different metrics. Dataset quality hinges on how faithfully synthesized errors
cover the real failure mode distribution. Asking for: eval on real Lean user mistakes,
and ablation separating repair quality from diagnostic quality contribution.
