# a. Compute the marginal distribution for each dimension.

p(x₁) = ∫ 0.4 (𝒩([10],[1 0],[2],[0 1]) + 0.6 𝒩([0],[8.4 2.0],[0],[2.0 1.7])) dx₂  (6.1)
= 0.4 ∫ 𝒩([10],[1 0],[2],[0 1]) dx₂ + 0.6 ∫ 𝒩([0],[8.4 2.0],[0],[2.0 1.7]) dx₂  (6.2)
= 0.4 𝒩(10, 1) + 0.6 𝒩(0, 8.4).

From (6.1) to (6.2), we used the result that the integral of a sum is the sum of the integrals.
Similarly, we can get
p(x₂) = 0.4 𝒩(2, 1) + 0.6 𝒩(0, 1.7).

# b. Compute the mean, mode and median for each marginal distribution.

Mean:
𝔼(x₁) = ∫ x₁ p(x₁) dx₁
= ∫ x₁ (0.4 𝒩(x₁ | 10, 1) + 0.6 𝒩(x₁ | 0, 8.4)) dx₁  (6.3)
= 0.4 ∫ x₁ 𝒩(x₁ | 10, 1) dx₁ + 0.6 ∫ x₁ 𝒩(x₁ | 0, 8.4) dx₁  (6.4)
= 0.4 · 10 + 0.6 · 0 = 4.
From step (6.3) to step (6.4), we use the fact that for Y ~ 𝒩(μ, σ), where 𝔼[Y] = μ.
Similarly,
𝔼(x₂) = 0.4 · 2 + 0.6 · 0 = 0.8.

Mode: In principle, we would need to solve for
 d p(x₁)/d x₁ = 0  and  d p(x₂)/d x₂ = 0.
However, we can observe that the modes of each individual distribution are the peaks of the Gaussians, that is the Gaussian means for each dimension. Median:
∫_{-∞}^{a} p(x₁) dx₁ = 1/2.

# c. Compute the mean and mode for the 2 dimensional distribution.

Mean:
From (6.30), we know that
𝔼[ [x₁],[x₂] ] = [ 𝔼[x₁] , 𝔼[x₂] ] = [ 4 , 0.8 ].
Mode:
The two dimensional distribution has two peaks, and hence there are