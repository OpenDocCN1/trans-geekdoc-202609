Next, we consider the test of hypothesis $\mathcal{H}_o : \boldsymbol{\beta}^*_{S_2} = 0$. For this problem, we consider the statistic
\[ \boldsymbol{L}_{n(2)}(\hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}, \mathbf{0}) = \left( L_{n(2)}(\hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}, 0), \dots L_{n(2)p_{2n}}(\hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}, 0) \right)^{\top} \] (10.4.17)

where
\[ \sup_{\|\mathbf{w}_{S_2}\| \leq k} n^{-\frac{1}{2}} \left\| \boldsymbol{L}_{n(2)} \left( \hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}, n^{-\frac{1}{2}} \mathbf{w}_{S_2} \right) - \boldsymbol{L}_{n(2)} \left( \boldsymbol{\beta}^*_{S_1}, \mathbf{0} \right) + \gamma(\phi, f) \mathbf{C}_{n22 \cdot 1} \mathbf{w}_{S_2} \right\| \to^P 0. \] (10.4.18)

Hence,
\[ \mathbf{w}_{S_2} = \sqrt{n} \left( \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_2} (\gamma_n) - \boldsymbol{\beta}^*_{S_2} \right) \]
\[ = \gamma^{-1}(\phi, f) \mathbf{C}_{n22 \cdot 1}^{-1} \boldsymbol{L}_{n(2)} (\boldsymbol{\beta}^*_{S_1}, \mathbf{0}) + o_p(1) \]
\[ \xrightarrow{\mathcal{D}} \mathcal{N}_{p_{2n}} (\mathbf{0}, \gamma^2 \mathbf{C}^{-1}_{22 \cdot 1}). \] (10.4.19)

For the test of $\mathcal{H}_o : \boldsymbol{\beta}^*_{S_2} = 0$, we define the test statistic
\[ \mathcal{L}_n = A_n^{-2} \left[ \boldsymbol{L}_{n(2)} \left( \hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}, \mathbf{0} \right) \right]^{\top} \mathbf{C}_{n22 \cdot 1} \left[ \boldsymbol{L}_{n(2)} \left( \hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}, \mathbf{0} \right) \right] \] (10.4.20)
\[ = \frac{1}{\eta^2} \left[ \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_2} (\gamma_n) \right]^{\top} \mathbf{C}_{n22 \cdot 1} \left[ \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_2} (\gamma_n) \right] + o_p(1). \] (10.4.21)

If we use Eq. (10.4.21), then we can estimate $\eta$ by using median $|y_\alpha - \sum_{1 \leq i \leq n}^{p_n} x_{\alpha i} \beta^*_j|$. Further, we note that
\[ \hat{\boldsymbol{\beta}}^{\text{RR}}_{1n} = \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_1} (\gamma_n) + \mathbf{c}_{n11}^{-1} \mathbf{c}_{n12} \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_2} (\gamma_n) + o_p(1). \] (10.4.22)

# 10.5 Post-selection Shrinkage R-estimators

We now have two R-estimators, namely, $\hat{\boldsymbol{\beta}}^{\text{RR}}_{1n}$ and $\hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_1} (\gamma_n)$. From Sen and Saleh (1987), first we define the preliminary test estimator.

# (a) Preliminary test R-estimator

\[ \hat{\boldsymbol{\beta}}^{\text{PTR}}_{S_1} (\gamma_n) = \hat{\boldsymbol{\beta}}^{\text{RR}}_{1n} I(\mathcal{L}_n \leq \lambda^2) + \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_1} (\gamma_n) I(\mathcal{L}_n > \lambda^2) \]
\[ = \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_1} (\gamma_n) - \left( \hat{\boldsymbol{\beta}}^{\text{ridgeR}}_{S_1} (\gamma_n) - \hat{\boldsymbol{\beta}}^{\text{RR}}_{1n} \right) I(\mathcal{L}_n \leq \lambda^2) \]