
where

\(\boldsymbol{B} = \left( \sqrt{C^{jj}} \left[ \Delta_j \mathcal{H}_3 \left( \lambda^2 \boldsymbol{\alpha}, \Delta_j^2 \right) - \lambda \boldsymbol{\alpha} \left( \Phi(\lambda \boldsymbol{\alpha} - \Delta_j) - \Phi(\lambda \boldsymbol{\alpha} + \Delta_j) \right) \right] \big| j=1, \dots, p \right)^\top\)

and

\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{nEnetR}}(\lambda, \boldsymbol{\alpha})) = \eta^2 \left[ \text{tr}\{(\mathbf{I} + \lambda(1-\boldsymbol{\alpha})\mathbf{C}^{-1})^{-2} \mathbf{C}^{-1} \} \right.\)
\(\left. + \lambda^2(1-\boldsymbol{\alpha})^2 \boldsymbol{\Delta}^\top (\mathbf{C} + \lambda(1-\boldsymbol{\alpha})\mathbf{I})^{-2} \boldsymbol{\Delta} \right.\)
\(\left. + 2\lambda(1-\boldsymbol{\alpha}) \mathbf{B}^\top (\mathbf{C} + \lambda(1-\boldsymbol{\alpha})\mathbf{I})^{-2} \boldsymbol{\Delta} \right]\)

## 6.6 Adaptive LASSO

### 6.6.1 Introduction

LASSO is a popular technique for simultaneous estimation and variable selection (Tibshirani, 1996). The Lasso R-estimator is defined as

\(\hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda_n) = \text{argmin}_{\boldsymbol{\beta} \in \mathbb{R}^p} \left\{ D_n(\boldsymbol{\beta}) + \lambda_n \sum_{j=1}^n |\beta_j| \right\}\) (6.6.1)

where \(\lambda_n\) is the tuning parameter for the "L\(_1\)-penalty" which the key to its success. Alternatively, we call it positive-rule Stein-Saleh-type estimator as it is related to the Stein-type estimator with one degree of freedom. The usual best subset selection rule is named "preliminary test subset selector" which is a discrete process. It is also extremely variable whereas LASSO continuously shrinks the coefficients towards 0 as \(\lambda_n\) increases and some shrink to 0 exactly if \(\lambda_n\) is sufficiently large. One may notice that the penalized \(\boldsymbol{\beta}\) are of equal weight, which does not offer any flexibility to seek better solutions. As an improvement, one may define a weighted "L\(_1\)-penalty" as \(\sum_{j=1}^p w_j |\beta_j|\) given by

\(\hat{\boldsymbol{\beta}}_n^{\text{aLassoR}}(\lambda_n) = \text{argmin} \left\{ D_n(\boldsymbol{\beta}) + \lambda_n \sum_{j=1}^p w_j |\beta_j| \right\}.\) (6.6.2)

This weighting factor opens the door to the notion of an “oracle property”. Accordingly, we define a procedure to be “oracle” if estimates \(\hat{\beta}_n\) asymptotically have the following “oracle features” (Fan and Li, 2001).

- (i) Identifies the right-subset model, where \(A = \{j : \beta_j \neq 0\}\) and \(|A| = p_0 < p\).
- (ii) Has the optimal rate. \(\sqrt{n}(\hat{\beta}_S - \beta_S) \xrightarrow{D} \mathcal{N}_{p_0}(\mathbf{0}, \Sigma^*)\), where \(\Sigma^*\) is the covariance matrix of the true sub-model.

Let \(A_n = \{j : \hat{\beta}_j \neq 0\}\). The LASSO selection is consistent if \(P(A_n = A) = 1\).

Now, we consider Eq. (6.6.2) with a specific (data-dependent) weight function, \(\hat{w}_j\), to produce the “adaptive LASSO” (aLASSO) to obtain \(A_n = \{j : \hat{\beta}_{jn}^{\text{UR}} \neq 0\}\) where

\(\hat{\beta}_n^{\text{aLASSO}}(\lambda_n) = \underset{\beta \in \mathbb{R}^p}{\text{argmin}} \left\{ D_n(\beta) + \lambda_n \sum_{j=1}^p \hat{w}_j |\beta_j| \right\}\)
\(= \left( \text{sgn}(\hat{\beta}_j^{\text{UR}}) \left( |\hat{\beta}_j^{\text{UR}}| - \lambda_n \hat{w}_j \eta \sqrt{C^{jj}} \right)^+ \middle| j = 1, \dots, p \right)^\top\)
\(= \left( \eta \sqrt{C^{jj}} \text{sgn}(Z_j) \left( |Z_j| - \lambda_n \hat{w}_j \right)^+ \middle| j = 1, \dots, p \right)^\top \quad (6.6.3)\)

where \(\hat{\beta}_j^{\text{UR}}\) is the usual unrestricted R-estimator discussed in Section 6.2 and \(\hat{w}_j\) is selected to be

\(\hat{w}_j = \frac{1}{|\hat{\beta}_j^{\text{UR}}|^{\gamma^*}}. \quad \gamma^* > 1. \quad (6.6.4)\)

### 6.6.2 Asymptotics for LASSO-type R-estimator

We estimate \(\beta\) by minimizing a penalized Jaeckel’s rank dispersion function, \(Q_n(\phi) + \lambda_n \sum_{j=1}^p |\phi_j|\) for a given \(\lambda_n\). Hence, the objective function given by

\(Q_n(\phi) = \sum_{i=1}^n (y_i - x_i^\top \phi) a_n(R_n(\phi)) + \lambda_n \sum_{j=1}^p |\phi_j| \quad (6.6.5)\)

is minimized at \(\phi = \hat{\beta}_n^{\text{LassoR}}\). The following shows that \(\hat{\beta}_n^{\text{LassoR}}\) is consistent provided that \(\lambda_n = o(n)\).

### Lemma 6.1

If \(\mathbf{C}\) is non-singular and \(\lambda_n/n \to \lambda_0 \ge 0\), then

$$\hat{\boldsymbol{\beta}}_n^{\text{LassoR}} - \text{argmin}\{Q(\boldsymbol{\phi})\} \xrightarrow{P} 0,$$

where

$$Q(\boldsymbol{\phi}) = (\boldsymbol{\phi} - \boldsymbol{\beta})^\top \mathbf{C} (\boldsymbol{\phi} - \boldsymbol{\beta}) + \lambda_0 \sum_{j=1}^p |\phi_j|. \quad (6.6.6)$$

Thus, if \(\lambda_0 = o(n)\), \(\text{argmin}(Q(\boldsymbol{\phi})) = \boldsymbol{\beta}\). So, \(\hat{\boldsymbol{\beta}}_n^{\text{LassoR}}\) is consistent.

**Proof:** Consider Eq. (6.6.5). We need to show that

$$\sup_{\boldsymbol{\phi} \in \mathcal{X}} |Q_n(\boldsymbol{\phi}) - Q(\boldsymbol{\phi}) - \eta^2| \xrightarrow{P} 0 \quad (6.6.7)$$

for any compact set \(\mathcal{K}\) and \(\hat{\boldsymbol{\beta}}_n^{\text{LassoR}} = O_p(1)\). Under Eqs. (6.6.6) and (6.6.7),

$$\left| \underset{\boldsymbol{\phi} \in \mathcal{X}} {\text{argmin}} \{Q_n(\boldsymbol{\phi})\} - \underset{\boldsymbol{\phi} \in \mathcal{X}} {\text{argmin}} \{Q(\boldsymbol{\phi})\} \right| \xrightarrow{P} 0. \quad (6.6.8)$$

Here, \(Q_n(\boldsymbol{\phi})\) is convex. Then Eqs. (6.6.6) and (6.6.7) follow from the point-wise convergence in probability of \(Q_n(\boldsymbol{\phi})\) to \(Q(\boldsymbol{\phi}) + \eta^2\) by standard results (Anderson and Gill, 1982; Pollard, 1991).

### Lemma 6.2

If \(\lambda_n/\sqrt{n} \to \lambda_0 \ge 0\) and \(\mathbf{C}\) is non-singular, then

$$\sqrt{n} \left( \hat{\boldsymbol{\beta}}_n^{\text{LassoR}} - \boldsymbol{\beta} \right) \xrightarrow{P} \underset{\boldsymbol{u} \in \mathbb{R}^p} {\text{argmin}} (V(\boldsymbol{u})), \quad (6.6.9)$$

where

$$V(\boldsymbol{u}) = -2\boldsymbol{u}^\top \boldsymbol{W} + \gamma(f, f)\boldsymbol{u}^\top \mathbf{C} \boldsymbol{u} + \lambda_0 \sum_{j=1}^p [u_j \text{sgn}(\beta_j) I(\beta_j \neq 0) + |u_j| I(\beta_j = 0)] \quad (6.6.10)$$

where \(\boldsymbol{W}\) has a \(\mathcal{N}_p(\boldsymbol{0}, A_\phi^2 \mathbf{C})\) distribution.

**Proof:** Define \(V_n(\boldsymbol{u})\) as

$$\begin{aligned} V_n(\boldsymbol{u}) &= \sup_{\|\boldsymbol{U}\| \le Mn^{-1/2}} \left| D_n(\boldsymbol{\beta}^* + \frac{\boldsymbol{u}}{\sqrt{n}}) - D_n(\boldsymbol{\beta}^*) \right. \\ &\quad \left. + n^{-1/2} \boldsymbol{L}_n^\top (\boldsymbol{\beta}^*) \boldsymbol{u} - \frac{1}{2} \gamma(\phi, f) n^{-1/2} \boldsymbol{u}^\top \mathbf{C} \boldsymbol{u} \right| \xrightarrow{P} 0 \end{aligned}$$

= -2\mathbf{u}^\top\mathbf{W} + \frac{1}{2}\gamma(\phi, f)^\top\mathbf{u}^\top\mathbf{C}\mathbf{u} + \lambda_n \sum_{j=1}^p \left( \left| \boldsymbol{\beta}^*_j + \frac{u_j}{\sqrt{n}} \right| - \left| \boldsymbol{\beta}^*_j \right| \right)

where we have

\(\lambda_n \sum_{j=1}^p \left[ \left| \boldsymbol{\beta}^*_j + \frac{u_j}{\sqrt{n}} \right| - \left| \boldsymbol{\beta}^*_j \right| \right] \rightarrow \lambda_0 \sum_{j=1}^p \left[ u_j \text{sgn}(\beta_j^*) I(\beta_j^* \neq 0) + |u_j| I(\beta_j^* = 0) \right] .\)

Thus, \(V_n(\mathbf{u}) \xrightarrow{D} V(\mathbf{u})\) with finite dimensional convergence. Since \(V(\mathbf{u})\) is convex and \(V(\mathbf{u})\) has a unique minimum, it follows from Geyer (1996); Knight and Fu (2000) that

\(\text{argmin}\{V_n(\mathbf{u})\} = \sqrt{n}(\hat{\boldsymbol{\beta}}_n^{\text{LassoR}} - \boldsymbol{\beta}) \xrightarrow{D} \text{argmin}\{V(\mathbf{u})\} .\)

If \(\lambda_n = 0\), then \(\text{argmin}\{V(\mathbf{u})\} = \mathbf{C}^{-1}\mathbf{W}, \mathbf{W} \sim \mathcal{N}_p(\mathbf{0}, \eta^2 \mathbf{C}^{-1}) .\)

This lemma implies that when \(\lambda_n = O(n^{\frac{1}{2}})\), essentially \(\mathcal{A}_n\) cannot actually be \(\mathcal{A}\) with a positive probability.

### Lemma 6.3

If \(\lambda_n/n \to 0\) and \(\lambda_n/\sqrt{n} \to \infty\) and \(\lambda_n \to \infty\), then

\(\frac{n}{\lambda_n}(\hat{\boldsymbol{\beta}}_n^{\text{LassoR}} - \boldsymbol{\beta}) \xrightarrow{P} \text{argmin}\{V_3(\mathbf{u})\}\)

where

\(V_3(\mathbf{u}) = \frac{1}{2}\gamma(\phi, f)^\top\mathbf{u}^\top\mathbf{C}\mathbf{u} + \sum_{j=1}^p [u_j \text{sgn}(\beta_j^*) I(\beta_j^* \neq 0) + |u_j| I(\beta_j^* = 0)] .\)

### 6.6.3 Oracle Property of aLASSO

Now, we present the theorem regarding the key “oracle” property of the aLASSO R-estimator.

### Theorem 6.1

Suppose that \(\lambda_n/\sqrt{n} \to 0\) and \(\lambda_n n^{(\gamma-1)/2} \to \infty\). Then, the aLASSO R-estimator satisfies asymptotic normality, \(\sqrt{n}(\hat{\boldsymbol{\beta}}_{\mathcal{A}}^{\text{aLassoR}} - \boldsymbol{\beta}_{\mathcal{A}}) \xrightarrow{D} \mathcal{N}_{p_0}(\mathbf{0}, \eta^2 \mathbf{C}_{11}^{-1}) .\)
