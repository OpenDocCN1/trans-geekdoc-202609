

# 基础期权与 Black–Scholes 模型  | 4.4

包含连续分红的欧式看涨期权的 Black–Scholes 公式如下：

```
$c(S,E,\tau) = S\exp(-q\tau)N_1(d_1) - E\exp(-r\tau)N_1(d_2),$
```

对应的看跌期权公式（使用看跌平价公式）可以表示：

```
$p(S,E,\tau) = -S\exp(-q\tau)N_1(-d_1) + E\exp(-r\tau)N_1(-d_2),$
```

或者等价于 $N_1(-x) = 1 - N_1(x)$，我们有：

```
$p(S,E,\tau) = E\exp(-r\tau)\{1 - N_1(d_2)\} - S\exp(-q\tau)\{1 - N_1(d_1)\},$
```

其中：

```
$d_1 = \frac{\log(S/E) + (r-q+\sigma^2/2)\tau}{\sigma\sqrt{\tau}}, \quad d_2 = \frac{\log(S/E) + (r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

因此，具有连续分红的欧式看跌/看涨期权可以使用方程 (4.4.47) 和 (4.4.50) 进行定价，并将 $S$ 替换为 $S\exp(-q\tau)$。

这些公式可以用到期值为 $T$ 的当前期货价格 $S(t,T)$ 重新表示：

```
$c_t = E\exp(-r(T-t))S(t,T)N_1(d_2) - EN_1(d_2),$
```

```
$p_t = E\exp(-r(T-t))\{-S(t,T)N_1(-d_1) - EN_1(-d_2)\},$
```

其中我们使用符号 $p_t$ 和 $c_t$ 表示看跌和看涨期权的当前 $(t)$ 价值，而到期值为 $T$ 的当前期货价格为：

```
$S(t,T) = S\exp((r-q)(T-t)), \quad t \le T$
```

以及

```
$d_1 = \frac{\log(S(t,T)/E) + (\sigma^2/2)(T-t)}{\sigma\sqrt{\tau}}, \quad d_2 = \frac{\log(S(t,T)/E) - (\sigma^2/2)(T-t)}{\sigma\sqrt{\tau}}$
```

# 离散分红的引入

在此，考虑在期权寿命内的 $n$ 个离散分红 $D_i,i=1,\dots,n$，分别对应时间点 $t_i=1,\dots,n$。在这种情况下，使用 Black–Scholes 公式为欧式期权定价，但当前资产价值通过现金分红的现值进行了。

这意味着我们使用的不是 $S$，而是使用数量 $S_D$，其计算方法为：

```
$S_D = S - \sum_{i=1}^{n} D_i\exp(-rt_i),$
```

其中 $r$ 是（在此情况下为常数的）利率。欧式看跌和看涨期权的公式为：

```
$c(S,E,\tau) = S_DN_1(d_1) - E\exp(-r\tau)N_1(d_2),$
```

```
$p(S,E,\tau) = E\exp(-r\tau)\{1 - N_1(d_2)\} - S_D\{1 - N_1(d_1)\},$
```

其中

$d_1 = \frac{\log(S_D/E) + (r + \sigma^2/2)\tau}{\sigma\sqrt{\tau}} \text{ and } d_2 = \frac{\log(S_D/E) + (r - \sigma^2/2)\tau}{\sigma\sqrt{\tau}} = d_1 - \sigma\sqrt{\tau}. (4.4.62)$

# 希腊字母 (The Greeks)

既然我们已经推导出了欧式基础看跌和看涨期权的定价公式，就可以计算它们的偏导数（对冲统计量）。现在我们只需列出欧式期权的希腊字母（对冲统计量）表达式。这里，下标 $c$ 指欧式看涨期权，下标 $p$ 指欧式看跌期权。这些结果的完全导数可以在附录 A 中找到。

# Gamma:

$$\Gamma_c = \frac{\partial^2 c}{\partial S^2} = \Gamma_p = \frac{\partial^2 p}{\partial S^2} = \exp(-q\tau)\frac{n(d_1)}{\sigma\sqrt{\tau}} (4.4.63)$$

# Delta:

$$\Delta_c = \frac{\partial c}{\partial S} = \exp(-q\tau)N_1(d_1), \Delta_p = \frac{\partial p}{\partial S} = \exp(-q\tau)\{N_1(d_2) - 1\}. (4.4.64)$$

# Theta:

$$\Theta_c = \frac{\partial c}{\partial t} = q\exp(-q\tau)N_1(d_1) - rE\exp(-r\tau)N_1(d_2) - \frac{Sn_1(d_2)\exp(-q\tau)}{2\sqrt{\tau}}$$
$$\Theta_p = \frac{\partial p}{\partial t} = -q\exp(-q\tau)N_1(d_1) + rE\exp(-r\tau)N_1(d_2) - \frac{Sn_1(d_2)\exp(-q\tau)}{2\sqrt{\tau}} (4.4.65)$$

# Rho,

$$\rho_c = \frac{\partial c}{\partial r} = EN_1(d_2), \rho_p = \frac{\partial p}{\partial r} = -EN_1(d_2). (4.4.66)$$

# Vega:

$$\nu_c = \frac{\partial c}{\partial \sigma} = \nu_p = \frac{\partial p}{\partial \sigma} = S\exp(-q\tau)n(d_1)\sqrt{\tau}, (4.4.67)$$

其中 $n(x) = \frac{1}{\sqrt{2\pi}}\exp(-x^2/2)$。Black-Scholes 期权价值和希腊字母在方程 (4.4.63) 到 (4.4.67) 中给出。我们使用 `EPS = 1e-6` 来识别参数是否过小，并使用 `cdf` 计算累积分布函数。

```c
void black_scholes(double value, double greeks[], double s0, double x) {
  double sigma, double t, double r, double q, long put; 
  // 输入参数:
  s0 - 资产当前价格
  x - 行权价
  sigma - 波动率
  t - 到期时间
  r - 利率
  put - 如果为看跌期权，否则为看涨期权
  // 输出参数:
  value - 期权价值
  greeks[0] - 对冲统计量如下：gamma
  greeks[1] - delta
  greeks[2] - theta
  greeks[3] - rho
  greeks[4] - vega
  flag - 错误指示
*/
```

计算欧式期权 Black–Scholes 价值的函数（代码示例 4.1 持续）。可以看出，看涨和看跌期权的 gamma 和 vega 值是相同的。当 $\tau=1.0$ 时，我们 $c(S,E,\tau) = 12.952$ 和 $p(S,E,\tau) = 9.260$。因此 $c(S,E,\tau) + E\exp(-q\tau) = 12.952 + 100\exp(-0.1) = 103.436$，且 $p(S,E,\tau) + S\exp(-q\tau) = 9.260 + 100\exp(-0.06) = 103.436$。

# 4.4 历史波动率与隐含波动率

在 Black-Scholes 公式中获取关键参数 $\sigma$ 的最佳估计非常重要。估计波动率的方法有很多种。现在我们同时考虑历史波动率和隐含波动率。

**表 4.1** 欧式看跌期权：价值与希腊字母。$S=100.0, E=100.0, r=0.10, q=0.06$。

| $\tau$ | 价值 | Delta | Gamma | Theta | Vega |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 0.100 | 3.558 | -0.462 | 0.042 | -16.533 | 12.490 |
| 0.200 | 4.879 | -0.444 | 0.029 | -10.851 | 17.487 |
| 0.300 | 5.824 | -0.431 | 0.024 | -8.298 | 21.204 |
| 0.400 | 6.571 | -0.419 | 0.020 | -6.758 | 24.241 |
| 0.500 | 7.191 | -0.408 | 0.018 | -5.698 | 26.832 |
| 0.600 | 7.720 | -0.399 | 0.016 | -5.296 | 29.100 |
| 0.700 | 8.179 | -0.390 | 0.015 | -4.292 | 31.118 |
| 0.800 | 8.582 | -0.381 | 0.014 | -3.792 | 32.935 |
| 0.900 | 8.940 | -0.373 | 0.013 | -3.377 | 34.585 |
| 1.000 | 9.260 | -0.366 | 0.012 | -3.025 | 36.093 |

**表 4.2** 欧式看涨期权：价值与希腊字母。$S=100.0, E=100.0, r=0.10, \sigma=0.30, q=0.06$。

| $\tau$ | 价值 | Delta | Gamma | Theta | Vega |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 0.100 | 3.955 | 0.532 | 0.042 | -20.469 | 12.490 |
| 0.200 | 5.667 | 0.544 | 0.029 | -14.724 | 17.487 |
| 0.300 | 6.996 | 0.552 | 0.024 | -12.109 | 21.204 |
| 0.400 | 8.121 | 0.558 | 0.020 | -10.508 | 24.241 |
| 0.500 | 9.113 | 0.562 | 0.018 | -9.387 | 26.832 |
| 0.600 | 10.007 | 0.566 | 0.016 | -8.539 | 29.100 |
| 0.700 | 10.826 | 0.565 | 0.015 | -7.863 | 31.118 |
| 0.800 | 11.584 | 0.572 | 0.014 | -7.305 | 32.935 |
| 0.900 | 12.290 | 0.574 | 0.013 | -6.832 | 34.585 |
| 1.000 | 12.952 | 0.576 | 0.012 | -6.422 | 36.093 |

# 历史波动率

在此方法中，我们使用 $n+1$ 个历史资产价格 $S_{i,i} = 0,\dots,n$ 来计算波动率，并假设资产价格是在常规的时间间隔 $dr$ 观测到的。由于资产价格假设遵循几何布朗运动（GBM），

