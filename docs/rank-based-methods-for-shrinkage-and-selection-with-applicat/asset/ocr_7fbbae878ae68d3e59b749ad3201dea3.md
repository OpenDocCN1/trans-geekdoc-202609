# ### 5.2.3 Preliminary Test R-estimator of \(\boldsymbol{\beta}\)

The PTRE of the slope vector is given by

```
\(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda) = \left( \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}^\top}, \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}^\top} I(\mathcal{L}_n \ge \lambda^2) \right)^\top\)
\(= \left( \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}^\top}, \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}^\top} - \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}^\top} I(\mathcal{L}_n \le \lambda^2) \right)^\top . \quad (5.2.21)\)
```

Then, using Theorem 5.1, we may establish the following theorem.

**Theorem 5.4** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and \(\text{ADL}_2\)-risk of the preliminary test R-estimator, \(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)\), are respectively given by

```
\(\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\boldsymbol{\delta}_2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \end{pmatrix}\)
```

and

```
\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \eta^2 \left[ \text{tr}(\boldsymbol{D}_{22}^{[1]}) + \text{tr}(\boldsymbol{D}_{22}^{[2]}) (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) \right.\)
\(\left. + \eta^{-1} \boldsymbol{\delta}_2^\top \boldsymbol{\delta}_2 \left( 2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) - \mathcal{H}_{p_2+4}(\lambda^2, \Delta^2) \right) \right]\)
```

where \(\boldsymbol{D}_{22} = \text{Diag}(\boldsymbol{D}_{22}^{[1]}, \boldsymbol{D}_{22}^{[2]}).\)

Hence, the lower bound is given by

```
\(\text{ADL}_2^*\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \eta^2 \left[ \text{tr}(\boldsymbol{D}_{22}^{[1]}) + \text{tr}(\boldsymbol{D}_{22}^{[2]})(1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) \right.\)
\(\left. + \Delta^2 \text{Ch}_{\min}(\boldsymbol{D}_{22}^{[2]}) \left( 2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) - \mathcal{H}_{p_2+4}(\lambda^2, \Delta^2) \right) \right].\)
```

Therefore, the lower bound ADRE of \(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)\) is given by

```
\(\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda) : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\boldsymbol{D}_{22}^{[2]})}{\text{tr}(\boldsymbol{D}_{22}^{[1]})} \right) \left\{ 1 + \frac{\text{tr}(\boldsymbol{D}_{22}^{[2]})}{\text{tr}(\boldsymbol{D}_{22}^{[1]})} \right.\)
\(\left. + \frac{\Delta^2 \text{Ch}_{\min}(\boldsymbol{D}_{22}^{[2]})}{\text{tr}(\boldsymbol{D}_{22}^{[1]})} \left( 2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) - \mathcal{H}_{p_2+4}(\lambda^2, \Delta^2) \right) \right\}^{-1} \ge 1.\)
```