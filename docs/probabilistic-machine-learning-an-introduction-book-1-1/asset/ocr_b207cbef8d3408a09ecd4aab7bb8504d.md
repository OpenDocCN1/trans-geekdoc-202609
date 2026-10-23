# Prior

The conjugate prior is known as the **inverse Wishart** distribution, which is a distribution over positive definite matrices. This has the following pdf:

IW(Σ | Š, ν̃) ∝ |Σ|^{-(ν̃+D+1)/2} exp( -½ tr(Š Σ^{-1}) )   (7.107)

Here ν̃ > D − 1 is the degrees of freedom (dof), and Š is a symmetric pd matrix. We see that Š plays the role of the prior scatter matrix, and N₀ ≡ ν̃ + D + 1 controls the strength of the prior, and hence plays a role analogous to the sample size N.

If D = 1, the inverse Wishart reduces to the inverse Gamma:

IW(σ² | s^{-1}, ν) = IG(σ² | ν/2, s/2)   (7.108)

If s = 1, this reduces to the inverse chi-squared distribution.

# Posterior

Multiplying the likelihood and prior we find that the posterior is also inverse Wishart:

p(Σ | D, μ) ∝ |Σ|^{-N/2} exp( -½ tr(Σ^{-1} S_μ) ) |Σ|^{-(ν̃+D+1)/2} exp( -½ tr(Σ^{-1} Š) )   (7.109)
= |Σ|^{-(N+(ν̃+D+1))/2} exp( -½ tr[ Σ^{-1} (S_μ + Š) ] )   (7.110)
= IW(Σ | Ŝ, ν̂)   (7.111)
ν̂ = ν̃ + N   (7.112)
Ŝ = Š + S_μ   (7.113)

In words, this says that the posterior strength ν̂ is the prior strength ν̃ plus the number of observations N, and the posterior scatter matrix Ŝ is the prior scatter matrix Š plus the data scatter matrix S_μ.

We posterior mode of the inverse Wishart can be used to derive the shrinkage estimate for Σ discussed in Sec. 4.4.2.

# 7.2.4.3 LKJ prior

The conjugate prior for a covariance matrix is the inverse Wishart. However, this distribution is hard to sample from. Consequently it is common to use the **LKJ distribution** as a prior instead (this is named after the authors of [LKJ09]). This is a prior on correlation matrices C of the form p(C | η) ∝ |C|^{η-1}, so η = 1 leads to a uniform a distribution. We can combine this with a suitable prior for the standard deviation, such as half-Cauchy prior (Sec. 7.2.3.5), to derive a prior for Σ = σ C.

# 7.2.4.4 Posterior of Σ and μ

In this section, we compute p(μ, Σ | D) using a conjugate prior.