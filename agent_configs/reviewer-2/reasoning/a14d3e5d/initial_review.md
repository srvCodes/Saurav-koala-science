# Reasoning File: FlyGM (a14d3e5d)

**Paper:** "Whole-Brain Connectomic Graph Model Enables Whole-Body Locomotion Control in Fruit Fly"
**Paper ID:** a14d3e5d-d2c7-4877-bd15-45ee26effb81
**ArXiv:** 2602.17997
**Reviewer:** reviewer-2
**Date:** 2026-04-25
**Domain:** Graph-Learning, Robotics, Neuroscience

---

## High-Level Abstraction

FlyGM asks: can the exact neural wiring of a fruit fly brain — the Drosophila connectome with ~3,000 neurons — serve as a graph neural network policy for embodied reinforcement learning? The answer is yes, and the paper demonstrates this with superior sample efficiency and task performance compared to random graphs, topology-preserving rewired graphs, and MLPs.

The core contribution is a biologically-grounded directed message-passing GNN whose weight matrix encodes neurotransmitter polarity (excitatory/inhibitory) from the FlyWire connectome. A two-stage training pipeline — imitation learning on expert MLP trajectories, then PPO RL — enables stable locomotion control across gait initiation, straight walking, turning, and flight tasks.

**Downstream impact:** This is the first demonstration that a whole-brain biological connectome can function as an RL policy controller. It opens a research direction at the intersection of connectomics, embodied AI, and graph learning. The ability to use real biological wiring diagrams as inductive biases for learning could inform both neuroscience (testing hypotheses about why brains are wired as they are) and robotics (biologically-grounded controllers for soft robots or drones mimicking insect flight).

---

## Evaluation of Strengths

**1. Genuinely novel research direction.**
Using an exact biological connectome as a GNN policy controller for embodied RL is unexplored. The paper correctly identifies this gap and the contribution is original. The intersection of connectomics and embodied AI is timely given recent advances in both fields.

**2. Principled biological grounding via neurotransmitter polarity.**
The signed weight matrix (W_vu = N_exc(u,v) - N_inh(u,v)) is not an arbitrary design choice — it encodes the actual excitatory/inhibitory character of synaptic connections from neurotransmitter labeling. This is more biologically faithful than binary adjacency or unsigned synapse counts.

**3. Informative topology comparison.**
Comparing against (a) Erdős–Rényi random graphs and (b) degree-preserving rewired graphs is the right experimental design. The degree-preserving rewiring isolates whether specific connection patterns matter beyond degree distribution. The fact that FlyGM (0.0364 position error) outperforms degree-preserving (0.0385) and random (0.0485) validates that the actual connectome topology carries task-relevant information.

**4. Sample efficiency advantage.**
FlyGM shows faster convergence during imitation learning across all three loss components (total, action mean, action std). This suggests the biological wiring provides inductive biases that accelerate learning — a meaningful result beyond raw performance numbers.

**5. Task breadth for a locomotion study.**
Testing across gait initiation, straight walking, turning, and flight covers the core locomotion repertoire of the fly. The turning task, which requires coordination of asymmetric leg movements, is the most demanding and the performance gap widens there (FlyGM: 8.29°; rewired: 13.55°; random: 125.36°).

---

## Evaluation of Weaknesses

**1. Narrow scope: single organism, single behavioral domain, simulation-only.**
The entire study uses one fruit fly connectome in a flybody physics simulator. There is no real-world validation, no extension to other organisms, and no attempt to apply the framework beyond locomotion. The authors acknowledge this limitation but the scope is genuinely narrow for an ICML paper.

**2. MLP baseline is not an apples-to-apples comparison.**
The MLP baseline uses "two 512-unit layers" — this is a flat, non-structured architecture with completely different inductive biases. A fairer comparison would be a GNN with the same number of parameters and a randomized weight matrix (which is partially the random graph baseline), or a graph with the human-designed topology for a locomotion controller. The MLP comparison tests "graph vs. no graph" rather than "connectome graph vs. alternative graph."

**3. No component-level ablations.**
The paper does not ablate individual design choices: (a) signed vs. unsigned synaptic weights, (b) the trainable intrinsic neuron descriptors η_v, (c) the per-neuron MLP update vs. a shared update, (d) the imitation learning stage (does direct PPO work without it?). These ablations are missing and would clarify which design choices are necessary.

**4. Computational overhead is acknowledged but not quantified.**
Authors state FlyGM "requires longer per-step computation and higher memory usage" than MLP but provide no numbers. For practitioners considering this approach, the computational cost matters — a 10x slowdown for a 6% performance gain is a very different proposition than a 2x slowdown for the same gain.

**5. Scalability to larger connectomes is unclear.**
The Drosophila connectome has ~3,000 neurons, which is feasible for a GNN. For more complex organisms (mouse: ~70M neurons; human: ~86B neurons), this approach as described is completely infeasible. The paper does not discuss what subset-based or hierarchical approaches might extend the framework.

**6. Two-stage training creates a dependency on the expert MLP.**
The imitation learning stage requires a pre-trained MLP expert policy. This means FlyGM cannot be trained tabula rasa and its quality ceiling is bounded below by the availability of a competent expert. This is a practical limitation not sufficiently discussed.

---

## Technical Assessment

The GNN formulation is technically sound: directed message passing with biologically-signed weights, per-neuron latent states, and PPO training is a coherent and implementable framework. The biology is handled with care (FlyWire connectome, neurotransmitter polarity).

The key weakness is the missing ablations — without them, we don't know how much of the performance gain comes from the topology (vs. signed weights, vs. trainable per-neuron descriptors). The degree-preserving comparison is a partial substitute but does not isolate all design choices.

---

## Verdict Calibration (Preliminary)

FlyGM is a novel, well-executed paper with a genuinely original contribution: it bridges connectomics and embodied RL for the first time with concrete results. The narrow scope (one organism, simulation-only, locomotion only) and missing ablations prevent a higher score.

**Preliminary assessment: weak accept (~5.5–6.0).** The novelty and correct experimental design (topology comparisons) are compelling, but the missing component-level ablations and narrow scope keep this from strong accept.
