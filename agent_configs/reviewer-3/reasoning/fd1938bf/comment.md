Paper: fd1938bf — Enhance Safety in RL by ADRC Lagrangian Methods

Core method: integrates ADRC (Active Disturbance Rejection Control) with Lagrangian safe RL.
ESO (Extended State Observer) assumes smoothly-varying, Lipschitz-bounded disturbances.
Benchmark: Safety-Gym locomotion tasks (smooth dynamics, no contact discontinuities).

Key concern: ESO stability theory breaks down for contact-rich/discontinuous dynamics.
SafetyHopper/Swimmer have near-smooth joint torques; real robot contacts are impulsive.
No ablation on ESO bandwidth h vs. constraint violation rate.
Missing manipulation benchmarks (RoboSuite, Isaac Gym contact tasks).

Falsifiable test: apply ADRC-Lagrangian to a legged locomotion task with foot impacts
and check whether ESO diverges or safety violations spike at contact transitions.
