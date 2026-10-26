We can take b = M², c₀ = 0, and c₁ = 4M². Let λ = 4M²/n, and note that ψ(b/(λn)) = ψ(0.25) < 0.6. We obtain the following bound from Corollary 10.20. With probability at least 1 − δ,

0.4 𝔼_{w∼\hat{q}(·|S_n)} φ(w,𝒟) ≤ 𝔼_{w∼\hat{q}(·|S_n)} φ(w,𝒮_n) + \frac{4M²}{n} [KL(\hat{q}||q₀) + ln(1/δ)] .

For least squares regression with sub-Gaussian noise, one can also perform a more direct calculation of logarithmic moment generating function with a slightly improved result. See Proposition 12.21.

A more recent development of the information theoretical approach to generalization analysis is to rewrite the expected generalization result in Theorem 10.18 in terms of the mutual information between a learning algorithm 𝒜 and the training data 𝒮_n. Using the notations of Theorem 10.18, we can define the mutual information of 𝒜 and 𝒮_n as follows:

I(𝒜,𝒮_n) = 𝔼_{𝒮_n} 𝔼_{w∼\hat{q}(·|S_n)} ln \frac{\hat{q}(w|𝒮_n)}{\hat{q}(w)}, \quad \hat{q}(w) = 𝔼_{𝒮_n} \hat{q}(w|𝒮_n).

We note that the mutual information optimizes the expected KL-divergence in Theorem 10.18 over prior q₀:

I(𝒜,𝒮_n) = inf_{q₀} 𝔼_{𝒮_n} KL(\hat{q}||q₀).

The following result is a direct consequence of Theorem 10.18 with q₀(w) = \hat{q}(w).

# Corollary 10.22 Under the assumptions of Theorem 10.18, we have the following expected generalization bound for all λ > 0:

𝔼_{𝒮_n} 𝔼_{𝒜} Λ(λ,𝒟) ≤ 𝔼_{𝒮_n} 𝔼_{𝒜} \frac{1}{n} \sum_{i=1}^{n} φ(w,Z_i) + λ I(𝒜,𝒮_n),

*where 𝔼_𝒜 denotes the expectation over the randomization of algorithm 𝒜; that is, w ∼ \hat{q}(·|𝒮_n).*

Similar to Example 10.19, we have the following result for sub-Gaussian loss functions. This is the result that is often stated in the literature.

# Example 10.23 Assume that sup[φ(w,z) − φ(w,z′)] ≤ M. Then we have the sub-Gaussian inequality

Λ(λ) ≤ \frac{λ² M²}{8}.

We obtain from Corollary 10.22,

𝔼_{𝒮_n} 𝔼_{𝒜} φ(w,𝒟) ≤ 𝔼_{𝒮_n} 𝔼_{𝒜} \frac{1}{n} \sum_{i=1}^{n} φ(w,Z_i) + inf_{λ>0} [ λ I(𝒜,𝒮_n) + \frac{M²}{8 λ n} ] = 𝔼_{𝒮_n} 𝔼_{𝒜} \frac{1}{n} \sum_{i=1}^{n} φ(w,Z_i) + M \sqrt{\frac{I(𝒜,𝒮_n)}{2n}}.

We may also derive fast rate results for the mutual information generalization bound as follows.