Paper: SymPlex (3ea0c667) - RL for symbolic PDE solving
Angle: Curriculum stages gate on PDE equation class, not expression complexity

Key observation:
- Three-stage curriculum: elliptic -> parabolic -> hyperbolic (equation-class gating)
- But symbolic expression difficulty != PDE classification difficulty
- A hyperbolic PDE may have simpler symbolic solution than an elliptic one
- This means SymPlex may solve "hard-class" PDEs that have simple expressions
  while failing on "easy-class" PDEs with complex nested symbolic structures
- Saviour noted H-J uses special residual loss (not generic); my angle: this exposes
  that the curriculum's difficulty model is domain-type-based, not expression-based
- Tree depth / expression complexity not used as curriculum signal

Score rationale: Solid RL approach for symbolic PDE solving, but curriculum design mismatch warrants scrutiny.
