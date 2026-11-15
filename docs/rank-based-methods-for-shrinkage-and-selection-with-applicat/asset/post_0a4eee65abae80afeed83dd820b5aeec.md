

**Theorem 4.6** Under the local alternatives, $K_{(n)}$, the asymptotic distributional bias, and $L_2$-risk of the ridge-type R-estimator, $\hat{\theta}_n^{\text{ridgeR}}(\lambda)$, are respectively given by

\[
ADB(\hat{\theta}_n^{\text{ridgeR}}(\lambda)) = \left( \mathbf{0}^\top, -\frac{\lambda}{1+\lambda}\delta_2^\top \right)^\top
\]

and

\[
ADL_2\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda)) = \eta^2 \left[ tr(\mathcal{K}_1) + \frac{tr(\mathcal{K}_2) + \lambda^2 \delta_2^\top \mathcal{S}_2}{(1+\lambda)^2} \right].
\]

The lower-bound of $ADL_2$-risk is

\[
ADL_2^*\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda)) = \eta^2 \left[ tr(\mathcal{K}_1) + \frac{tr(\mathcal{K}_2) + \lambda^2 \Delta^2 Ch_{\min}(\mathcal{K}_2)}{(1+\lambda)^2} \right].
\]

We may note that the optimum value of $\lambda$ for $ADL_2^*\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda))$ equals

\[
\lambda_{opt} = tr(\mathcal{K}_2)\Delta^{-2}(Ch_{\min}(\mathcal{K}_2))^{-1}.
\]

Thus,

\[
ADL_2^*\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda_{opt})) = \eta^2 \left[ tr(\mathcal{K}_1) + \frac{tr(\mathcal{K}_2)\Delta^2 Ch_{\min}(\mathcal{K}_2)}{tr(\mathcal{K}_2) + \Delta^2 Ch_{\min}(\mathcal{K}_2)} \right],
\]

and

\[
ADRE(\hat{\theta}_n^{\text{ridgeR}}(\lambda) : \hat{\theta}_n^{UR}) = \left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \right) \times \left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \frac{\Delta^2 Ch_{\min}(\mathcal{K}_2)}{[tr(\mathcal{K}_2) + \Delta^2 Ch_{\min}(\mathcal{K}_2)]} \right)^{-1} \quad (4.7.6)
\]

which is a decreasing function of $\Delta^2$. At $\Delta^2 = 0$, the value is $\left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \right)$ and for $\Delta^2 \to \infty$, it is 1. Clearly,

\[
0 \le \left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \right) \left( 1 + \frac{(tr(\mathcal{K}_2))\Delta^2 Ch_{\min}(\mathcal{K}_2)}{(tr(\mathcal{K}_1))(tr(\mathcal{K}_2) + \Delta^2 Ch_{\min}(\mathcal{K}_2))} \right)^{-1} < 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \quad \forall \Delta^2 \in \mathbb{R}^+.

## 4.8 Subset Selection Penalty R-estimators

In the prior section, we described methods to handle sparsity in the model. In this section, we discuss several penalty R-estimators that seek to find the parameters that lead to sparsity in the model, such as

- (i) Preliminary test R-estimator (PTRE) generally designated as a hard threshold estimators (HTE) due to Donoho and Johnstone (1994).
- (ii) LASSO proposed by Tibshirani (1996) designated as a soft threshold estimator (STE) due to Donoho and Johnstone (1994). Saleh et al. (2019) identified LASSO as equivalent to the positive-rule Saleh selector (PRSS) for the location model, as noted in Chapter 3.
- (iii) The adaptive LASSO-type estimator.
- (iv) The elastic-net-type estimator.

As mentioned before, we use the “-type” designation since we are applying the shrinkage factor directly to the unrestricted estimate to obtain a closed-form estimator rather than minimizing a penalized loss function.

### 4.8.1 Preliminary Test Subset Selector R-estimator

The preliminary test subset selector R estimator (PTSSRE) is defined by

\[
\hat{\boldsymbol{\theta}}_n^{\text{PTSSR}}(\lambda) = \left( \hat{\theta}_{n_j}^{\text{UR}} I(\mathcal{L}_{n_j} > \lambda^2) \mid j = 1, ..., p \right)^{\top}
\]

where

\[
\mathcal{L}_{n_j} = \frac{n \left( \hat{\theta}_{n_j}^{\text{UR}} \right)^2}{\hat{\eta}^2 \varkappa_j}, \quad j = 1, ..., p
\]

is the test statistic.
Each component is a PTSSRE of \(\theta_j, j = 1, ..., p\).

**Theorem 4.7** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and ADL$_2$-risk of the preliminary test subset selector R-estimator, \(\hat{\boldsymbol{\theta}}^{\text{PTSSR}}\), are respectively given by

\[
\text{ADB}(\hat{\boldsymbol{\theta}}_n^{\text{PTSSR}}(\lambda)) = -\eta \left( \delta_j \mathcal{H}_3(\lambda^2, \Delta_j) \mid j = 1, ..., p \right)^{\top},
\]

and

\[
\text{ADL}_2\text{-risk}(\hat{\theta}^{PTSSR}_n(\lambda)) = \eta^2 \Big\{ \sum_{j=1}^p \kappa_j (1 - \mathcal{H}_3(\lambda^2, \Delta_j^2)) + \sum_{j=1}^p \Delta_j^2 (2\mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2)) \Big\}.
\]

**Proof:** We begin by showing that

\[
\sqrt{n} \hat{\theta}^{PTSSR}_n(\lambda) = \Big( \sqrt{n} \hat{\theta}^{UR}_{n_j} I(| \sqrt{n} \hat{\theta}^{UR}_{n_j} | > \lambda \kappa_j^{\frac{1}{2}} \eta) \mid j=1, ..., p \Big)^\top = \Big( \eta \kappa_j^{\frac{1}{2}} Z_{n_j} I(|Z_{n_j}| > \lambda) \mid j=1, ..., p \Big)^\top,
\]

where

\[
Z_{n_j} = \frac{\sqrt{n} \hat{\theta}^{UR}_{n_j}}{\eta \sqrt{\kappa_j}}, \quad j=1, ..., p.
\]

Clearly, $Z_{n_j} \sim \mathcal{N}(\Delta_j, 1), \ j=1, ..., p$, as $n \to \infty$, and $\Delta_j = \delta_j / (\eta \sqrt{\kappa_j})$. Since the proof of this theorem is similar to Theorem 3.5, we leave the details to the reader.

### 4.8.2 Saleh-type R-estimator

We noted that the hard threshold R-estimator is discrete in nature and may be extremely variable and unstable due to the fact that small changes in the data can result in a very different model and may reduce the prediction accuracy. The Saleh R-estimator is a continuous version of the hard threshold estimator and is defined as

\[
\hat{\theta}^{SR}_n(\lambda) = \Big( \hat{\theta}^{UR}_{n_j} \Big( 1 - \frac{\lambda}{\mathcal{L}_{n_j}} \Big) \Big| j=1, ..., p \Big)^\top, \quad \mathcal{L}_{n_j} = |Z_{n_j}|.
\]

**Theorem 4.8** Under the local alternatives, $K_{(n)}$, the asymptotic distributional bias, and $ADL_2$-risk of the Saleh R-estimator, $\hat{\theta}^{SR}_n$, are respectively given by

\[
ADB(\hat{\theta}^{SR}_n(\lambda)) = \Big( -\lambda \eta \sqrt{\kappa_j} (2\Phi(\Delta_j) - 1) \mid j=1, ..., p \Big)^\top,
\]

and

\[
\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SR}}(\lambda)) = \eta^2 \sum_{j=1}^p \left( 1 + \lambda^2 - 2\lambda \sqrt{\frac{2}{\pi}} \exp\left(-\frac{\Delta_j^2}{2}\right) \right).
\]

**Proof:** We first show that

\[
\begin{aligned}
\sqrt{n}\hat{\theta}_n^{\text{SR}}(\lambda) &= \left( \sqrt{n}\hat{\theta}_{n_j}^{\text{UR}} - \lambda \eta \sqrt{\kappa_j} \left| \frac{\sqrt{n}\hat{\theta}_{n_j}^{\text{UR}}}{|\sqrt{n}\hat{\theta}_{n_j}^{\text{UR}}|} \right| j = 1, ..., p \right)^{\top} \\
&= \left( \eta \sqrt{\kappa_j} \left( 1 - \frac{\lambda}{|Z_{n_j}|} \right) Z_{n_j} \bigg| j = 1, ..., p \right)^{\top}
\end{aligned}
\]

where \( Z_{n_j} = \sqrt{n}\hat{\theta}_{n_j}^{\text{UR}} / (\eta \sqrt{\kappa_j}), j = 1, ..., p \). Clearly, \( Z_{n_j} \sim \mathcal{N}(\Delta_j, 1) \), as \( n \to \infty \), and \( \Delta_j = \delta_j / (\eta \sqrt{\kappa_j}) \). Since the proof of this theorem is similar to Theorem 3.7, we leave the remainder to the reader.

Hence, for \( \lambda_{\max}^* = \sqrt{\frac{2}{\pi}} \), we obtain

\[
\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SR}}(\lambda^*)) = \eta^2 \sum_{j=1}^p \left[ 1 - \frac{2}{\pi} \left( 2 \exp\left\{ -\frac{\Delta_j}{2} \right\} - 1 \right) \right].
\]

Finally,

\[
\text{ADRE}(\hat{\theta}_n^{\text{SR}}(\lambda^*) : \hat{\theta}_n^{\text{UR}}) = \left( \sum_{j=1}^p \left[ 1 - \frac{2}{\pi} \left( 2 \exp\left\{ -\frac{\Delta_j}{2} \right\} - 1 \right) \right] \right)^{-1}.
\]

### 4.8.3 Positive-rule Saleh Subset Selector (PRSS)

The Saleh R-estimator described in the previous section changes sign and this may not be desirable. However, the LASSO R-estimator, which is given by

\[
\hat{\theta}_n^{\text{LassoR}}(\lambda) = \underset{\theta \in \mathbb{R}}{\text{argmin}} \left\{ \sum_{i=1}^p \sum_{j=1}^{n_i} |y_{ij} - \theta_j| a_n^+(R_{n_j}(\theta_j)) + \lambda \sum_{i=1}^p |\theta_i| \right\}
\]

does not have this issue. Motivated by LASSO and soft threshold estimator (Donoho and Johnstone, 1994), we consider the positive-rule of Saleh subset selector (PRSS) to remedy this problem. It can be defined as

\[
\hat{\theta}_n^{\text{SR+}}(\lambda) = \left( \text{sgn}(\hat{\theta}_{n_j}^{\text{UR}}) \left( |\hat{\theta}_{n_j}^{\text{UR}}| - \lambda \right) I(\mathcal{L}_{n_j} > \lambda^2) \bigg| j = 1, 2, ..., p \right)^{\top}

