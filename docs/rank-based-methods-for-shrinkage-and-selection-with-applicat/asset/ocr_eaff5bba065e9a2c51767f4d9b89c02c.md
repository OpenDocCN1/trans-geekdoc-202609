It may be shown that

```
ADB(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) = -\eta \left( [\Delta_j \mathcal{H}_3(\lambda^2, \Delta_j^2) - \lambda(\Phi(\lambda - \Delta_j) \right.
\left. - \Phi(\lambda + \Delta_j)) \mid j = 1, ..., p \right)^T
```

and

```
ADL_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) = \eta^2 \left( \text{tr}(\mathbf{C}_{22 \cdot 1}^{-1}) + \sum_{j=1}^p \left\{ C^{jj} \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) \right. \right.
\left. \left. + C^{jj} \Delta_j^2 \left( 2 \mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2) \right) \right. \right.
\left. \left. + C^{jj} \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) \right) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right\} \right).
```

Thus, the ADRE is obtained by

```
ADRE(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda) : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22 \cdot 1}^{-1})}{\text{tr}(\mathbf{C}_{11 \cdot 2}^{-1})} \right) \left( 1 + \frac{1}{\text{tr}(\mathbf{C}_{11 \cdot 2}^{-1})} \right)
\times \sum_{j=p_1+1}^p \left[ C^{jj} \left\{ \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) + \Delta_j^2 \left( 2 \mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2) \right) \right. \right.
\left. \left. + \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) \right) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right\} \right]^{-1}. \quad (6.5.10)
```

Note that we may write that

```
ADL_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) = ADL_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda))
+ \sum_{j=p_1+1}^p C^{jj} \left[ \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right) \right]
```

and

```
ADL_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) \le ADL_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSR}}(\lambda)).
```