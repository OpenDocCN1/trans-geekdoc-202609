

# 单资产美式期权

```
jj = 2;
for (ml = 2; ml >= 1; --ml) {
  ind = M-ml;
  for (n = 0; n < N; ++n) {
    hold = P*v[5-jj-1] + p_u*v[5-jj];
    if (is_american) {
      if (put)
        v[5-jj] = MAX(hold,s[ind]);
      } else
        v[5-jj] = MAX(hold,s[ind]-X);
      }
    } else {
      v[5-jj] = hold;
      --jj;
      ind = ind + 2;
    }
  }
  *value = v[5];
```

**代码片段 5.9** 该代码片段展示了如何存储前两个时间步的期权值，以便在根节点 R 附近计算希腊字母（Greeks）。

| 节点 | 时间步 | 资产数组元素 | 资产价值 | 期权数组元素 |
|---|---|---|---|---|
| R | 0 | s [M] | S | v[5] |
| S | 1 | s [M+1] | Su | v[4] |
| T | 1 | s [M-1] | Sd | v[3] |
| U | 2 | s [M+2] | Su² | v[2] |
| V | 2 | s [M] | S | v[1] |
| W | 2 | s [M-2] | Sd² | v[0] |

**表 5.4** 根节点 R 附近的格节点

# 计算希腊字母：$\Delta$、$\Gamma$ 和 $\Theta$

现在我们将描述如何计算期权的对冲统计量（希腊字母）。设格节点 $k$ 处的期权值和资产价值分别为 $f_k$ 和 $S_k$。例如，$S_T$ 代表节点 $T$ 的资产价格，$f_T$ 是节点 $T$ 对应的期权值。表 5.4 提供了根节点 R 附近格节点的详细信息。现在考虑每个希腊字母的计算。

# Delta

$\Delta$ 的定义是在其他所有参数保持不变的情况下，期权值随资产价格变化的变化率。因此：

> $\Delta = \frac{\partial f}{\partial S} = \frac{\Delta f}{\Delta S}$

其中 $\Delta f$ 是对应于资产价格 $S$ 变化的数值。理想情况下，我们希望在根节点 R (ml=0) 处评估此偏导数；但我们无法这样做，因为至少需要两个格节点来计算。我们能做的是在第一个时间步 (ml=1) 如下评估导数：

> $\Delta = \frac{f_S - f_T}{S_S - S_T} = \frac{v[4] - v[3]}{s[M+1] - s[M-1]}$

# Gamma

$\Gamma$ 的定义是在其他所有参数保持不变的情况下，$\Delta$ 随资产价格变化的变化率。因此：

```
$$\Gamma = \frac{\partial^2 f}{\partial S^2} = \frac{\partial \Delta}{\partial S}$$
```

为了评估 $L^*$，我们需要至少两个 $\Delta$ 值。离根节点 R 最近的情况是在第 2 步，此时我们：

```
$$\Gamma = \frac{\Delta^*_{UV} - \Delta^*_{VW}}{S^*_{UV} - S^*_{VW}}$$
```

其中中点为：

```
$S^*_{UV} = \frac{1}{2}\{S_U + S_V\}$
```

中点 $S^*_{UV}$ 和 $S^*_{VW}$ 处的 $\Delta$ 值分别表示为 $\Delta^*_{UV}$ 和 $\Delta^*_{VW}$。由于：

```
$$\Delta^*_{UV} = \frac{f_U - f_V}{S_U - S_V}$$
```

```
$$\Delta^*_{VW} = \frac{f_V - f_W}{S_V - S_W}$$
```

以及

```
$S^*_{UV} = \frac{1}{2}\{S_U - S_W\}$
```

我们得到：

```
$$\Delta^*_{UV} = \frac{v[2] - v[1]}{s[M+2] - s[M]}$$
```

```
$$\Delta^*_{VW} = \frac{v[1] - v[0]}{s[M] - s[M-2]}$$
```

因此，$\Gamma$ 的值可以近似为：

```
$$\Gamma = \frac{2(\Delta^*_{UV} - \Delta^*_{VW})}{s[M+2] - s[M-2]}
```

# Theta

$\Theta$ 的定义是在其他所有参数保持不变的情况下，期权值随时间变化的变化率。因此：

```
$$\Theta = \frac{\partial f}{\partial t} = \frac{\Delta f}{\Delta t}$$
```

离根节点 最近的是使用第 0 步到第 2 步的时间间隔计算的。我们得到以下近似值：

```
$$\Theta = \frac{f_V - f_R}{2\Delta t} = \frac{v[1] - v[5]}{2\Delta t}$$
```

# 单美式期权

代码片段 5.10 使用我们刚刚讨论的近似方法计算 $\Delta$、$\Gamma$ 和 $\Theta$。

# Vega
$\mathcal{V}$ 的定义是期权值随波动率变化的变化率：

```
$$\mathcal{V} = \frac{\partial f}{\partial\sigma}$$
```

在二项链格中，无法直接计算 $\mathcal{V}$。一种简单的方法是使用两个二项链格：

```
$$\mathcal{V} = \frac{f_{\sigma+\Delta\sigma} - f_{\sigma}}{\Delta\sigma}$$
```

其中 $f_{\sigma+\Delta\sigma}$ 是使用波动率为 $\sigma+\Delta\sigma$ 的二项链格计算的期权值，$f_{\sigma}$ 是使用另一个波动率为 $\sigma$ 的二项链格计算的期权值；所有其他格参数保持不变。

美式期权的隐含波动率可以使用 5.4.4 节中用于欧式期权的方法计算；但在情况下，值和希腊字母是通过二项链格计算的（参见代码片段 5.11）。

```
// 分配 delta 的值（从 ml=1 获取）/
ge[1] = (v[4]-v[2])/(s[M]-s[1])
// 分配 gamma 的值（使用步长 ml=2 的时间）/
dv1 = v[2]-v[1]
dv2 = v[1]-v[0]
h = s[M-1]-s[M-2]
greeks[0] = ((dv1/ds1) - (dv2/ds2))
// 分配 theta 的值 /
也可以这样写：greeks[2] = (v[1]-v[5])/(2.0*dt);
Greeks[2] = (v[1]-value)/(2.0*dt)
```

格节点 r 附近的希腊字母 Gamma 和 Theta 的值。

```
void standard_lattice(double value, double Greeks[], double s0,
    double x, double sigma, double t, double r,
    double q, long put, long is_american, long M, long iflag {
    // 输入参数：
    s0          = 标的资产的当前价格
    x           = 行权价
    sigma       = 波动率
    t           = 到期时间
    r           = 利率
    q           = 利率
    put         = 1 为看跌期权，0 为看涨期权
    is_american = 1 为美式，0 为欧式
    M           = 步数
    // 输出参数：
    value       = 期权价值
    Greeks[]    = delta, gamma, 和 theta
    iflag       = 指示符
```

