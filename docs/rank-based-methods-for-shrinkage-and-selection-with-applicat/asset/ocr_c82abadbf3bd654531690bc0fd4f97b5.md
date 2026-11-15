We consider the expressions for the asymptotic distributional bias (ADB), L$_2$-risk (ADL$_2$-risk) and the weighted ADL$_2$-risk of various R-estimators. The ADB and ADL$_2$-risk expressions are defined by

\(\text{ADB}(\hat{\theta}_n^*) = \left( \lim_{n \to \infty} \mathbb{E} \left[ \sqrt{n}(\hat{\theta}_{1n}^* - \theta_1)^\top \right], \lim_{n \to \infty} \mathbb{E} \left[ \sqrt{n}(\hat{\theta}_{2n}^* - \theta_2)^\top \right] \right)^\top,\)
(4.4.5)

and

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^* : \mathbf{W}_1, \mathbf{W}_2) = \lim_{n \to \infty} \mathbb{E} \left[ n(\hat{\theta}_{1n}^* - \theta)^\top \mathbf{W}_1(\hat{\theta}_{1n}^* - \theta_1) \right]\)
\(+ \lim_{n \to \infty} \mathbb{E} \left[ n(\hat{\theta}_{n2}^* - \theta)^\top \mathbf{W}_2(\hat{\theta}_{2n}^* - \theta_2) \right]\)
\(= \text{tr}(\mathbf{W}_1 \mathbf{M}_1) + \text{tr}(\mathbf{W}_2 \mathbf{M}_2) \quad (4.4.6)\)

where \(\mathbf{W}_1\) and \(\mathbf{W}_2\) are the weight matrices of \(p_1\) and \(p_2\) dimensions, respectively.

If \(\mathbf{W}_1 = \mathbf{I}_{p_1}\) and \(\mathbf{W}_2 = \mathbf{I}_{p_2}\), then we obtain the trace of the MSE matrices of \(\mathbf{M}_1\) and \(\mathbf{M}_2\) as \(\text{tr}(\mathbf{M}_1) = \sum_{i=1}^{p_1} \chi_i\) and \(\text{tr}(\mathbf{M}_2) = \sum_{i=p_1+1}^p \chi_i\), respectively, where

\(\mathbf{M}_i = \lim_{n \to \infty} n \mathbb{E} \left[ (\hat{\theta}_{in}^* - \theta_i)(\hat{\theta}_{in}^* - \theta_i)^\top \right], \quad \forall i = 1, 2.\)

Thus,

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^* : \mathbf{W}_1, \mathbf{W}_2) = \text{ADL}_2\text{-risk}(\hat{\theta}_{1n}^* : \mathbf{W}_{p_1})\)
\(+ \text{ADL}_2\text{-risk}(\hat{\theta}_{2n}^* : \mathbf{W}_{p_2}).\)

Briefly, the unrestricted R-estimator of \(\theta\) may be written as \((\hat{\theta}_{1n}^{\text{UR}\top}, \hat{\theta}_{2n}^{\text{UR}\top})^\top\) with the marginal asymptotic distribution of \(\hat{\theta}_{in}^{\text{UR}}\) given by \(\mathcal{N}_{p_i}(\theta_i, \eta^2 \mathcal{K}_i)\), where \(\mathcal{K} = \text{blockdiagonal}(\mathcal{K}_1, \mathcal{K}_2)\).

# **Theorem 4.1** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and ADL$_2$-risk of the unrestricted R-estimator, \(\hat{\theta}_n^{\text{UR}}\), are respectively given by

\(\text{ADB}(\hat{\theta}_n^{\text{UR}}) = (\mathbf{0}_{p_1}^\top, \mathbf{0}_{p_2}^\top)^\top,\)
\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{UR}}) = \eta^2 \left( \sum_{i=1}^{p_1} \chi_i + \sum_{i=p_1+1}^{p} \chi_i \right).\)