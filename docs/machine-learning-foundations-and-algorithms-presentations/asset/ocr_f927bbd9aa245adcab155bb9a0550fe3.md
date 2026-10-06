# # Generative vs. discriminative modelling

# Discriminative Models:

![](bbox=[0.241, 0.323, 0.391, 0.417])

# Discriminative

![](bbox=[0.726, 0.403, 0.917, 0.765])

+   - Directly assume some functional form for $p(c|x)$ (or any other predictor $f(x)$ that returns the class label).
- This is a ‘discriminative’ model of the data!
- Estimate parameters of $p(c|x)$ directly from training data

# Modelling needs to consider only points on the border

+   - Typically much simpler than generative modelling
- We therefore concentrate on discriminative models