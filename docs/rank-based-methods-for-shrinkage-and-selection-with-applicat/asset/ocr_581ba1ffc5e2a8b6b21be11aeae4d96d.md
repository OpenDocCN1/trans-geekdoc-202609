```
\(\times \mathcal{H}_{\mathcal{P}_{p+2}}(\lambda^2, \Delta^2) + \delta_2^T T_2^T \delta_2 \left( 2 \mathcal{H}_{\mathcal{P}_{p+2}}(\lambda^2, \Delta^2) - \mathcal{H}_{\mathcal{P}_{p+4}}(\lambda^2, \Delta^2) \right) \right] .\)
```

The lower bound of the asymptotic risk of \(\hat{\theta}_n^{\text{PTR}}(\lambda)\) is

```
\(\text{ADL}_{2}^*\text{-risk}(\hat{\theta}_n^{\text{PTR}}(\lambda)) = \eta^2 \left[ \text{tr}(\mathcal{K}_1^{-1} + \mathbf{T}_1 \mathbf{D}_{22}^{[1]} \mathbf{T}_1) \right.\)
\(\left. + \text{tr}(\mathcal{K}_2^{-1} + \mathbf{T}_2 \mathbf{D}_{22}^{[2]} \mathbf{T}_2) \mathcal{H}_{\mathcal{P}_{p+2}}(\lambda^2, \Delta^2) \right.\)
\(\left. + \Delta^2 \text{Ch}_{\min}(\mathbf{T}_2 \mathbf{D}_{22}^{[2]} \mathbf{T}_2) \left( 2 \mathcal{H}_{\mathcal{P}_{p+2}}(\lambda^2, \Delta^2) - \mathcal{H}_{\mathcal{P}_{p+4}}(\lambda^2, \Delta^2) \right) \right] .\)
```

Hence,

```
\(\text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathcal{K}_2^{-1} + \mathbf{T}_2 \mathbf{D}_{22}^{[2]} \mathbf{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \mathbf{T}_1 \mathbf{D}_{22}^{[1]} \mathbf{T}_1)} \right)\)
\(\times \left\{ 1 + \frac{\text{tr}(\mathcal{K}_2^{-1} + \mathbf{T}_2 \mathbf{D}_{22}^{[2]} \mathbf{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \mathbf{T}_1 \mathbf{D}_{22}^{[1]} \mathbf{T}_1)} (1 - \mathcal{H}_{\mathcal{P}_{p+2}}(\lambda^2, \Delta^2)) \right.\)
\(\left. - \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{T}_2 \mathbf{D}_{22}^{[2]} \mathbf{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \mathbf{T}_1 \mathbf{D}_{22}^{[1]} \mathbf{T}_1)} \left( 2 \mathcal{H}_{\mathcal{P}_{p+2}}(\lambda^2, \Delta^2) - \mathcal{H}_{\mathcal{P}_{p+4}}(\lambda^2, \Delta^2) \right) \right\}^{-1} \ge 1 .\)
```

# 5.7 Stein–Saleh-type R-estimator of \(\theta\)

In this case, we define the Stein–Saleh-type R-estimator of the intercept vector as

```
\(\hat{\theta}_n^{\text{SSR}} = \begin{pmatrix} \hat{\theta}_{1n}^{*\text{UR}} - \mathbf{T}_1 \hat{\beta}_{1n}^{\text{UR}} \\ \hat{\theta}_{2n}^{*\text{UR}} - \mathbf{T}_2 \hat{\beta}_{2n}^{\text{UR}} (1 - (p_2 - 2) \mathcal{L}_n^{-1}) \end{pmatrix} . \tag{5.7.1}\)
```

**Theorem 5.12** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and the lower bound of ADL2-risk of the Stein–Saleh-type R-estimator, \(\hat{\theta}_n^{\text{SSR}}\), are respectively given by

```
\(\text{ADB}(\hat{\theta}_n^{\text{SSR}}) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -(p_2 - 2) \mathbf{T}_2 \delta_2 \mathbb{E} \left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] \end{pmatrix}\)
```