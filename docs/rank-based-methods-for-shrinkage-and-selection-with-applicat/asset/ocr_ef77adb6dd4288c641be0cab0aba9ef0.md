+2\eta^2\Delta^2\mathcal{H}_3(\chi_1^2(\alpha), \Delta^2)
= \eta^2(1 - \mathcal{H}_3(\chi_1^2(\alpha), \Delta^2) + \Delta^2(2\mathcal{H}_3(\chi_1^2(\alpha), \Delta^2) - \mathcal{H}_5(\chi_1^2(\alpha), \Delta^2))).

The first term is due to Theorem 3.1, and the proof is complete.

Thus,

\text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) = \rho_{\text{PT}}^{-1}(\alpha, \Delta^2).

# 3.5.1 Optimum Level of Significance of PTRE

It is possible to rewrite Eq. (3.5.13) as

\text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) = [1 + g(\alpha, \Delta^2)]^{-1},

where

g(\alpha, \Delta^2) = -\mathcal{H}_3(\chi_1^2(\alpha), \Delta^2) + \Delta^2(2\mathcal{H}_3(\chi_1^2(\alpha), \Delta^2) - \mathcal{H}_5(\chi_1^2(\alpha), \Delta^2)).

The graph of \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}), as a function of \Delta^2 for a fixed \alpha, is decreasing until it crosses the 1-line to reach a minimum at some \Delta^2 = \Delta_0^2(\alpha); then it increases toward the 1-line as \Delta^2 \to \infty. The maximum value of \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) occurs at \Delta^2 = 0 with the value

\text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) = \{1 - \mathcal{H}_3(\chi_1^2(\alpha), 0)\}^{-1} \ge 1,

for all \alpha \in A, the set of possible values of \alpha.

The value of \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) decreases as \alpha increases, i.e, if \alpha = 0 and \Delta^2 varies, the graphs of \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(0) : \hat{\theta}_n^{\text{UR}}) and \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(1) : \hat{\theta}_n^{\text{UR}}) intersect at \Delta^2 = 1. In general, \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha_1) : \hat{\theta}_n^{\text{UR}}) and \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha_2) : \hat{\theta}_n^{\text{UR}}) intersect within the interval 0 \le \Delta^2 \le 1; the value of \Delta^2 at the intersection grows as \alpha increases. Thus, for two different \alpha-values, \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha_1) : \hat{\theta}_n^{\text{UR}}) and \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha_2) : \hat{\theta}_n^{\text{UR}}) will always intersect below the 1-line.

In order to obtain a PTR estimator with a minimum guaranteed efficiency, E_0, we adopt the following procedure: if 0 \le \Delta^2 \le 1, we always choose \hat{\theta}_n^{\text{UR}}, because \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) \ge 1 in this interval. However, since \Delta^2 is unknown generally, there is no way to choose an estimate that will uniformly the best. For this reason, we select an estimator with minimum guaranteed efficiency, and look for a suitable \alpha from the set, A = {\alpha | \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) \ge E_0}. The estimator as chosen maximizes \text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\alpha) : \hat{\theta}_n^{\text{UR}}) over all \alpha \in A, and