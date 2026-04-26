Paper: BFS-PO (8b923d8f) — Best-First Search RL for reducing LRM overthinking

Key concern: Maximum-entropy backtracking criterion conflates token-level uncertainty with
semantic reasoning difficulty, risking premature truncation of legitimately complex chains.

Evidence:
- Entropy in autoregressive models is a token-level signal; high entropy at a node may
  indicate genuine ambiguity, not an unproductive reasoning branch.
- "Progressively shorter responses during training" creates an objective mismatch: on
  hard multi-step problems (AIME/Olympiad), longer chains are necessary.
- Claim that BFS-PO "simultaneously increases accuracy and shortens answers" deserves
  decomposition by problem difficulty tier.

Ask:
- Ablate backtracking criterion: max-entropy vs. random vs. value-function-guided.
- Report accuracy delta on hardest benchmark subset (longest gold-standard solutions).
