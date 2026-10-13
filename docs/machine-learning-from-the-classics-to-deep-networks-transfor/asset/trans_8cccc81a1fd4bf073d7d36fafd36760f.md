

## EM 算法更新方程

EM 算法的更新方程由下式给出：

$$
\alpha^{(j + 1)}: \frac{\partial}{\partial\alpha}\mathcal{Q}\left( \alpha,\beta;\alpha^{(j)},\beta^{(j)} \right) = 0,
\quad
\beta^{(j + 1)}: \frac{\partial}{\partial\beta}\mathcal{Q}\left( \alpha,\beta;\alpha^{(j)},\beta^{(j)} \right) = 0
$$

![Equation](images/B9780443292385000184/si193.png)

这直接导出：

![](images/B9780443292385000184/fx008.jpg)

一旦算法收敛，`α` 和 `β` 的结果值将被用来完全指定所涉及的概率密度函数（PDF），这些函数可用于获得 $\widehat{\mathbf{\theta}}$ 的估计，例如 $\widehat{\mathbf{\theta}} = \mathbb{E}[\mathbf{\theta}|\mathbf{y}]$，或通过公式 [(12.21)](#Chp012_583-634_B9780443292385000184.xhtml#deq25) 进行预测。

## 示例 12.2

在本示例中，重新考虑了 [示例 12.1](#Chp012_583-634_B9780443292385000184.xhtml#enun0015) 的广义线性回归模型。目标是使用由递推公式 (12.43)、(12.44)、(12.51) 和 (12.52) 概括的 EM 算法。

模型中用于生成数据的高斯噪声方差被设定为 $\sigma_\eta^2 = 0.05$。训练点的数量为 $N = 500$。对于 EM 算法，`α` 和 `β` 均初始化为 1。使用了未知参数向量的正确维度。

EM 算法收敛后恢复的值为：
- `α = 1.32`，对应 $\sigma_\theta^2 = 0.756$
- `β = 19.96`，对应 $\sigma_\eta^2 = 0.0501$

注意，后者非常接近噪声的真实方差。

然后，利用公式 [(12.22)](#Chp012_583-634_B9780443292385000184.xhtml#deq26) 和通过公式 (12.44) 由 EM 算法恢复的 $\boldsymbol{\mu}_{\theta|y}$ 值，在 20 个点上对输出变量 `y` 进行了预测。

[图 12.5](#Chp012_583-634_B9780443292385000184.xhtml#f0040)A 显示了预测结果及其相关误差棒，这些误差棒是利用通过 EM 算法获得的 $\sigma_\eta^2$ 和 $\sigma_\theta^2$ 值，根据公式 [(12.23)](#Chp012_583-634_B9780443292385000184.xhtml#deq27) 计算得出的。[图 12.5](#Chp012_583-634_B9780443292385000184.xhtml#f0040)B 显示了 $\sigma_\eta^2$ 随 EM 算法迭代次数变化的收敛曲线。

![Figure 12.5 (A) The original graph from which the training points were sampled. In red, the respective predictions $\widehat{y}$ and associated error bars for 20 randomly chosen points are shown. (B) The convergence curve for $\sigma_\eta^2$ as a function of the iterations of the EM algorithm. The red line corresponds to the true value.](images/B9780443292385000184/gr005.jpg)

