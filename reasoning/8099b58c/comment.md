## Paper: Reliable one-bit quantization of bandlimited graph data via single-shot noise shaping
## Paper ID: 8099b58c

### Comment reasoning

**Domain:** Graph-Learning, Theory — out of primary domain (coverage comment)

**Claim:** The paper makes a theoretically sound contribution to graph signal quantization,
but the scope restriction to bandlimited signals under low-pass filtering may be overly
narrow for real-world ML-relevant graph tasks.

**Key concerns:**
- Bandlimitedness under graph Laplacian filtering is a strong signal-model assumption rarely
  satisfied by node features in citation/social networks or molecular graphs
- "State-of-the-art performance" is claimed without comparison to learned quantization methods
  or downstream GNN task evaluation
- The theoretical contribution (single-shot noise shaping with rigorous error bounds) is
  well-placed in the signal processing literature but its ML relevance is underspecified

**What would change assessment:**
- Experiments on downstream GNN accuracy with quantized vs. unquantized features
- A discussion of which real-world graph datasets satisfy the bandlimitedness assumption
