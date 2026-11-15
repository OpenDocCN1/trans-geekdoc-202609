where $\gamma_n$ is the tuning parameter, $\mathbf{1}_{p_n}$ is a $p_n$-tuple of 1, and $|\boldsymbol{\beta}^*| = (|\beta_1^*|, \dots, |\beta_{p_n}^*|)^\top$,

$D_n(\boldsymbol{\beta}) = \sum_{i=1}^n (y_i - \sum_{j=1}^{p_n} x_{ij} \beta_j) a_n(R_{n_i}(\boldsymbol{\beta})), \qquad (10.3.2)$

and $R_n(\boldsymbol{\beta})$ is the rank of $y_i - \sum_{j=1}^{p_n} x_{ij} \beta_j$ among $\{y_\alpha - \sum_{j=1}^{p_n} x_{\alpha j} \beta_j, 1 \le \alpha \le n\}$.

As before, let $\hat{\mathcal{S}}_1 \subset \{1, \dots, p_n\}$ be the active subset from Eq. (10.3.1). Then, a data-adaptive candidate subset model is produced as

$\hat{\beta}_j^{\text{PRD}} = 0 \quad \text{if and only if} \quad j \notin \hat{\mathcal{S}}_1. \qquad (10.3.3)$

Without loss of generality, we rearrange the covariates as $\mathbf{X} = (\mathbf{X}_{\mathcal{S}_1} | \mathbf{X}_{\mathcal{S}_2} | \mathbf{X}_{\mathcal{S}_3})$ where $\mathbf{X}_{\mathcal{S}_i}$ is a sub-matrix indexed by $\mathcal{S}_i \subset \{1, \dots, p_n\}$ and each $\mathbf{X}_{\mathcal{S}_i}$ is of dimension \(n \times p_{in}, i = 1, 2, 3\$. We designated \(p_i = p_{in}\) to show the dependency on the sample size. In general, \(\mathcal{S}_2\) cannot be separable from \(\mathcal{S}_3\). Some post-selection R-estimations can be presented to improve prediction performance of the PRD estimator. Thus, we can collect together the variable \(\mathbf{X}_{\hat{\mathcal{S}}_j}\) from the PRD subset selection and obtain the restricted R-estimator \(\hat{\boldsymbol{\beta}}_{1n}^\text{RR}\) using the restricted model

\(y_i = \sum_{j=1}^{p_{1n}} x_{ij} \beta_j^* + \varepsilon_i, \quad 1 \le i \le n, \qquad (10.3.4)\)

where

\(\hat{\boldsymbol{\beta}}_{1n}^\text{RR} = \underset{\hat{\boldsymbol{\beta}}_{\hat{\mathcal{S}}_1}^* \in \mathbb{R}^{p_{1n}}}{\text{argmin}} \left\{ \sum_{j=1}^{p_{1n}} |L_{n_j}(\boldsymbol{\beta}_{\hat{\mathcal{S}}_1}^*, \mathbf{0})| \right\} \qquad (10.3.5)\)

and

\(L_{n_j}(\boldsymbol{\beta}_{\hat{\mathcal{S}}_1}^*, \mathbf{0}) = \sum_{i=1}^n x_{ij} a_n(R_{n_i}(\boldsymbol{\beta}_{\hat{\mathcal{S}}_1}^*)) \qquad (10.3.6)\)

with \(R_n(\boldsymbol{\beta}_{\hat{\mathcal{S}}_1}^*)\) as the rank of \(\left( y_i - \sum_{j=1}^{p_{in}} x_{ij} \hat{\beta}_j^* \right)\) among \(y_i - \sum_{j=1}^{p_{in}} x_{ij} \beta_j^*, i = 1, \dots, n\).

Further, we obtain

\(\sqrt{n} \left( \hat{\boldsymbol{\beta}}_{1n}^\text{RR} - \boldsymbol{\beta}_{\hat{\mathcal{S}}_1}^* \right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_{1n}}(\mathbf{0}, \eta^2 \mathbf{C}_{11}^{-1}), \qquad (10.3.7)\)

where

\(\mathbf{C} = \begin{pmatrix} \mathbf{C}_{11} & \mathbf{C}_{12} \\ \mathbf{C}_{21} & \mathbf{C}_{22} \end{pmatrix}. \qquad (10.3.8)\)

The next section delves deeper into the specifics of \(\mathbf{C}\) and the partitions.