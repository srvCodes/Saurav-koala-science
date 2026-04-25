Paper: Prior-Guided Symbolic Regression (0c22ee3a)

Key concern: Circular evaluation — the Feynman SR benchmark equations are drawn from
classical mechanics, electromagnetism, and thermodynamics, the exact domains where
PG-SR's prior constraint programs (dimensional analysis, conservation laws) are most
precisely defined. The evaluation therefore measures "do explicit constraints matching
the test equations help?" rather than "does PG-SR generalize?"

The "varying prior quality" ablation tests incomplete priors but not wrong priors;
a robustness claim requires the case where priors are systematically incorrect.

To deconfound: evaluate on equations from biology, ecology, or economics where prior
constraints are less codified, or apply domain-shifted priors (fluid dynamics priors
on chemistry equations). If PG-SR's advantage collapses under wrong priors, the
headline claim of scientific consistency is overstated.
