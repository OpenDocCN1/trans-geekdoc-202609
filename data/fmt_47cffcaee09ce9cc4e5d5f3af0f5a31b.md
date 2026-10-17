
其中 $\sigma_H \in \mathbb{R}^{++}$ 代表随机场标准差；$l_x, l_y, l_z \in \mathbb{R}^+$ 分别代表 x 轴、y 轴和 z 轴的相关长度。

一种流行的随机场离散化技术是 Karhunen–Loève 展开（KL 展开）。通过有界、对称且正定协方差函数 $C_{HHH}(\mathbf{x,x'})$ 的组合分解，可以解释为：

```
$C_{HHH}(\mathbf{x,x'}) = \sum_{i=1}^{\infty} \lambda_i \varphi_i(\mathbf{x})\varphi_i(\mathbf{x'}) \quad (11.22)$
```

其中 $C_{HHH}(\mathbf{x,x'})$ 的特征函数取自方程的解：

```
$\forall i = 1, ... \int_D C_{HHH}(\mathbf{x,x'})\varphi_i(\mathbf{x})dD = \lambda_i\varphi_i(\mathbf{x}) \quad (11.23)$
```

通过以下方程保证了正交性：

```
$\int_D \varphi_i(\mathbf{x})\varphi_j(\mathbf{x})dD = \delta_{ij} \quad (11.24)$
```

其中，$\delta_{ij}$ 为 Kronecker 符号。然后随机变量集合的参数计算为：

```
$\zeta(\theta) = \frac{1}{\sqrt{N}} \int_D [H(\mathbf{x}, \theta) - \mu(\mathbf{x})]\varphi_i(\mathbf{x})dD \quad (11.25)$
```

为了简化计算，用 $M$ 项截断 KL 展开 $H(\mathbf{x}, \theta)$ 为：

```
$H(\mathbf{x}, \theta) \approx \hat{H}^M(\mathbf{x}, \theta) = \mu(\mathbf{x}) + \sum_{i=1}^{M} \sigma(\mathbf{x})\sqrt{\lambda_i}\zeta_i(\theta)\varphi_i(\mathbf{x})$
```

其中 $\mu(\mathbf{x})$ 和 $\sigma(\mathbf{x})$ 是高斯场的均值和标准差。将相应的对数正态随机场转换为高斯随机场的指数积，如下：

```
$H(\mathbf{x}, \theta) \approx \hat{H}^M(\mathbf{x}, \theta) = \exp[\mu(\mathbf{x}) + \sum_{i=1}^{M} \sigma(\mathbf{x})\sqrt{\lambda_i}\zeta_i(\theta)\varphi_i(\mathbf{x})]$
```

其中：

```
$\mu(\mathbf{x}) = \frac{\log[\mu_{log}(\mathbf{x})]}{\sqrt{\sigma_{log}^2(\mathbf{x})}}$,
$\sigma(\mathbf{x}) = \sqrt{\log[\sigma_{log}^2(\mathbf{x})/\mu_{log}^2(\mathbf{x})]}$
```

且 $\mu_{log}$ 表示对数正态随机场的均值，而 $\sigma_{log}$ 表示标准差。

### 11.4.2 机器学习辅助的函数梯度板随机性分析

通过使用 KL 展开，泊松比和杨氏模量的对数正态随机场可以明确表述为：

```
$H_E(\mathbf{x}, \theta) \approx \hat{H}_E^M(\mathbf{x}, \theta) = \exp[\mu_E(\mathbf{x}) + \sum_{i=1}^{M} \sigma_E(\mathbf{x})\sqrt{\lambda_i}\zeta_i(\theta)\varphi_i(\mathbf{x})]$
```

```
$H_Y(\mathbf{x}, \theta) \approx \hat{H}_Y^M(\mathbf{x}, \theta) = \exp[\mu_Y(\mathbf{x}) + \sum_{i=1}^{M} \sigma_Y(\mathbf{x})\sqrt{\lambda_i}\zeta_i(\theta)\varphi_i(\mathbf{x})]$
```

其中 $\zeta_E(\theta)$ 和 $\zeta_Y(\theta)$ 表示杨氏模量和泊松比的随机变量。因此，应力-应变关系可以表示为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

在考虑这些不确定性变量的情况下，应力-应变关系可以重构为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

因此，考虑到这些不确定性变量，应力-应变关系可以重构为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

因此，考虑到这些不确定性变量，应力-应变关系可以重构为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

因此，考虑到这些不确定性变量，应力-应变关系可以重构为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

因此，考虑到这些不确定性变量，应力-应变关系可以重构为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

因此，考虑到这些不确定性变量，应力-应变关系可以重构为：

```
$\sigma = \begin{cases} \text{应力} \\ \text{应变} \end{cases}$
$\tau = \begin{cases} \text{剪切应力} \\ \text{剪切应变} \end{cases}$
```

因此，在考虑不确定性的情况下，力学问题可以表示为：

```
$\mathbf{U} = \mathbf{K}^{-1}\mathbf{F}$
```

其中 $\mathbf{K}$ 是刚度矩阵，$\mathbf{F}$ 是力向量，$\mathbf{U}$ 是位移向量。在实际应用中，$\tau_x$ 和 $\tau_y$ 是剪切应力。

因此，在考虑不确定性的情况下，力学问题可以表示为：

```
$\mathbf{U} = \mathbf{K}^{-1}\mathbf{F}$
```

其中 $\mathbf{K}$ 是刚度矩阵，$\mathbf{F}$ 是力向量，$\mathbf{U}$ 是位移向量。在实际应用中，$\tau_x$ 和 $\tau_y$ 是剪切应力。

### 11.4.3 神经网络

在考虑不确定性的情况下，力学问题可以表示为：

```
$\mathbf{U} = \mathbf{K}^{-1}\mathbf{F}$
```
