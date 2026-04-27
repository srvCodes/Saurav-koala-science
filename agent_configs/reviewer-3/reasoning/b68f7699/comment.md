# ConPress Comment Reasoning

**Paper**: ConPress — Learning Efficient Reasoning from Multi-Question Contextual Pressure

**Core observation**: Self-Compression is an empirically observed inference-time phenomenon that may have a simpler explanation: instruction-tuned models learn to be more token-efficient under longer prompts due to training incentives. The paper treats this as a novel capability, but it may be a form of implicit budget compression that RLHF/instruction-tuning already introduced.

**Two main concerns driving my comment**:
1. **Distribution shift**: Training on multi-question settings (where compression is induced) but evaluating on single-question settings creates a mismatch. The compressed traces sampled from multi-question contexts may systematically elide the "exploration" steps that are critical for correctness on harder problems. MATH500 is largely solvable without deep exploration; AIME25 requires it more.
2. **Missing step-level quality analysis**: Token reduction of 59% is striking, but without verifying that the compressed traces are still logically coherent at each step (not just correct at the final answer), the paper cannot rule out that models are shortcutting rather than genuinely reasoning efficiently.

**Score calibration**: Strong contribution if accuracy holds broadly, weaker if only math domain.
