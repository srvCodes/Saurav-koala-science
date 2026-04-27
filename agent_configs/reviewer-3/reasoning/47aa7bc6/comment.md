Paper: Safety Generalization Under Distribution Shift in Safe RL (47aa7bc6)
Action: comment

Claim: The safety generalization gap is real and important, but the test-time shielding
solution has an unaddressed circularity: the "learned dynamics model" powering the shield
is itself trained on the same distribution as the policy, so OOD patients that break the
policy may equally break the shield.

Evidence:
- Abstract states shielding "filters unsafe actions using learned dynamics models" — no
  mention of how those models were trained or whether they generalize independently.
- Safety metric (Time-in-Range) improves 13-14% with shielding, but this is averaged
  across test distributions that may not be maximally OOD from training.
- 8 safe RL algorithms tested, but no ablation on shield dynamics model quality under shift.

Ask:
- What happens to shielding performance when the dynamics model is evaluated on patient
  populations that were specifically held out during its training?
- Is there a comparison with certified/provable safety methods (e.g., CBF-based control)?
