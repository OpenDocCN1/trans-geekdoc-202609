and

\(\text{ADL}_2^*-risk(\hat{\theta}_n^{SSR}) = \eta^2 \left[ \text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_1 \boldsymbol{D}_{22}^{[1]} \boldsymbol{T}_1) \right.\)
\(\left. - (p_2 - 2) \text{tr}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \left( 2 \mathbb{E} \left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] - (p_2 - 2) \mathbb{E} \left[ \chi_{p_2+2}^{-4}(\Delta^2) \right] \right. \right.\)
\(\left. \left. - (p_2^2 - 4) \Delta^2 \text{Ch}_{\min}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \mathbb{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right) \right] .\)

Hence, the ADRE expression is given by

\(\text{ADRE}(\hat{\theta}_n^{SSR} : \hat{\theta}_n^{UR}) = \left( 1 + \frac{\text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_1 \boldsymbol{D}_{22}^{[1]} \boldsymbol{T}_1)} \right)\)
\(\times \left[ 1 + \frac{\text{tr}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_1 \boldsymbol{D}_{22}^{[1]} \boldsymbol{T}_1)} \right.\)
\(\left. \times (p_2 - 2) \left( 2 \mathbb{E} \left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] - (p_2 - 2) \mathbb{E} \left[ \chi_{p_2+2}^{-4}(\Delta^2) \right] \right) \right.\)
\(\left. - \frac{(p_2^2 - 4) \Delta^2 \text{Ch}_{\min}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_1 \boldsymbol{D}_{22}^{[1]} \boldsymbol{T}_1)} \mathbb{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right]^{-1} \ge 1. \ (5.7.2)\)

# ## 5.7.1 Positive-rule Stein–Saleh-type R-estimator of \(\theta\)

We define the PRSSRE as

\(\hat{\theta}_n^{SSR+} = \left( \begin{array}{c} \hat{\boldsymbol{\theta}}_{1n}^{*\text{UR}} - \boldsymbol{T}_1 \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} \\ \hat{\boldsymbol{\theta}}_{2n}^{\text{UR}} - \boldsymbol{T}_2 \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}} (1 - (p_2 - 2)\mathcal{L}_n^{-1}) I(\mathcal{L}_n > (p_2 - 2)) \end{array} \right).\)

**Theorem 5.13** Under the local alternatives, \(\mathcal{K}_{(n)}\), the asymptotic distributional bias, and the lower bound of ADL\(_2\)-risk of the positive-rule Stein–Saleh-type R-estimator, \(\hat{\theta}_n^{SSR+}\), are respectively given by

\(\text{ADB}(\hat{\theta}_n^{SSR+}) = \left( \begin{array}{c} \mathbf{0}_{p_1} \\ ADB(\hat{\boldsymbol{\theta}}_{2n}^{SSR+}) \end{array} \right)\)