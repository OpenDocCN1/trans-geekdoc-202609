If $\mathcal{C}(\cdot; X, y)$ is strongly convex (on a subset of its domain that contains $\hat{\beta}^k, \hat{\beta}^*$) with high probability, then the desired conclusion (4.36) follows readily from (4.37) and the basic inequality $\mathcal{C}(\hat{\beta}^*; X, y) \le \mathcal{C}(\hat{\beta}^k; X, y)$; see (98)-(100) in Donoho and Montanari (2016). Otherwise (as in the case of the Lasso in Section 4.5), further work must be done to show that in a random design setting, it is vanishingly unlikely that $\|\hat{\gamma}^k\|_p$ is small but $\|\hat{\beta}^k - \hat{\beta}^*\|_p$ is large (cf. Bayati and Montanari, 2012, Theorem 1.8 and Lemma 3.1).

# 4.5 AMP for the Lasso

In high-dimensional linear models $y = X\beta + \varepsilon$, the Lasso (Tibshirani, 1996) is a popular method for obtaining sparse estimates of $\beta \in \mathbb{R}^p$ via $\ell_1$-penalised least squares. Given $X \in \mathbb{R}^{n \times p}, y \in \mathbb{R}^n$ and a regularisation parameter $\lambda > 0$, the Lasso estimator is defined by

\(\hat{\beta}^{\mathrm{L}, \lambda} \in \operatorname{argmin}_{\hat{\beta} \in \mathbb{R}^p} \left\{ \frac{1}{2} \| y - X \hat{\beta} \|^2 + \lambda \| \hat{\beta} \|_1 \right\}.\) (4.38)

In the random design setting of (G0) and (G1), Bayati and Montanari (2012) derived an exact expression (4.46) for the asymptotic estimation error of $\hat{\beta}^{\mathrm{L}, \lambda}$ as \(n, p \to \infty\) with \(n/p \to \delta \in (0, \infty)\). By following the GAMP recipe in Section 4.4, we will show how to design and calibrate an AMP iteration that is central to the proof of their main result (Theorem 4.5 below).

To begin with, note that $\hat{\beta}^{\mathrm{L}, \lambda}$ solves a convex optimisation problem of the form (4.22) with \(\ell: (u, v) \mapsto (u-v)^2/2\) and \(J: x \mapsto \lambda|x|\). For \(k \in \mathbb{N}_0\), the corresponding \(\bar{g}_k, g_k, f_{k+1}\) in (4.23)-(4.24) are given by

\(\bar{g}_k(u, v) = \frac{u + \bar{b}_k v}{1 + \bar{b}_k}, \qquad g_k(u, v) = \frac{v - u}{1 + \bar{b}_k},\)

\(f_{k+1}(w) = -\mathrm{ST}_{\lambda/\bar{c}_k} \left( -\frac{w}{\bar{c}_k} \right) = -\frac{\mathrm{ST}_{\lambda}(w)}{\bar{c}_k},\) (4.39)

where as in Section 3.3, we denote by \(\mathrm{ST}_t\) the soft-thresholding function \(w \mapsto \operatorname{sgn}(w)(|w|-t)_+\) for \(t > 0\). Given \(\hat{r}^1 = 0 \in \mathbb{R}^n, \bar{b}_0 \equiv \bar{b}_0 > 0\)