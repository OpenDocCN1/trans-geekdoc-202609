

### 费舍尔信息与克拉梅尔-罗界

$$I(\theta): = - \mathbb{E}\ \left\lbrack \frac{\partial^{2}\ln p(\mathcal{X};\theta)}{\partial\theta^{2}} \right\rbrack.$$

此外，获得达到该界的无偏估计量的必要充分条件是存在函数 $g(\cdot)$，使得对所有可能的 $\theta$ 值均有：

$$\frac{\partial\ln p(\mathcal{X};\theta)}{\partial\theta} = I(\theta)\left( g(\mathcal{X}) - \theta \right).$$

此时 MVU 估计由下式给出：

$$\hat{\theta} = g(\mathcal{X}) \equiv g(\boldsymbol{x}[1], \boldsymbol{x}[2], \dots, \boldsymbol{x}[N]),$$

相应估计量的方差等于 $1/I(\theta)$。

当 MVU 估计量达到克拉梅尔-罗界时，我们称其为**有效**的。上述所有期望均针对 $p(\mathcal{X};\theta)$ 计算。感兴趣的读者可参考统计学专著 [20,27,36] 了解更多细节。

### 示例 3.2

考虑公式 [(3.10)](#Chp003_65-117_B9780443292385000093.xhtml#deq13) 中线性回归模型的简化版本，其中回归变量为实值且偏置项为零：

$$y[n] = \theta x + \eta[n],$$

此处显式标注了对 $n$ 的依赖，$n$ 遍历所有可用观测值。为进一步简化讨论，我们假设 $N$ 个观测值仅源于噪声变量的不同实现，且输入值 $x$ 保持常数（不失一般性可视为等于 1）；即任务简化为从含噪测量中估计参数。因此，观测值为标量输出 $y[n]$ ($n = 1, 2, \dots, N$)，视为向量 $\boldsymbol{y} \in \mathbb{R}^{N}$ 的分量。进一步假设 $\eta[n]$ 为零均值、方差为 $\sigma_{\eta}^{2}$ 的白高斯噪声样本（第 [2.4](#Chp002_19-64_B9780443292385000081.xhtml) 节），即连续样本独立同分布（i.i.d.），故互不相关（$\mathbb{E}[\eta[i]\eta[j]] = 0, i \neq j$）。此时输出观测值的联合 PDF 由下式给出：

