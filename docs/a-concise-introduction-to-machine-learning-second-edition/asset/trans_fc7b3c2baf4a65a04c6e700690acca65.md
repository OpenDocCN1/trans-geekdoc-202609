

# 12 ■ 机器学习简要介绍

![](img/c6c76bf52016db7e78a5e30d4766ef81_40_0.png)

图 2.2：不同 $\mu$ 和 $\sigma$ 取值的正态概率密度函数。

...-太小到无法解释。这被称为*过拟合*（overfitting），即模型无法泛化到未见的数据上。例如，假设我们将年龄离散化得非常细，导致每个年龄组中只有一个女性，那么如果该年龄组为空，我们可能无法对研究中的新参与者做出任何预测；或者我们将根据该年龄组该女性的死亡率进行预测，而这可能是完全错误的。

离散化处理连续值变量 $x$ 概率的一种方法。另一种方法是关于 $x$ 的*概率密度函数 (pdf)* $f(x)$，它描述了分布。从形式上说，它的定义为当区间大小 $\Delta x$ 趋于 0 时，$f(x)\Delta x$ 是样本落在区间 $(x, x+\Delta x)$ 内的概率。概率密度函数始终是非负的。它可以被看作是离散化的极限。$x$ 落在区间 $(a, b)$ 内有一个有效概率，其公式为：

> $$p(x \in (a, b)) = \int_{a}^{b} f(x)dx$$

如果 $a = -\infty$ 且 $b = \infty$，即对 $x$ 的所有可能值积分，概率为一。

由于连续变量可以离散化，离散变量也可以被视为连续变量。在这种情况下，$f(x)$ 被称为*概率质量函数 (pmf)*，因为 $x$ 每个离散可能值的概率都集中在这些值上的点质量。对于 $x$ 的所有其他值，概率均为零。

概率密度函数的一个著名例子是正态分布的钟形曲线，也称为高斯分布 $x \sim \mathcal{N}(\mu, \sigma^2)$，其中 $\mu$ 表示“分布为”。它的概率密度函数给出：

```
$$\mathcal{N}(x|\mu, \sigma^2) = \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right), \quad (2.4)$$
```

它的位置和形状由参数 $\mu$（称为均值）和 $\sigma^2$（称为方差）决定。方差的平方根 $\sigma$ 是标准差。图 2.2 展示了均值和方差不同值时的钟形曲线形状。当 $\mu=0$ 且 $\sigma^2=1$ 时，它被称为标准正态分布。

有一个常见的误解认为“正态”（normal）意味着“普通”。高斯在第 8.4 节的普通最小二乘法中引入了“normal”一词，指的是范数（norm）。最小化的一种技术是求解“正规”方程（normal equations），高斯在选择词汇时指的就是这些方程。关于“normal”含义的工具工具。

正态分布确实非常常见。Lyon (2014) 详述道，如果 $x_1, \dots, x_n$ 是均值为零、方差为 $\sigma^2$ 的独立同分布（i.i.d）随机变量，那么归一化和的分布

```
$S_n = \frac{x_1 + \dots + x_n}{\sqrt{n}}$
```

在 $n$ 足够大时接近于正态分布。当 $n$ 趋于无穷大且 $S_n \to S$ 时，它趋于正态分布 $\mathcal{N}(0,\sigma^2)$。无论 $x_1, \dots, x_n$ 最初的分布是什么，只要它们是独立同分布的，结论就成立。然而，这是本解释的核心。

虽然我们想要用概率密度函数描述的某些现象可能是独立同分布和的结果，但也可能受到不同因素的影响，而所有因素都有其独特的分布。例如一个人的身高。存在由遗传组成决定的增长潜力。这是后天的部分。营养、污染、疾病等都是因素。所有因素都不是独立同分布的，但身高仍然呈正态分布。

为了证明正态分布的积分值为一，我们考虑：

```
$$\int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx$$
```

令 $x-\mu = \sigma y$，则 $dx = \sigma dy$。积分范围随此变量替换而不改变。我们得到：

```
$$\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right) dy$$
```

# 14 机器学习简要介绍

![](img/c6c76bf52016db7e78a5e30d4766ef81_42_0.png)

接下来我们考虑积分的平方：

```
$$\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy = \frac{1}{2\pi} \left(\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy\right) \times \left(\int_{-\infty}^{\infty} \exp\left(-\frac{z^2}{2}\right)dz\right) = \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2+z^2}{2}\right)dydz.$$
```

转换到极坐标，$y = r\cos\theta, z = r\sin\theta$ 且 $dydz = r^2dr\theta$，得到：

```
$$\int_0^{2\pi} \int_0^{\infty} \exp\left(-\frac{r^2}{2}\right)rdrd\theta = \dots$$
```

这里使用了 $\cos^2\theta+\sin^2\theta = 1$。（注：OCR文本关于积分计算包含重复/损坏内容）

正态分布的积分值为一。![](img/c6c76bf52016db7e78a5e30d4766ef81_43_0.png)

图 2.3：不同 $\mu$ 和 $\sigma$ 取值的累积分布函数。

| 区间 | 百比 |
| :--- | :--- |
| $(-\sigma, \mu+\sigma)$ | 68.2% |
| $(-\2\sigma, \mu+2\sigma)$ | 95.4% |
| $(-\3\sigma, \mu+3\sigma)$ | 99.7% |
| $(-\4\sigma, \mu+4\sigma)$ | 99.97% |
| $(-\5\sigma, \mu+5\sigma)$ | 99.999% |

正态分布确实非常常见。Lyon (2014) 详述道，如果 $x_1, \dots, x_n$ 是均值为零、方差为 $\sigma^2$ 的独立同分布（i.i.d）随机变量，那么归一化和的分布

```
$S_n = \frac{x_1 + \dots + x_n}{\sqrt{n}}$
```

在 $n$ 足够大时接近于正态分布。当 $n$ 趋于无穷大且 $S_n \to S$ 时，它趋于正态分布 $\mathcal{N}(0,\sigma^2)$。无论 $x_1, \dots, x_n$ 最初的分布是什么，只要它们是独立同分布的，结论就成立。然而，这是本解释的核心。

虽然我们想要用概率密度函数描述的某些现象可能是独立同分布和的结果，但也可能受到不同因素的影响，而所有因素都有其独特的分布。例如一个人的身高。存在由遗传组成决定的增长潜力。这是后天的部分。营养、污染、疾病等都是因素。所有因素都不是独立同分布的，但身高仍然呈正态分布。

为了证明正态分布的积分值为一，我们考虑：

```
$$\int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx$$
```

令 $x-\mu = \sigma y$，则 $dx = \sigma dy$。积分范围随此变量替换而不改变。我们得到：

```
$$\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right) dy$$
```

接下来我们考虑积分的平方：

```
$$\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy = \frac{1}{2\pi} \left(\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy\right) \times \left(\int_{-\infty}^{\infty} \exp\left(-\frac{z^2}{2}\right)dz\right) = \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2+z^2}{2}\right)dydz.$$
```

转换到极坐标，$y = r\cos\theta, z = r\sin\theta$ 且 $dydz = r^2dr\theta$，得到：

```
$$\int_0^{2\pi} \int_0^{\infty} \exp\left(-\frac{r^2}{2}\right)rdrd\theta = \dots$$
```

正态分布在相同 $\mu$ 和 $\sigma$ 取下的累积分布函数显示了值落在均值一定范围内的概率。

