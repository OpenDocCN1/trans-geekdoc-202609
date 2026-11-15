# 6.5.2 Stein–Saleh-type R-estimator

We want to define the Stein–Saleh-type R-estimator for our considered restriction, \(\boldsymbol{\beta}_2 = \mathbf{0}\). For this purpose, we use

```
\(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda) = \left( \hat{\beta}_j^{\text{UR}}(1 - \frac{\lambda \eta \sqrt{C^{jj}}}{\sqrt{n}|\hat{\beta}_j^{\text{UR}}|}), \ | j=1, \dots, p) \right)^{\top}\) (6.5.4)
```

which is equivalent to

```
\(\hat{\beta}_j^{\text{SR}}(\lambda) = \hat{\beta}_j^{\text{UR}} - \lambda \eta \sqrt{C^{jj}} \text{sgn}(\hat{\beta}_j^{\text{UR}})/\sqrt{n}, \quad j=1, \dots, p.\) (6.5.5)
```

Thus, we can rewrite \(\hat{\boldsymbol{\beta}}^{\text{SR}}(\lambda)\) w.r.t. \(Z_j\) as

```
\(\sqrt{n}\hat{\beta}_j^{\text{SR}}(\lambda) = \sqrt{n}\hat{\beta}_j^{\text{UR}} \eta \sqrt{C^{jj}} \left( Z_j - \lambda \text{sgn}(Z_j) \right), \quad j=1, \dots, p.\) (6.5.6)
```

Then, finally, we obtain \(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)\) as

```
\(\hat{\beta}_j^{\text{SR}}(\lambda) = \eta \sqrt{C^{jj}} \text{sgn}(Z_j)(|Z_j| - \lambda), \quad j=1, \dots, p.\)
```

Next, the ADB and ADL$_2$-risk of this estimator are given by

```
\(\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)) = \left( -\lambda \eta \sqrt{C^{jj}} \left( 2\Phi(\Delta_j) - 1 \right) | j=1, \dots, p \right)^{\top}\)
```

and

```
\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)) = \eta^2 \left[ \text{tr}(\mathbf{C}_{11.2}^{-1}) \right.\)
\(\left. + \sum_{j=p_1+1}^p C^{jj} \left( 1 + \lambda^2 - 2\lambda \sqrt{\frac{2}{\pi}} \exp \left\{ -\frac{\Delta_j^2}{2} \right\} \right) \right].\) (6.5.7)
```

The optimum value of \(\lambda\) is

```
\(\lambda_{\text{opt}} = \sqrt{\frac{2}{\pi}} \exp \left\{ -\frac{\Delta_j^2}{2} \right\},\)
```

with a maximum

```
\(\lambda^* = \sqrt{\frac{2}{\pi}} \quad \text{when } \Delta_j^2 = 0 \ \) \(\forall j\)
```