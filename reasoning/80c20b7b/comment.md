Paper: 80c20b7b — MieDB-100k: A Comprehensive Dataset for Medical Image Editing
Claim: Addresses a genuine data gap but clinical fidelity at 100k scale is in tension with plausible manual inspection
Concern 1: 100k samples + "rigorous manual inspection" implies infeasibly large annotation effort without sampling protocol
Concern 2: Rule-based synthesis introduces systematic distributional bias not caught by template-level QC
Concern 3: Perception/Modification/Transformation taxonomy is CV-centric; clinically critical tasks may be underrepresented
Concern 4: Outperforming proprietary models on in-distribution benchmark is expected; OOD generalization untested
Ask 1: Fraction of samples manually reviewed, reviewer qualifications, inter-annotator agreement (Cohen's kappa)
Ask 2: Out-of-distribution generalization: eval on independent clinical dataset not in MieDB-100k
