
# Sparsity Promoting Estimators and Oracle Properties

When dealing with sparsity promoting estimators such as the LASSO, two crucial issues emerge: (a) whether the estimator, even asymptotically, can obtain the support, if the true parameter vector is a sparse one; and (b) to quantify the performance of the estimator with respect to the estimates of the nonzero components—that is, those components whose index belongs to the support. Especially for LASSO, the latter issue becomes to study whether LASSO behaves as well as the unregularized LS with respect to these nonzero components. This task was addressed for the first time and in a more general setting in [55].

Let the support of the true, yet unknown, `k`-sparse parameter vector `θ[o]` be denoted as `S`. Let also `Σ[|S|]` be the `k × k` covariance matrix `E[x[|S|]x[|S|]^(T)]`, where `x[|S|] ∈ ℝ^(k)` is the random vector that contains only the `k` components of `x`, with indices in the support `S`. Then we say that an estimator satisfies asymptotically the *oracle properties* if:

*   `lim_{n→∞} Prob{ S_{θ̂_n} = S } = 1`; this is known as *support consistency*;
*   `√n ( θ̂_{n|S} - θ_{o|S} ) ⟶ N( 0, σ_η^2 Σ_{|S|}^{-1} )`; this is the `√n`-*estimation consistency*.

We denote as `θ[o|S]` and `θ̂_{n|S}` the `k`-dimensional vectors that result from `θ_o, θ̂_n`, respectively, if we keep the components whose indices lie in the support `S`, and the limit is meant in distribution. In other words, according to the oracle properties, a good sparsity promoting estimator should be able to predict, asymptotically, the true support, and its performance with respect to the nonzero components should be as good as that of a genie-aided LS estimator, which is informed in advance of the positions of the nonzero coefficients.

Unfortunately, the LASSO estimator *cannot* satisfy simultaneously both conditions. It has been shown [55,74,127] that:

*   For support consistency, the regularization parameter `λ := λ[n]` should be time-varying, such that
