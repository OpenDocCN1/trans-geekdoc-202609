

# 134 章 | 5 单一资产美式期权

这里我们使用了 $S_j = j\Delta S$ 这一事实，并且为了简洁起见，定义了以下项：

$\mathcal{A}_1 = \Theta_m f_{i+1,j+1} - \Theta_m f_{i+1,j-1} + \Theta_m^* f_{i,j+1} - \Theta_m^* f_{i,j-1}$

以及

$\mathcal{A}_2 = \Theta_m f_{i+1,j+1} + \Theta_m f_{i+1,j-1} - 2\Theta_m f_{i,j} + \Theta_m^* f_{i,j+1} + \Theta_m^* f_{i,j-1} - 2\Theta_m^* f_{i,j}$。

将 $f_{i,j}, f_{i+1,j}, f_{i+1,j+1}$ 等项合并，得到：

$\mathcal{B}_1 f_{i,j-1} + \mathcal{B}_2 f_{i,j} + \mathcal{B}_3 f_{i,j+1} + C_1 f_{i+1,j-1} + C_2 f_{i+1,j} + C_3 f_{i+1,j+1} = 0$，(5.4.13)

其中

$$\mathcal{B}_1 = \frac{-\Theta_m^*(r-q)\Delta t}{2} + \frac{\Theta_m^*\sigma^2 j\Delta t}{2}$$
$$\mathcal{B}_2 = -1 - r\Delta\Theta_m^* - \frac{\Theta_m^*\sigma^2 j\Delta t}{2}$$
$$\mathcal{B}_3 = \frac{\Theta_m(r-q)\Delta t}{2} + \frac{\Theta_m\sigma^2 j\Delta t}{2}$$
$$C_1 = \frac{\Theta_m\sigma^2 j\Delta t}{2} - \frac{\Theta_m(r-q)\Delta t}{2}$$
$$C_2 = -1 - r\Delta\Theta_m - \Theta_m\sigma^2 j\Delta t$$
$$C_3 = \frac{\Theta_m(r-q)\Delta t}{2} + \frac{\Theta_m\sigma^2 j\Delta t}{2}$$

由于我们是在反向求解该方程，并且想要根据时间索引 $i+1$ 处的已知期权值 $(f_{i+1,j+1}, f_{i+1,j}$ 和 $f_{i+1,j-1})$ 来确定时间索引 $i$ 处的期权值。这可以通过如下重组方程 (5.4.13) 来：

$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i,j+1} = R_{i,j}, \quad (5.4.14)$

$R_{i,j} = \tilde{a}_j f_{i+1,j-1} + \tilde{b}_j f_{i+1,j} + \tilde{c}_j f_{i+1,j+1}, \quad (5.4.15)$

这六个系数如下：

$a_j = (1 - \Theta_m)\frac{\Delta t}{2}\{(r-q)j - \sigma^2 j\}, \quad (5.4.16)$
$b_j = 1 + (1 - \Theta_m)\frac{\Delta t}{2}\{r + \sigma^2 j\}, \quad (5.4.17)$
$c_j = -(1 - \Theta_m)\frac{\Delta t}{2}\{(r-q)j + \sigma^2 j\}, \quad (5.4.18)$
$\tilde{a}_j = -\Theta_m\frac{\Delta t}{2}\{(r-q)j - \sigma^2 j\}, \quad (5.4.19)$
$\tilde{b}_j = \Theta_m\frac{\Delta t}{2}\{r + \sigma^2 j\}, \quad (5.4.20)$
$\tilde{c}_j = \Theta_m\frac{\Delta t}{2}\{(r-q)j + \sigma^2 j\}, \quad (5.4.21)$

## 欧式期权的网格方法 | 5.4.3 节

对于每个 $j$ 值，方程 (5.4.14) 为我们提供了时间索引 $i+1$ 处的三个期权值 $f_{i+1,j-1}, f_{i+1,j}$ 和 $f_{i+1,j+1}$ 与时间索引 $i$ 处的三个期权值 $f_{i,j-1}, f_{i,j}$ 和 $f_{i,j+1}$ 之间的关系。

这种情况在图 5.5 中所示，我们标记了对期权值 $f_{5,5}$ 有贡献的网格节点：
- A：$f_{6,6}$
- B B：$f_{6,5}$
- C：$f_{6,4}$
- D：$f_{5,3}$
- E ：$f_{5,5}$
- F：$f_{5,4}$

在求解方程 (5.4.14) 之前，我们将简要考虑不同权重参数 $\Theta_m$ 的特性。当 $\Theta_m = 1$ 时，方程 (5.4.14) 中的系数值为 $a_j = c_j$ 且 $b_j = 1$。这意味着方程 (5.4.14) 简化：

$f_{i,j} = a_j f_{i+1,j-1} + b_j f_{i+1,j} + c_j f_{i+1,j+1}$。

这被称为**显式方法**，可以看到节点 $(i,j)$ 处的未知值 $f_{i,j}$ 仅仅是已知期权值 $f_{i+1,j-1}, f_{i+1,j}$ 和 $f_{i+1,j+1}$ 的加权和。这是最简单的情况，实际上对应于三叉网格；然而它需要非常小的步长才能获得结果。

当 $\Theta_m < 1$ 时，未知值 $f_{i,j}$ 不仅依赖于已知期权值 $f_{i+1,j-1}, f_{i+1,j}$ 和 $f_{i+1,j+1}$（如上述显式方法），还依赖于相邻值 $f_{i,j-1}$ 和 $f_{i,j+1}$。现在需要求解一组方程来计算 $f_{i,j}$。因此被称为**隐式方法**。

隐式方法 $\Theta_m = 0$ 也是全隐式方法，因为值 $f_{i,j}$ 只依赖于相邻值 $f_{i,j-1}, f_{i,j+1}$ 和之前的值 $f_{i,j}$。这可以通过在方程 (5.4.16) 中代入 $\Theta_m = 0$ 来证明，此时 $\tilde{a}_j = \tilde{c}_j$ 且 $\tilde{b}_j = 1$，这意味着方程 (5.4.14) 简化为：

$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i,j+1} = f_{i+1,j}$。

隐式方法 $\Theta_m = 0.5$ 也是 Crank-Nicolson 方法（由 John Crank 和 Phyllis Nicholson 在 1946 年提出），它通过赋予时间步长 $i+1$ 和时间步长 $i$ 相等的权重来计算 $f_{i,j}$。在方程 (5.4.16) 中代入 $\Theta_m = 0.5$，得到 Crank-Nicolson 系数：

$a_j - \tilde{a}_j = \frac{\Delta t}{4}\{(r-q)j - \sigma^2 j\}$,
$\tilde{b}_j = 1 + \frac{\Delta t}{2}\{r + \sigma^2 j\}$,
$\tilde{c}_j = 1 - \frac{\Delta t}{4}\{ r + \sigma^2 j\}$,
$c_j = -\tilde{c}_j = -\frac{\Delta t}{4}\{(r-q)j + \sigma^2 j \}$

## 136 章 | 5 单一资产美式期权

我们注意到，由于我们是在反向求解但在向前方向上是隐式的，我们对应隐式和显式的 $\Theta_m$ 值与通常使用的不同。例如，在 Smith (1985) 中，$\Theta_m = 0$ 是显式方法而 $\Theta_m = 1$ 是隐式方法；Crank-Nicolson 方法为 $\Theta_m = 0.5$。

## 边界条件

为了在时刻 $j\Delta t$ 处求解 (5.4.14)，我们需要获得上边界、下边界以及期权到期时指定的初始值。在这里，我们使用网格内第 $j$ 个资产索引处的无无关收益 $p_j$ 计算边界值。如果 $E$ 是行权价，那么欧式看涨期权的收益为：

$p_j = \max(j\Delta S - E), \quad j = 0, \dots, n_s-1$

欧式看跌期权的收益为：

$p_j = \max(E - j\Delta S), \quad j = 0, \dots, n_s-1$

**上边界**
在上边界，$j = n_s - 1$ 且 $(n_s - 1)\Delta S = S_{max}$，我们注意到为了网格有用，我们需要 $S_{max} > E$。在这里，我们观察到 $S_{max} > E$，因此看涨期权：

$p_{n_s-1} = S_{max} - E$，

对于看跌期权，$p_{n_s-1} = 0$。

上边界期权值标记为 $f_{BU}$设置为 $p_{n_s-1}$，有 $f_{i,n_s-1}=f_{BU}, i = 0, \dots, n_t$。

**下边界**
在下边界，$j = 0$ 且 $j\Delta S$ 的值为零。所以看涨期权 $p_0 = 0$，对于看跌期权，下边界期权值标记为 $f_{BL}$设置为 $p_0$，有 $f_{i,0}=f_{BL}, i = 0, \dots, n_t$。

**期权到期时的边界值**
在期权到期时（$i = n_t$），初始期权（边界）值为前述值。如果 $E$ 是行权价，那么欧式看涨期权的 $f_{n_t,j} = \max(j\Delta S - E), \quad j = 0, \dots, n_s-1$，对于欧式看跌期权，$f_{n_t,j} = \max(E - j\Delta S), \quad j = 0, \dots, n_s-1$。这在图 5.5 中展示了对于看跌期权，在到期时，期权值 $f_{n_t,j}$ 为 0，且时间索引 $i \Delta t$。

## 在给定时刻的期权值计算

