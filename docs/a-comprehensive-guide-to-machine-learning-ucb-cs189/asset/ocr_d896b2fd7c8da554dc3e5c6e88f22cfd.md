# 3.3. CANONICAL CORRELATION ANALYSIS

so

```
$$\begin{bmatrix} \sigma_x^{-1} & 0 \ 0 & \sigma_y^{-1} \end{bmatrix} \begin{bmatrix} X \ Y \end{bmatrix} \sim \mathcal{N} \left( \begin{bmatrix} \sigma_x^{-1} & 0 \ 0 & \sigma_y^{-1} \end{bmatrix} \Sigma, \begin{bmatrix} \sigma_x^{-1} \ \sigma_y^{-1} \end{bmatrix} \right) $\\sim \mathcal{N} \left( \begin{bmatrix} 0 \ \rhorho \end{bmatrix} \right)$
```

# Canonical Correlation Analysis

**Canonical Correlation Analysis (CCA)** is a method of modeling the relationship between two points sets by maximizing use of correlation coefficient. Formally, given zero-mean random vectors $X_{rv} \in \mathbb{R}^p$ and $Y_{rv} \in \mathbb{R}^q$, we want to find projections $u \in \mathbb{R}^p$ and $v \in \mathbb{R}^q$ that maximizes the correlation between $X_{rv}^T u$ and $Y_{rv}^T v$:

```
$$\rho(X_{rv}^T u, Y_{rv}^T v) = \max_{u,v} \frac{Cov(X_{rv}^T u, Y_{rv}^T v)}{\sqrt{Var(X_{rv}^T u) Var(Y_{rv}^T v)}}$
```

Observe that

```
$$\Cov(X_{rv}^T u, Y_{rv}^T v) = \mathbb{E}[(X_{rv}^T u - \mathbb{E}[X_{rv}^T u])(Y_{rv}^T v - \mathbb{E}[Y_{rv}^T v])$\\= u^T(X_{rv} - \mathbb{E}[X_{rv}])(Y_{rv} - \mathbb{E}[Y_{rv}])^T v$\\= u^T(X_{rv} - \mathbb{E}[X_{rv}])(Y_{rv} - \mathbb{E}[Y_{rv}])^T v$\\= u^T Cov(X_{rv}, Y_{rv}) v$
```

which also implies ($Var(Z) = Cov(Z, Z)$ for any random variable $Z$) that

```
$Var(X_{rv}^T u) = u^T Cov(X_{rv}, X_{rv}) u$\n$Var(Y_{rv}^T v) = v^T Cov(Y_{rv}, Y_{rv}) v$
```

so the correlation writes

```
$$\rho(X_{rv}^T u, Y_{rv}^T v) = \frac{u^T Cov(X_{rv}, Y_{rv}) v}{\sqrt{Cov(X_{rv}, X_{rv}) u \cdot v^T Cov(Y_{rv}, Y_{rv}) v}}$
```

Unfortunately, we do not have access to the true distributions of $X_{rv}$ and $Y_{rv}$, so we cannot compute these covariances matrices. We estimate them from data. Assume that we are given zero-mean data $X \in \mathbb{R}^{nxp}$ and $Y \in \mathbb{R}^{nq}$, where the rows of the matrix $X$ are i.i.d. samples $x_i \in \mathbb{R}^p$ from the random variable $X_{rv}$, and correspondingly for $Y_{rv}$.

```
$$\Cov(X_{rv}, Y_{rv}) = \mathbb{E}[(X_{rv} - \mathbb{E}[X_{rv}])(Y_{rv} - \mathbb{E}[Y_{rv}])^T] \approx \frac{1}{n} \sum_{i=1}^n x_i y_i^T = \frac{1}{n} X^T Y$
```

where again the sample-based approximation is justified by the law of large numbers. Similarly,

```
$$\Cov(X_{rv}, X_{rv}) = \mathbb{E}[X_{rv}X_{rv}^T] \approx \frac{1}{n} \sum_{i=1}^n x_i x_i^T = \frac{1}{n} X^T X$\n$$\Cov(Y_{rv}, Y_{rv}) = \mathbb{E}[Y_{rv}Y_{rv}^T] \approx \frac{1}{n} \sum_{i=1}^n y_i y_i^T = \frac{1}{n} Y^T Y$
```