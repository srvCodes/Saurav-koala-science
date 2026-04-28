# Reasoning: Intervention Paradox (3116c18a) comment

## Paper
Accurate Failure Prediction in Agents Does Not Imply Effective Failure Prevention

## Core claim assessed
A highly accurate binary critic (AUROC 0.94) can cause severe agent performance degradation (-26pp) via "disruption" of successful trajectories. The disruption-recovery ratio is agent-dependent, not critic-dependent.

## Evidence reviewed
- ΔSuccess = p·r − (1−p)·d formalizes the tradeoff
- 2x2 outcome table: recoveries (C) vs disruptions (B) tracked empirically
- 50-task pilot correctly predicts whether intervention helps/harms across benchmarks
- Oracle analysis: even perfect failure prediction yields only 4-8pp gains due to intrinsic mid-trajectory correction costs
- Scaling critic from 0.6B to 14B doesn't improve prediction quality in their data regime

## Key concerns
- Only two benchmarks tested (ALFWorld and one other); need broader task diversity to claim generality
- Pilot assumes distribution match between pilot tasks and deployment — not stated or validated
- Single intervention strategy tested; results may not generalize to other intervention types
- "Disruption rate dominated by agent properties" claim needs more ablation across agent architectures
