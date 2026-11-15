
tr(\boldsymbol{M}_{22:1}^{-1})\left\{\mathcal{H}_{p_2+2}(\lambda^2, 0) - p_2^{-1}c(2 - c/(p_2-2))\right\}. (9.5.12)

Now, c p_2^{-1}(2-c/(p_2-2)) attains a maximum (over c \in (0, 2(p_2-2)) at c = p_2-2 while by Eq. (9.5.6), c \leq 2\lambda^{-1} - 4. Hence, defining q as in Eq. (9.5.9), we note that Eq. (9.5.12) is bounded from below by

tr(\boldsymbol{M}_{22:1}^{-1})\left\{\mathcal{H}_{p_2+2}(\lambda^2, 0) - q \frac{2(p_2-2)-q}{p_2(p_2-2)}\right\}. (9.5.13)

Thus, ensuring positiveness of Eq. (9.5.12) implies that \hat{\rho}_{1n}^{SS} fails to dominate \hat{\rho}_{1n}^{PTR}(\lambda).

## 9.6 Summary

In this chapter, we proposed shrinkage and penalty R-estimators for the vector parameter of the auto-regression model of order p. Given the detailed discussions and their usages for the R-estimators in previous chapters, we constructed this chapter concisely, where we only gave the form of the R-estimators along with their asymptotic distributional L_2-risk, through some theorems. The results of this chapter will be useful for time-series regression in the context of robust rank regression.

To end this chapter, in what follows, we provide the ADRE expressions. We first note that the ADL_2-risk(\hat{\rho}_n^{UR}) is given by Eq. (9.4.6),

ADL_2-risk(\hat{\rho}_n^{UR}) = \eta^2 \left( \text{tr}(\Sigma_{11:2}^{-1}) + \text{tr}(\Sigma_{22:1}^{-1}) \right). (9.6.1)

Then, we have

ADRE(\hat{\rho}_{1n}^{PTSSR}(\lambda) : \hat{\rho}_{1n}^{UR}) = \left( 1 + \frac{\Delta^2 \text{Ch}_{\max}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} \right)^{-1} (9.6.2)

ADRE(\hat{\rho}_{1n}^{LassOR}(\lambda) : \hat{\rho}_{1n}^{UR}) = \left( 1 + \frac{\Delta^2 \text{Ch}_{\max}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} \right)^{-1} (9.6.3)

ADRE(\hat{\rho}_{1n}^{RR} : \hat{\rho}_{1n}^{UR}) = \left( \frac{\text{tr}(\Sigma_{11:2}^{-1})}{\text{tr}(\Sigma_{11}^{-1})} \right) \left( 1 + \frac{\Delta^2 \text{Ch}_{\max}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11}^{-1})} \right)^{-1} (9.6.4)

ADRE(\hat{\rho}_{1n}^{PTR}(\lambda) : \hat{\rho}_n^{UR}) = \left[ 1 + \frac{\text{tr}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) + \frac{\text{tr}(\Sigma_{11}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \right]
+\frac{\Delta^2 \text{Ch}_{\max}(\mathbf{M}_{22,1}^{-1})}{\text{tr}(\mathbf{\Sigma}_{11}^{-1})}\left(2\mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) - \mathcal{H}_{p_2+4}(\lambda^2, \Delta^2)\right)\right]^{-1}

\text{ADRE}(\hat{\rho}_{1n}^{\text{SSR}}(\lambda) : \hat{\rho}_{1n}^{\text{UR}}) = \left[ 1 + \frac{\text{tr}(\mathbf{M}_{22,1}^{-1})}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})}\left\{ 1 - (p_2 - 2)\times\left( 2\mathbb{E}\left[\chi_{p_2+2}^{-2}(\Delta^2)\right] - (p_2 - 2)\mathbb{E}\left[\chi_{p_2+4}^{-4}(\Delta^2)\right]\right)\right\}\right.\\
\left. + (p_2^2 - 4)\frac{\Delta^2 \text{Ch}_{\max}(\mathbf{M}_{22,1})}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})}\mathbb{E}\left[\chi_{p_2+4}^{-4}(\Delta^2)\right]\right]^{-1}

\text{ADRE}(\hat{\rho}_{1n}^{\text{SSR+}}(\lambda) : \hat{\rho}_{1n}^{\text{UR}}) = \left[ \text{ADRE}(\hat{\rho}_{1n}^{\text{SSR}}(\lambda) : \hat{\rho}_{1n}^{\text{UR}}) \right]^{-1}\\
- \frac{\text{tr}(\mathbf{M}_{22,1}^{-1})}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})}\mathbb{E}\left[ \left( 1 - (p_2 - 2)\chi_{p_2+2}^{-2}(\Delta^2)\right)^2 I(\chi_{p_2+2}^2(\Delta^2) < (p_2 - 2)) \right]\\
+ \frac{\Delta^2 \text{Ch}_{\max}(\mathbf{M}_{22,1}^{-1})}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})}\left[ 2\mathbb{E}\left[ \left( 1 - (p_2 - 2)\chi_{p_2+2}^{-2}(\Delta^2)\right)^2 I(\chi_{p_2+2}^2(\Delta^2) < (p_2 - 2)) \right] \right.\\
\left. - \mathbb{E}\left[ \left( 1 - (p_2 - 2)\chi_{p_2+4}^{-2}(\Delta^2)\right)^2 I(\chi_{p_2+4}^2(\Delta^2) < (p_2 - 2)) \right] \right]^{-1}

\text{ADRE}(\hat{\rho}_{1n}^{\text{ridgeR}}(\lambda) : \hat{\rho}_{n}^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{M}_{22,1}^{-1})}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})} \right)\\
\times \left\{ 1 + \frac{\text{tr}\left( \left( \mathbf{I}_{p_1} + k\mathbf{\Sigma}_{22,1}^{-1} \right) \mathbf{\Sigma}_{22,1}^{-1} \right)}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})} + k^2 \frac{\boldsymbol{\delta}_2^\top (\mathbf{\Sigma}_{22,1} + k\mathbf{I}_{p_2}) \boldsymbol{\delta}_2}{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1})} \right\}

\text{ADRE}(\hat{\rho}_{1n}^{\text{EnetR}}(\lambda, \alpha) : \hat{\rho}_{1n}^{\text{UR}}) = \frac{\text{tr}(\mathbf{\Sigma}_{11,2}^{-1}) + \text{tr}(\mathbf{\Sigma}_{22,1}^{-1})}{G(\lambda, \alpha)}

where

G(\lambda, \alpha) = \text{tr}\left( \left( \mathbf{I}_{p_1} + \lambda(1-\alpha)\mathbf{\Sigma}_{11,2}^{-1} \right)^{-2} \mathbf{\Sigma}_{11,2}^{-1} \right)\\
+ \lambda^2(1-\alpha)^2 \Delta^\top \left( \mathbf{\Sigma}_{22,1} + \lambda(1-\alpha)\mathbf{I}_{p_2} \right)^{-2} \Delta\\
+ 2\lambda(1-\alpha)\mathbf{B}^\top \left( \mathbf{C} + \lambda(1-\alpha)\mathbf{I}_{p_1} \right)^{-1} \mathbf{\Delta}.

## 9.7 Problems

- 9.1. Prove Theorem 9.1.

- 9.2. Find the asymptotic null distribution of the test statistic \(\mathcal{L}_n\) for testing \(\mathcal{H}_0 : \rho_2 = \mathbf{0}\).

- 9.3. Prove Theorem 9.2.

- 9.4. Compare the asymptotic distribution L_2-risks of the ridge regression R-estimator with that of the Enet R-estimator of $\rho$.

- 9.5. Show that ADL_2^*-risk($\hat{\beta}_n^{\text{EnetR}}(\lambda, \alpha)$) equals Theorem 9.3 (ix).

- 9.6. Verify Theorem 9.3.

- 9.7. Calculate the ADL_2-risk of $\hat{\rho}_n^{\text{SSR}}$.

## 10 High-Dimensional Models

### 10.1 Introduction

In this chapter, we consider robust rank-based high-dimensional data analysis, where the data may arise from biological, medical, social and economical studies. High-dimensional problems are typically characterized by \( p \gg n \), that is, the number of variables, \( p \), greatly exceeds the number of observations, \( n \). They also pertain to cases when \( p \approx n \). In either of these domains, the nature of the problem changes significantly. We cannot simply apply the techniques described in the previous chapters without modification. Instead, we must rely on the fact that there is a high degree of sparsity in the parameter set. Under this assumption, we can perform subset selection to identify variables that are clearly zero, those that are clearly non-zero and those that lie between these two sets. Due to complexity and model prediction in the presence of outliers, statistical theory is very important using rank-based methodology. This chapter is an extension of chapter 11 of Saleh et al. (2019), where they studied the \( p_n \)-dimensional ridge regression from a post-selection viewpoint. The notation of \( p_n \) is used to show that the dimension of the coefficient set depends on \( n \).

In the high-dimensional problem addressed in this chapter, we assume the model is sparse. As such we consider a multiple regression model for the ith response with covariate \( x_{ij} \) as follows,

\( y_i = \sum_{j=1}^{p_n} x_{ij} \beta_j^* + \varepsilon_i, 1 \le i \le n. \) (10.1.1)

In matrix form, the model is given by

\( \mathbf{y} = \mathbf{X} \boldsymbol{\rho}^* + \boldsymbol{\varepsilon}, \boldsymbol{\rho}^* = (\beta_1^*, ..., \beta_{p_n}^*)^\top, \) (10.1.2)

where \(\boldsymbol{y} = (y_1, \dots, y_n)^\top\) is the response vector, \(\boldsymbol{X} = (\boldsymbol{x}_1, \dots, \boldsymbol{x}_n)^\top\), \(\boldsymbol{x}_i = (x_{i1}, \dots, x_{ip_n})^\top \in \mathbb{R}^{p_n}\), is an \(n \times p_n\) fixed-design matrix, \(\boldsymbol{\beta}^*\) is the true regression coefficient vector/set, and \(\boldsymbol{\varepsilon} = (\varepsilon_1, \dots, \varepsilon_n)^\top\) is independently distributed with c.d.f. \(F(x)\) having finite Fisher information,

\(I(f) = \int \left( \frac{f'(x)}{f(x)} \right)^2 dF(x) < \infty. \quad (10.1.3)\)

The score generating function \(\boldsymbol{\phi}(\boldsymbol{u})\) satisfies

- (i) \(\int_0^1 |\boldsymbol{\phi}(\boldsymbol{u})|\{n(1-u)\}^{-\frac{1}{\zeta}} du < \infty\),
- (ii) \(A_{\boldsymbol{\phi}}^2 = \int_0^1 \boldsymbol{\phi}^2(\boldsymbol{u}) du - \left( \int_0^1 \boldsymbol{\phi}(\boldsymbol{u}) du \right)^2\),
- (iii) \(\gamma(\boldsymbol{\phi}, f) = \int_{-\infty}^{+\infty} f(x) d\boldsymbol{\phi}(F(x)), \ d\boldsymbol{\phi}(F(x)) = \boldsymbol{\phi}(\boldsymbol{u}, f) du. \quad (10.1.4)\)

Also, let

\(\eta^2 = \frac{A_{\boldsymbol{\phi}}^2}{\gamma^2(\boldsymbol{\phi}, f)}. \quad (10.1.5)\)

For any subset \(S \subset \{1, \dots, p_n\}\), with cardinal value \(|S|\), denote \(\boldsymbol{\beta}_S^*\) as a sub-vector of \(\boldsymbol{\beta}^*\) indexed by \(S\). Further, suppose we can divide the index set \(\{1, \dots, p_n\}\) into three disjoint subsets: \(S_1, S_2\), and \(S_3\). In particular, \(S_1\) includes indexes of non-zero \(\boldsymbol{\beta}_i^*\) which are moderately large and easily detected (called effective coefficients); \(S_3\) includes indexes with only zero coefficients; \(S_2\), being the intermediate, includes indexes of those non-zero \(\boldsymbol{\beta}_j^*\) with weak but non-zero effects. We further assume \(S_2 \cup S_3\) are small effect coefficients and thus the complement of \(S_1\), i.e. \(\mathcal{S}_1^c\) is negligible. In other words, \(\sum_{j \in S_1^c} |\boldsymbol{\beta}_j^*|\) is small.

In this chapter, we shall consider the use of LASSO and ridge penalties for selection and estimation simultaneously, in order to keep calculations simple, under some model assumptions as follows:

- A(i) There exist some \(\beta_j^{*'}\)s such that \(|\boldsymbol{\beta}_j^*| \ge c_1 \sqrt{\frac{\log(p_n)}{n}}\) for \(\forall j \in S_1\).
- A(ii) Some \(\beta_j^{*'}\) exist such that \(\|\boldsymbol{\beta}_{S_2}^*\| = O(n^\tau)\) for some \(0 < \tau < 1\).
- A(iii) \(\beta_i^* = 0\) for \(\forall j \in S_3\).
- A(iv) \(\sum_{j \notin S_1} |\boldsymbol{\beta}_j^*| \le \eta_1\) for some \(\eta_1 \ge 0\).
