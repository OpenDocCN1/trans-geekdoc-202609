
Equivalently, we may write

$$\sup_{\|\hat{\theta}^* - \theta'\| \le M n^{-1/2}} \left\| \boldsymbol{T}_n(\theta^* + \frac{\boldsymbol{u}}{\sqrt{n}}) - \boldsymbol{T}_n(\theta^*) + \gamma(\phi, f) \mathcal{K} \boldsymbol{u} \right\| \xrightarrow{P} 0 \quad \text{(4.8.11)}$$

and

$$\sup_{\|\hat{\theta}^* - \theta'\| \le M n^{-1/2}} n^{-\frac{1}{2}} \left| D_n(\theta^* + \frac{\boldsymbol{u}}{\sqrt{n}}) - D_n(\theta^*) - \boldsymbol{u}^{\top} \boldsymbol{T}_n(\mathbf{0}) + \frac{1}{2} \gamma(\phi, f)^{\top} \boldsymbol{u}^{\top} \mathcal{K} \boldsymbol{u} \right| \xrightarrow{P} 0 \quad \text{(4.8.12)}$$

as \( n \to \infty \),

\( W_n(\boldsymbol{u}) = \boldsymbol{u}^{\top} \boldsymbol{T}_n(\mathbf{0}) + \frac{1}{2} \gamma(\phi, f)^{\top} \boldsymbol{u}^{\top} \mathcal{K}_{p_0} \boldsymbol{u} \)
\( n^{-\frac{1}{2}} \boldsymbol{T}_n(\boldsymbol{0}) \xrightarrow{\mathcal{D}} \mathcal{N}_{p}(\mathbf{0}, A_{\phi}^2, \mathcal{K}^{-1}) \).

Hence, we have

$$\left| \sqrt{n}(\hat{\theta}_n^{\text{UR}} - \boldsymbol{\theta}) - \text{argmin} \{ W(\boldsymbol{u}) \} \right| \xrightarrow{P} 0 \quad \text{(4.8.13)}$$

which leads to

$$\sqrt{n} \left( \hat{\theta}_n^{\text{UR}} - \boldsymbol{\theta} \right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p}(\mathbf{0}, \gamma^2 \mathcal{K}). \quad \text{(4.8.14)}$$

Also,

$$n^{\frac{1}{2}} \mathcal{K}_{p_0} \gamma(\phi, f) \left\{ \hat{\theta}_{1n}^* - \theta_1 + n^{-\frac{1}{2}} \gamma^{-1}(\phi, f) \mathcal{K}_{p_0}^{-1} \lambda_0 \boldsymbol{b} \right\} = n^{-\frac{1}{2}} \boldsymbol{T}_{n(1)}(\theta) + o_p(1). \quad \text{(4.8.15)}$$

Given that

$$n^{-\frac{1}{2}} \boldsymbol{T}_{n_1}(\theta) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_0}(\mathbf{0}, A_{\phi}^2 \mathcal{K}_{p_0}^{-1}), \quad \text{(4.8.16)}$$

we can infer that

$$\sqrt{n}(\hat{\theta}_{1n}^* - \theta_1) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_0}(\mathbf{0}, A_{\phi}^2 \mathcal{K}_{p_0}), \quad \text{(4.8.17)}$$

where \(\mathcal{K}_{p_0} = \text{Diag}(\kappa_1, ..., \kappa_{p_0})\).

### 4.8.5 Elastic-net-type R-estimator

Consider the R-estimation of $\theta$ by using a combination of the $L_1$ and $L_2$ penalty functions. That is, if ridge and LASSO are used together, it is possible to retain the benefits of both shrinkage and subset selection in one penalized R-estimator. We require the introduction of two tuning parameters, $\lambda$ and $\alpha$, to formulate the estimator as follows:

$\hat{\theta}_n^{\text{EnetR}}(\lambda, \alpha) = \underset{\theta \in \mathbb{R}^p}{\text{argmin}} \big\{ \sum_{i=1}^p \sum_{j=1}^{n_i} |y_{ij} - \theta_i| a_n^+(R_{n_i}(\theta_i)) + \lambda \sum_{i=1}^p \{ \eta \sqrt{\kappa_i} (\alpha |\theta_i| + \frac{1}{2} (1-\alpha) \theta_i^2) \} \big\}.$ (4.8.18)

By the same token, the combination of ridge-type and LASSO-type R-estimators can be used to formulate a naive Enet-type (nEnet) R-estimator as follows

$\hat{\theta}_n^{nEnetR}(\lambda, \alpha) = \begin{pmatrix} \hat{\theta}_{n_1}^{\text{UR}} \left( 1 - \frac{\eta \lambda \alpha \sqrt{\kappa_1}}{\sqrt{L_{n_1}}} \right) \frac{I(L_{n_1} > \lambda^2 \alpha^2)}{1+\lambda(1-\alpha)\kappa_1} \\ \vdots \\ \hat{\theta}_{n_p}^{\text{UR}} \left( 1 - \frac{\eta \lambda \alpha \sqrt{\kappa_p}}{\sqrt{L_{n_p}}} \right) \frac{I(L_{n_p} > \lambda^2 \alpha^2)}{1+\lambda(1-\alpha)\kappa_p} \end{pmatrix}.$

**Theorem 4.11** Under the local alternatives, $K_{(n)}$, the asymptotic distributional bias, and L$_2$-risk of the nEnet R-estimator, $\hat{\theta}_n^{nEnetR}(\lambda)$, are respectively given by

$\text{ADB}(\hat{\theta}_n^{nEnetR}(\lambda, \alpha)) = \left( \frac{-\eta \sqrt{\kappa_j}}{[1 + \lambda(1-\alpha)\kappa_j]} \left[ \Delta_j \mathcal{H}_3(\lambda^2 \alpha^2, \Delta_j^2) - \lambda \alpha (\Phi(\lambda \alpha - \Delta_j) - \Phi(\lambda \alpha + \Delta_j)) - \lambda(1-\alpha)\Delta_j \right] \bigg| j = 1, 2, ..., p \right)^\top$

and

$\text{ADL}_2\text{-risk}(\hat{\theta}_n^{nEnetR}(\lambda, \alpha)) = \eta^2 \left[ \sum_{j=1}^p \frac{1}{[1 + \lambda(1-\alpha)\kappa_j]^2} \left\{ \kappa_j (1 - \mathcal{H}_3(\lambda^2 \alpha^2, \Delta_j^2)) + \Delta_j^2 (2 \mathcal{H}_3(\lambda^2 \alpha^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2 \alpha^2, \Delta^2)) + \lambda^2 (1 - \mathcal{H}_1(\lambda^2 \alpha^2, \Delta_j^2)) - 2\lambda (\Phi(\lambda \alpha - \Delta_j) + \Phi(\lambda \alpha + \Delta_j)) + \lambda^2 (1-\alpha)^2 \Delta_j^2 - 2\lambda (1-\alpha) \Delta_j (\Delta_j \mathcal{H}_3(\lambda^2 \alpha^2, \Delta_j^2)) - \lambda \alpha (\Phi(\lambda \alpha - \Delta_j) - \Phi(\lambda \alpha + \Delta_j)) \right\} \right].$

If \(\alpha = 1\),

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha = 1)) = \eta^2 \left[ \sum_{j=1}^p \kappa_j \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) + \Delta_j^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta^2) \right) + \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) \right) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right].\)

If \(\alpha = 0\),

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha = 0)) = \eta^2 \sum_{j=1}^p \frac{1}{[1 + \lambda \kappa_j]^2} \times \left\{ \kappa_j + \lambda^2 - 4\lambda \phi(\Delta_j) + \lambda^2 \Delta_j^2 \right\}.\)

Now, using the family of linear projections, we obtain the lower bound of the ADL$_2$-risk($\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha)$) as

\(\frac{\eta^2}{[1 + \lambda(1 - \alpha)]^2} \left[ \text{tr}(\mathcal{K}_1) + \Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) - 2\lambda(1 - \alpha)\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) \sum_{j=1}^p \mathcal{H}_3(\lambda^2 \alpha^2, \Delta_j^2) + 2\lambda(1 - \alpha) \sum_{j=1}^p \left( \Phi(\lambda \alpha - \Delta_j) - \Phi(\lambda \alpha + \Delta_j) \right)^2 \right]\)

where \(\mathcal{K} = \text{Diag}(\mathcal{K}_1, \mathcal{K}_2)\) and \(\Delta^2 = (\delta_2^T \mathcal{K}_2^{-1} \delta) / \eta^2\). Hence,

\(\text{ADRE}(\hat{\theta}_n^{\text{nEnetR}}(x, \alpha); \hat{\theta}_n^{\text{UR}}) = \begin{cases} \left[ (1 + \lambda)^2 \left[ \text{tr}(\mathcal{K}_1) + \Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) + 2\lambda \sum_{j=1}^p (2\Phi(\Delta_j) - 1)^2 \right] \right]^{-1} & \alpha = 0 \\ \left[ \text{tr}(\mathcal{K}_1) + \Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) \right]^{-1} & \alpha = 1 . \end{cases}\)

## 4.9 Comparison of the R-estimators

In this section, we compare all the proposed R-estimators discussed with respect to the unrestricted R-estimator of \(\theta = (\theta_1, ..., \theta_p)^T\).

### 4.9.1 Comparison of URE and RRE

From Sections 4.4 and 4.6, we have

$\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{RR}}) - \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{UR}}) = \delta_2^T \delta_2 - \eta^2 \text{tr}(\mathcal{K}_2) \ge \eta^2 [\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) - \text{tr}(\mathcal{K}_2)] \quad (4.9.1)$

Based on Eq. (4.9.1), we find that $\hat{\theta}_n^{\text{UR}}$ outperforms $\hat{\theta}_n^{\text{RR}}$ whenever

$\Delta^2 \ge \frac{\text{tr}(\mathcal{K}_2)}{\text{Ch}_{\min}(\mathcal{K}_2)}$

and $\hat{\theta}_n^{\text{RR}}$ outperforms $\hat{\theta}_n^{\text{UR}}$ whenever

$0 \le \Delta^2 \le \frac{\text{tr}(\mathcal{K}_2)}{\text{Ch}_{\min}(\mathcal{K}_2)}.$

### 4.9.2 Comparison of URE and Stein-Saleh-type R-estimators

From Section 4.7.2, we find that ADL$_2$-risk difference of $\hat{\theta}_n^{\text{UR}}$ and $\hat{\theta}_n^{\text{SSR}}$ is given by

$\eta^2 \left\{ (p_2 - 2) \text{tr}(\mathcal{K}_2) \left( \text{E} \left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] + \Delta^2 \text{E} \left[ \chi_{p_2+2}^{-4}(\Delta^2) \right] \right) \right. \left. -(p_2 - 2)(p_2 + 2)\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) \text{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right\} \ge 0$

for all $\Delta^2 \in \mathbb{R}^2$. Thus, $\hat{\theta}_n^{\text{SSR}}$ outperforms $\hat{\theta}_n^{\text{UR}}$ uniformly. Furthermore,

$\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR}+}) \le \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR}}) \le \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{UR}}).$

### 4.9.3 Comparison of URE and Ridge-type R-estimators

We consider ADL$_2$-risk difference expressions of $\hat{\theta}_n^{\text{UR}}$ and $\hat{\theta}_n^{\text{ridge}_R}(\lambda_{\text{opt}})$, with

$\lambda_{\text{opt}} = \text{tr}(\mathcal{K}_2)\Delta^{-2} (\text{Ch}_{\min}(\mathcal{K}_2))^{-1},$

given by

$\eta^2 \left[ (\text{tr}(\mathcal{K}_1) + \text{tr}(\mathcal{K}_2)) - \text{tr}(\mathcal{K}_1) - \frac{\text{tr}(\mathcal{K}_2)\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_2) + \Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)} \right] = \eta^2 \text{tr}(\mathcal{K}_2) \left[ 1 - \frac{\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_2) + \Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)} \right]$
