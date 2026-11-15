```
\times(2\mathcal{H}_{p_2+2}(\chi^2_{p_2}(\alpha); \Delta^2) - \mathcal{H}_{p_2+4}(\chi^2_{p_2}(\alpha); \Delta^2))\right]
```

where \(\mathcal{H}_\nu(c;\Delta^2)\) is the c.d.f. of \(\chi^2\)-distribution with \(\nu\) d.f. and non-centrality parameter \(\Delta^2\) evaluated at \(c\). Further,

```
ADL_2\text{-risk}\left(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\alpha):\mathbf{C}_{11\cdot 2},\mathbf{C}_{22\cdot 1}\right) = \eta^2 p_1\n+\eta^2 p_2(1-\mathcal{H}_{p_2+2}(\chi^2_{p_2}(\alpha); \Delta^2))\n+\Delta^2(2\mathcal{H}_{p_2+2}(\chi^2_{p_2}(\alpha); \Delta^2) - \mathcal{H}_{p_2+4}(\chi^2_{p_2}(\alpha); \Delta^2)).
```

# (iv) Stein–Saleh-type Shrinkage R-estimator

```
ADB(\hat{\boldsymbol{\beta}}_n^{\text{SSR}}) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\boldsymbol{\delta}_2(p_2-2)\mathbb{E}[\chi_{p_2+2}^{-2}(\Delta^2)] \end{pmatrix},
```

```
ADL_2^*\text{-risk}\left(\hat{\boldsymbol{\beta}}_n^{\text{SSR}}\right) = \eta^2\left[\text{tr}(\mathbf{C}_{11\cdot 2}^{-1}) + \text{tr}(\mathbf{C}_{22\cdot 1}^{-1})\right.\n-\{(p_2-2)\text{tr}(\mathbf{C}_{22\cdot 1}^{-1})\left(2\mathbb{E}[\chi_{p_2+2}^{-2}(\Delta^2)]-(p_2-2)\mathbb{E}[\chi_{p_2+2}^{-4}(\Delta^2)]\right)\}\n\left.+(p_2^2-4)\Delta^2\text{Ch}_{\min}(\mathbf{C}_{22\cdot 1}^{-1})\mathbb{E}[\chi_{p_2+4}^{-4}(\Delta^2)]\right]
```

where

```
\mathbb{E}[\chi_{p_2}^{-2\nu}(\Delta^2)] = \int_0^\infty x^{-2\nu} d\mathcal{H}_{p_2}(x;\Delta^2).
```

Furthermore,

```
ADL_2\text{-risk}\left(\hat{\boldsymbol{\beta}}_n^{\text{SSR}}:\mathbf{C}_{11\cdot 2},\mathbf{C}_{22\cdot 1}\right) = \eta^2 p_1 + \eta^2\left(p_2-(p_2-2)^2\mathbb{E}[\chi_{p_2+2}^{-2}(\Delta^2)]\right).
```

# (v) Positive-rule Stein–Saleh-type Shrinkage R-estimator

```
ADB(\hat{\boldsymbol{\beta}}_n^{\text{SSR+}}) = \begin{pmatrix} \mathbf{0}_{p_1} \\ ADB(\hat{\boldsymbol{\beta}}_{2n}^{\text{SSR}}) - \delta_2 \mathbb{E}[(1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2))I(\chi_{p_2+2}^2(\Delta^2) < p_2-2)] \end{pmatrix},
```

```
ADL_2^*\text{-risk}\left(\hat{\boldsymbol{\beta}}_n^{\text{SSR+}}\right) = ADL_2^*\text{-risk}\left(\hat{\boldsymbol{\beta}}_n^{\text{SSR}}\right)\n-\eta^2 \text{tr}(\mathbf{C}_{22\cdot 1}^{-1})\mathbb{E}[(1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2))^2 I(\chi_{p_2+2}^2(\Delta^2) < p_2-2)]\n-\Delta^2\text{Ch}_{\min}(\mathbf{C}_{22\cdot 1}^{-1})\{2\mathbb{E}[(1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2))I(\chi_{p_2+2}^2(\Delta^2) < p_2-2)]
```