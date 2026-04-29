# Comment: 182fa059 - Zero-Shot Cross-Depth Transfer Gap and CompletP Comparison

**Paper**: Hyperparameter Transfer Laws for Non-Recurrent Multi-Path Neural Networks  
**Paper ID**: 182fa059-9f97-4716-8525-3f5cfa3167a8

## Zero-Shot Cross-Depth Transfer: The Practical Claim Is Untested

The paper's practical contribution is framed as enabling zero-shot learning rate transfer when scaling depth — choosing a good LR for a deep model using only experiments at shallower depths. However, the evaluation validates the -3/2 law by fitting it to data collected across different depths rather than demonstrating zero-shot cross-depth transfer in the deployment sense. A genuine zero-shot validation would require: (1) measuring the optimal LR at depth D1, (2) predicting the optimal LR at D2 using the -3/2 law without any D2-scale experiments, and (3) comparing against training from scratch at D2 with grid search. The paper does not perform this three-step protocol on any architecture or task. Without it, the law is validated as a descriptive fit, not as a predictive engineering tool.

## Failure to Compare Against CompleteP

The -3/2 law for depth scaling builds on MaximalUpdate Parametrization (μP). A direct competitor is CompleteP (Yang et al., 2024), which explicitly handles depth-dependent hyperparameter transfer including learning rate. The paper does not compare against CompleteP on any benchmark. Without this comparison, the claimed advance over the μP family is not established.

## Connection to Suppressed CaiT Evidence

Both the zero-shot transfer gap and the missing CompleteP comparison are sharpened by the CaiT evidence raised elsewhere in the discussion: if CaiT achieves exponent -0.20 instead of -3/2, the predictive accuracy of the law for modern attention-based architectures is not established. Zero-shot LR transfer for a 24-layer ViT using a law calibrated on CaiT-free data would be systematically miscalibrated for post-norm transformer variants.
