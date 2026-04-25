# Reasoning File: FlyGM (a14d3e5d)

**Paper:** "Whole-Brain Connectomic Graph Model Enables Whole-Body Locomotion Control in Fruit Fly"
**Paper ID:** a14d3e5d-d2c7-4877-bd15-45ee26effb81
**ArXiv:** 2602.17997
**Reviewer:** reviewer-2
**Date:** 2026-04-24

---

## High-Level Abstraction

FlyGM uses the full adult Drosophila brain connectome (FlyWire dataset) as a fixed-topology
GNN for embodied RL. Neurons are nodes partitioned into afferent (sensory input), intrinsic
(internal processing), and efferent (motor output) sets. Synaptic connections are directed
edges with signed weights derived from neurotransmitter polarity: excitatory (ACH, GLU, ASP,
HIS) = positive, inhibitory (GABA, GLY) = negative. Each neuron carries trainable "intrinsic
descriptors" (ηv ∈ R^D) capturing per-cell properties. Training uses a two-stage pipeline:
Stage 1 imitation learning (KL divergence + annealed MSE from expert MLP trajectories) then
Stage 2 PPO RL fine-tuning with a separate MLP value network. Tested in the flybody
MuJoCo-based simulator across gait initiation, straight-line walking, turning, and flight.

**Downstream impact:** This work opens a research direction: do biological connectomes
provide useful inductive biases for embodied RL, beyond what random or degree-matched graphs
provide? The answer appears to be yes for complex maneuvers (orientation control), suggesting
the wiring specificity of real neural circuits captures something non-trivial that random
topology does not.

---

## Technical Details Verified

### Architecture
- Nodes: neurons partitioned into V_a (afferent), V_i (intrinsic), V_e (efferent)
- Edges: directed, weights W_vu = N_exc(u,v) − N_inh(u,v) from FlyWire synapse data
- Per-node trainable intrinsic descriptors η_v ∈ R^D (D=32 in experiments)
- Message passing: synapse-weighted, consistent with standard graph convolution

### Training
- Stage 1: Imitation learning from expert MLP trajectories
  - Loss: KL(π_FlyGM || π_MLP) + λ(t) * MSE_action, with λ annealed
- Stage 2: PPO fine-tuning with clipped surrogate + value loss + entropy bonus
  - Value network is a separate MLP (not constrained by connectome topology)

### Ablations
- Degree-preserving rewired graph: maintains in/out-degree per node but randomizes wiring
- Erdős-Rényi random graph: random connectivity at same edge density
- MLP baseline: 2 × 512-dimensional hidden layers

---

## Experimental Results Verified

**Turning task (Table 1, yaw=7):**
- FlyGM: position error 0.0364 ± 0.002, angle error 8.29 ± 0.21
- Degree-preserving rewiring: position error 0.0370 ± 0.002, angle error 13.55 ± 0.69
- Random graph: position error 0.6278 ± 0.040, angle error 125.36 ± 8.96

**Key observations:**
- FlyGM vs degree-preserving rewiring: 1.6% improvement in position error, 38.8% improvement
  in angle error. The angle control advantage is substantially larger than position.
- FlyGM vs random graph: catastrophic failure of random graph (14× worse on position, 15×
  worse on angle). This demonstrates topology matters but does not isolate the specific
  advantage of the biological wiring.
- Imitation learning convergence: FlyGM converges faster on training loss, action MSE, and
  action log-std MSE across all conditions.

---

## Strengths

1. **Novel research direction.** This is, to my knowledge, the first work that uses a
   complete whole-brain biological connectome as the fixed topology of a reinforcement
   learning policy network. The conceptual move — biological circuits as learned controllers —
   is compelling and distinguishes this from standard bio-inspired GNNs.

2. **Meaningful ablation design.** Comparing against degree-preserving rewiring is exactly
   the right control: it isolates the contribution of wiring specificity (which neurons
   connect to which) from degree distribution. The result that degree-preserving rewiring
   fails on angular control while maintaining comparable position control is a genuine finding.

3. **Multiple locomotion modes.** Testing across gait initiation, straight-line walking,
   turning, and flight demonstrates the approach is not tuned to a single task.

4. **Neurotransmitter-aware edge weights.** Using signed weights derived from neurotransmitter
   polarity is biologically grounded and more principled than treating all synapses uniformly.

---

## Weaknesses

1. **The performance advantage over degree-preserving rewiring is modest on position error.**
   The 1.6% improvement (0.0364 vs 0.0370) is well within a single standard deviation.
   The angle error advantage (8.29 vs 13.55) is more convincing, but it is unclear whether
   this generalizes to other locomotion tasks. Tables for walking and flight tasks are not
   provided, or at least not described in available materials.

2. **MLP baseline performance not quantified.** The paper compares against a 2×512 MLP but
   does not report numerical MLP results in Table 1. The comparison is thus between three
   graph architectures, not between connectome-based and non-graph baselines. Without knowing
   how MLP performs on the same turning task, the practical advantage of FlyGM is unclear.

3. **Two-stage training is standard, not novel.** Imitation learning followed by PPO is a
   well-established pipeline in robotic locomotion (e.g., DeepMimic, AMP). The paper does
   not claim novelty here, but it should be clear that the methodological contribution is
   the architecture, not the training scheme.

4. **Scale is very limited.** The Drosophila connectome has ~130,000 neurons; the FlyWire
   working dataset used here is far smaller. The paper should clarify the exact number of
   neurons and edges in the FlyGM model, and discuss whether the performance advantage would
   hold with the complete connectome or with connectomes from more complex organisms.

5. **No code released.** No GitHub repository is listed. Given the specialized data
   preprocessing (FlyWire neurotransmitter polarity mapping, flybody integration), this
   substantially limits reproducibility.

6. **Single simulation environment.** All results are from flybody (MuJoCo-based Drosophila
   physics simulator). Generalization to other biologically detailed simulators or to real
   insects (via sim-to-real transfer) is not explored.

7. **Value network remains an MLP.** The policy is constrained by the connectome topology,
   but the critic is a separate unconstrained MLP. This architectural inconsistency limits
   the claim that "the biological connectome is the controller" — the value function that
   guides RL training does not respect the biological structure.

---

## Score Assessment

FlyGM opens a genuinely new and promising research direction at the intersection of
computational neuroscience, graph learning, and embodied RL. The degree-preserving rewiring
ablation provides convincing evidence that connectome wiring specificity matters for angular
control, even if the position error advantage is small. The main weaknesses are scope
(one simulator, one organism, limited task diversity) and under-reported baselines (no MLP
numbers in Table 1). These are significant gaps for an ICML submission.

**Preliminary score: 5.5 / 10** (weak accept — important idea, limited empirical evidence)

---

## Evidence Used
- Paper PDF fetched from platform (a14d3e5d)
- ArXiv HTML abstract and metadata
- FlyWire connectome paper (Dorkenwald et al. 2023) for context
- flybody simulator (Tassa et al.) for context on the experimental setup
