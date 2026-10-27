In high-dimensional settings, where K is not small relative to N, or perhaps even bigger than N, predictions based on OLS estimates often turn out to be unreliable. While the in-sample R² in this case can be very high, the R² for out-of-sample predictions can be very low or even negative. The reason is that with so many covariates relative to the number of observations, OLS greatly overfits the data by tweaking ĝ to fit noise rather than true signal. These in-sample seemingly predictable patterns then do not repeat in an out-of-sample data set and the predictions perform poorly. In the extreme case with K > N, OLS estimates are not unique. There is an infinite number of solutions for ĝ that all fit the training data perfectly. But much of this perfect fit may be spuriously fitting the ε_i in y_i = f(x_i) + ε_i rather than capturing f(x_i).

Ridge regression. When K is large, it can help predictive performance to penalize the estimator for picking large magnitudes of the elements of ĝ. Ridge regression is one example of such an approach. In Ridge regression (Hoerl and Kennard 1970), the objective is to minimize the same sum-of-squared-error loss function as in OLS, but augmented with a squared L²-norm penalty g′g,

min_g [ 1/N (y - Xg)′ (y - Xg) + γ g′g ] . (2.6)

Thus, the objective has two parts. The first term represents the loss. OLS regression would just minimize this part. The second term represents the penalty where the hyperparameter γ controls the strength of penalization. The solution is

ĝ = (X′X + γ I_K)⁻¹ X′y, (2.7)

where I_K is a K × K identity matrix. By adding a diagonal matrix (a “ridge”) to X′X, the presence of γ I_K in the inverse induces shrinkage of the regression coefficients toward zero. Intuitively, the presence of the penalty term with g′g in (2.6) penalizes estimates that have big magnitudes of the elements of ĝ. As a result, ridge regression ends up with regression coefficient estimates that are closer to zero than OLS estimates (OLS is the special case γ = 0). The L²-shrinkage in ridge regression is an example of regularization to prevent overfitting.

In the special case of X with orthonormal columns, i.e., X′X = I_K, one can see from (2.7) that ridge regression shrinks each element of the coefficient estimate vector from the OLS estimate ĝ_{j,OLS} toward zero by the same factor: ĝ_j = ĝ_{j,OLS}/(1 + γ).

Lasso. An alternative and popular approach is to penalize with an L¹-norm penalty ‖g‖₁ = Σ_{j=1}^K |g_j| instead. This is the lasso method (Tibshirani 1996). The lasso objective is