# Review: Truncation Blind Spot - Corpus Confound and Incoherence Pareto Argument

## Paper
The Truncation Blind Spot: How Decoding Strategies Systematically Exclude Human-Like Token Choices (ce9dc1c2)

## Central Claims
1. 8-18% of human-selected tokens fall outside typical truncation boundaries
2. Truncation parameters account for most variance in AI text detectability
3. Model scale and architecture do not strongly correlate with detectability
4. Low-detectability configurations often produce incoherent text

## Key Methodological Concern: The Corpus Confound

The study's "human-selected tokens" come from corpora with specific distributional properties. Low-probability tokens in human writing fall into multiple categories that the paper does not disaggregate:

- **Intentional stylistic choices**: archaisms, neologisms, technical vocabulary (legitimate "blind spot" candidates)
- **OCR artifacts and typos**: distributional noise that is "human-selected" only accidentally
- **Domain-specific jargon**: globally rare but locally appropriate tokens (e.g., clinical terms in medical text)
- **Code-switching**: multilingual insertions that have low probability in monolingual models

Without disaggregating these categories, the 8-18% figure is ambiguous. If a substantial fraction of out-of-truncation human tokens are artifacts (typos, OCR errors) rather than genuine communicative choices, the "blind spot" estimate overstates the true gap between human-appropriate and model-reachable token spaces.

**A direct test**: Apply a high-quality spell-checker and language-appropriateness filter to the human corpora before computing the out-of-truncation fraction. If the estimate drops significantly, the blind spot is primarily an artifact confound.

## The Incoherence Pareto Argument (Paper's Own Finding)

The paper's finding that "configurations achieving low detectability often produce incoherent text" is a self-undermining result for the paper's central framing.

If:
1. Evading detection requires low-probability token selection
2. Low-probability token selection produces incoherent text
3. Incoherent text is easily distinguishable from human text by other means

Then truncation boundary modification does not provide a viable path to undetectable-yet-coherent AI text. The detectability "problem" is not solvable through decoding strategy modification alone—it is an inherent consequence of coherence-constrained token selection.

This doesn't undermine the descriptive contribution (the 8-18% figure remains interesting), but it does undermine the implied prescriptive framing that better decoding strategies could close the gap.

## Causality Direction

The paper hypothesizes that truncation *causes* detectability. The evidence is correlational: detectability classifiers work well using features related to truncation (predictability, lexical diversity). But the causal direction could be reversed:
- Human text is structured by syntactic and semantic constraints that create predictable token distributions
- AI text is structured by statistical patterns in pretraining data that create different token distributions
- Both truncation behavior and detectability may be *effects* of the underlying difference in text generation mechanisms, not causes and effects of each other

## Significance Assessment

The descriptive finding (8-18% human token choices outside truncation bounds) is a useful empirical measurement for the AI text detection community. However, the paper's framing—that this "blind spot" is a fundamental limitation of decoding strategies—overstates the causal claim, and the practical implications for improving AI text generation are limited by the incoherence-detectability tradeoff the paper itself documents.
