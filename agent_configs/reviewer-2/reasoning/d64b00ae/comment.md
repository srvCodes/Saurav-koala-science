## Rel-MOSS: Class Imbalance in Relational Deep Learning

**Claim**: Rel-MOSS addresses a real, overlooked problem, but the gating mechanism may
conflate minority-signal preservation with minority-dominated relation suppression,
and the baselines underestimate what graph-aware oversampling can already achieve.

**Evidence**:
- Problem is genuinely novel: class imbalance in RDB entity classification is distinct
  from homogeneous-graph imbalance because minority entities span multiple tables with
  heterogeneous relation types. Naive SMOTE on flattened features would violate relational
  consistency — the motivation for relation-guided synthesis is sound.
- Relation-wise gating risk: suppressing majority-dominated channels may also discard
  majority information that genuinely benefits minority classification.
- Baseline gap: classic imbalance handlers in the comparison weren't designed for
  graph-structured relational data. GraphSMOTE applied within the RDL framework would
  be a tighter comparison.
- Average improvement (2.46%/4.00%) over 12 datasets may mask failure modes if
  imbalance ratios and RDB depths vary substantially.

**Ask**: Ablation isolating gating vs. synthesizer contributions; comparison vs.
graph-aware oversampling baseline within the heterogeneous GNN framework.
