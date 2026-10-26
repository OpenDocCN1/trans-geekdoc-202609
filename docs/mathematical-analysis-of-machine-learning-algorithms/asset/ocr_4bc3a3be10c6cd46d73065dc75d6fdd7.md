Now by using the logarithmic moment generating functions of Chapter 2, we obtain the following results.

# Theorem 13.3 (Martingale Sub-Gaussian Inequality)

Consider a sequence of random functions ξ₁(S₁), …, ξₜ(Sₜ), … Assume each ξᵢ is sub-Gaussian with respect to Zᵢ^(y):

$$\ln \mathbb{E}_{Z_i^{(y)}} e^{\lambda \xi_i} \le \lambda \mathbb{E}_{Z_i^{(y)}} \xi_i + \frac{\lambda^2 \sigma_i^2}{2}$$

for some σᵢ that may depend on Sᵢ₋₁ and Zᵢ^(x). Then for all σ > 0, with probability at least 1 − δ,

$$\forall n > 0: \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i < \sum_{i=1}^n \xi_i + \left(\sigma + \frac{\sum_{i=1}^n \sigma_i^2}{\sigma}\right) \sqrt{\frac{\ln(1/\delta)}{2}}.$$

Proof We can let λ = √{2 ln(1/δ)}/σ, and then apply the first inequality of Theorem 13.2.

Since we allow σᵢ to be data dependent in Theorem 13.3, we cannot in general choose σ² = ∑ᵢ₌₁ⁿ σᵢ². However, if σᵢ does not depend on data, then we can further optimize σ for specific time horizon n. In particular, a direct consequence of the sub-Gaussian inequality is the additive Chernoff bound, which can be stated below. It is often referred to as Azuma's inequality (Azuma, 1967).

# Theorem 13.4 (Azuma's Inequality)

Consider a sequence of random functions ξ₁(S₁), …, ξₙ(Sₙ) with a fixed number n > 0. If for each i, sup ξᵢ − inf ξᵢ ≤ Mᵢ for some constant Mᵢ, then with probability at least 1 − δ,

$$\frac{1}{n} \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i < \frac{1}{n} \sum_{i=1}^n \xi_i + \sqrt{\frac{\sum_{i=1}^n M_i^2 \ln(1/\delta)}{2 n^2}}.$$

Proof Using the sub-Gaussian moment bound (see Example 2.14), we can obtain the desired bound by taking σᵢ = Mᵢ/2, and 4σ² = ∑ᵢ₌₁ⁿ Mᵢ² in Theorem 13.3.

For the analogy of multiplicative Chernoff bound, we can obtain a weaker version than Corollary 2.18.

# Theorem 13.5

Consider a sequence of random functions ξ₁(S₁), …, ξₜ(Sₜ), … such that ξᵢ ∈ [0,1] for all i. We have for λ > 0, with probability at least 1 − δ,

$$\forall n > 0: \frac{1}{n} \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i < \frac{\lambda}{1 - e^{-\lambda}} \frac{1}{n} \sum_{i=1}^n \xi_i + \frac{\ln(1/\delta)}{(1 - e^{-\lambda}) n}.$$

Similarly, for λ > 0, with probability at least 1 − δ,

$$\forall n > 0: \frac{1}{n} \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i > \frac{\lambda}{e^{\lambda} - 1} \frac{1}{n} \sum_{i=1}^n \xi_i - \frac{\ln(1/\delta)}{(e^{\lambda} - 1) n}.$$