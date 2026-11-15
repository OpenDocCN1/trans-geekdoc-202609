where

$$\mathcal{L}_{n_j} = \frac{(\sqrt{n}\hat{\vartheta}_j^\text{UR})^2}{\hat{\eta}^2\kappa_j}.$$ 
(4.8.2)

**Theorem 4.9** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and ADL\(_2\)-risk of the positive-rule Saleh R-estimator, \(\hat{\vartheta}_n^{\text{SR}+}\), are respectively given by

$$\text{ADB}(\hat{\vartheta}_n^{\text{SR}+}(\lambda)) = -\eta \left(\Delta_j\mathcal{H}_3(\lambda^2,\Delta^2) - \lambda \left(\Phi(\lambda - \Delta_j)\right.\right.\left.\left. -\Phi(\lambda + \Delta_j)\right)\right| j = 1, \dots, p\right)^\top, $$

and

$$\text{ADL}_2\text{-risk}(\hat{\vartheta}_n^{\text{SR}+}(\lambda)) = \eta^2\left(\sum_{j=1}^p \left\{\kappa_j \left(1 - \mathcal{H}_3(\lambda^2,\Delta_j^2)\right)\right.\right.\left.\left. + \Delta_j^2 \left(2\mathcal{H}_3(\lambda^2,\Delta_j^2) - \mathcal{H}_5(\lambda^2,\Delta_j^2)\right)\right.\right.\left.\left. + \lambda^2(1 - \mathcal{H}_1(\lambda^2,\Delta_j^2)) - 2\lambda \left(\phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j)\right)\right\}\right). $$

To obtain the LASSO R-estimator, one minimizes the rank dispersion function (Jaeckel, 1972) with an \(L_1\) penalty as follows,

$$\hat{\vartheta}_{n_j}^{\text{LassoR}}(\lambda) = \left(\underset{\vartheta}{\text{argmin}} \left\{\sum_{j=1}^{n_j}|y_{i_j} - \vartheta|a_n^+(R_{n_j}(\vartheta_i)) + \lambda\kappa_j^\frac{1}{2}|\vartheta_i|\right\}\right| j = 1, \dots, p\right)^\top. $$

Now, consider a family of diagonal linear projections,

$$T_\text{DP}(\vartheta, \lambda) = \left(\lambda_1\hat{\vartheta}_{n_1}^\text{UR}, \dots, \lambda_p\hat{\vartheta}_{n_p}^\text{UR}\right)^\top. $$

Such estimators _keep_ or _kill_ each coordinate. Suppose we have available an oracle which would supply for us the optimal coefficients, \((\lambda_j| j = 1, \dots, p)\), for use in the diagonally linear projection scheme. These ideal coefficients are \(I(|\delta_j| > \eta\sqrt{\kappa_j})\), \(j = 1, \dots, p\). These yield the ideal asymptotic distributional L\(_2\)-risk as

$$\text{ADL}_2^*\text{-risk}(T_\text{DP}(\vartheta, \lambda)) = \sum_{j=1}^p \min(\delta_j^2, \eta^2\kappa_j). $$

Now suppose \(p_1\) of them satisfy \(\{\delta_j^2 < \eta^2| j = 1, \dots, p\}\) and \(p_2\) of them satisfy \(\{\delta_j^2 > \eta^2| j = 1, \dots, p\}\). Then we obtain \(\text{ADL}_2^*\text{-risk}(T_\text{DP}(\vartheta, \lambda))\) as

$$\text{ADL}_2^*\text{-risk}(\hat{\vartheta}_n^{\text{LassoR}}(\lambda)) = \eta^2(\text{tr}(\mathcal{K}_1) + \Delta^2\text{Ch}_{min}(\mathcal{K}_2)), $$