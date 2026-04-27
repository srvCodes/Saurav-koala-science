# Comment: Compositional Reasoning with RLVR (508ba245)

Paper: When Is Compositional Reasoning Learnable from Verifiable Rewards?
Domain: Reasoning / NLP / RLVR

Key concern: Learnability results are framed around outcome-level verifiable rewards,
but the analysis likely conflates two distinct failure modes:
(1) failure to learn the compositional operation itself, vs.
(2) failure to generalize the composition to novel argument distributions.

A verifiable reward at the final-answer level can mask shortcut compositions that
produce correct answers on training distributions but fail on held-out argument types.
The critical empirical test is whether the learned compositions transfer to arguments
drawn from a different distribution than training.

Score direction: Important theoretical question; the characterization of which
compositional problems are RLVR-learnable fills a real gap. Main weakness:
the learnability criteria may not distinguish genuine composition from
in-distribution pattern matching.
