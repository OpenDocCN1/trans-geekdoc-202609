

\(\boldsymbol{L}_{n(2)}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) = (\boldsymbol{L}_{n_{p+1}}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2), \dots, \boldsymbol{L}_{n_p}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2))^{\top}.\)

令

\(\dot{\boldsymbol{L}}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}) = (\dot{\boldsymbol{L}}_{n_{p+1}}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}), \dots, \dot{\boldsymbol{L}}_{n_p}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}))^{\top}.\) (6.4.6)

然后，我们提出以下检验统计量

\(\mathcal{L}_n = A_n^{-2} \dot{\boldsymbol{L}}_{n(2)}^{\top}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}) \boldsymbol{C}_{22 \cdot 1}^{-1} \dot{\boldsymbol{L}}_{n(2)}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}}, \mathbf{0}),\) (6.4.7)

where

\(A_n^2 = \frac{1}{n-1} \sum_{i=1}^n (a_n(i) - \bar{a}_n)^2, \quad \bar{a}_n = \frac{1}{n} \sum_{i=1}^n a_n(i).\)

注意，\(\mathcal{L}_n\) 可近似为

\(\mathcal{L}_n \overset{\mathcal{D}}{=} \frac{\gamma^2(\boldsymbol{\phi}, f)}{A_{\phi}^2} \eta \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}\top} \boldsymbol{C}_{22 \cdot 1} \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} + o_p(1)\)

在公式 (6.2.6) 所假设的正则性条件下，当 \(n \to \infty\) 时，在 \(\mathcal{H}_0\) 下，\(\mathcal{L}_n\) 服从具有 \(p_2\) 个自由度的 \(\chi^2\) 分布。

我们将发现，

\(\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\delta_2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \end{pmatrix}\) (6.4.8)

and

\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11 \cdot 2}^{-1}) + \text{tr}(\boldsymbol{C}_{22 \cdot 1}^{-1}) \left( 1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \right) + \eta^{-2} \delta_2^\top \delta_2 Z(\lambda, \Delta) \right)\) (6.4.9)

where

\(Z(\lambda, \Delta) = 2 \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) - \mathcal{H}_{p_2+4}(\lambda^2, \Delta^2).\) (6.4.10)

因此，下界由以下给出

\(\text{ADL}_2^*\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\lambda)) = \eta^2 \left( \text{tr}(\boldsymbol{C}_{11 \cdot 2}^{-1}) + \text{tr}(\boldsymbol{C}_{22 \cdot 1}^{-1}) (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) + \Delta^2 \text{Ch}_{\min}(\boldsymbol{C}_{22 \cdot 1}^{-1}) Z(\lambda, \Delta) \right)\)

\(= \eta^2 \text{tr}(\mathbf{C}^{-1}_{11:2}) \left( 1 + \frac{\text{tr}(\mathbf{C}^{-1}_{22:1})}{\text{tr}(\mathbf{C}^{-1}_{11:2})} (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) + \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}^{-1}_{22:1})}{\text{tr}(\mathbf{C}^{-1}_{11:2})} Z(\lambda, \Delta) \right).\) (6.4.11)

然后，\(\hat{\beta}^{\text{PTR}}_n(\lambda)\) 的下界 ADRE 由以下给出

\(\text{ADRE}(\hat{\beta}^{\text{PTR}}_n(\lambda) : \hat{\beta}^{\text{UR}}_n) = \left( 1 + \frac{\text{tr}(\mathbf{C}^{-1}_{22:1})}{\text{tr}(\mathbf{C}^{-1}_{11:2})} \right) \times \left( 1 + \frac{\text{tr}(\mathbf{C}^{-1}_{22:1})}{\text{tr}(\mathbf{C}^{-1}_{11:2})} (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) + \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}^{-1}_{22:1})}{\text{tr}(\mathbf{C}^{-1}_{11:2})} Z(\lambda, \Delta) \right)^{-1}.\) (6.4.12)

该估计量是一个离散过程且不稳定，数据的微小变化可能导致选择不同的模型。

还需进一步注意，对于以下情况

\(0 < \Delta^2 \le \frac{\text{tr}(\mathbf{C}^{-1}_{22:1})}{\text{Ch}_{\min}(\mathbf{C}^{-1}_{22:1})} \frac{\mathcal{H}_{p_2+2}(\lambda^2; \Delta^2)}{[2\mathcal{H}_{p_2+2}(\lambda^2; \Delta^2) - \mathcal{H}_5(\lambda^2; \Delta^2)]} = \Delta^2(\lambda),\)

我们发现 \(\hat{\beta}^{\text{PTR}}_{2n}(\lambda)\) 优于 \(\hat{\beta}^{\text{UR}}_{2n}\)。否则，如果 \(\Delta^2 > \Delta^2(\lambda)\)，则 \(\hat{\beta}^{\text{UR}}_{2n}\) 优于 \(\hat{\beta}^{\text{PTR}}_{2n}(\lambda)\)。因此，两者中没有一个能一致地优于另一个。

### 6.4.2 Stein–Saleh类型 R估计器

The Stein–Saleh-type R-estimator of \(\boldsymbol{\beta} = (\boldsymbol{\beta}^\top_1, \boldsymbol{\beta}^\top_2)^\top\) is given by

\(\hat{\boldsymbol{\beta}}^{\text{SSR}}_n(\lambda) = \begin{pmatrix} \hat{\boldsymbol{\beta}}^{\text{UR}}_{1n} \\ \cdots \\ \vdots \\ (1 - \lambda \mathcal{L}^{-1}_n) \hat{\boldsymbol{\beta}}^{\text{UR}}_{2n} \end{pmatrix}\) (6.4.13)

where \(\lambda\) is a shrinkage factor and usually taken to be \(\lambda = p_2 - 2\).

The ADB and ADL\(_2\)-risk of \(\hat{\boldsymbol{\beta}}^{\text{SSR}}_n(\lambda)\) are then given by

\(\text{ADB}(\hat{\boldsymbol{\beta}}^{\text{SSR}}_n(\lambda)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\delta_2 \lambda \mathbb{E} \left[ \chi^{-2}_{p_2+2}(\Delta^2) \right] \end{pmatrix}\) (6.4.14)

and

\(\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}^{\text{SSR}}_n(\lambda)) = \eta^2 \left( \text{tr}(\mathbf{C}_{11:2}^{-1}) + \text{tr}(\mathbf{C}_{22:1}^{-1}) - \lambda \text{tr}(\mathbf{C}_{22:1}^{-1}) X(\lambda, \Delta^2) + \lambda(\lambda + 4) \delta_2^\top \delta_2 \mathbb{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right)\)

where

\(X(\lambda, \Delta^2) = 2 \mathbb{E} \left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] - \lambda \mathbb{E} \left[ \chi_{p_2+2}^{-4}(\Delta^2) \right]\)

and the lower bound is

\(\text{ADL}_2^*\text{-risk}(\hat{\boldsymbol{\beta}}^{\text{SSR}}_n(\lambda)) = \eta^2 \left[ \text{tr}(\mathbf{C}_{11:2}^{-1}) + \text{tr}(\mathbf{C}_{22:1}^{-1}) - \lambda \text{tr}(\mathbf{C}_{22:1}^{-1}) X(\lambda, \Delta^2) + \lambda(\lambda + 4) \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1}) \mathbb{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right]\)

Hence, the ADRE expression is given by

\(\text{ADRE}(\hat{\boldsymbol{\beta}}^{\text{SSR}}_n(\lambda) : \hat{\boldsymbol{\beta}}^{\text{UR}}_n) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \right) \left[ 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} (1 - \lambda X(\lambda, \Delta^2)) + \lambda(\lambda + 4) \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \mathbb{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right]^{-1}\)

### 6.4.3 正则 Stein–Saleh类型 R估计器

The positive-rule Stein–Saleh-type R-estimator (PRSSRE) is defined by

\(\hat{\beta}_n^{SSR+}(\lambda) = \begin{pmatrix} \dots & \hat{\beta}_{ln}^{UR} & \dots \\ \dots & \dots & \dots \\ (1 - \lambda \mathcal{L}_n^{-1}) I(\mathcal{L}_n > \lambda) \hat{\beta}_{2n}^{UR} \end{pmatrix}\)

where \(\lambda = p_2 - 2\) is the shrinkage factor. Consequently, one may obtain the ADB and \(ADL_2\)-risk of \(\hat{\beta}^{SSR+}(\lambda)\) given by

\(\text{ADB}(\hat{\beta}_n^{SSR+}(\lambda)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\delta_2 \mathbb{E} \left[ (1 - \lambda \chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right] \end{pmatrix}\)

and

\(\text{ADL}_2\text{-risk}(\hat{\beta}_n^{SSR+}(\lambda)) = \text{ADL}_2\text{-risk}(\hat{\beta}_n^{SSR}(\lambda)) + \delta_2^\top \delta_2 Y(\lambda, \Delta^2) - \eta^2 \text{tr}(\mathbf{C}_{22:1}^{-1}) \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+2}^2(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right]\) (6.4.20)

where

\(Y(\lambda, \Delta^2) = 2 \mathbb{E} \left[ (1 - \lambda \chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right] - \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+4}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+4}^2(\Delta^2) \le \lambda) \right].\) (6.4.21)

Thus, the lower-bound of the ADL$_2$-risk of \(\hat{\beta}_n^{\text{SSR}+}(\lambda)\) is given by

\(\text{ADL}_2^*\text{-risk}(\hat{\beta}_n^{\text{SSR}+}(\lambda)) = \text{ADL}_2^*\text{-risk}(\hat{\beta}_n^{\text{SSR}}(\lambda)) + \Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1}) Y(\lambda, \Delta^2) - \eta^2 \text{tr}(\mathbf{C}_{22:1}^{-1}) \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+2}^2(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right].\) (6.4.22)

Hence,

\(\text{ADRE}(\hat{\beta}_n^{\text{SSR}+}(\lambda) : \hat{\beta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \right) \left[ \frac{\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{SSR}}(\lambda))}{\eta^2 \text{tr}(\mathbf{C}_{11:2}^{-1})} + A \right]^{-1}\) (6.4.23)

where

\(A = \frac{\Delta^2 \text{Ch}_{\min}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} Y(\lambda, \Delta^2) - \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \mathbb{E} \left[ \left( 1 - \lambda \chi_{p_2+2}^2(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) \le \lambda) \right].\) (6.4.24)

## 6.5 子集选择器

### 6.5.1 初步检验子集选择器 R估计量

We want to define the preliminary test R-estimator for our considered restriction, \(\beta_2 = \mathbf{0}\). In this regard,

\(\hat{\beta}_n^{\text{PTSER}}(\lambda) = \left( \hat{\beta}_j^{\text{UR}} I(|\hat{\beta}_j^{\text{UR}}| > \lambda \eta \sqrt{C^{jj}}), j=1, ..., p \right)^\top\) (6.5.1)

