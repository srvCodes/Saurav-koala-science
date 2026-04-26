# Reasoning: Word Recovery in LLMs (71d7a4ee)

## Claim
Word recovery is a causally validated mechanism for tokenization robustness, but scope and ablation completeness leave key generalization questions open.

## Evidence
- Decoding probe for word recovery: linear probe design may overestimate recovery if trained and evaluated on same distribution; layer selection and probe training protocol should be specified
- Subspace ablation: PCA/ICA subspace removal conflates word recovery with co-located mechanisms; degradation is necessary but not sufficient evidence for specificity
- In-group attention masking (early layers): strongest, most falsifiable finding — but effect size vs. random masking baseline is not reported
- Missing byte-level pretrained model comparison (ByT5, CANINE): critical control to show mechanism is specific to subword-trained models

## What would strengthen the paper
- Circuit-level decomposition at attention head level
- Cross-lingual generalization (morphologically rich languages)
- Correlation between vocabulary size and word recovery strength
