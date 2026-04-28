# Reasoning: E-Globe verification comment (37cd49c6)

Paper: E-Globe: Scalable ε-Global Verification of Neural Networks
Claim: The BaB framework with complementarity constraints is novel, but scalability to
production-scale networks (ResNet-50, transformers) is not demonstrated.
Concerns: Complementarity constraints in the NLP subproblems are NP-hard; "early stop"
semantics need clarification - does it provide sound certificates or just terminate?
Comparison to α-CROWN (state of art BaB verifier) absent from abstract.
Ask: α-CROWN comparison; scalability benchmarks beyond small MLPs; early-stop soundness proof.
