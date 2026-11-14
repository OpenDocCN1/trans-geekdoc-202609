![](bbox=[0.15, 0.1, 0.85, 0.32])

Figure 28.6: Illustration of the FA generative process, where we have L = 1 latent dimension generating D = 2 observed dimensions; we assume \(\Psi = \sigma^2 \mathbf{I}\). The latent factor has value \(z \in \mathbb{R}\), sampled from \(p(z)\); this gets mapped to a 2d offset \(\delta = z\mathbf{w}\), where \(\mathbf{w} \in \mathbb{R}^2\), which gets added to \(\mu\) to define a Gaussian \(p(\mathbf{x}|z) = \mathcal{N}(\mathbf{x}|\mu + \delta, \sigma^2 \mathbf{I}\). By integrating over \(z\), we “slide” this circular Gaussian “spray can” along the principal component axis \(\mathbf{w}\), which induces elliptical Gaussian contours in \(\mathbf{x}\) space centered on \(\mu\). Adapted from Figure 12.9 of [Bis06].

# 28.3.1.2 Computing the posterior

We can compute the posterior over the latent codes, \(p(\mathbf{z}|\mathbf{x})\), using Bayes’ rule for Gaussians. In particular, from Equation (2.121), we have

```
p(\mathbf{z}|\mathbf{x}) = \mathcal{N}(\mathbf{z}|\mu_{z|x}, \Sigma_{z|x})
\Sigma_{z|x} = (\mathbf{I} + \mathbf{W}^T \Psi^{-1} \mathbf{W})^{-1} = \mathbf{I} - \mathbf{W}^T (\mathbf{W}\mathbf{W}^T + \Psi)^{-1} \mathbf{W}
\mu_{z|x} = \Sigma_{z|x} [\mathbf{W}^T \Psi^{-1} (\mathbf{x} - \mu)] = \mathbf{W}^T (\mathbf{W}\mathbf{W}^T + \Psi)^{-1} (\mathbf{x} - \mu)
```

We can avoid inverting the \(D \times D\) matrix \(\mathbf{C} = \mathbf{W}\mathbf{W}^T + \Psi\) by using the matrix inversion lemma:

```
\mathbf{C}^{-1} = (\mathbf{W}\mathbf{W}^T + \Psi)^{-1}
= \Psi^{-1} - \Psi^{-1} \mathbf{W} (\mathbf{I} + \mathbf{W}^T \Psi^{-1} \mathbf{W})^{-1} \mathbf{W}^T \Psi^{-1}
```

where \(\mathbf{L} = \mathbf{I} + \mathbf{W}^T \Psi^{-1} \mathbf{W}\) is \(L \times L\).

# 28.3.1.3 Computing the likelihood

In this section, we discuss how to efficiently compute the log (marginal) likelihood, which is given by

```
\log p(\mathbf{x}|\mu, \mathbf{C}) = -\frac{1}{2} [D \log(2\pi) + \log \det(\mathbf{C}) + \hat{\mathbf{x}}^T \mathbf{C}^{-1} \hat{\mathbf{x}}]
```