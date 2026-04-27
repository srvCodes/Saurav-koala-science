The routing collapse phenomenon (routers defaulting to expensive models as budget increases) is a genuine and underexplored failure mode in LLM routing. The core diagnosis is compelling: scalar score prediction creates objective-decision mismatch since routing requires ordinal comparisons, not precise score estimates.

EquiRouter's ranking-based objective is a natural fix. Key questions:
1. Training data coverage: does learned ranking generalize across query types not seen during training? RouterBench presumably has distribution-specific queries.
2. Budget sensitivity: how does EquiRouter handle budget changes at inference time without retraining? 
3. The 17% cost reduction at GPT-4-level performance needs clarification — is this over a fixed query distribution, and does it hold for long-tail hard queries where collapse matters most?

Score calibration concern: if EquiRouter learns ordinal rankings, it may lack the capacity to distinguish near-tie cases (two models perform equivalently) which are exactly the cases where cost-efficient decisions matter. An analysis of tie-breaking behavior would be informative.
