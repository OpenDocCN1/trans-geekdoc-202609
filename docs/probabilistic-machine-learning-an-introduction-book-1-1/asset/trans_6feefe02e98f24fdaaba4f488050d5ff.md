

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_87_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_87_1.png)

*图 3.8：* (a) $\mathcal{N}(0,1)$，$\mathcal{T}(\mu=0,\sigma=1,\nu=1)$，$\mathcal{T}(\mu=0,\sigma=1,\nu=2)$ 以及 $\mathrm{Lap}(0,1/\sqrt{2})$ 的概率密度函数（pdf）。高斯分布和拉普拉斯分布的均值均为 0，方差均为 1。当 $\nu=1$ 时，学生氏分布等同于柯西分布，后者没有明确定义的均值和方差。(b) 这些概率密度函数的对数。请注意，对于任何参数值，学生氏分布都不是对数凹的，这与拉普拉斯分布不同。尽管如此，两者都是单峰的。由 *student_laplace_pdf_plot.py* 生成。

如下：

$$\mathcal{T}(y|\mu,\sigma^2,\nu) \propto \left[1 + \frac{1}{\nu}\left(\frac{y-\mu}{\sigma}\right)^2\right]^{-(\nu+1)/2}\tag{3.60}$$

其中 $\mu$ 是均值，$\sigma > 0$ 是尺度参数（而非标准差），$\nu > 0$ 被称为**自由度**（尽管更好的术语是**正态度** [Kru13]，因为 $\nu$ 的值越大，该分布的行为就越像高斯分布）。

我们可以看到，概率密度随着距中心距离的平方以多项式函数的形式衰减，而不是指数函数，因此与高斯分布相比，尾部有更多的概率质量，如图 3.8 所示。我们说学生氏分布具有**重尾**，这使其对异常值具有鲁棒性。

为了说明学生氏分布的鲁棒性，请参考图 3.9。左侧展示了拟合在没有异常值的一些数据的高斯分布和学生氏分布。右侧加入了一些异常值。我们可以看到，高斯分布受影响很大，而学生氏分布几乎不变。我们将在 11.4.1 节中讨论如何使用学生氏分布进行鲁棒线性回归。

供日后参考，我们注意到学生氏分布具有以下性质：

$$\text{均值} = \mu,\ \text{众数} = \mu,\ \text{方差} = \frac{\nu\sigma^2}{\nu-2}\tag{3.61}$$

仅当 $\nu > 1$ 时均值才有定义。仅当 $\nu > 2$ 时方差才有定义。当 $\nu \gg 5$ 时，学生氏分布迅速逼近高斯分布并失去其鲁棒性特性。通常使用 $\nu = 4$，这在一类问题中表现良好 [LLT89]。

“学生氏”分布。术语 $t$ 的起源似乎出现在学生氏分布表格的语境中，费希尔在建立经典统计推断的基础时使用过这些表格。有关更多历史细节，请访问 http://jeff560.tripod.com/s.html。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_88_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_88_1.png)

图 3.9：展示异常值对拟合高斯、学生氏和拉普拉斯分布的影响。(a) 无异常值（高斯和学生氏曲线重叠在一起）。(b) 有异常值。我们可以看到，与拉普拉斯分布相比，高斯分布更容易受到异常值的影响。改编自 [Bis06] 的图 2.16。由 robust_pdf_plot.py 生成

### 3.4.2 柯西分布

如果 $\nu = 1$，学生氏分布被称为柯西分布或洛伦茨分布。其概率密度函数定义为

$\mathcal{C}(x|\mu,\gamma)=\frac{1}{\gamma\pi}\left[1+\left(\frac{x-\mu}{\gamma}\right)^2\right]^{-1}$  (3.62)

与高斯分布相比，该分布的尾部非常厚重。例如，标准正态分布中 95% 的值位于 -1.96 和 1.96 之间，但对于标准柯西分布，它们位于 -12.7 和 12.7 之间。事实上，尾部如此厚重，以至于定义均值的积分不收敛。

半柯西分布是柯西分布（均值为 0）的一个版本，它“折叠”在自身上，因此其所有概率密度都位于正实数上。因此它具有以下形式

$\mathcal{C}_+(x|\gamma)\triangleq\frac{2}{\pi\gamma}\left[1+\left(\frac{x}{\gamma}\right)^2\right]^{-1}$  (3.63)

这在贝叶斯建模（第 7.2.3.5 节）中非常有用，在那里我们希望使用具有重尾但在原点处密度有限的正实数分布。

### 3.4.3 拉普拉斯分布

另一种具有重尾的分布是拉普拉斯分布³，也称为双侧指数分布。它具有以下概率密度函数：

$\text{Lap}(y|\mu,b)\triangleq\frac{1}{2b}\exp\left(-\frac{|y-\mu|}{b}\right)$  (3.64)

3. 皮埃尔-西蒙·拉普拉斯（1749–1827）是一位法国数学家，在创建贝叶斯统计学领域方面发挥了关键作用。

参见图 3.8 的绘图。这里 $\mu$ 是位置参数，$b > 0$ 是尺度参数。该分布具有以下性质：

均值 = $\mu$，众数 = $\mu$，方差 = $2b^2$  (3.65)

在 11.4.2 节中，我们讨论如何使用拉普拉斯分布进行鲁棒线性回归；在 11.5 节中，我们讨论如何使用拉普拉斯分布进行稀疏线性回归。

### 3.4.4 贝塔分布

贝塔分布的支持区间为 [0, 1]，定义如下：

$\text{Beta}(x|a,b) = \frac{1}{B(a,b)} x^{a-1} (1 - x)^{b-1}$  (3.66)

其中 $B(a,b)$ 是贝塔函数，定义为

$B(a,b) \triangleq \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}$  (3.67)

其中 $\Gamma(a)$ 是由以下式子定义的伽玛函数

$\Gamma(a) \triangleq \int_0^\infty x^{a-1} e^{-x} dx$  (3.68)

参见图 3.10a 中一些贝塔分布的图示。

我们需要 $a,b > 0$ 以确保分布可积（即确保 $B(a,b)$ 存在）。如果 $a = b = 1$，我们得到均匀分布。如果 $a$ 和 $b$ 都小于 1，我们得到一个在 0 和 1 处有“尖峰”的双峰分布；如果 $a$ 和 $b$ 都大于 1，分布是单峰的。

供日后参考，我们注意到该分布具有以下性质（练习 D.12）：

均值 = $\frac{a}{a+b}$，众数 = $\frac{a-1}{a+b-2}$，方差 = $\frac{ab}{(a+b)^2(a+b+1)}$  (3.69)

### 3.4.5 伽玛分布

伽玛分布是正值随机变量 $x > 0$ 的一个灵活分布。它由两个参数定义，称为形状 $a > 0$ 和速率 $b > 0$：

$\text{Ga}(x| \text{形状} = a, \text{速率} = b) \triangleq \frac{b^{a}}{\Gamma(a)} x^{a-1} e^{-x b}$  (3.70)

有时分布是用形状 $a$ 和尺度 $s = 1/b$ 来参数化的：

$\text{Ga}(x| \text{形状} = a, \text{尺度} = s) \triangleq \frac{1}{s^{a}\Gamma(a)} x^{a-1} e^{-x/s}$  (3.71)

参见图 3.10b 中伽玛概率密度函数的一些图示。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_90_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_90_1.png)

图 3.10：(a) 一些贝塔分布。由 beta_dist_plot.py 生成。(b) 一些 Ga(a, b = 1) 分布。如果 a ≤ 1，众数在 0，否则 > 0。随着速率 b 的增加，我们缩小水平尺度，从而将所有内容向左和向上压缩。由 gamma_dist_plot.py 生成。

供参考，我们注意到该分布具有以下性质：

均值 = $a/b$，众数 = $(a-1)/b$，方差 = $a/b^2$  (3.72)

有几个分布只是伽玛分布的特例，我们稍后讨论。

- **指数分布。** 其定义为
  
  $\text{Expon}(x|\lambda) \triangleq \text{Ga}(x| \text{形状} = 1, \text{速率} = \lambda)$  (3.73)
  
  该分布描述了泊松过程中事件之间的时间间隔，即事件以恒定的平均速率 $\lambda$ 连续且独立发生的过程。

- **卡方分布。** 其定义为
  
  $\chi^2_\nu(x) \triangleq \text{Ga}(x| \text{形状} = \nu/2, \text{速率} = 1/2)$  (3.74)
  
  其中 $\nu$ 被称为自由度。这是平方高斯随机变量之和的分布。更准确地说，如果 $Z_i \sim \mathcal{N}(0,1)$，且 $S = \sum_{i=1}^\nu Z_i^2$，则 $S \sim \chi^2_\nu$。

- **逆伽玛分布**是假设 $X \sim \text{Ga}(a,b)$ 时 $Y = 1/X$ 的分布。可以证明（练习 D.11）其概率密度函数为
  
  $\text{IG}(x| \text{形状} = a, \text{尺度} = s) \triangleq \frac{b^a}{\Gamma(a)} x^{-(a+1)} e^{-s/x}$  (3.75)
  
  该分布具有以下性质
  
  均值 = $s/(a-1)$，众数 = $s/(a+1)$，方差 = $s^2 / [(a-1)^2(a-2)]$  (3.76)
  
  仅当 $a > 1$ 时均值才存在。仅当 $a > 2$ 时方差才存在。

## 3.5 多元高斯（正态）分布

用于连续随机变量的联合概率分布中，最常用的是**多元高斯**或**多元正态（MVN）**。这主要是因为它在数学上方便，而且因为在许多情况下，高斯假设是相当合理的（参见 3.3.4 节的讨论）。

### 3.5.1 定义

MVN 密度由以下式子定义：

$$\mathcal{N}(\mathbf{y}|\boldsymbol{\mu},\boldsymbol{\Sigma}) \triangleq \frac{1}{(2\pi)^{D/2}|\boldsymbol{\Sigma}|^{1/2}} \exp\left[-\frac{1}{2}(\mathbf{y}-\boldsymbol{\mu})^{\top}\boldsymbol{\Sigma}^{-1}(\mathbf{y}-\boldsymbol{\mu})\right] \tag{3.77}$$

其中 $\boldsymbol{\mu}=\mathbb{E}[\mathbf{y}]\in\mathbb{R}^D$ 是均值向量，$\boldsymbol{\Sigma}=\mathrm{Cov}[\mathbf{y}]$ 是 $D\times D$ 的**协方差矩阵**，定义如下：

$$\mathrm{Cov}[\mathbf{y}] \triangleq \mathbb{E}\left[(\mathbf{y}-\mathbb{E}[\mathbf{y}])(\mathbf{y}-\mathbb{E}[\mathbf{y}])^{\top}\right] \tag{3.78}$$

$$\mathrm{Cov}[\mathbf{y}] = \begin{pmatrix} \mathbb{V}[Y_1] & \mathrm{Cov}[Y_1,Y_2] & \cdots & \mathrm{Cov}[Y_1,Y_D] \\ \mathrm{Cov}[Y_2,Y_1] & \mathbb{V}[Y_2] & \cdots & \mathrm{Cov}[Y_2,Y_D] \\ \vdots & \vdots & \ddots & \vdots \\ \mathrm{Cov}[Y_D,Y_1] & \mathrm{Cov}[Y_D,Y_2] & \cdots & \mathbb{V}[Y_D] \end{pmatrix} \tag{3.79}$$

其中

$$\mathrm{Cov}[Y_i,Y_j] \triangleq \mathbb{E}[(Y_i-\mathbb{E}[Y_i])(Y_j-\mathbb{E}[Y_j])] = \mathbb{E}[Y_iY_j] - \mathbb{E}[Y_i]\mathbb{E}[Y_j] \tag{3.80}$$

且 $\mathbb{V}[Y_i]=\mathrm{Cov}[Y_i,Y_i]$。由公式 (3.78)，我们得到重要结果 $$\mathbb{E}[\mathbf{y}\mathbf{y}^{\top}] = \boldsymbol{\Sigma} + \boldsymbol{\mu}\boldsymbol{\mu}^{\top} \tag{3.81}$$

公式 (3.77) 中的归一化常数 $Z=(2\pi)^{D/2}|\boldsymbol{\Sigma}|^{1/2}$ 仅确保概率密度函数积分为 1（参见练习 3.3）。

