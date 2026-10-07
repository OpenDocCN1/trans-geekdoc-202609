
$$rf_{i,j} = r \{\Theta_m f_{i+1,j} + (1 - \Theta_m) f_{i,j}\}$$

并且方程 `(5.4.1)` 中的项 $\frac{\partial f}{\partial S}_{i,j}$ 近似于：

$$\frac{\partial f}{\partial S}_{i,j} = \{\Theta_m \frac{\partial f}{\partial S}_{i+1,j} + (1 - \Theta_m) \frac{\partial f}{\partial S}_{i,j}\}$$

使用这种方法，我们在节点 $(i, j)$ 处得到方程 `(5.4.1)` 的以下离散化版本：

$$\frac{f_{i+1,j} - f_{i,j}}{\Delta t} + (r - q)S_j \{\Theta_m^* f_{i+1,j} + \Theta_m^* f_{i,j}\}$$

$$\frac{1}{2}\sigma^2S_j^2 \{\Theta_m^* f_{i+1,j} + \Theta_m^* f_{i,j}\} = r \{\Theta_m f_{i+1,j} + \Theta_m^* f_{i,j}\} (5.4.7)$$

其中为了紧凑，我们写了 $\Theta_m^* = 1 - \Theta_m$，并将节点 $(i, j)$ 处对 $S$ 的偏导记为 $f'_{i,j} = \frac{\partial f}{\partial S}_{i,j}$ 和 $f''_{i,j} = \frac{\partial^2 f}{\partial S^2}_{i,j}$。

通过将方程 `(5.4.10)` 和方程 `(5.4.11)` 给出的一阶和二阶导数近似代入方程 `(5.4.7)`，可以找到 Black-Scholes 方程的完整有限差分近似。我们得到：

$$r\Delta t \Theta_m f_{i+1,j} + \Theta_m^* f_{i,j} = f_{i,j+1} - f_{i,j} - \frac{(r-q)S_j\Delta t}{2} + \frac{\sigma^2 S_j^2 \Delta t^2}{2}, (5.4.12)$$

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

由于我们是在反向求解该方程，并且想要根据时间索引 $i+1$ 处的已知期权值 $(f_{i+1,j+1}, f_{i+1,j}$ 和 $f_{i+1,j-1})$ 来确定时间索引 $i$ 处的期权值。这可以通过如下重组方程 `(5.4.13)` 来：

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

对于每个 $j$ 值，方程 `(5.4.14)` 为我们提供了时间索引 $i+1$ 处的三个期权值 $f_{i+1,j-1}, f_{i+1,j}$ 和 $f_{i+1,j+1}$ 与时间索引 $i$ 处的三个期权值 $f_{i,j-1}, f_{i,j}$ 和 $f_{i,j+1}$ 之间的关系。

这种情况在图 5.5 中所示，我们标记了对期权值 $f_{5,5}$ 有贡献的网格节点：

- A：$f_{6,6}$
- B B：$f_{6,5}$
- C：$f_{6,4}$
- D：$f_{5,3}$
- E ：$f_{5,5}$
- F：$f_{5,4}$

在求解方程 `(5.4.14)` 之前，我们将简要考虑不同权重参数 $\Theta_m$ 的特性。当 $\Theta_m = 1$ 时，方程 `(5.4.14)` 中的系数值为 $a_j = c_j$ 且 $b_j = 1$。这意味着方程 `(5.4.14)` 简化：

$f_{i,j} = a_j f_{i+1,j-1} + b_j f_{i+1,j} + c_j f_{i+1,j+1}$。

这被称为**显式方法**，可以看到节点 $(i,j)$ 处的未知值 $f_{i,j}$ 仅仅是已知期权值 $f_{i+1,j-1}, f_{i+1,j}$ 和 $f_{i+1,j+1}$ 的加权和。这是最简单的情况，实际上对应于三叉网格；然而它需要非常小的步长才能获得结果。

当 $\Theta_m < 1$ 时，未知值 $f_{i,j}$ 不仅依赖于已知期权值 $f_{i+1,j-1}, f_{i+1,j}$ 和 $f_{i+1,j+1}$（如上述显式方法），还依赖于相邻值 $f_{i,j-1}$ 和 $f_{i,j+1}$。现在需要求解一组方程来计算 $f_{i,j}$。因此被称为**隐式方法**。

隐式方法 $\Theta_m = 0$ 也是全隐式方法，因为值 $f_{i,j}$ 只依赖于相邻值 $f_{i,j-1}, f_{i,j+1}$ 和之前的值 $f_{i,j}$。这可以通过在方程 `(5.4.16)` 中代入 $\Theta_m = 0$ 来证明，此时 $\tilde{a}_j = \tilde{c}_j$ 且 $\tilde{b}_j = 1$，这意味着方程 `(5.4.14)` 简化为：

$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i,j+1} = f_{i+1,j}$。

隐式方法 $\Theta_m = 0.5$ 也是 Crank-Nicolson 方法（由 John Crank 和 Phyllis Nicholson 在 1946 年提出），它通过赋予时间步长 $i+1$ 和时间步长 $i$ 相等的权重来计算 $f_{i,j}$。在方程 `(5.4.16)` 中代入 $\Theta_m = 0.5$，得到 Crank-Nicolson 系数：

$a_j - \tilde{a}_j = \frac{\Delta t}{4}\{(r-q)j - \sigma^2 j\}$,

$\tilde{b}_j = 1 + \frac{\Delta t}{2}\{r + \sigma^2 j\}$,

$\tilde{c}_j = 1 - \frac{\Delta t}{4}\{ r + \sigma^2 j\}$,

$c_j = -\tilde{c}_j = -\frac{\Delta t}{4}\{(r-q)j + \sigma^2 j \}$

## 136 章 | 5 单一资产美式期权

我们注意到，由于我们是在反向求解但在向前方向上是隐式的，我们对应隐式和显式的 $\Theta_m$ 值与通常使用的不同。例如，在 Smith (1985) 中，$\Theta_m = 0$ 是显式方法而 $\Theta_m = 1$ 是隐式方法；Crank-Nicolson 方法为 $\Theta_m = 0.5$。

### 边界条件

为了在时刻 $j\Delta t$ 处求解 `(5.4.14)`，我们需要获得上边界、下边界以及期权到期时指定的初始值。在这里，我们使用网格内第 $j$ 个资产索引处的无无关收益 $p_j$ 计算边界值。如果 $E$ 是行权价，那么欧式看涨期权的收益为：

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

# 第138 章 | 5 单资产美美式期权

```
$R_{i+1,n_{s-2}} = \tilde{a}_{n_{s-2}}f_{i,n_{s-3}} + b_{n_{s-2}}f_{i+1,n_{s-2}} + (\tilde{c}_{n_{s-2}} - c_{n_{s-2}})fBU \quad (5.4.25)$
```

### 情况 3

在这种情况下，边界值不进入表达式，我们简单地将方程 `(5.4.144)` 等于：

```
$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i+1,j+1} = R_{i+1,j}, \quad j = 3, \dots, n_{s-3}, \quad (5.4.26)$
```

其中右侧 $R_{i+1,j}$ 为：

```
$R_{i+1,j} = \tilde{a}_j f_{i,j-1} + b_j f_{i,j} + \tilde{c}_j f_{i+1,j+1}. \quad (5.4.27)$
```

现在我们可以提取方程 `(5.4.23)` `(5.4.27)` 中的所有信息，并将其表示为以下三对角方程：

```
$$\begin{pmatrix} b_1 & c_1 & 0 & 0 & 0 & f_{i,1} \\ a_2 & b_2 & c_2 & 0 & 0 & f_{i,2} \\ 0 & 0 & \cdot & 0 & 0 & \cdot \\ 0 & 0 & 0 & \cdot & 0 & \cdot \\ 0 & 0 & a_{n_{s-3}} & b_{n_{s-3}} & c_{n_{s-3}} & f_{i,n_{s-3}} & R_{i+1,n_{s-3}} \\ 0 & 0 & 0 & a_{n_{s-2}} & b_{n_{s-2}} & f_{i,n_{s-2}} & R_{i+1,n_{s-2}} \end{pmatrix} = \dots \quad (5.4.28)$$
```

用矩阵表示法，方程 `(5.4.28)` 可以写为：

```
$AX = R, \quad (5.4.29)$
```

其中 $A$ 是一个 $n_{s-2} \times n_{s-2}$ 的三对角矩阵，包含已知系数 $a_j, j = 2, \dots, n_{s-2}, b_{j,j} = 1, \dots, n_{s-2},$ 以及 $c_{j,j} = 1, \dots, n_{s-3}$。向量 $R$ 代表已知的右侧 $R_{i+1,j} = 1, \dots, n_{s-2}$，向量 $x$ 包含我们想要计算的期权值 $f_{i,j} = 1, \dots, n_{s-2}$。

众周知，如果矩阵 $A$ 是“非奇异的”，则方程 `(5.4.29)` 可以使用 LU 分解求解，即我们将 $n \times n$ 矩阵 $A$ 分解为：

```
$A = LU,$
```

其中 $L$ 是一个对角线元素为 1 的 $n \times n$ 下三角矩阵，$U$ 是一个 $n \times p$ 的上三角矩阵。以下是 $4 \times 4$ 矩阵的 LU 分解：

```
$$\begin{pmatrix} a_{1,1} & a_{1,2} & a_{1,3} & a_{1,4} \\ a_{2,1} & a_{2,2} & a_{2,3} & a_{2,4} \\ a_{3,1} & a_{3,2} & a_{3,3} & a_{3,4} \\ a_{4,1} & a_{4,2} & a_{4,3} & a_{4,4} \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 & 0 \\ l_{2,1} & 1 & 0 & 0 \\ l_{3,1} & l_{3,2} & 1 & 0 \\ l_{4,1} & l_{4,2} & l_{4,3} & 1 \end{pmatrix} \begin{pmatrix} u_{1,1} & u_{1,2} & u_{1,3} & u_{1,4} \\ 0 & u_{2,2} & u_{2,3} & u_{2,4} \\ 0 & 0 & u_{3,3} & u_{3,4} \\ 0 & 0 & 0 & u_{4,4} \end{pmatrix} \quad (5.4.30)$$
```

## 欧式期权网格法章节 | 5.4

如果 A 是三对角矩阵，则 LU 分解具有更简单的形式：

```
\begin{pmatrix} a_{1,1} & a_{1,2} & 0 & 1 & 0 & 0 & u_{1,1} & 2 & 0 \\ a_{2,1} & a_{2,2} & a_{2,3} & 0 & l_{2,1} & 1 & 0 & 0 & u_{2,2} & u_{2,3} & 0 \\ 0 & a_{3,2} & a_{3,3} & a_{3,4} & 0 & l_{3,2} & 1 & 0 & 0 & u_{3,3} & u_{3,4} \\ 0 & 0 & a_{4,3} & a_{4,4} & 0 & 0 & l_{4,3} & 1 & u_{4,4} \end{pmatrix} = (5.4.31)
```

可以看到 L 和 U 是双三角的。一旦找到 A 的分解，就可以使用两阶段方法(例如 Golub 和 Loan (1989))求解方程 `(5.4.29)` 中的 $x$。这里使用前向消元求解 $Ly = R$，并回代求解 $Ux = y$。我们可以将过程写为：

```
Ax = (LU)x = Ly.
```
