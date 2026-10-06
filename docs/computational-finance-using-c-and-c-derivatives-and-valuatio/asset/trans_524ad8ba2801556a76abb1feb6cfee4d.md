

## 第 5 章 | 单资产美式期权

将上述方程的左侧代入方程 (5.2.20)，我们得到关于 $S^*$ 的方程：

```
$S^* - E = c(S^*, E, \tau) + \frac{S^*}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*))}. \quad (5.2.24)
```

可以使用标准的迭代方法求解 $S^*$（参见临界资产价值的数值求解章节）。当找到 $S^*$ 后，方程 (5.2.23) 给出

```
$ha_2 = A_2S^{*\gamma_2}.
```

其中

```
$A_2 = \frac{S^*}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*))\}$.
```

根据 (5.2.19)，美式看涨期权的价值为：

```
$C(S,E, \tau) = c(S,E, \tau) + A_2(\frac{S}{S^*})^{\gamma_2} \quad \text{当 } S < S^*, \quad (5.2.25)
```

```
$C(S,E, \tau) = S - E \quad \text{当 } S \geq S^*. \quad (5.2.26)
```

## 美式看跌期权

对于美式看跌期权，我们采用与美式看涨期权类似的方法。现在我们利用美式看跌期权的价值和提前行溢价 $(y_p(S,E,\tau) = h_p(S,E,\tau))$ 在资产价格 $S \to \infty$ 时均趋于零。因此，当 $S \to \infty$ 时，$q_p(S,E,\tau) \to 0$。由于 $\gamma_2 > 0$，方程 (5.2.18) 实现这一点的唯一方法是 $a_2 = a_1S^{*\gamma_1}$，美式看跌期权的价值为：

```
$P(S,E,\tau) = p(S,E,\tau) + ha_1S^{*\gamma_1}. \quad (5.2.27)
```

通过考虑临界资产价格 $S^*$，可以找到 $a_1$ 的表达式，在该价格以下，美式期权将被行权。对于 $S > S^*$，美式看跌期权的价值由方程 (5.2.27) 给出；对于 $S < S^*$，我们有 $P(S,E,\tau) = S - E$。

临界资产价格处期权价值的连续性给出：

```
$E - S^* = p(S,E,\tau) + ha_1S^{*\gamma_1}. \quad (5.2.28)
```

临界资产价格处期权价值梯度的连续性产生：

```
$\frac{\partial(E - S^*)}{\partial S^*} = \frac{\partial}{\partial S^*}\{p(S^*,E,\tau) + ha_1S^{*\gamma_1}\}. \quad (5.2.29)
```

可以简化为

```
$-1 = -N_1(d_1(S^*))\exp(-q\tau) + \gamma_1 a_1. \quad (5.2.30)
```

其中我们使用了欧式看跌期权的对冲值 $\Delta_p$ 值：

```
$\frac{\partial\Delta_p(S^*,\tau)}{\partial S^*} = \{N_1(d_1(S^*)) - 1\}\exp(-q\tau).
```

## 美式期权的近似

因此，方程 (5.2.30)可以写为：

```
$ha_1S^{\gamma_1} = \frac{S^{**}}{\gamma_1}\{1 - N_1(d_1(S^{**}))\}\exp(-q\tau). \quad (5.2.31)
```

将上述的左侧代入方程 (5.2.28)，我们得到关于 $S^{**}$ 的以下方程：

```
$E - S^{**} = p(S^{**}, \tau) + \{1 - \exp(-q\tau)N_1(d_1(S^{**}))\}\frac{S^{**}}{\gamma_1}. \quad (5.2.32)
```

可以通过迭代求解来得到 $S^*$（见临界资产价值章节）。当找到 $S^{**}$ 后，方程 (5.2.31) 给出

```
$ha_1 = A_1S^{**\gamma_1},
```

其中

```
$A_1 = -\frac{S^{**}}{\gamma_1}\{1 - \exp(-q\tau)N_1(d_1(S^{**}))\}$. 
```

我们在此注意到 $A_1 > 0$，因为 $\gamma_1 < 0$，$S^{**} > 0$ 且 $N_1(d_1(S^{**}))\exp(-q\tau) < 1$。

根据 (5.2.27)，美式看跌期权的价值为：

```
$P(S, \tau) = p(S, \tau) + A_1\frac{S^{\gamma_2}}{S^{**}} \quad \text{当 } S > S^{**},
```

```
$P(S, \tau) = E - S \quad \text{当 } S \le S^{**}.
```

## 临界值的的数值求解

我们提供了如何迭代求解方程 (5.2.24) 和方程 (5.2.32) 中临界价格的细节。

## 美式看涨期权

对于美式看涨期权，我们需要求解方程 (5.2.24)，其为：

```
$S^* - E = c(S^*, \tau) + \frac{S^*}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*))\}$.
```

我们将临界资产价值 $S^*$ 的第 $i$ 次近似表示为 $S^*_i$，并将第 $i$ 次迭代的左侧表示为

```
$LHS(S^*_i, \tau) = S^*_i - E,
```

并将方程的右侧表示为

```
$RHS(S^*_i, \tau) = c(S^*_i, \tau) + \frac{S^*_i}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*_i))\}$.
```

如果我们令 $K(S^*_i, \tau) = RHS(S^*_i, \tau) - LHS(S^*_i, \tau)$，那么我们要找到 $S^*_i$ 的值使得在指定的容差范围内 $K(S^*_i, \tau) \sim 0$。这可以通过牛顿法实现，其中更好的近似 $S_{i+1}^*$ 通过下式找到：

```
$S_{i+1}^* = S^*_i - \frac{K(S^*_i, \tau)}{K'(S^*_i, \tau)}, \quad (5.2.33)
```

其中

```
$K'(S^*_i, \tau) = \frac{\partial}{\partial S^*}\{RHS(S^*_i, \tau) - LHS(S^*_i, \tau)\}
= \frac{\partial}{\partial S^*}\{RHS(S^*_i, \tau)\} - \frac{\partial}{\partial S^*}\{LHS(S^*_i, \tau)\}
= b_i - 1.
```

在这里，我们使用了 $b_i = \frac{\partial}{\partial S^*}\{RHS(S^*_i, \tau)\}$，且 $b_i$ 的表达式由方程 (5.2.35) 给出。将 $K(S^*_i, \tau)$ 和 $K'(S^*_i, \tau)$ 代入方程 (5.2.32)，我们得到

```
$S_{i+1}^* = S^*_i - \frac{RHS(S^*_i, \tau) - LHS(S^*_i, \tau)}{b_i - 1} = S^*_i - \frac{RHS(S^*_i, \tau) - (S^*_i - E)}{b_i - 1} = \frac{b_i S^*_i - RHS(S^*_i, \tau) + E}{b_i - 1}$
```

美式看涨期权的最终算法为：

```
$S_{i+1}^* = \frac{E + RHS(S^*_i, \tau) - b_i S^*_i}{1 - b_i}, \quad (5.2.34)
```

其中可以使用 $S^*_i = E$ 作为临界值的初始估计。计算机代码如下：$b_i$ 的表达式

在这里，我们推导了方程 (5.2.34) 中的 $b_i$ 项：

```
$b_i = \frac{\partial(S^*_i, E, \tau)}{\partial S^*_i} + \frac{1}{\gamma_2}\{1 - \exp(-q\tau)N_1(d_1(S^*_i))\}$.
```

现在我们将引用附录 A 中推出的结果：

- 附录 A，方程 (A.1.3)：$n(d_1(S^*_i)) = \frac{\partial d_1(S^*_i)}{\partial S^*_i}$
- 附录 A，方程 (A.1.6)：$\frac{\partial d_1(S^*_i)}{\partial S^*_i} = \frac{1}{\sigma\sqrt{\tau}}$
- 附录 A，方程 (A.3.2)：$\Delta_c = \frac{\partial c(S^*_i, E, \tau)}{\partial S^*_i} = \exp(-q\tau)N_1(d_1(S^*_i))$

将这些结果代入上述表达式，得到：

```
$b_i = \exp(-q\tau)N_1(d_1(S^*_i)) + \frac{1}{\gamma_2} \frac{\exp(-q\tau)N_1(d_1(S^*_i))}{\gamma_2} - \frac{\exp(-q\tau)n(d_1(S^*_i))}{\gamma_2\sqrt{\tau}}$
```

可以重新整理得到：

```
$b_i = \exp(-q\tau)N_1(d_1(S^*_i)) \left\{ 1 - \frac{1}{\gamma_2} \right\} + \frac{1}{\gamma_2} \left\{ 1 - \frac{\exp(-q\tau)n(d_1(S^*_i))}{\sqrt{\tau}} \right\} \quad (5.2.35)
```

## 美式看跌期权

对于看跌期权，我们需要求解 (5.2.32)，其为：

```
$E - S_i^{**} = p(S_i^{**}, E, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - N_1(d_1(S_i^{**}))\}\exp(-q\tau)
```

如果我们令 $S_i^{**}$ 表示临界资产价值 $S^{**}$ 的命中近似，我们可以用以下方式表示方程的左侧：

```
$LHS(S_i^{**}, E, \tau) = E - S_i^{**}$
```

并将方程的右侧表示为：

```
$RHS(S_i^{**}, E, \tau) = p(S_i^{**}, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - N_1(-d_1(S_i^{**}))\}\exp(-q\tau)
= p(S_i^{**}, E, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - N_1(d_1(S_i^{**}))\}\exp(-q\tau)
= p(S_i^{**}, E, \tau) - \frac{S_i^{**}}{\gamma_1} \{ 1 - \exp(-q\tau) + N_1(d_1(S_i^{**}))\}\exp(-q\tau)
```

我们令 $K(S_i^{**}, E, \tau) = RHS(S_i^{**}, E, \tau)$ 并使用牛顿法，得到：

```
$S_{i+1}^{**} = S_i^{**} - \frac{K(S_i^{**}, E, \tau)}{K'(S_i^{**}, E, \tau)} \quad (5.2.36)
```

其中之前

```
$K'(S_i^{**}, E, \tau) = \frac{\partial}{\partial S_i^{**}} RHS(S_i^{**}, E, \tau)\}$
```

所以 $K'(S_i^{**}, E, \tau) = 1 + b_i$，其中 $b_i = [\partial(RHS(S_i^{**}, E, \tau))]/\partial S_i^{**}$。

