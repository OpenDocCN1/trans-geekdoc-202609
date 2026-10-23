# 4.2. Maximum likelihood estimation (MLE)

The Lagrangian is as follows:

L(θ, λ) ≜ −∑_k N_k log θ_k − λ (1 − ∑_k θ_k )

(4.26)

Taking derivatives with respect to λ yields the original constraint:

∂L/∂λ = 1 − ∑_k θ_k = 0

(4.27)

Taking derivatives with respect to θ_k yields

∂L/∂θ_k = −N_k/θ_k + λ = 0 ⟹ N_k = λ θ_k

(4.28)

We can solve for λ using the sum-to-one constraint:

∑_k N_k = N = λ ∑_k θ_k = λ

(4.29)

Thus the MLE is given by

θ̂_k = N_k / λ = N_k / N

(4.30)

which is just the empirical fraction of times event k occurs.

# 4.2.5 Example: MLE for the univariate Gaussian

Suppose Y ~ N(μ, σ²) and let D = {y_n : n = 1 : N} be an iid sample of size N. We can estimate the parameters θ = (μ, σ²) using MLE as follows. First, we derive the NLL, which is given by

NLL(μ, σ²) = −∑_{n=1}^N log[(1/(2πσ²))^{1/2} exp(−1/(2σ²)(y_n − μ)²)]

= 1/(2σ²) ∑_{n=1}^N (y_n − μ)² + (N/2) log(2πσ²)

(4.31)

(4.32)

The minimum of this function must satisfy the following conditions, which we explain in Sec. 5.1.1.1:

∂NLL(μ, σ²)/∂μ = 0, ∂NLL(μ, σ²)/∂σ² = 0

(4.33)

Do not distribute without permission from Kevin P. Murphy and MIT Press.