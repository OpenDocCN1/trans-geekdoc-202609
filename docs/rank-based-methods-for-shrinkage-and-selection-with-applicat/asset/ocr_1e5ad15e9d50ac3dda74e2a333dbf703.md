we use the lower bound of Eq. (7.3.5) of the L$_2$-risk functions for all estimators except the unrestricted R-estimator. This result will enhance the provided comparisons.

For any estimator $\hat{\boldsymbol{\beta}}_n$, we define

$$\text{ADRE}(\hat{\boldsymbol{\beta}}_n : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \frac{\text{ADL}_2^*\text{-risk}\left(\hat{\boldsymbol{\beta}}_n^{\text{UR}}\right)}{\text{ADL}_2^*\text{-risk}\left(\hat{\boldsymbol{\beta}}_n\right)}.$$

# **Theorem 7.3** The ADRE of the R-estimators are given by

+   (i) $$\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{RR}} : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \frac{\text{tr}(\mathbf{C}_{11.2}^{-1}) + \text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1}) + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22.1}^{-1)},$$

+   (ii) $$\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{Lasso}_{\lambda (\lambda_{\text{opt}})}} : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \frac{\text{tr}(\mathbf{C}_{11.2}^{-1}) + \text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1}) + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22.1}^{-1})} = \left(1 + \frac{\text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})}\right) \left(1 + \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})}\right)^{-1},$$

+   (iii) $$\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{ridge}(k)} : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \frac{\text{tr}(\mathbf{C}_{11.2}^{-1}) + \text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1}) + \text{tr}(\mathbf{I}_{p_2} + k\mathbf{C}_{22.1}^{-1})^{-2}\mathbf{C}_{22.1} + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22.1}^{-1})} = \left(1 + \frac{\text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})}\right) \left(1 + \frac{\text{tr}(\mathbf{I}_{p_2} + k\mathbf{C}_{22.1}^{-1})^{-2}\mathbf{C}_{22.1}}{\text{tr}(\mathbf{C}_{11.2}^{-1})} + \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})}\right)^{-1},$$

+   (iv) $$\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}} : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \left(1 + \frac{\text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})}\right) \times \left\{ 1 + \frac{\text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})} \left(1 - \mathcal{H}_{p_2+2}(\chi_{p_2}^2(\alpha); \Delta^2)\right) + \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})} \left(2\mathcal{H}_{p_2+2}(\chi_{p_2}^2(\alpha); \Delta^2) - \mathcal{H}_{p_2+4}(\chi_{p_2}^2(\alpha); \Delta^2)\right) \right\}^{-1},$$

+   (v) $$\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{SSR}} : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \left(1 + \frac{\text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})}\right) \times \left\{ 1 + \frac{\text{tr}(\mathbf{C}_{22.1}^{-1})}{\text{tr}(\mathbf{C}_{11.2}^{-1})} \times \left\{ (p_2 - 2) \text{tr}(\mathbf{C}_{22.1}^{-1}) \left( 2\mathbb{E}\left[\chi_{p_2+2}^{-2}(\Delta^2)\right] - (p_2 - 2)\mathbb{E}\left[\chi_{p_2+4}^{-4}(\Delta^2)\right] \right) \right\} \right\}$$