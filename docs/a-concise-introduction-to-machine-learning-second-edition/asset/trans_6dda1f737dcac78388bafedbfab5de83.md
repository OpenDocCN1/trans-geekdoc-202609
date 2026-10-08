
利用期望的定义，这变为：

```
var[x] = \int_{-\infty}^{\infty} (x^2 - 2E[x] + E[x]^2)f(x)dx
= \int_{-\infty}^{\infty} x^2f(x)dx - 2E[x]\int_{-\infty}^{\infty} xf(x)dx + \int_{-\infty}^{\infty} f(x)dx
= E[x^2] - E[x]^2,
```

由于 $f(x)$ 的积分为1且 $\int_{-\infty}^{\infty} xf(x)dx = E[x]$。该公式也适用于具有点质量的离散概率分布。方差的平方根是**标准差**。

我们看到这个公式涉及 $x$ 的期望。这被称为*二阶原矩*或*粗略矩*。第 $i$ 阶原矩（粗略矩）定义为：

```
\int_{-\infty}^{\infty} f(x)x^i dx,
```

而第 $i$ 阶阶差矩为：

```
\int_{-\infty}^{\infty} f(x)(x-E[x])^i dx,
```

归一化第 $i$ 阶阶矩是第 $i$ 阶阶矩除以标准差的 $i$ 次方，即 $var[x]^{i/2}$。归一化阶矩对于任何线性变换是不变的。如果 $y = ax + b$，则 $x$ 和 $y$ 的阶矩是相同的。归一化阶矩用于量化概率密度的形状。三阶阶矩被称为*偏度*，用于衡量围绕均值的非对称性。。如果分布是对称的，偏度为零。如果更多概率位于均值左侧，则偏度为负；如果更多概率在右侧，则偏度为正。四阶阶矩是*峰度*，用于衡量分布的尾部浓度。它与正态分布进行比较。如果它更大，则分布被称为*尖峰分布*；这意味着极值出现的概率更高。如果它较小，则是*平峰分布*；在这种情况下，离群值很少见。如果底层分布是正态的，峰度为3。然而，如果这些事件是灾难性的，峰度就会被低估。

矩可以从样本中计算，并用于为随机变量选择概率密度函数。更一般地说，随机变量本身不是关注点，而是它的期望 $E[g(x)]$ 和方差 $Var[g(x)]$。如果有多个随机变量，则使用下标来表示相对于哪个变量取期望。例如，$E_y[g(x)]$。

该期望是相对于 $y$ 取的，结果是 $x$ 的函数。由于在进行积分或求和时顺序并不重要，如果先对 $x$ 取期望再对 $y$ 取期望，结果是相同的，即 $f(x, y) = f(x)f(y)$。回到正态分布，我们计算期望（一阶矩）的下式为：

```
$E[X] = \int_{-\infty}^{\infty} \frac{x}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.
```

令 $y = x - \mu$，则 $dy = dx$，通过此变量替换，积分结果保持为：

```
$E[X] = \int_{-\infty}^{\infty} \frac{y+\mu}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy
= \int_{-\infty}^{\infty} \frac{y}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy + \mu \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy.
```

第一个积分的被积函数是奇函数，$f(-y)=-f(y)$。奇函数在关于原点对称的区间上的积分值为零。第二个积分的结果为1，因为它在整个范围内积分了均值为零、方差为 $\sigma^2$ 的正态分布概率密度函数。对于方差，我们计算：

```
$Var[x] = \int_{-\infty}^{\infty} \frac{(x-\mu)^2}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.
```

再次像之前一样令 $y = x - \mu$，我们得到：

```
$Var[x] = \int_{-\infty}^{\infty} \frac{y^2}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy.
```

这个积分可以通过*分部积分法*计算，分部积分可以被看作是*乘积微分法则*的逆过程，该法则为：

```
$d(uv) = \frac{du}{dy}v + u\frac{dv}{dy}.
```

则分部积分为：

$$\int_{a}^{b} udv = [uv]_{a}^{b} - \int_{a}^{b} vdu.$$

令 $u = y$ 且 $dv = y \exp \left(-\frac{y^2}{2\sigma^2}\right)dy$，$du = dy$ 且 $v = -\sigma^2 \exp \left(-\frac{y^2}{2\sigma^2}\right).$

通过此我们得到

$var[x] = \left[ \frac{-\sigma^2 y}{\sqrt{2\pi}\sigma} \exp \left(-\frac{y^2}{2\sigma^2}\right) \right]_{-\infty}^{\infty} = \int_{-\infty}^{\infty} \frac{-\sigma^2 y}{\sqrt{2\pi}\sigma} \exp \left(-\frac{y^2}{2\sigma^2}\right) dy.$

正态分布的一阶矩为：

$E[X] = \int_{-\infty}^{\infty} \frac{x}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.$

正态分布的二阶矩为：

$Var[x] = \int_{-\infty}^{\infty} \frac{(x-\mu)^2}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.$

正态分布的三阶矩为：

正态分布的四阶矩为：

## 2.3 离散质量示例

在下面的概述中，我们考虑离散变量。例如，硬币投掷，有两种结果：正面或反面，真或假。这些也被称为布尔变量。正面的概率为 $\mu$，反面的概率为 $1-\mu$。伯努利分布为：

$Bern(x=\mu) = \mu^x (1-\mu)^{1-x}.$
