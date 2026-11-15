

其中，$\hat{\beta}_j^{\text{UR}}$ 是向量 $\hat{\beta}_n^{\text{PTSSR}}(\lambda)$ 的第 $j$ 个分量，$C^{jj}$ 是矩阵 $C_{22:1}^{-1}$ 的第 $j$ 个对角元。让我们考虑

$$Z_j = \frac{\sqrt{n}\hat{\beta}_j^{\text{UR}}}{\eta \sqrt{C^{jj}}}, j = 1, ..., p.$$

在方程 (6.3.8) 的局部备择假设下，\(K_{(n)} : \beta_2 = n^{-\frac{1}{2}} \delta_2, \delta_2 = (\delta_1, ..., \delta_p)^\top\),

$$\sqrt{n} \left( \hat{\beta}_j^{\text{UR}} - \beta_j \right) \xrightarrow{D} \mathcal{N}(\delta_j, \eta^2 C^{jj}), \quad j = 1, ..., p.$$

因此，

$$Z_j \xrightarrow{D} \mathcal{N}(\Delta_j, 1), \quad \text{where } \Delta_j = \frac{\delta_j}{\eta \sqrt{C^{jj}}}.$$

这个定义源自 Donoho 和 Johnstone (1994)，称为硬阈值 R-估计器 (HTE)。我们可以基于 \(Z_j\) 将 \(\hat{\beta}_n^{\text{PTSSR}}(\lambda)$ 重写为

$$\sqrt{n}\hat{\beta}_n^{\text{PTSSR}}(\lambda) = \left( \eta \sqrt{C^{jj}} Z_j I(|Z_j| > \lambda), j = 1, ..., p \right)^\top . \quad (6.5.2)$$

因此，该估计器的 ADB 和 ADL$_2$-风险很容易得到为

$$\text{ADB}(\hat{\beta}_n^{\text{PTSSR}}(\lambda)) = -\eta (\sqrt{C^{jj}} \Delta_j \mathcal{H}_3(\lambda^2, \Delta^2), j = 1, ..., p)^\top$$

and

$$\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{PTSSR}}(\lambda)) = \eta^2 \left[ \text{tr}(C_{11:2}^{-1}) + \sum_{j=p_1+1}^p C^{jj} \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) + \sum_{j=p_1+1}^p \Delta_j^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2) \right) \right], j = p_1 + 1, ..., p. \quad (6.5.3)$$

因此，对于 \(j = 1, ..., p$， ADRE 由下式给出

$$\text{ADRE}(\hat{\beta}_n^{\text{PTSSR}}(\lambda) : \hat{\beta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(C_{22:1}^{-1})}{\text{tr}(C_{11:2}^{-1})} \right) \left[ 1 + \frac{1}{\text{tr}(C_{11:2}^{-1})} \left( \sum_{j=p_1+1}^p C^{jj} \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) + \sum_{j=p_1+1}^p \Delta_j^2 \left( 2\mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2) \right) \right) \right]^{-1}.$$

## 6.5.2 Stein–Saleh 类型 R-估计器

我们希望为我们考虑的限制 \(\boldsymbol{\beta}_2 = \mathbf{0}$ 定义 Stein–Saleh 类型 R-估计器。为此，我们使用

$$\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda) = \left( \hat{\beta}_j^{\text{UR}}\left(1 - \frac{\lambda \eta \sqrt{C^{jj}}}{\sqrt{n}|\hat{\beta}_j^{\text{UR}}|}\right), j = 1, \dots, p \right)^{\top} \quad (6.5.4)$$

其等价形式为

$$\hat{\beta}_j^{\text{SR}}(\lambda) = \hat{\beta}_j^{\text{UR}} - \lambda \eta \sqrt{C^{jj}} \text{sgn}(\hat{\beta}_j^{\text{UR}})/\sqrt{n}, \quad j=1, \dots, p. \quad (6.5.5)$$

因此，我们可以用 \(Z_j$ 重写 \(\hat{\boldsymbol{\beta}}^{\text{SR}}(\lambda)$ 为

$$\sqrt{n}\hat{\beta}_j^{\text{SR}}(\lambda) = \eta \sqrt{C^{jj}} \left( Z_j - \lambda \text{sgn}(Z_j) \right), \quad j=1, \dots, p. \quad (6.5.6)$$

最后，我们得到 \(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)$ 为

$$\hat{\beta}_j^{\text{SR}}(\lambda) = \eta \sqrt{C^{jj}} \text{sgn}(Z_j)(|Z_j| - \lambda), \quad j=1, \dots, p.$$

接下来，该估计器的 ADB 和 ADL$_2$-风险由下式给出

$$\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)) = \left( -\lambda \eta \sqrt{C^{jj}} \left( 2\Phi(\Delta_j) - 1 \right), j=1, \dots, p \right)^{\top}$$

and

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)) = \eta^2 \left[ \text{tr}(\mathbf{C}_{11.2}^{-1}) + \sum_{j=p_1+1}^p C^{jj} \left( 1 + \lambda^2 - 2\lambda \sqrt{\frac{2}{\pi}} \exp \left\{ -\frac{\Delta_j^2}{2} \right\} \right) \right]. \quad (6.5.7)$$

\(\lambda$ 的最优值为

$$\lambda_{\text{opt}} = \sqrt{\frac{2}{\pi}} \exp \left\{ -\frac{\Delta_j^2}{2} \right\},$$

其最大值为

$$\lambda^* = \sqrt{\frac{2}{\pi}} \quad \text{when } \Delta_j^2 = 0 \ \forall j$$

在 \(\Delta_j^2 = 0$ 处，最优值为

$$\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{SR}}(\lambda^*)) = \eta^2 \left[ \text{tr}(\mathbf{C}_{11:2}^{-1}) + \sum_{j=p_1+1}^p C^{jj} \left[ 1 - \frac{2}{\pi} \left( 2 \exp\left(-\frac{\Delta_j^2}{2}\right) - 1 \right) \right] \right].$$

最后，

$$\text{ADRE}(\hat{\beta}_n^{\text{SR}}(\lambda^*) : \hat{\beta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22:1}^{-1})}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \right) \times \left[ 1 + \frac{1}{\text{tr}(\mathbf{C}_{11:2}^{-1})} \sum_{j=p_1+1}^p C^{jj} \left[ 1 - \frac{2}{\pi} \left( 2 \exp\left(-\frac{\Delta_j^2}{2}\right) - 1 \right) \right] \right]^{-1} \geq 1.$$

请注意，当 \(|Z_j| \to \infty$ 时，该估计器会改变符号。因此，我们需要定义一个相关的 R-估计器来消除这种异常。

## 6.5.3 正则 Stein–Saleh 类型 R-估计器 (LASSO 类型)

我们注意到，Stein–Saleh 类型 R-估计器最终会改变符号。一个简单的解决方案是保持其符号直到它达到零，此时它保持为零。这个版本是正则 Stein–Saleh R-估计器 (PRSRE)，也称为 LASSO 类型 R-估计器，是 LASSO (Tibshirani, 1996) 的简化版，也是软阈值估计器 (Donoho and Johnstone, 1994)。

正则 Stein–Saleh 类型子集 R-估计器 (PRSRE) 定义为

$$\hat{\beta}_n^{\text{PRSR}}(\lambda) = \left( \gamma \sqrt{C^{jj}} \text{sgn}(Z_j) (|Z_j| - \lambda)^+ \mid j = 1, \dots, p \right)^{\top} \quad (6.5.8)$$

其中，\(a^+ = \max\{0, a\}$.

\(\hat{\beta}_n^{\text{PRSR}}(\lambda)$ 是一种扰动 LASSO。对于正交情况，正则 Stein–Saleh 类型 R-估计器是 Tibshirani (1996) 的秩版本 LASSO。必须注意的是，对于非正交情况，LASSO R-估计器没有闭式解。

可以证明

$$\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) = -\eta \left( [\Delta_j \mathcal{H}_3(\lambda^2, \Delta_j^2) - \lambda(\Phi(\lambda - \Delta_j) - \Phi(\lambda + \Delta_j)) \mid j = 1, ..., p \right)^T$$

and

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) = \eta^2 \left( \text{tr}(\mathbf{C}_{22 \cdot 1}^{-1}) + \sum_{j=1}^p \left\{ C^{jj} \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) + C^{jj} \Delta_j^2 \left( 2 \mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2) \right) + C^{jj} \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) \right) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right\} \right).$$

因此，ADRE 由下式得到

$$\text{ADRE}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda) : \hat{\boldsymbol{\beta}}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathbf{C}_{22 \cdot 1}^{-1})}{\text{tr}(\mathbf{C}_{11 \cdot 2}^{-1})} \right) \left( 1 + \frac{1}{\text{tr}(\mathbf{C}_{11 \cdot 2}^{-1})} \right) \times \sum_{j=p_1+1}^p \left[ C^{jj} \left\{ \left( 1 - \mathcal{H}_3(\lambda^2, \Delta_j^2) \right) + \Delta_j^2 \left( 2 \mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2) \right) + \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) \right) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right\} \right]^{-1}. \quad (6.5.10)$$

请注意，我们可以写成

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) = \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SR}}(\lambda)) + \sum_{j=p_1+1}^p C^{jj} \left[ \lambda^2 \left( 1 - \mathcal{H}_1(\lambda^2, \Delta_j^2) - 2\lambda \left( \phi(\lambda - \Delta_j) + \phi(\lambda + \Delta_j) \right) \right) \right]$$

and

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PRSR}}(\lambda)) \le \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSR}}(\lambda)).$$

## 6.5.4 岭回归类型子集选择器

我们定义岭回归类型子集选择器为

$$\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}}(\lambda) = \left( \frac{\hat{\boldsymbol{\beta}}_{jn}^{\text{UR}}}{1 + \lambda C^{jj}}, j = 1, ..., p \right)^{\top}.$$

因此，我们可以推导出两个感兴趣的量为

$$\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}}(\lambda)) = \left( \frac{-\lambda C^{jj}}{1 + \lambda C^{jj}} \Delta, j = 1, ..., p \right)^{\top}$$

and

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}}(\lambda)) = \eta^2 \left( \left[ \text{tr}[(I + \lambda C^{-1})^{-2} C^{-1}] + \lambda^2 \Delta^{\top} (C + \lambda I)^{-1} \Delta \right] \right),$$

其中，\(\Delta = (\Delta_1, ..., \Delta_p)^{\top}.$

## 6.5.5 弹性网络类型 R-估计器

在这种情况下，我们定义 naive elastic-net R-估计器 (nEnetRE) 为

$$\sqrt{n} \hat{\beta}_n^{\text{nEnetR}}(\lambda, \alpha) = \left( \frac{\text{sgn}(\sqrt{n} \hat{\beta}_{jn}^{\text{UR}})}{[1 + \lambda(1 - \alpha) C^{jj}]} \left( |\sqrt{n} \hat{\beta}_{jn}^{\text{UR}}| - \lambda \alpha \eta \sqrt{C^{jj}} \right)^+, j = 1, ..., p \right)^{\top} = \underset{\beta \in \mathbb{R}^p}{\text{argmin}} \left\{ D_n(\beta) + \lambda \left[ \frac{1}{2} \alpha \eta D[\beta] + \frac{1}{2} (1 - \alpha) \beta^{\top} C \beta \right] \right\} = \left( \eta \sqrt{C^{jj}} \frac{\text{sgn}(Z_j)}{[1 + \lambda(1 - \alpha) C^{jj}]} (|Z_j| - \lambda \alpha \epsilon)^+, j = 1, ..., p \right)^{\top} \quad (6.5.11)$$

其中，\(\boldsymbol{D} = \text{Diag}\left( \frac{1}{\sqrt{C^{jj}}}, j = 1, ..., p \right) \text{ 且 } Z_j = \frac{\sqrt{n}}{\eta \sqrt{C^{jj}}} \hat{\beta}_{jn}^{\text{UR}}.$

该估计器与正则 Stein–Saleh 类型 R-估计器完美契合。确实，我们有

$$\hat{\boldsymbol{\beta}}_n^{\text{nEnetR}}(\lambda, \alpha) = [I + \lambda(1 - \alpha)C^{-1}]^{-1} \hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda \alpha). \quad (6.5.12)$$

那么，

$$\text{ADB}(\hat{\boldsymbol{\beta}}_n^{\text{nEnetR}}(\lambda, \alpha)) = [I_p + \lambda(1 - \alpha)C^{-1}]^{-1} [B - \lambda(1 - \alpha)C^{-1} \Delta]$$

