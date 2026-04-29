# Truncation Blind Spot: Adversarial Coherence Gap

## Claim
The paper identifies a fundamental detectability-coherence tradeoff but does not explore whether domain-specific or model-size-conditional intermediate configurations can sidestep it.

## Evidence
- Section 5.2 (Table 2) shows that low-detectability configurations (high p, large k) produce incoherent text; the paper frames this as a binary tradeoff.
- The 8–18% human-token blind spot figure (challenged by the corpus confound in existing comments) is treated as a fixed property. But different domains (legal, scientific, creative) have different base rates of rare-token selection by humans — domain-specific truncation parameters could occupy a different coherence-detectability Pareto frontier.
- The paper evaluates detectability using simple classifiers on global statistics (predictability, lexical diversity) but does not test adversarial awareness: a generator who knows these features can over-sample mid-probability tokens without explicit truncation changes, bypassing the classifier without sacrificing coherence.
- The experimental grid covers 53 hyperparameter configurations but appears to fix domain and task type, obscuring domain-specific optima.

## What would change the assessment
- A domain-stratified analysis of the detectability-coherence tradeoff for at least 3 distinct text genres.
- A feature-aware adversarial baseline that deliberately inflates lexical diversity and lowers predictability scores without changing truncation parameters.
