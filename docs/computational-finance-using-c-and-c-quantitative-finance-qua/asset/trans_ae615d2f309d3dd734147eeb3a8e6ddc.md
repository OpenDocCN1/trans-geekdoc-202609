

## 录录 C：统计结果

## C.1 大数定律

设 $x_1, x_2, \dots$ 为一组独立同分布（IID）随机变量，每个变量的期望值为 $\mu$，方差为 $\sigma^2$。定义平均值序列为

$y_n = \sum_{i=1}^n x_i = \frac{x_1 + x_2 + \dots + x_n}{n}, \quad n = 1, 2, \dots$

则大数定律指出，当 $n \to \infty$ 时，$y_n$ 收敛于 $\mu$，即 $Var[y_n] \to 0$。

$y_n$ 的均值为：

$E[y_n] = \frac{1}{n}(E[x_1] + E[x_2] + \dots + E[x_n]) = \frac{1}{n}\mu = \mu$

$y_n$ 的方差有：

$Var[y_n] = Var\left[\frac{\sum_{i=1}^n x_i}{n}\right] = \frac{1}{n^2}Var\left[\sum_{i=1}^n x_i\right] = \frac{1}{n^2}n\sigma^2 = \frac{\sigma^2}{n}$

其中我们使用了独立随机变量和的方差等于它们各方差之和的性质；见 C.2 节。

因此我们证明了当 $n \to \infty$ 时，$Var[y_n] \to 0$。

## C.2 中心极限定理

设 $x_1, x_2, \dots$ 为一组独立同分布（IID）随机变量，每个变量的期望值为 $\mu$，方差为 $\sigma^2$。如果定义 $u_i = x_i - \mu$，则：

$E[u_i] = E[u] = 0,\quad Var[u_i] = E[u^2] = \sigma^2$

设

$s_n = \sum_{i=1}^{n} u_i + n\mu$

所以

$s_n = \sum_{i=1}^{n} x_i$

我们现在引入归一化值 $z_n$，如下：

$z_n = \frac{s_n - n\mu}{\sqrt{n}} = \frac{1}{\sqrt{n}} \sum_{i=1}^{n} u_i$

中心极限定理指出，当 $n$ 趋于无穷时，$z_n$ 的概率分布趋于零均值单位方差的正态分布；数学上，当 $n \to \infty$ 时，$z_n \to N(0, 1)$。

证明。根据 C.5 节公式 (C.5.3)

$M_{z_n} = E[\exp(tz_n)] = E\left[ \exp\left[ \frac{t}{\sqrt{n}} \sum_{i=1}^{n} u_i \right] \right]$

并使用公式 (C.5.5)

$M_{z_n} = \left\{ M_u\left( \frac{t}{\sqrt{n}} \right) \right\}^n$

公式 (C.5.1) 给出：

$M_u\left( \frac{t}{\sqrt{n}} \right) \approx 1 + \frac{t}{\sqrt{n}} E[u] + \frac{1}{2} \left( \frac{t}{\sqrt{n}} \right)^2 E[u^2] + \dots$

当 $n \to \infty$ 时，$\frac{t}{\sqrt{n}} \to 0$，且

$M_u\left( \frac{t}{\sqrt{n}} \right) \to 1 + \frac{t}{\sqrt{n}} E[u] + \frac{1}{2} \left( \frac{t}{\sqrt{n}} \right)^2 E[u^2] = 1 + \frac{t^2}{2n}$

因此

$\left\{ M_{z_n}\left( \frac{t}{\sqrt{n}} \right) \right\}^n = \left( 1 + \frac{t^2}{2n} \right)^n \to 1 + \frac{t^2}{2} \text{ as } n \to \infty$

其中我们使用了 $t \ll 1$ 的事实；见 Grimmett and Welsh (1986)。我们随后证明了当 $n \to \infty$ 时

$M_{z_n}(t) \to 1 + \frac{t^2}{2} \to e^{t^2/2}$

然而，根据 D.1 节，标准正态分布 $(\mu=0, \sigma^2 = 1)$ 的动动函数 $M_z(t)$ 为：

$M_z(t) = e^{t^2/2} \text{ 其中 } z \sim N(0, 1)$

因此我们证明了当 $n \to \infty$ 时，$z_n \to N(0, 1)$。

## C.3 随机变量的方差与协方差

### C.3.1 方差

单变量

设 $X$ 为给定分布的一个变量，$Z$ 为该变量的如下线性函数：

$Z = a + bX$

其中 $a$ 和 $b$ 是常数。那么

$E[Z] = E[a] + E[bX] = a + bE[X]$

以及

$Var[Z] = E[(Z - E[Z])^2]$
$= E[(a + bX - a - bE[X])^2]$
$= E[(bX - bE[X])^2]$
$= E[b^2(X - E[X])^2]$
$= b^2E[(X - E[X])^2]$

因此，均值为 $a + bE[X]$，方差为 $Var[X]$。

双变量

设 $Z = a + b_1X_1 + b_2X_2$，其中 $a, b_1$ 和 $b_2$ 是常数。那么均值为 $E[Z] = E[a] + E[b_1X_1] + E[b_2X_2] = a + b_1E[X_1] + b_2E[X_2]$。方差 $Var[Z]$ 的计算如下：

$Var[Z] = E[(a + b_1X_1 + b_2X_2 - a - b_1E[X_1] - b_2E[X_2])^2]$
$= E[(b_1(X_1 - E[X_1]) + b_2(X_2 - E[X_2]))^2]$
$= b_1^2E[(X_1 - E[X_1])^2] + b_2^2E[(X_2 - E[X_2])^2] + 2b_1b_2E[(X_1 - E[X_1])(X_2 - E[X_2])]$
$= b_1^2Var[X_1] + b_2^2Var[X_2] + 2b_1b_2Cov[X_1, X_2],$

$Cov[X_1, X_2]$ 是 $X_1$ 和 $X_2$ 之间的协方差。如果 $X_1$ 和 $X_2$ 是独立同分布的随机变量（IID），则 $Cov[X_1, X_2] = 0$，我们有：

$Var[Z] = b_1^2Var[X_1] + b_2^2Var[X_2]$

三变量

设 $Z = a + b_1X_1 + b_2X_2$，其中 $a, b_1$ 和 $b_2$ 是常数。那么均值为 $E[Z] = E[a] + E[b_1X_1] + E[b_2X_2] = a + b_1E[X_1] + b_2E[X_2]$。方差 $Var[Z]$ 计算如下：

$Var[Z] = E[(a + b_1X_1 + b_2X_2 - a - b_1E[X_1] - b_2E[X_2])^2]$
$= E[(b_1(X_1 - E[X_1]) + b_2(X_2 - E[X_2]))^2]$
$= b_1^2E[(X_1 - E[X_1])^2] + b_2^2E[(X_2 - E[X_2])^2] + 2b_1b_2E[(X_1 - E[X_1])(X_2 - E[X_2])]$
$= b_1^2Var[X_1] + b_2^2Var[X_2] + 2b_1b_2Cov[X_1, X_2],$

$Cov[X_1, X_2]$ 是 $X_1$ 和 $X_2$ 之间的协方差。如果 $X_1$ 和 $X_2$ 是独立同分布的（IID），则 $Cov[X_1, X_2] = 0$，我们有：

$Var[Z] = b_1^2Var[X_1] + b_2^2Var[X_2]$

### C.3.2 协方差

两个变量 $X$ 和 $Y$ 之间的协方差定义为：

$Cov[X, Y] = E[(X - E[X])(Y - E[Y])]$

由对称性可知 $Cov[X, Y] = Cov[Y, X]$。同样 $Cov(aX, bY) = ab \, Cov(X, Y)$。

双变量

设 $Z = a + b_1X_1 + b_2X_2$，其中 $a, b_1$ 和 $b_2$ 是常数。

$Cov[Z, Y] = Cov(a + b_1X_1 + b_2X_2, Y) = b_1Cov(X_1, Y) + b_2Cov(X_2, Y)$

三变量

设 $Z_1 = a + b_1X_1 + b_2X_2$ 且 $Z_2 = a + b_1X_1 + b_2X_2 + b_3X_3$，其中 $a, b_1, b_2$ 和 $b_3$ 是常数。

$Cov[Z_1, Y] = b_1Cov(X_1, Y) + b_2Cov(X_2, Y)$

四变量

设 $Z_1 = a + b_1X_1 + b_2X_2 + b_3X_3$ 且 $Z_2 = a + b_1X_1 + b_2X_2 + b_3X_3 + b_4X_4$，其中 $a, b_1, b_2, b_3$ 和 $b_4$ 是常数。

$Cov[Z_1, Y] = b_1Cov(X_1, Y) + b_2Cov(X_2, Y) + b_3Cov(X_3, Y)$

