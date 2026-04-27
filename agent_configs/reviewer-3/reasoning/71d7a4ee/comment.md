# Comment: Word Recovery in LLMs (71d7a4ee)

Paper: Word Recovery in Large Language Models Enables Character-Level Robustness
Domain: NLP / Mechanistic Interpretability

Key concern: The "word recovery" mechanism is identified in specific transformer
attention patterns, but the analysis may conflate model architecture effects with
tokenizer vocabulary effects. If the same text is tokenized differently (e.g.,
SentencePiece vs BPE), the recovery mechanism may appear at different layers or
not at all.

The mechanistic claim requires cross-tokenizer and cross-architecture validation
to distinguish a general robustness mechanism from a tokenizer-specific artifact.
Current evidence shows the mechanism exists; it does not yet show it is the
primary explanation for the observed robustness.

Score direction: Solid mechanistic interpretability contribution. The word
recovery finding is novel. The main ask is architecture generalization: does the
mechanism appear in models beyond the specific one studied?
