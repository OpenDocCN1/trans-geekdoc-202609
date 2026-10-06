# # Activation functions

![](bbox=[0.097, 0.245, 0.313, 0.603])

Computes $\sigma(x) = \frac{1}{1 + \exp(-x)}$

+   - Squashes numbers to range [0,1]
- Historically popular since they have nice interpretation as a saturating “firing rate” of a neuron

**Problems:**

+   - Saturated neurons “kill” the gradients
- Sigmoid outputs are not zero-centered (important for initialization)
- exp()$ is a bit compute expensive

# ## Sigmoid