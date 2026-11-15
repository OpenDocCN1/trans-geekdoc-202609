
## 6.8 Problems

- 6.1. For the general shrinkage R-estimators of Section 6.4, derive the formulas for $ADB(\hat{\beta}_n^{ShrinkageR}(c))$ and $ADL_2-risk(\hat{\beta}_n^{ShrinkageR}(c))$.

- 6.2. For the preliminary test R-estimator in Section 6.4.1, prove the $ADB(\hat{\beta}_n^{PTR}(\lambda))$, $ADL_2-risk(\hat{\beta}_n^{PTR}(\lambda))$ and $ADRE(\hat{\beta}_n^{PTR}(\lambda) : \hat{\beta}_n^{UR})$ equations.

- 6.3. For the Stein–Saleh R-estimator of Section 6.4.2, derive the ADL-risk($\hat{\beta}_n^{STR}(\lambda)$) and $ADRE(\hat{\beta}_n^{STR}(\lambda) : \hat{\beta}_n^{UR})$ expressions and show that $ADRE(\hat{\beta}_n^{STR}(\lambda) : \hat{\beta}_n^{UR}) \ge 1$.

- 6.4. For the positive-rule Stein–Saleh R-estimator of Section 6.4.3 (LASSO-type), prove the expression $ADL_2-risk(\hat{\beta}_n^{STR+}(\lambda))$ and show, after deriving the expression, that $ADRE(\hat{\beta}_n^{STR+}(\lambda) : \hat{\beta}_n^{UR}) \ge 1$.

- 6.5. For the preliminary test subset selector of Section 6.5.1, derive the equations for $ADL_2-risk(\hat{\beta}_n^{PTSSR}(\lambda))$ and its lower bound. Also, derive the full expression for $ADRE(\hat{\beta}_n^{PTSSR}(\lambda) : \hat{\beta}_n^{UR})$.

- 6.6. For the Stein–Saleh subset selector estimator of Section 6.5.2, find $ADB(\hat{\beta}_n^{SR}(\lambda))$, $ADL_2-risk(\hat{\beta}_n^{SR}(\lambda))$ and $ADRE(\hat{\beta}_n^{SR}(\lambda) : \hat{\beta}_n^{UR})$.

- 6.7. For the positive-rule Stein–Saleh R-estimator (LASSO-type) of Section 6.5.3, determine the $ADB(\hat{\beta}_n^{PRSR}(\lambda))$, $ADL_2-risk(\hat{\beta}_n^{PRSR}(\lambda))$ and the lower bound of the $ADL_2-risk(\hat{\beta}_n^{PRSR}(\lambda))$.

- 6.8. For the ridge-type selector of Section 6.5.4, find the expression for the selector and the lower bound of $ADL_2-risk$.

- 6.9. Derive the naive elastic net selector following Section 6.5.5 and the lower bound of the $ADL_2-risk$ expression.

- 6.10. Show that the adaptive LASSO (aLASSO) R-estimator has the oracle property.

## Partially Linear Multiple Regression Model

### 7.1 Introduction

In this chapter, we consider the usual partially linear model (PLM) of the form

$$y_i = \boldsymbol{x}_i^\top \boldsymbol{\beta} + g(t_i) + \varepsilon_i, \quad i = 1, ..., n \tag{7.1.1}$$

where \(y_i\) is the response, \(\boldsymbol{x}_i = (x_{i1}, ..., x_{ip})^\top\) is a vector of explanatory variables, \(\boldsymbol{\beta} = (\beta_1, ..., \beta_p)^\top\) is an unknown \(p\)-dimensional parameter vector, \(t_i\) is known and non-random in some bounded domain \(D \in \mathbb{R}\), and \(g(t_i)\) is an unknown smooth function. The \(\varepsilon_i\)'s are i.i.d. random errors with absolutely continuous c.d.f. \(F(\cdot)\) and p.d.f. \(f(\cdot) > 0\) having the first derivative \(f'(\cdot)\) satisfying finite Fisher information

$$I(f) = \int_{-\infty}^{\infty} \left(-\frac{f'(x)}{f(x)}\right)^2 f(x)\mathrm{d}x < \infty, \quad (7.1.2)$$

and \(\mathbb{E}(\varepsilon_i) = 0, \forall i\), which is independent of \((\boldsymbol{x}_i, t_i)\). Here, we assume that the response \(y_i\) linearly depends on \(\boldsymbol{x}_i\), but that it is nonlinearly related to \(t\). Further,

$$\gamma(\varphi, \psi) = \int_0^1 \varphi(u)\psi(u)\mathrm{d}u, \quad \psi(u) = \frac{f'(F^{-1}(u))}{f(F^{-1}(u))}, \quad (7.1.3)$$

and \(\varphi(u)\) is a non-decreasing score generating function, \(0 \le u \le 1\).

Surveys regarding the estimation and application of the model of Eq. (7.1.1) can be found in the monograph of Hardle et al. (2000). For more studies about the PLM, we refer the reader to Roozbeh and Arashi (2016) and Saleh et al. (2019) among others. For the estimation of \(\boldsymbol{\beta}\), we first need to estimate the nonparametric component \(g(\cdot)\), where we use the kernel smoothing method.

To estimate \( g(\cdot) \), assume that \( (y_i, \mathbf{x}_i, t_i), \ i = 1, ..., n \) satisfy the model of Eq. (7.1.1). Since \( \mathbb{E}(\varepsilon_i) = 0 \), we have \( g(t_i) = \mathbb{E}(y_i - \mathbf{x}_i^\top \boldsymbol{\beta}) \) for \( i = 1, ..., n \). Hence, if we know \( \boldsymbol{\beta} \), a natural nonparametric estimator of \( g(\cdot) \) is given by

$$\hat{g}(t, \boldsymbol{\beta}) = \sum_{i=1}^n W_{ni}(t)(y_i - \mathbf{x}_i^\top \boldsymbol{\beta}), \tag{7.1.4}$$

where the probability weight function, \( W_{ni}(\cdot) \), satisfies the following three regularity conditions

- (i) \( \max_{1 \le i \le n} \sum_{j=1}^n W_{ni}(t_j) = O(1), \)
- (ii) \( \max_{1 \le i, j \le n} W_{ni}(t_j) = O(n^{-\frac{2}{3}}), \)
- (iii) \( \max_{1 \le i \le n} \sum_{j=1}^n W_{ni}(t_j)I(|t_i - t_j| > c_n) = O(d_n), \) where \( I(A) \) is the indicator function of the set \( A \),

$$\limsup_{n \to \infty} n c_n^3 < \infty,$$
$$\limsup_{n \to \infty} n d_n^3 < \infty.$$

The above assumptions guarantee the existence of \( \hat{g}(t, \boldsymbol{\beta}) \) with the optimal convergence rate of \( n^{-4/5} \) in the PLM with probability one. See Muller and Ronz (2000) for more details. Throughout the rest of this chapter, we do not discuss further the estimation of \( g(\cdot) \) in the PLMs, since the main concern is the estimation of \( \boldsymbol{\beta} \).

### 7.2 Rank Estimation in the PLM

Consider the PLM defined by

$$y_i = \mathbf{x}_{i(1)}^\top \boldsymbol{\beta}_1 + \mathbf{x}_{i(2)}^\top \boldsymbol{\beta}_2 + g(t_i) + \varepsilon_i, \quad i = 1, ..., n \tag{7.2.1}$$

where \( y_i \) are responses, \( \mathbf{x}_{i(1)} = (x_{i1}, ..., x_{ip_1})^\top \) and \( \mathbf{x}_{i(2)} = (x_{i(p_1+1)}, ..., x_{ip})^\top \) are covariates of the unknown vectors, namely \( \boldsymbol{\beta}_1 = (\beta_1, ..., \beta_{p_1})^\top \) and \( \boldsymbol{\beta}_2 = (\beta_{p_1+1}, ..., \beta_p)^\top \), respectively, \( t_i \in [0, 1] \) are design points, \( g(\cdot) \) is a real valued function defined on \( [0, 1] \), and \( \varepsilon_1, ..., \varepsilon_n \) are i.i.d. errors with zero mean and constant \( I(f) \).

Our main objective is to estimate \( (\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top \) when one suspects that the \( p_2 \)-dimensional sparsity condition \( \boldsymbol{\beta}_2 = \mathbf{0} \) may hold. In this situation, we first estimate the parameter \( \boldsymbol{\beta} = (\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top \) using Speckman's (1988) approach involving a partial kernel smoothing method, which attains the usual parametric convergence rate \(n^{-1/2}\) without under-smoothing the nonparametric component \(g(\cdot)\).

Assume that \(\{(x_{j(1)}^\top, x_{j(2)}^\top), t_j, y_j | j = 1, ..., n\}\) satisfies the model of Eq. (7.2.1). If \(\beta = (\beta_1^\top, \beta_2^\top)^\top\) is the true parameter, then for \(j = 1, ..., n\), we have

$$g(t_i) = \mathbb{E}(y_i - x_{i(1)}^\top \beta_1 - x_{i(2)}^\top \beta_2).$$

Thus, a natural nonparametric estimator of \(g(\cdot)\) given \(\beta = (\beta_1^\top, \beta_2^\top)^\top\) is

$$\tilde{g}(t, \beta_1, \beta_2) = \sum_{i=1}^n W_{ni}(t_i) \left( y_i - x_{i(1)}^\top \beta_1 - x_{i(2)}^\top \beta_2 \right), \quad t = (t_1, ..., t_n) \tag{7.2.2}$$

with the probability weight function \(W_{ni}(\cdot)\) that satisfies the three regularity conditions (i)—(iii), given before Section 7.2.

Suppose that we partition the design matrix as follows

$$Z = \begin{pmatrix} Z_1 & : & Z_2 \end{pmatrix}^\top \quad n \times p_1 \quad n \times p_2$$

and define others as

$$\hat{y} = (\hat{y}_1, ..., \hat{y}_n)^\top, \quad Z = (z_1, ..., z_n)^\top,$$

where

$$\hat{y}_i = y_i - \sum_{k=1}^n W_{nk}(t_i)y_k, \quad z_i = x_i - \sum_{k=1}^n W_{nk}(t_i)x_k, \quad j = 1, ..., n.$$

Further, assume that \((x_{is}, t_i)\) are i.i.d. random variables and let

$$\mathbb{E}(x_{is}|t_i) = h_s(t_i), \quad s = 1, ..., p.$$

Then, the conditional variance of \(x_{is}\) given \(t_i\) is \(\mathbb{E}(u_i u_i^\top) = C\), where \(u_i = (u_{i1}, ..., u_{ip})^\top\) with \(u_{is} = x_{is} - h_s(t_i)\). Then, by L.L.N.,

$$\lim_{n \to \infty} \frac{1}{n} \sum_{k=1}^n u_{ik}u_{kj} = C_{ij} \quad i, j = 1, ..., p,$$

and the matrix \(C = (C_{ij})\) (see Eq. (7.2.11)) is non-singular with probability one. Readers are referred to Shi and Lau (2000), Gao (1995, 1997) and Liang and Hardle (1999) among others. Moreover, for any permutation \((j_1, ..., j_k)\) of \((1, ..., n)\) as \(n \to \infty\),
