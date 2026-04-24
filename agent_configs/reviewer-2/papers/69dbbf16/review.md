# Reasoning File: RoboAlign (69dbbf16)

**Paper:** "RoboAlign: Learning Test-Time Reasoning for Language-Action Alignment in Vision-Language-Action Models"
**Paper ID:** 69dbbf16-a716-4f44-8a1a-d1fc5b32da6b
**ArXiv:** 2603.21341
**Reviewer:** reviewer-2
**Date:** 2026-04-24

---

## High-Level Abstraction

This paper addresses a critical failure mode in building Vision-Language-Action (VLA) models on top of pretrained Multimodal Large Language Models (MLLMs): existing embodied-reasoning fine-tuning methods (SFT on VQA data) either fail to improve or actively degrade downstream robotic manipulation performance. RoboAlign proposes a two-stage pipeline — SFT followed by GRPO-based RL — that directly aligns MLLM representations with low-level action tokens (FAST tokens), bridging the modality gap between language reasoning and continuous motor control.

**Downstream impact:** VLAs that inherit strong MLLM reasoning capabilities without sacrificing motor performance are a sought-after architecture for general robotic manipulation. The 17.5% improvement on LIBERO and 106.6% on real-world robot tasks (over SFT-only baseline) suggest this alignment technique could substantially accelerate the development of generalist robots. The GRPO reward formulation (format + prefix accuracy) is also directly reusable for other action-token prediction tasks.

---

## Technical Details Verified

### Stage 1: SFT for FAST token capability

The SFT stage trains on a 1.88M QA mixture including:
- General MLLM tasks (LLaVA-OneVision, 100K)
- Embodied reasoning (RefSpatial 300K, RoboPoint 200K, EgoPlan-IT 50K, multi-view 500K)
- Robot-specific VQA (ShareRobot 100K, RobotVQA 100K, proprietary VQA 150K)
- BridgeV2 + Droid robot QA (300K)
- FAST token prediction (BridgeV2, 400K)

Key contribution: incorporating **zero-shot reasoning data** (50K MCQAs + 50K spatial QAs distilled from a GRPO-trained model) transfers chain-of-thought reasoning to FAST token generation. Without this data, the model produces minimal reasoning ("Go to the cup."), which provides insufficient diversity for subsequent RL training.

### Stage 2: RL alignment with GRPO

Reward function:
$$r = \frac{r_f + r_a}{2}$$

where $r_f \in \{0,1\}$ checks reasoning format (`<think>...</think><answer>...</answer>`) and $r_a \in [0,1]$ is prefix accuracy:

$$r_a = \frac{1}{m} \max\{i : T^\text{gen}_{1:i} = T^\text{target}_{1:i}\}$$

Trained on 12.8K BridgeV2 samples using GRPO. The RL stage uses ~1 hour of training on 8×H200 GPUs — minimal compute relative to the SFT stage (30 hours).

---

## Experimental Results

**LIBERO (Table 1):**
- Baseline (Qwen2.5VL-7B-Ins, no fine-tuning): 73.9% avg
- Action-Only SFT: 81.5%
- RoboAlign SFT (w/o RL): 78.7%
- RoboAlign (SFT + RL, Ours): **86.8%** — highest, with particularly large gains in Goal (87.2% vs 59.0% w/o RL) and Long (70.0% vs 65.6%)
- Reference methods: ThinkAct 84.4%, CoT-VLA 83.9%

**CALVIN ABC→D (Table 4):**
- Baseline: 2.16 success length
- Language-Only SFT: 2.32
- RoboAlign w/o RL: 1.89 (slight degradation from SFT fine-tuning)
- RoboAlign (Ours): **2.57** — improvement across all chain lengths, including task 4 (32.8%) and 5 (22.2%)

**Real robot (Table 5):**
- Baseline: 32.3% avg
- RoboAlign w/o RL: 55.2%
- RoboAlign (Ours): **66.7%** — particularly large gain on "Basket to bowl" (70.8% vs 37.5%)

**Multimodal benchmarks (Table 3):**
- RoboAlign maintains general MLLM capability: MMStar 62.80% (slight gain), Robot-R1 Bench 1.38 (vs 1.02 baseline), RoboSpatial 50.86%

**Generalization (Table 6):** Method generalizes to Qwen3VL-8B backbone: 92.5% on LIBERO vs 85.2% baseline.

---

## Strengths

**1. The RL-over-SFT gain is significant and generalizable.** The 8.1-point improvement from SFT to SFT+RL on LIBERO (86.8 vs 78.7) is not a marginal increment — it closes most of the gap between specialized embodied models and the best prior work. More importantly, the gain is consistent across LIBERO, CALVIN, real robot, and a different backbone (Qwen3VL), ruling out overfitting to a specific benchmark or architecture.

**2. The modality gap diagnosis is correct and well-supported.** The key insight — that language-based VQA training cannot bridge the language-to-action modality gap because language and FAST tokens occupy different representation spaces — is validated by the KNN analysis (Table 3): RL training improves the KNN accuracy of MLLM hidden representations from 43.2% to 69.8%, showing that RL genuinely reorganizes the representation space around actionable state information.

**3. The reward formulation is elegant and minimal.** Using prefix accuracy as the action reward is computationally cheap, does not require executing actions in simulation, and provides a dense training signal for sequential prediction. This is a significant practical advantage over methods requiring environment rollouts.

**4. Computational efficiency of RL stage.** 1 hour of RL training (12.8K samples) on top of 30 hours of SFT to unlock substantially better VLA performance is a favorable trade-off, and the paper is transparent about compute costs.

**5. Consistent gains on long-horizon tasks.** The most pronounced improvements are on "Long" LIBERO tasks and long CALVIN chains — exactly the setting where MLLM reasoning ability should matter most. This alignment between the method's mechanism (improving reasoning quality) and its observed benefit (long-horizon gains) is strong indirect validation.

---

## Weaknesses

**1. The SFT data mixture is large and partially proprietary.** Stage 1 uses 1.88M samples from diverse sources including a "proprietary RoboAlign VQA dataset" (150K) and internally generated multi-view instruction data (500K). The total dataset size makes the SFT stage expensive and not directly reproducible. Without the proprietary VQA data, practitioners cannot replicate the results.

**2. CALVIN performance without RL is concerning.** RoboAlign w/o RL achieves 1.89 success length on CALVIN, which is *below* the baseline's 2.16. This means the SFT stage actually hurts CALVIN performance, and the RL stage must recover and surpass this. The paper notes this but does not explain it. This is an important failure mode: if RL training fails or is applied incorrectly, the user ends up worse than the starting model.

**3. The reward function has a known weakness.** Prefix accuracy measures token-level matching to a single ground-truth action trajectory. However, in manipulation tasks, there are often multiple valid action sequences to complete a task. A trajectory that diverges from the training target early but still succeeds would receive low $r_a$. The paper does not address this multi-modality issue, which could limit performance in scenarios with significant trajectory diversity.

**4. Limited analysis of when RL alignment fails.** The paper shows consistent improvements overall but does not characterize which task types or environments benefit least from RL alignment. Understanding the boundary conditions (e.g., tasks with highly multi-modal action distributions, novel object categories, long-context reasoning) would substantially improve the paper's scientific value.

**5. Comparison scope could be wider.** The paper compares against ThinkAct and CoT-VLA as "reference" results but not under the same experimental setup (the setup section notes these use different action heads and training protocols). A controlled comparison against ThinkAct under the same setup would be more convincing.

---

## Score Assessment

This paper makes a genuine contribution: a practical, computationally efficient method for aligning MLLMs with low-level robotic actions that consistently outperforms prior work across simulation and real-robot benchmarks. The reward design, KNN analysis, and generalization to Qwen3VL are particularly strong elements. The main concerns are reproducibility (proprietary data), the unexplained CALVIN SFT regression, and the single-modal reward function. These are addressable in revision.

**Preliminary score: 7.0 / 10** (solid accept range)

---

## Evidence Used
- Paper source (LaTeX) from platform tarball for 69dbbf16
- Tables from resources/*.tex files
- Method section from sections/method.tex
- Appendix from sections/appendix.tex (compute costs, dataset details)
