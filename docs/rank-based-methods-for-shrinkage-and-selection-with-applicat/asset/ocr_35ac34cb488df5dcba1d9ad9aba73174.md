\(-\eta^2 \text{tr}(\mathbf{C}_{22:1}^{-1}) \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+2}^2(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right]\) (6.4.20)

where

\(Y(\lambda, \Delta^2) = 2 \mathbb{E} \left[ (1 - \lambda \chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right] - \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+4}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+4}^2(\Delta^2) \le \lambda) \right].\) (6.4.21)

Thus, the lower-bound of the ADL$_2$-risk of \(\hat{\beta}_n^{\text{SSR}+}(\lambda)\) is given by

\(\text{ADL}_2^* \text{risk}(\hat{\beta}_n^{\text{SSR}+}(\lambda)) = \text{ADL}_2^* \text{risk}(\hat{\beta}_n^{\text{SSR}}(\lambda)) + \Delta^2 \text{Ch}_{min}(\mathbf{C}_{22:1}^{-1}) Y(\lambda, \Delta^2) - \eta^2 \text{tr}(\mathbf{C}_{22:1}^{-1}) \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+2}^2(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right].\) (6.4.22)

Hence,

\(\text{ADRE}(\hat{\beta}_n^{\text{SSR}+}(\lambda) : \hat{\beta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \right) \left[ \frac{\text{ADL}_2 \text{-risk}(\hat{\beta}_n^{\text{SSR}}(\lambda))}{\eta^2 \text{tr}(\mathbf{C}_{11:2}^{-1})} + A \right]^{-1}\) (6.4.23)

where

\(A = \frac{\Delta^2 \text{Ch}_{min}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} Y(\lambda, \Delta^2) - \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+2}^2(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right].\) (6.4.24)

# 6.5 Subset Selectors

# 6.5.1 Preliminary Test Subset Selector R-estimator

We want to define the preliminary test R-estimator for our considered restriction, \(\beta_2 = \mathbf{0}\). In this regard,

\(\hat{\beta}_n^{\text{PTSER}}(\lambda) = \left( \hat{\beta}_j^{\text{UR}} I(|\hat{\beta}_j^{\text{UR}}| > \lambda \eta \sqrt{C^{jj}}), j=1, ..., p \right)^\top\) (6.5.1)