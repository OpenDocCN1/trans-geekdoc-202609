Let \(\boldsymbol{C}^{-1} = (C^{ij})\) and \(C^{ij}\) be the \(j\)th block diagonal of \(\boldsymbol{C}^{-1}\). Then

```
\(\boldsymbol{C}^{-1} = \begin{pmatrix} \boldsymbol{C}^{11} & \boldsymbol{C}^{12} \\ \boldsymbol{C}^{21} & \boldsymbol{C}^{22} \end{pmatrix}.\)
```

We are basically interested in the R-estimation of \(\boldsymbol{\beta} = (\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top\) when we suspect that \(\boldsymbol{\beta}_2\), a \(p_2\)-vector of coefficients, is zero and \(\boldsymbol{\beta}_1\), a \(p_1\)-vector of coefficients, is non-zero. Then, we may write, the URE and RRE of \(\boldsymbol{\beta}\), respectively, as

```
\(\hat{\boldsymbol{\beta}}_n^{\text{UR}} = \begin{pmatrix} \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} \\ \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}} \end{pmatrix} \text{ and } \hat{\boldsymbol{\beta}}_n^{\text{RR}} = \begin{pmatrix} \hat{\boldsymbol{\beta}}_{1n}^{\text{RR}} \\ \boldsymbol{0} \end{pmatrix}. \quad (6.3.6)\)
```

From the marginal distribution of \(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}\) and \(\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}}\), we have

```
\(\begin{aligned} \sqrt{n}\left(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} - \boldsymbol{\beta}_1\right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_1}\left(\boldsymbol{0}, \eta^2 \boldsymbol{C}_{11|2}^{-1}\right) \\ \sqrt{n}\left(\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}} - \boldsymbol{\beta}_2\right) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_2}\left(\boldsymbol{0}, \eta^2 \boldsymbol{C}_{22:1}^{-1}\right), \end{aligned}\)
```

where

```
\(\begin{aligned} \boldsymbol{C}_{11\cdot 2} &= \boldsymbol{C}_{11} - \boldsymbol{C}_{12} \boldsymbol{C}_{22}^{-1} \boldsymbol{C}_{12} \\ \boldsymbol{C}_{22\cdot 1} &= \boldsymbol{C}_{22} - \boldsymbol{C}_{21} \boldsymbol{C}_{11}^{-1} \boldsymbol{C}_{21}. \end{aligned}\)
```

The ADL\(_2\)-risk of \(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}\) is given by

```
\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11\cdot 2}^{-1}) + \text{tr}(\boldsymbol{C}_{22:1}^{-1}) \right). \quad (6.3.7)\)
```

Next, consider the local alternative as

```
\(\mathcal{H}_{\mathcal{A}} : \boldsymbol{\beta}_{2(n)} = \frac{1}{\sqrt{n}} \boldsymbol{\delta}_2, \quad \boldsymbol{\delta}_2 = (\delta_2, \dots, \delta_{2_{p_2}})^\top. \quad (6.3.8)\)
```

Under the local alternatives, ADL\(_2\)-risk\((\hat{\boldsymbol{\beta}}_n^{\text{RR}})\) is given by

```
\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{RR}}) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11}^{-1}) + \frac{1}{\eta^2} \boldsymbol{\delta}_2^\top \boldsymbol{\delta}_2 \right). \quad (6.3.9)\)
```

In what follows, based on the definition of \(\Delta^2\), we use the Courant theorem (see Theorem A.2.4 of Anderson, 2003) to obtain

```
\(\text{Ch}_{\min}(\boldsymbol{C}_{22:1}^{-1}) \leq \frac{\boldsymbol{\delta}_2^\top \boldsymbol{\delta}_2}{\boldsymbol{\delta}_2^\top \boldsymbol{C}_{22:1} \boldsymbol{\delta}_2} \leq \text{Ch}_{\max}(\boldsymbol{C}_{22:1}^{-1}),\)
```