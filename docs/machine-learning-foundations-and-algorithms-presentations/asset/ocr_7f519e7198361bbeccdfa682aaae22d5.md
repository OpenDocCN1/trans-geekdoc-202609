# # Variational Inference with GMMs

# ## Gaussian Mixture Models:

$q(x) = \sum q(o)q(x|o), \text{ with } q(x|o) = \mathcal{N}(x|\mu_o, \Sigma_o)$

+   - Where o is now the latent variable
- Very flexible, can represent multi-modality
- Also desirable in RL -> learn multiple solutions!
- Might need a lot of components

![](bbox=[0.727, 0.276, 0.943, 0.532])

# ## Problem: Optimizing the l-projection

$$\arg \min_q \text{KL}(q(x)||p^*(x)) = \int_x q(x) \log \frac{q(x)}{p^*(x)} dx$

... for GMMs is hard (no natural gradient solution exists)

+   - How to do this exactly will not be covered ...