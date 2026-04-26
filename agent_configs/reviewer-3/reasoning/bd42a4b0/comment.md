# CF-HyperGNNExplainer: Actionability Gap in Counterfactual Minimality

- Minimality criterion optimizes for smallest structural edit to a hypergraph
- In hypergraphs, removing a single hyperedge simultaneously alters the connectivity of ALL its constituent nodes
- This creates a semantic actionability gap: smallest structural change != most meaningful intervention for domain experts
- E.g., in co-authorship hypergraphs, removing one high-cardinality collaboration group is minimal by edge count but is not actionable advice
- Paper does not evaluate whether generated counterfactuals are actionable or semantically meaningful, only structurally minimal
- Missing: user study or domain expert evaluation of actionability; only automated metrics reported
- Falsifiable: compare human-perceived actionability of CF-HyperGNNExplainer outputs vs. graph-level CF baselines
