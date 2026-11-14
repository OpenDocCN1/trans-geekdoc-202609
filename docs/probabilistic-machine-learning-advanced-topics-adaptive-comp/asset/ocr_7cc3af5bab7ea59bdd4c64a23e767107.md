in FA (excluding the mean).¹ The disadvantage of this method is that the first L visible variables, known as the **founder variables**, affect the interpretation of the latent factors, and so must be chosen carefully.

+   • **Sparsity promoting priors on the weights.** Instead of pre-specifying which entries in **W** are zero, we can encourage the entries to be zero, using ℓ₁ regularization [ZHT06], ARD [Bis99; AB08], or spike-and-slab priors [Rat+09]. This is called sparse factor analysis. This does not necessarily ensure a unique MAP estimate, but it does encourage interpretable solutions.

+   • **Choosing an informative rotation matrix.** There are a variety of heuristic methods that try to find rotation matrices **R** which can be used to modify **W** (and hence the latent factors) so as to try to increase the interpretability, typically by encouraging them to be (approximately) sparse. One popular method is known as varimax [Kai58].

+   • **Use of non-Gaussian priors for the latent factors.** If we replace the prior on the latent variables, p(**z**), with a non-Gaussian distribution, we can sometimes uniquely identify **W**, as well as the latent factors. See e.g., [KKH20] for details.

# 28.3.2 Probabilistic PCA

In this section, we consider a special case of the factor analysis model in which **W** has orthogonal columns and Ψ = σ²**I**, so p(**x**) = N(**x**|**μ**, **C**) where **C** = **WWᵀ** + σ²**I**. This model is called **probabilistic principal components analysis** (**PPCA**) [TB99], or **sensible PCA** [Row97].

The advantage of PPCA over factor analysis is that the MLE has a closed form solution, as we show in Section 28.3.2.2. The advantage of PPCA over non-probabilistic PCA is that the model defines a proper likelihood function, which makes it easier to extend in various ways e.g., by creating mixtures of PPCA models (see Section 28.3.3).

# 28.3.2.1 Derivation of the MLE

The log likelihood for PPCA is given by

```
log p(X|μ, W, σ²) = -ND/2 log(2π) - N/2 log|C| - 1/2 Σⁿ₌₁ (**xₙ** - **μ**)ᵀ **C⁻¹** (**xₙ** - **μ**) (28.65)
```

The MLE for **μ** is x̄. Plugging in gives

```
log p(X|μ, W, σ²) = -N/2 [D log(2π) + log|C| + tr(**C⁻¹ S**)] (28.66)
```

where S = 1/N Σⁿ₌₁ (**xₙ** - x̄)(**xₙ** - x̄)ᵀ is the empirical covariance matrix. In [TB99; Row97] they show that the maximum of this objective must satisfy

```
Ŵ = **U_L** (Λ_L - σ²**I**)¹ᐟ² **R** (28.67)
```

1. We get D parameters for Ψ and DL for **W**, but we need to remove L(L - 1)/2 degrees of freedom coming from **R**, since that is the dimensionality of the space of orthogonal matrices of size L × L. To see this, note that there are L - 1 free parameters in **R** in the first column (since the column vector must be normalized to unit length), there are L - 2 free parameters in the second column (which must be orthogonal to the first), and so on.