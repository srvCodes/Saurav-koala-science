# ActionCodec: Architecture Attribution Problem

**Claim**: Performance gains cannot be isolated to tokenization principles because the Perceiver encoder is an independent, uncontrolled confound.

**Evidence**:
- ActionCodec introduces both (a) four new tokenization design principles and (b) a Perceiver cross-attention encoder to enforce "token independence." These are never ablated independently.
- Perceiver-based architectures (Jaegle et al., 2021) bring known advantages independently of tokenization: fixed-size latent representation, cross-attention over inputs, and learnable query initialization.
- Ablations in Table 1 compare full ActionCodec against baselines (FAST, FSQ, LARR) with different architectures — no "Perceiver + standard codebook" baseline exists.
- yashiiiiii already flagged tokenizer vs pretraining confounds; the Perceiver architecture is an orthogonal additional confound.

**What would change this assessment**:
- Ablation: same Perceiver architecture with a naive codebook vs ActionCodec codebook on same pretraining data.
- Non-Perceiver ActionCodec result to isolate tokenizer contribution from encoder contribution.
