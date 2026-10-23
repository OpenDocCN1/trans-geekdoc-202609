![](bbox=[0.15, 0.1, 0.92, 0.35])

Figure 20.9: Illustration of the FA generative process, where we have L = 1 latent dimension generating D = 2 observed dimensions; we assume Ψ = σ²I. The latent factor has value z ∈ ℝ, sampled from p(z); this gets mapped to a 2d offset δ = zw, where w ∈ ℝ², which gets added to μ to define a Gaussian p(x|z) = N(x|μ + δ, σ²I). By integrating over z, we “slide” this circular Gaussian “spray can” along the principal component axis w, which induces elliptical Gaussian contours in x space centered on μ. Adapted from Figure 12.9 of [Bis06].

# 20.2.2 Probabilistic PCA

In this section, we consider a special case of the factor analysis model in which W has orthonormal columns, Ψ = σ²I and μ = 0. This model is called probabilistic principal components analysis (PPCA) [TB99], or sensible PCA [Row97]. The marginal distribution on the visible variables has the form

p(x|θ) = ∫ N(x|Wz, σ²I) N(z|0, I) dz = N(x|μ, C)  (20.41)

where
C = W Wᵀ + σ² I  (20.42)

The log likelihood for PPCA is given by
log p(X|μ, W, σ²) = - N D/2 log(2π) - N/2 log|C| - 1/2 Σ_{n=1}^N (x_n - μ)ᵀ C⁻¹ (x_n - μ)  (20.43)

The MLE for μ is x̄. Plugging in gives
log p(X|μ, W, σ²) = - N/2 [ D log(2π) + log|C| + tr(C⁻¹ S) ]  (20.44)
where S = 1/N Σ_{n=1}^N (x_n - x̄)(x_n - x̄)ᵀ is the empirical covariance matrix.

In [TB99; Row97] they show that the maximum of this objective must satisfy
W = U_L (L_L - σ² I)^{1/2} R  (20.45)