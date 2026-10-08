

# 单资产美式期权

为了简洁起见，我们写下 $\Theta_m = 1-\Theta_m^*$，并将节点 $(i, j)$ 处关于 $S$ 的偏阶导数记为：$f_{i,j}' = \frac{af}{S}l_{i,j}$ 和 $f_{i,j}'' = \frac{af^2}{S^2}l_{i,j}$。

这些偏导数的有限差分近似可以通过考虑关于点 $f_{i,j}$ 的泰勒展开来获得。处理步骤如下：

```
$f_{i,j}+1 = f_{i,j} + f_{i,j}'\Delta S + \frac{1}{2}f_{i,j}''(\Delta S)^2 $\quad (5.4.8)
```

```
$f_{i,j}-1 = f_{i,j} - f_{i,j}'\Delta S + \frac{1}{2}f_{i,j}''(\Delta S)^2 $\quad (5.4.9)
```

从等式 (5.4.8) 减去等式 (5.4.9)，得到：

```
$f_{i,j}+1 - f_{i,j}-1 = 2f_{i,j}'\Delta S$
```

以及：

```
$f_{i,j}'' = \frac{f_{i,j}+1 - f_{i,j}-1}{2\Delta S}$ $\quad (5.4.10)
```

将等式 (5.4.9) 和 (5.4.8) 相加得到：

```
$f_{i,j}+1 + f_{i,j}-1 = 2f_{i,j}' + f_{i,j}''\Delta S^2$
```

得出：

```
$f_{i,j}'' = \frac{f_{i,j}+1 - 2f_{i,j} + f_{i,j}-1}{\Delta S^2}$ $\quad (5.4.11)
```

在给定等式 (5.4.10) 和 (5.4.11) 的情况下，将一阶和二阶偏阶导数的近似值代入 (5.4.7)，即可找到完整的有限差分方程。我们得到：

```
$r\Delta t{\{\Theta_m f_{i,j}+1 + \Theta_m^* f_{i,j}\} = f_{i,j}-1 - f_{i,j} + \frac{(r-q)j\Delta t.A_1}{2} + \frac{\sigma^2j^2\Delta t.A_2}{2}$ $\quad (5.4.12)
```

其中我们使用了 $S_j = j\Delta S$ 这一，并为了简洁定义了项：

```
$A_1 = \Theta_m f_{i,j}+1 - \Theta_m f_{i,j}-1 + \Theta_m^* f_{i,j}+1 - \Theta_m^* f_{i,j}-1$
```

以及：

```
$A_2 = \Theta_m f_{i,j}+1 + \Theta_m f_{i,j}-1 - 2\Theta_m f_{i,j}+1 + \Theta_m^* f_{i,j}+1 + \Theta_m^* f_{i,j}-1 - 2\Theta_m^* f_{i,j}$
```

合并关于 $f_{i,j}, f_{i,j}^*$ 等的同类项，得到：

```
$B_1 f_{i,j}+1 + B_2 f_{i,j} + B_3 f_{i,j}+1 + C_1 f_{i,j}-1 + C_2 f_{i,j}+1 + C_3 f_{i,j}+1 = 0$ $\quad (5.4.13)
```

其中：

```
$B_1 = \frac{\Theta_m^*(r-q)j\Delta t}{2} + \frac{\Theta_m^*\sigma^2 j^2\Delta t}{2}$
$B_2 = -1-r\Delta t\Theta_m^*-\Theta_m^*\sigma^2 j^2$
$B_3 = \frac{\Theta_m^*(r-q)j\Delta t}{2} + \frac{\Theta_m^*\sigma^2 j^2\Delta t}{2}$
$C_1 = \frac{\Theta_m\sigma^2 j^2\Delta t}{2} + \frac{\Theta_m(r-q)j\Delta t}{2}$
$C_2 = 1-r\Delta t\Theta_m-\Theta_m\sigma^2 j^2$
$C_3 = \frac{\Theta_m(r-q)j\Delta t}{2} + \frac{\Theta_m^*\sigma^2 j^2\Delta t}{2}$
```

由于我们是在反向时间求解方程，并且根据时间索引 $i+1$ 处的已知期权值 $(f_{i+1,j+1}, f_{i+1,j}$ 和 $f_{i+1,j-1})$ 来确定时间索引 $i$ 处的期权值。这可以通过如下重组等式 (5.4.13) 来实现：

```
$a_j f_{i,j-1}+b_j f_{i,j}+c_j f_{i,j+1}=R_{i+1,j}$
```

其中右侧 $R_{i+1,j}$ 为：

```
$R_{i+1,j}=\tilde{a}_j f_{i+1,j-1}+\tilde{b}_j f_{i+1,j}+\tilde{c}_j f_{i+1,j+1}$
```

六个系数为：

```
$a_j=(1-\Theta_m)\frac{\Delta t}{2}\{(r-q)j-\sigma^2 j\}$
$b_j=(1-\Theta_m)\Delta t\{r+\sigma^2 j\}$
$c_j=(1-\Theta_m)\frac{\Delta t}{2}\{(r-q)j+\sigma^2 j\}$
$a_j=-\Theta_m\frac{\Delta t}{2}\{(r-q)j\}$
$b_j=1-\Theta_m\Delta t\{r+\sigma^2 j\}$
$c_j=\Theta_m\frac{\Delta t}{2}\{(r-q)j+\sigma^2 j\}$ （此处原文公式重复）
```

这种情况如图 5.5 所示，其中我们标记了对期权值 $f_{5,5}$ 有贡献的节点。这些已知值为：

- 节点 A：$f_{6,6}$
- 节点 B：$f_{6,5}$
- 节点 C：$f_{6,4}$

以及未知期权值：

- 节点 D：$f_{5,6}$
- 节点 E：$f_{5,5}$
- 节点 F：$f_{5,4}$

在求解等式 (5.4.14) 之前，我们将简要考虑权重参数 $\Theta_m$ 的不同值。当 $\Theta_m=1$ 时，等式 (5.4.14) 中的系数值为 $a_j=c_j=0$ 且 $b_j=1$。这意味着等式 (5.4.14) 变为：

```
$f_{i,j} = \tilde{a}_j f_{i+1,j-1} + b_j f_{i+1,j} + \tilde{c}_j f_{i+1,j+1}$
```

这是**显式方法**，可以看到网格 $(i,j)$ 处的未知期权值 $f_{i,j}$ 是已知期权值 $f_{i+1,j-1}, f_{i+1,j}, f_{i+1,j+1}$ 的加权和。这是最简单的情况，但数值性质较差，需要非常小的步长才能获得准确结果；见 Smith (1985)。

当 $\Theta_m \neq 1$ 时，未知期权值 $f_{i,j}$ 不取决于已知值 $f_{i+1,j-1}, f_{i+1,j}, f_{i+1,j+1}$（如显式方法所示），还取决于未知期权值 $f_{i+1,j-1}$ 和 $f_{i+1,j+1}$。现在需要求解方程组来计算值 $f_{i,j}$。因此这被称为**隐式方法**；见 Smith (1985)。

隐式 $\Theta_m=0$ 也称为**全隐式方法**，因为新的未知值 $f_{i,j}$ 仅取决于时间步 $i+1$ 处的邻值 $f_{i+1,j-1}, f_{i+1,j+1}$。这可以通过代入 $\tilde{a}_j = \tilde{c}_j$ 且 $b_j=1$ 得到，这意味着等式 (5.4.14) 变为：

```
$a_j f_{i,j-1} + b_j f_{i,j} + c_j f_{i,j+1} = f_{i+1,j}$
```

隐式 $\Theta_m=0.5$ 也称为 **Crank-Nicolson 方法**。该方法由 John 和 Nicolson (1947) 首次使用，通过给时间步 $i+1$ 和时间步 $i$ 的贡献赋予相同的权重来计算 $f_{i,j}$。将 $\Theta_m = 0.5$ 代入等式 (5.4.16) 到 (5.4.21)，我们得到 Crank-Nicolson 系数：

```
$a_j = -\frac{\Delta t}{4}\{(r-q)j - \sigma^2 j^2\}$
$b_j = 1 + \frac{\Delta t}{2}\{r + \sigma^2 j^2\}$
$\tilde{b}_j = 1 - \frac{\Delta t}{2}\{r + \sigma^2 j^2\}$
$c_j = -\tilde{c}_j = \frac{\Delta t}{4}\{(r-q)j + \sigma^2 j^2\}$
```

我们注意到我们是在反向求解，但时间索引是正向的，我们对应隐式和显式的 $\Theta_m$ 值与通常使用的不同。例如，在 Smith (1985) 中，$\Theta_m=0$ 是显式方法，$\Theta_m=1$ 是隐式方法；Crank-Nicolson 方法仍然是 $\Theta_m=0.5$。

