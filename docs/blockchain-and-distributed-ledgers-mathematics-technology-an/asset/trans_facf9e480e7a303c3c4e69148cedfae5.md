

# 300 | 区块链与分布式账本：数学、技术与经济学

稳定分布为金融工具收益率提供了极佳的拟合；参见 Mandelbrot (1997)。在分析中，我们认为必须涵盖稳定分布。

对于学生 $t$ 分布，$x \sim ST(\mu, \nu, \sigma)$，其 $f_{ST}(x)$ 和 $\phi_{ST}(\chi)$ 形式如下：

```
$f_{ST}(x) = \frac{\Gamma(\frac{\nu+1}{2})}{\sigma\sqrt{\nu\pi}\Gamma(\frac{\nu}{2})} (1 + \frac{(x-\mu)^2}{\nu\sigma^2})^{-(-(\nu+1)/2)} \quad (10.8)$
```

```
$$\phi_{ST}(\chi) = \frac{\sigma(\nu\sigma|\chi|)^{\nu/2}\exp(i\mu\chi)K_{\nu/2}(\nu\sigma|\chi|)}{2^{\nu-1}\Gamma(\nu)}$$
```

参见 Gosset (1908)；Abowitz and Stegun (1994)；Johnson et al. (1995)。参数的含义如下：$\mu$ — 位置，$\nu$ — 自由度，$\sigma$ — 波动率。t 分布呈钟形且关于其均值对称，与正态分布相似。一个重要的区别是 t 分布具有厚尾，产生的离均值比正态分布更多。因此，它是拟合 BTC 收益的合适候选。

对于正态逆高斯分布，$x \sim N\{IG}(\alpha, \beta, \delta, \mu)$，$f_{NIG}(x)$ 和 $f_{NIG}(\chi)$ 如下：

```
$f_{NIG}(x) = \frac{(y/\delta)^{-1/2}e^{\alpha\beta(x-\mu)}}{\sqrt{2\pi}y^{-1/2}} y^{-1}K_{-1}(\alpha) \quad (10.9)$
```

```
$$\alpha\delta e^{\gamma\delta+\beta x}/\pi y^{-1}K_{-1}(\alpha)$$
```

```
$$\phi_{NIG}(\chi) = \exp(\gamma\delta+i\mu\chi-\delta\nu)$$
```

其中

```
$$\gamma = \sqrt{\alpha^2-\beta^2}, y = \sqrt{\delta^2+(x-\mu)^2}, \nu = \sqrt{|\delta^2+(i\chi)^2}, \quad (10.10)$$
```

参见 Aas and Hobaek Haff (2005)；Barndorff-Nielsen (1997)。这里 K 是第二类修正贝塞尔函数。对应参数的含义如下：$\alpha$ — 尾部浓度，$\beta$ — 不对称性，$\delta$ — 尺度，$\mu$ — 位置。

对于广义双曲分布，$x \sim GH(\alpha, \beta, \delta, \lambda, \mu)$，相应的 $f_{GH}(x)$ 和 $f_{GH}(\chi)$ 可以写为：

```
$f_{GH}(x) = \frac{(\gamma/y)^{\alpha}e^{\beta(x-\mu)}y^{\lambda-1/2}K_{\lambda-1/2}(\gamma)}{\sqrt{2\pi}K_{\lambda}(\gamma)} \quad (10.11)$
```

```
$$\phi_{GH}(\chi) = \frac{\gamma^{\alpha}\exp(i\mu\chi)K_{\lambda}(\delta\nu)}{K_{\lambda}(\delta\nu)v^{\lambda}}$$
```

# 第 10 章 加密货币与定量金融 | 301

参见 Barndorff-Nielsen (1977)。除了 $\alpha, \beta, \delta, \mu$ 之外，我们添加了参数 $\lambda$，它决定了分布的形状。当离均值的巨大偏差至关同时，可以使用广义双曲分布，例如建模金融工具。它是我们在分析中包含的最通用分布。学生 $t$ 分布和正态逆高斯分布属于广义双曲 (GH) 分布类。遗憾的是，广义双曲分布在其成员的线性组合下是不封闭的，这使得每日收益聚合为每月或每年非常困难，见下一节。

双曲分布是 $\mathcal{GH}$ 在 $\lambda = 1$ 时的特殊情况：

```
$H(\alpha, \beta, \delta, \mu) = \mathcal{GH}(\alpha, \beta, \delta, 1, \mu),$
```

被用拟合 BTC 收益的候选；参见 Barndorff-Nielsen (1977)。然而，我们的经验表明，相应的拟合效果通常并不好，因此为了起见，我们省略了相应的计算。

对相应特征函数的直接比较证实了一个已知事实：正态分布和柯西分布是特殊分布的特殊情况：

```
$\mathcal{N}(\mu, \sigma^2) = S\left(2, 0, \frac{\sigma}{\sqrt{2}}, \mu\right),$
```

```
$C(\delta, \mu) = S(1, 0, \delta, \mu).$
```

学生 $t$ 分布和正态逆高斯分布是广义双曲分布的特殊（或极限）情况：

```
$\mathcal{ST}(\mu, v, \sigma) = \mathcal{GH}(0, 0, \sqrt{v}\sigma, -\frac{v}{2}, \mu).$
```

```
$\mathcal{NIG}(\alpha, \beta, \delta, \mu) = \mathcal{GH}(\alpha, \beta, \delta, -\frac{1}{2}, \mu).$
```

正态分布和柯西分布也可以通过极限获得，尽管它们都不属于 $\mathcal{GH}$ 类。每种分布都通过经典的极大似然法进行拟合；例如，Hamilton (2020) 等许多人。我们在 $L(\Theta)$ 中引入惩罚项如下：

```
$ln L(\Theta) = \sum_{n=1}^{N} ln(x_n),$
```

关于 $\Theta$ 最大化它，并选择相应的最优值 $\hat{\Theta}$。$\hat{\Theta}$ 的置信区间通过用信息矩阵的逆来近似方差矩阵来计算。因此，

```
$cov(\hat{\Theta}) = (H(\hat{\Theta}))^{-1}$
```

其中 $H(\hat{\Theta})$ 是相应的海森森矩阵，

```
$H(\hat{\Theta}) = \begin{pmatrix} \frac{\partial^2 L(\Theta)}{\partial\theta_1^2} & \frac{\partial^2 L(\Theta)}{\partial\theta_1\partial\theta_2} & \dots & \frac{\partial^2 L(\Theta)}{\partial\theta_1\partial\theta_k} \\ \frac{\partial^2 L(\Theta)}{\partial\theta_2\partial\theta_1} & \frac{\partial^2 L(\Theta)}{\partial\theta_2^2} & \dots & \frac{\partial^2 L(\Theta)}{\partial\theta_2\partial\theta_k} \\ \vdots & \vdots & \ddots & \vdots \\ \frac{\partial^2 L(\Theta)}{\partial\theta_k\partial\theta_1} & \frac{\partial^2 L(\Theta)}{\partial\theta_k\partial\theta_2} & \dots & \frac{\partial^2 L(\Theta)}{\partial\theta_k^2} \end{pmatrix} \quad (10.17)$
```

为了考虑到选择拟合候选中参数数量的差异，我们使用几个标准来挑选胜者：

- (1) 赤池信息准则 (AIC)，如 Akaike (1974)：
$AIC = 2K - 2\ln L(\hat{\Theta}) \quad (10.18)$

赤池信息准则估计了给定一组数据对不同统计模型的样本外预测误差。可以通过添加额外参数来增加似然性。例如，正态分布有两个参数 $\mu, \sigma$，而广义双曲分布有五个 $\alpha, \beta, \delta, \lambda$。然而，引入额外参数会增加数据过拟合的风险。

- (2) Hannan–Quinn 信息准则 (HQIC)，如 Hannan and Quinn (1979)：
$HQIC = 2K\ln(N) - 2\ln L(\hat{\Theta}) \quad (10.19)$

- (3) Schwarz 信息准则 (SIC)，也称为贝叶斯信息准则 (BIC)，如 Schwarz (1978)：
$SIC = K\ln N - 2\ln L(\hat{\Theta}) \quad (10.20)$

BIC 和 AIC 严格接近，但惩罚项在 BIC 中比在 AIC 和 HQIC 中大。对于上述每个标准，目标是选择产生最小值的分布。

- (1) Anderson-Darling 检验，如 Anderson and Darling (1954)：
$ADT = -N - \sum_{n=1}^{N} (2n-1)\ln(\hat{F}(y_n)) + \ln(1-\hat{F}(y_{n+1})) \quad (10.21)$

其中 $y_1 \le \dots \le y_N$ 是按顺序排列的观测。Anderson-Darling 检验 (AD test) 估计给定概率分布的拟合优度。

(2) Kolmogorov-Smirnov 检验，参见 Kolmogorov (1933)；Smirnov (1948)：
$KST = \sup_{x} |F_N(x) - \hat{F}(x)| \quad (10.22)$

其中 $F_N(x)$ 是经验分布，而 $\hat{F}(x)$ 是似然分布，

```
$F_N(x) = \frac{1}{N} \sum_{n=1}^N \delta_{[-infty,x]}(x_n) \quad (10.23)$
```

$\delta_{[-infty,x]}()$ 是指示函数，如果 $x_n \le x$ 则为 1，否则为 0。Kolmogorov-Smirnov 检验 (KS test) 是一种比较数据样本与给定概率分布的非参数检验。对于 AD 检验，该分布的参数是通过极大似然法计算的。

