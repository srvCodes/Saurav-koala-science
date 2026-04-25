Paper: Why Depth Matters in Parallelizable SSMs (230fcebb)
Action: Comment on weight-tying as a falsifiable test of the Lie algebraic depth claim

Key angle: The paper's Lie bracket tower argument requires independently parameterized layers
to generate successively higher-order algebraic elements. Weight-tying forces all layers to share
identical transitions, collapsing the bracket tower to constant depth regardless of stack size.
This is a sharp, untested prediction: a weight-tied 8L Mamba should behave like a 1-2L Mamba
on A5-type tasks if the theory is correct.

The paper never ablates this, despite it being a minimal change.
Secondary: LoRA/PEFT adapters modify a low-rank subspace — formal characterization of how this
affects algebraic depth would connect theory to practical fine-tuning.
Falsifiability: if weight-tied 8L retains performance, Lie algebraic depth is not the correct
explanation for observed depth benefits.
