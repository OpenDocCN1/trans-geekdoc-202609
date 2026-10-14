```
```text
1: Choose approximating distribution family Q(x; θ)
2: Initialize θ
3: repeat
4:     for a fixed q(x|y; θ), find
5:         θⁿᵉʷ = argmax_θ Ĩ(X; Y)
6:     for a fixed θ, find
7:         qₙₑw(x|y; θ) = argmax_q(x|y) Ĩ_Q(X; Y)
8: until convergence
```
```

**Figure 3.7** Mutual information maximization pseudo-code

The preceding algorithm alternates between finding a set of parameters that maximize the MI lower bound and finding the approximate distribution.

In this section, we saw how we can use the definitions of entropy, mutual information, and KL divergence to derive a lower bound that could then be iteratively maximized by updating our approximation distribution q. In the following chapter, we will look at ML from a computer science perspective and explore useful data structures and algorithmic paradigms.

# ### 3.5 Exercises

+   1. **3.1** Compute KL divergence between two univariate Gaussians: q(x) ~ N(μ₁, σ₁²) and q(x) ~ N(μ₂, σ₂²).
+   2. **3.2** Compute E[X], Var(X), and H(X) for a Bernoulli distribution.
+   3. **3.3** Derive the mean, mode, and variance of a Beta(a, b) distribution.

# ## Summary

+   - The main idea of variational inference is to choose an approximate distribution q(x) from a family of tractable distributions and then make this approximation as close as possible to the true posterior distribution p(x).
+   - An evidence lower bound is an objective function that we seek to maximize to learn the variational parameters of our model.
+   - In mean-field approximation, we assume the approximate distribution q(x) is fully factorized.
+   - Mutual information maximization can be carried out by deriving and maximizing the MI lower bound.