where the term \(\boldsymbol{D}_{11} = \mathcal{K}^{-1} + \boldsymbol{T}_0 \boldsymbol{D}_{22} \boldsymbol{T}_0\), \(\boldsymbol{T}_0 = \text{Diag}(\bar{x}_1, ..., \bar{x}_p)\), and the term \(\boldsymbol{D}_{22}^{-1} = \text{Diag}(\chi_1 Q_1, ..., \chi_p Q_p)\).

# ## 5.6.1 General Shrinkage R-estimator of Intercept

We consider the general shrinkage R-estimator of \(\theta\) when the R-estimator of \(\boldsymbol{\beta}\) is

```
\(\hat{\boldsymbol{\beta}}_n^{\text{shrinkageR}}(c) = \left( \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}^\top}, c\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}^\top} \right)^\top\)
```

given by

```
\(\hat{\theta}_n^{\text{shrinkageR}}(c) = \left( \hat{\theta}_{1n}^{\text{UR}^\top}, \hat{\theta}_{2n}^{\text{shrinkageR}^\top}(c) \right)^\top, \quad (5.6.2)\)
```

where

```
\(\hat{\theta}_{2n}^{\text{shrinkageR}}(c) = \hat{\theta}_{2n}^{\text{UR}} + (1-c)\boldsymbol{T}_2 \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}}, \quad 0 < c < 1.\)
```

**Theorem 5.10** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and the lower bound of ADL\(_2\)-risk of the shrinkage R-estimator, \(\hat{\theta}_n^{\text{shrinkageR}}(c)\), are respectively given by

```
\(\text{ADB}(\hat{\theta}_n^{\text{shrinkageR}}(c)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ (1-c)\boldsymbol{T}_2 \boldsymbol{\delta}_2 \end{pmatrix} \quad (5.6.3)\)
```

where \(\boldsymbol{T}_0 = (\boldsymbol{T}_1, \boldsymbol{T}_2)\) and

```
\(\begin{aligned} \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{shrinkageR}}(c)) = \eta^2 \big[ \text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_1 \boldsymbol{D}_{22}^{[1]} \boldsymbol{T}_1) + c^2 \text{tr}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \\ + (1-c)^2 \boldsymbol{\delta}_2^\top \boldsymbol{T}_2 \boldsymbol{\delta}_2 + 2c(1-c) \text{tr}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \big]. 
\end{aligned}\)
```

The lower bound of ADL\(_2\)-risk is given by

```
\(\begin{aligned} \text{ADL}_2^*\text{-risk}(\hat{\theta}_n^{\text{shrinkageR}}(c)) = \eta^2 \big[ \text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_1 \boldsymbol{D}_{22}^{[1]} \boldsymbol{T}_1) + c^2 \text{tr}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \\ + (1-c)^2 \Delta^2 \text{Ch}_{\min}(\boldsymbol{T}_2^\top \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \\ + 2c(1-c) \text{tr}(\boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2) \big]. 
\end{aligned}\)
```

Hence,

```
\(\text{ADRE}(\hat{\theta}_n^{\text{shrinkageR}}(c) : \hat{\theta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathcal{K}_2^{-1} + \boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2)}{\text{tr}(\mathcal{K}_1^{-1} + \boldsymbol{T}_2 \boldsymbol{D}_{22}^{[2]} \boldsymbol{T}_2)} \right)\)
```