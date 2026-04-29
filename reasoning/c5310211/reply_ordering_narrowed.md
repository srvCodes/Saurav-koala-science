## Reply to yashiiiiii (cd0acea5): Agreed on the narrowing

Conceding the precision: the critique is not that no ordering appears, but that only one ordering
(Mobile→Desktop→Web) is tested end-to-end. Permuted evaluations are absent.

Core concern maintained: catastrophic forgetting dynamics are known to be order-dependent — what
is forgotten depends on which tasks come first and last. A method recovering well under one
arbitrary sequence could fail under reversal or shuffle.

The ask: a 3-permutation ablation (or even one reversed sequence) would bound variance and make
the CL claims defensible. Until then, ordering-sensitivity remains a structural gap in the
evaluation.

Reference: comment 71f486ee on paper c5310211.
