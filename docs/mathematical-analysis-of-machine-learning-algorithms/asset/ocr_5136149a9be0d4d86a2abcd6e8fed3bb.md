This implies that

L(\hat{f}, \mathcal{D}) \le \frac{1}{n} \sum_{i=1}^{n} L(\hat{f}(X_i), Y_i) + \frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} \underbrace{-\frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} + \epsilon_M + \epsilon_B \|\hat{f}\|_{\mathcal{H}}}_{V}
\le \frac{1}{n} \sum_{i=1}^{n} L(\hat{f}(X_i), Y_i) + \frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} + \epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}
\le \frac{1}{n} \sum_{i=1}^{n} L(f(X_i), Y_i) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^{2} + \epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}
\le L(f, \mathcal{D}) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^{2} + \epsilon_B \|f\|_{\mathcal{H}} + 2\epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}.

The first inequality used (9.13). The second inequality can be obtained by maximizing V over \|\hat{f}\|_{\mathcal{H}}. The third inequality used the fact that \hat{f} is the solution of (9.10). The last inequality used (9.13) again.

**Example 9.28** Consider the soft-regularized SVM in (9.10). We can let γ = 1 and M₀ = 1/B. It follows that if we take λ = O(1/√n), then we get an oracle inequality from Corollary 9.27 with a convergence rate of O(√(ln ln n / n)).

# 9.4 Vector-Valued Functions

We now consider vector-valued functions using kernels. In this case, we have f(x): 𝒳 → ℝ^q for some q > 1. Let f(x) = [f₁(x),...,f_q(x)]. If we consider the feature space representation, then there are two possibilities. One is to treat these functions as sharing the same feature vector, but with different w:

f_ℓ(x) = ⟨w_ℓ, ψ(x)⟩      (ℓ = 1,...,q).

Another view is to consider the same w, but with different features for different dimension:

f_ℓ(x) = ⟨w, ψ(x,ℓ)⟩. (9.14)

The second view is more general because we may write the first view as follows. We concatenate the feature representation by letting w = [w₁,...,w_q] and ψ(x,ℓ) = [0,...,0,ψ(x),0,...,0] with only the ℓth concatenating component to be ψ(x), and the other components as zeros. With this representation, ⟨w, ψ(x,ℓ)⟩ = ⟨w_ℓ, ψ(x)⟩. In the following discussions, we focus on (9.14).

Similar to (9.2), we have the following formulation in feature representation:

ĥw = arg min_{w∈ℋ} [ 1/n ∑_{i=1}^{n} L(⟨w, ψ(X_i,·)⟩, Y_i) + λ/2 ‖w‖² ], (9.15)