
**定理 4.6** 在局部替代下，$K_{(n)}$，渐近分布偏差，以及岭型 R 估计器 $\hat{\theta}_n^{\text{ridgeR}}(\lambda)$ 的 $L_2$-风险分别由下式给出

\[
ADB(\hat{\theta}_n^{\text{ridgeR}}(\lambda)) = \left( \mathbf{0}^\top, -\frac{\lambda}{1+\lambda}\delta_2^\top \right)^\top
\]

和

\[
ADL_2\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda)) = \eta^2 \left[ tr(\mathcal{K}_1) + \frac{tr(\mathcal{K}_2) + \lambda^2 \delta_2^\top \mathcal{S}_2}{(1+\lambda)^2} \right].
\]

$ADL_2$-风险的下界为

\[
ADL_2^*\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda)) = \eta^2 \left[ tr(\mathcal{K}_1) + \frac{tr(\mathcal{K}_2) + \lambda^2 \Delta^2 Ch_{\min}(\mathcal{K}_2)}{(1+\lambda)^2} \right].
\]

需注意的是，对 $ADL_2^*\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda))$ 取得最优的 $\lambda$ 值为

\[
\lambda_{opt} = tr(\mathcal{K}_2)\Delta^{-2}(Ch_{\min}(\mathcal{K}_2))^{-1}.
\]

因此，

\[
ADL_2^*\text{-risk}(\hat{\theta}_n^{\text{ridgeR}}(\lambda_{opt})) = \eta^2 \left[ tr(\mathcal{K}_1) + \frac{tr(\mathcal{K}_2)\Delta^2 Ch_{\min}(\mathcal{K}_2)}{tr(\mathcal{K}_2) + \Delta^2 Ch_{\min}(\mathcal{K}_2)} \right],
\]

以及

\[
ADRE(\hat{\theta}_n^{\text{ridgeR}}(\lambda) : \hat{\theta}_n^{UR}) = \left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \right) \times \left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \frac{\Delta^2 Ch_{\min}(\mathcal{K}_2)}{[tr(\mathcal{K}_2) + \Delta^2 Ch_{\min}(\mathcal{K}_2)]} \right)^{-1} \quad (4.7.6)
\]

这是 $\Delta^2$ 的递减函数。当 $\Delta^2 = 0$ 时，其值为 $\left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \right)$；而当 $\Delta^2 \to \infty$ 时，其值为 1。显然，

\[
0 \le \left( 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \right) \left( 1 + \frac{(tr(\mathcal{K}_2))\Delta^2 Ch_{\min}(\mathcal{K}_2)}{(tr(\mathcal{K}_1))(tr(\mathcal{K}_2) + \Delta^2 Ch_{\min}(\mathcal{K}_2))} \right)^{-1} < 1 + \frac{tr(\mathcal{K}_2)}{tr(\mathcal{K}_1)} \quad \forall \Delta^2 \in \mathbb{R}^+.

## 4.8 子集选择惩罚 R 估计器

如前所述，我们在上一节中介绍了处理模型稀疏性的方法。在本节中，我们讨论了几种惩罚 R 估计器，它们旨在找到导致模型稀疏性的参数，例如

- (i) 初步检验 R 估计器 (PTRE)，一般由于 Donoho 和 Johnstone (1994) 被指定为硬阈值估计器 (HTE)。
- (ii) Tibshirani (1996) 提出的 LASSO，由于 Donoho 和 Johnstone (1994) 被指定为软阈值估计器 (STE)。Saleh 等人 (2019) 将 LASSO 识别为位置模型中正则 Saleh 选择器 (PRSS) 的等价形式，如第 3 章所述。
- (iii) 自适应 LASSO-型估计器。
- (iv) 弹性网-型估计器。

如前所述，我们使用“-型”这一称谓，因为我们是将收缩因子直接应用于无限制估计以得到封闭形式估计器，而非最小化惩罚损失函数。

### 4.8.1 初步检验子集选择器 R 估计器

初步检验子集选择器 R 估计器 (PTSSRE) 定义为

\[
\hat{\boldsymbol{\theta}}_n^{\text{PTSSR}}(\lambda) = \left( \hat{\theta}_{n_j}^{\text{UR}} I(\mathcal{L}_{n_j} > \lambda^2) \mid j = 1, ..., p \right)^{\top}
\]

其中

\[
\mathcal{L}_{n_j} = \frac{n \left( \hat{\theta}_{n_j}^{\text{UR}} \right)^2}{\hat{\eta}^2 \varkappa_j}, \quad j = 1, ..., p
\]

是检验统计量。
每个分量都是 $\theta_j, j = 1, ..., p$ 的 PTSSRE。

**定理 4.7** 在局部替代下，$K_{(n)}$，初步检验子集选择器 R 估计器 $\hat{\boldsymbol{\theta}}^{\text{PTSSR}}$ 的渐近分布偏差和 ADL$_2$-风险分别由下式给出

\[
\text{ADB}(\hat{\boldsymbol{\theta}}_n^{\text{PTSSR}}(\lambda)) = -\eta \left( \delta_j \mathcal{H}_3(\lambda^2, \Delta_j) \mid j = 1, ..., p \right)^{\top},
\]

和

\[
\text{ADL}_2\text{-risk}(\hat{\theta}^{PTSSR}_n(\lambda)) = \eta^2 \Big\{ \sum_{j=1}^p \kappa_j (1 - \mathcal{H}_3(\lambda^2, \Delta_j^2)) + \sum_{j=1}^p \Delta_j^2 (2\mathcal{H}_3(\lambda^2, \Delta_j^2) - \mathcal{H}_5(\lambda^2, \Delta_j^2)) \Big\}.
\]

**证明：** 首先我们证明

\[
\sqrt{n} \hat{\theta}^{PTSSR}_n(\lambda) = \Big( \sqrt{n} \hat{\theta}^{UR}_{n_j} I(| \sqrt{n} \hat{\theta}^{UR}_{n_j} | > \lambda \kappa_j^{\frac{1}{2}} \eta) \mid j=1, ..., p \Big)^\top = \Big( \eta \kappa_j^{\frac{1}{2}} Z_{n_j} I(|Z_{n_j}| > \lambda) \mid j=1, ..., p \Big)^\top,
\]

其中

\[
Z_{n_j} = \frac{\sqrt{n} \hat{\theta}^{UR}_{n_j}}{\eta \sqrt{\kappa_j}}, \quad j=1, ..., p.
\]

显然，当 $n \to \infty$ 时，$Z_{n_j} \sim \mathcal{N}(\Delta_j, 1), \ j=1, ..., p$，且 $\Delta_j = \delta_j / (\eta \sqrt{\kappa_j})$。由于本定理的证明与定理 3.5 类似，详细过程留给读者。

### 4.8.2 Saleh-型 R 估计器

我们注意到，硬阈值 R 估计器在本质上是离散的，并且由于数据的微小变化可能导致非常不同的模型并可能降低预测精度，因此可能变得极具变异性和不稳定性。Saleh R 估计器是硬阈值估计器的连续版本，定义为

\[
\hat{\theta}^{SR}_n(\lambda) = \Big( \hat{\theta}^{UR}_{n_j} \Big( 1 - \frac{\lambda}{\mathcal{L}_{n_j}} \Big) \Big| j=1, ..., p \Big)^\top, \quad \mathcal{L}_{n_j} = |Z_{n_j}|.
\]

**定理 4.8** 在局部替代下，$K_{(n)}$，Saleh R 估计器 $\hat{\theta}^{SR}_n$ 的渐近分布偏差和 $ADL_2$-风险分别由下式给出

\[
ADB(\hat{\theta}^{SR}_n(\lambda)) = \Big( -\lambda \eta \sqrt{\kappa_j} (2\Phi(\Delta_j) - 1) \mid j=1, ..., p \Big)^\top,
\]

和

\[
\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SR}}(\lambda)) = \eta^2 \sum_{j=1}^p \left( 1 + \lambda^2 - 2\lambda \sqrt{\frac{2}{\pi}} \exp\left(-\frac{\Delta_j^2}{2}\right) \right).
\]

**证明：** 首先我们展示

\[
\begin{aligned}
\sqrt{n}\hat{\theta}_n^{\text{SR}}(\lambda) &= \left( \sqrt{n}\hat{\theta}_{n_j}^{\text{UR}} - \lambda \eta \sqrt{\kappa_j} \left| \frac{\sqrt{n}\hat{\theta}_{n_j}^{\text{UR}}}{|\sqrt{n}\hat{\theta}_{n_j}^{\text{UR}}|} \right| j = 1, ..., p \right)^{\top} \\
&= \left( \eta \sqrt{\kappa_j} \left( 1 - \frac{\lambda}{|Z_{n_j}|} \right) Z_{n_j} \bigg| j = 1, ..., p \right)^{\top}
\end{aligned}
\]

其中 \( Z_{n_j} = \sqrt{n}\hat{\theta}_{n_j}^{\text{UR}} / (\eta \sqrt{\kappa_j}), j = 1, ..., p \)。显然，当 $n \to \infty$ 时，$Z_{n_j} \sim \mathcal{N}(\Delta_j, 1)$，且 $\Delta_j = \delta_j / (\eta \sqrt{\kappa_j})$。由于本定理的证明与定理 3.7 类似，其余部分留给读者。

因此，对于 $\lambda_{\max}^* = \sqrt{\frac{2}{\pi}}$，我们得到

\[
\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SR}}(\lambda^*)) = \eta^2 \sum_{j=1}^p \left[ 1 - \frac{2}{\pi} \left( 2 \exp\left\{ -\frac{\Delta_j}{2} \right\} - 1 \right) \right].
\]

最后，

\[
\text{ADRE}(\hat{\theta}_n^{\text{SR}}(\lambda^*) : \hat{\theta}_n^{\text{UR}}) = \left( \sum_{j=1}^p \left[ 1 - \frac{2}{\pi} \left( 2 \exp\left\{ -\frac{\Delta_j}{2} \right\} - 1 \right) \right] \right)^{-1}.
\]

### 4.8.3 正则 Saleh 子集选择器 (PRSS)

前一节中描述的 Saleh R 估计器会改变符号，这可能并不理想。然而，LASSO R 估计器（由以下公式给出）

\[
\hat{\theta}_n^{\text{LassoR}}(\lambda) = \underset{\theta \in \mathbb{R}}{\text{argmin}} \left\{ \sum_{i=1}^p \sum_{j=1}^{n_i} |y_{ij} - \theta_j| a_n^+(R_{n_j}(\theta_j)) + \lambda \sum_{i=1}^p |\theta_i| \right\}
\]

不存在此问题。受 LASSO 和软阈值估计器（Donoho 和 Johnstone, 1994）的启发，我们考虑正则 Saleh 子集选择器 (PRSS) 来解决此问题。它可定义为

\[
\hat{\theta}_n^{\text{SR+}}(\lambda) = \left( \text{sgn}(\hat{\theta}_{n_j}^{\text{UR}}) \left( |\hat{\theta}_{n_j}^{\text{UR}}| - \lambda \right) I(\mathcal{L}_{n_j} > \lambda^2) \bigg| j = 1, 2, ..., p \right)^{\top}
