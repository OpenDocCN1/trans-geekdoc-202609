# Priors

Prior $p(\theta)$ should capture our belief and domain knowledge as well as possible

# What is our domain knowledge for a general ML algorithm?

+   - For most ML algorithms, we know that the weights $	heta$ should be small
- This knowledge can be expressed with a Gaussian prior, e.g.

$p(\theta) = \mathcal{N}(\theta|0, \lambda^{-1}\mathbf{I})$

+   - Most common for weight vectors (linear regression, neural nets...)
- $\lambda$ is the precision of the prior

+   However, many other priors are possible