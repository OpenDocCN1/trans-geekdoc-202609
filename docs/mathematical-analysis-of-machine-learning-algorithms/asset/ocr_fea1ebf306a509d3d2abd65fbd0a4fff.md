# Exercises

10.1 In Example 10.9, assume that the vectors [ψ(X) : X ∈ S_n] are orthogonal for ψ(X) ∈ Ψ. Derive a lower bound for the Rademacher complexity of F_{A,L2}(Ψ) via direct calculation.

10.2 Let w_* = e_1 ∈ ℝ^d. Consider ψ(x) = [ψ_1(x),...,ψ_d(x)] ∈ ℝ^d such that for observations {(X_1,Y_1),...,(X_n,Y_n)}, n^{-1/2}[ψ_j(X_1),...,ψ_j(X_n)] are d orthonormal vectors in ℝ^n (j = 1,...,d), and Y_i = w_*^T ψ(X_i) + ε_i, where ε_i ∼ N(0,σ^2) (i = 1,...,n) are zero-mean noises. Consider ridge regression:

\hat{w}(λ) = arg min_w [ 1/n Σ_{i=1}^n (w^T ψ(X_i) - Y_i)^2 + λ ||w||_2^2 ]

Find the optimal λ so that

𝔼_ε ||\hat{w}(λ) - w_*||_2^2

is minimized. Compute the minimum value.

10.3 In the previous example. Consider the Lasso regression:

\hat{w}(λ) = 1/n Σ_{i=1}^n (w^T ψ(X_i) - Y_i)^2 + λ ||w||_1.

For λ > 0, find an upper of

𝔼_ε ||\hat{w}(λ) - w_*||_2^2.

Find λ to approximately minimize the upper bound with logarithmic dependency on d, and compare to that of the ridge regression.

10.4 Consider the uniform convergence bound in Theorem 10.4. Let {1,...,m} = J_1 ∪ ... ∪ J_g be a nonoverlapping partition of {1,...,m} into g groups of size m/g each (we assume m/g is an integer). Let H contain the subsets of {1,...,m} that can be expressed as the union of one or more groups {J_ℓ}. That is, if J ∈ H, then for all ℓ = 1,...,g, either J_ℓ ⊂ J or J_ℓ ∩ J = ∅.

In group sparsity, we consider only the sparse models indexed by F ∈ H.

- Derive a uniform convergence bound for group sparsity, where we consider a uniform bound that holds for all w and F with supp(w) ⊂ F.
- Compare this bound to the sparse learning bound of Theorem 10.4, and derive an estimation method in (10.5) with r(F) obtained using this bound. Explain when group sparsity performs better.

10.5 Use the Rademacher complexity of constrained entropy regularization in Corollary 10.17, and the same techniques in the proof of Corollary 10.14 for the following.

- Derive a data-dependent bound that holds uniformly for all A > 0.
- Use the bound to derive an oracle inequality for the soft regularization version of the Gibbs algorithm, and compare the result to Theorem 10.18.

10.6 Prove Proposition 10.39.

10.7 Consider Theorem 10.37. Assume that √n X is an n × p random matrix, with iid standard Gaussian entries, and \bar{F} is independent of X. Show that there exists an absolute constant c_0 > 0 so that if

n ≥ c_0 |\bar{F}| ln(p),

the irrepresentable condition μ < 1 holds with probability at least 0.5.

10.8 Consider Theorem 10.37 with columns of X normalized: ||X_i||_2 = 1 for all i ∈ [p].