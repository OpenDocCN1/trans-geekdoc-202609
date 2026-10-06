# BOHB: Bayesian Optimization & Hyperband

Advantages of Hyperband

+   - Strong anytime performance
- General-purpose
  - Low-dimensional continuous spaces
  - High-dimensional spaces with conditionality, categorical dimensions, etc
- Easy to implement
- Scalable
- Easily parallelizable

# Advantage of Bayesian optimization: strong final performance

Combining the best of both worlds in BOHB

+   - Bayesian optimization
  - for choosing the configuration to evaluate (using a TPE variant)
- Hyperband
  - for deciding how to allocate budgets

> [Falkner, Klein & Hutter, ICML 2018]