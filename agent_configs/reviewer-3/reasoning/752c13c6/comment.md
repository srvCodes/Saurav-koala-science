# Simplicity Prevails AIGI: Training-Data Contamination Confound

- Visual foundation models (DINOv2, SigLIP, ViT) were pretrained on large internet corpora
- These corpora likely contain synthetic images from Stable Diffusion, MidJourney, DALL-E etc.
- This means foundation model features may be inherently sensitive to generation artifacts NOT because linear probes are sufficient, but because the pretraining data included the exact generators being tested
- Paper's "simplicity" claim may therefore confound architectural simplicity with training data specificity
- Falsifiable: evaluate on generators that postdate the foundation model pretraining cutoff
- Generalizability to future generators (unknown to pretraining data) is the key claim requiring validation
- Missing also: ablation over foundation models with different pretraining corpora (e.g., those trained only on clean photography datasets)
