

# 欧式期权

因此，迭代过程为：

```
\sigma_{i+1} = \sigma_i - \frac{c(S, E, \tau, \sigma)}{\Gamma_c}
```

其中 $\sigma_0$ 是初始估计值$\sigma_{i+1}$ 是通过第 $i$ 次估计值 $\sigma_i$ 得到的隐含波动率改进估计值。当 $ABS(\sigma_{i+1} - \sigma_i) < tol$（指定的容差）时，迭代停止。

可以看出，当 $\sigma \to 0, d_1 \to \infty, d_2 \to \infty$ 时，根据公式 (4.4.67)，有 $V_c \to 0$。在这种情况下，牛顿法失效。

同样的方法可以计算欧式认跌权的隐含波动率，在这种情况下，我们只需要将 $c(S, E, \tau, \sigma)$ 替换为 $p(S, E, \tau, \sigma)$，即欧式认跌权的价值；根据公式 (4.4.67)，$V_c = V_p$。

如果需要美式期权的隐含波动率，该过程完全相同。然而，我们不再使用 Black-Scholes 公式来计算期权价值，而是使用二项树模型来实现。使用二项树计算期权价格和希腊字母（Greeks）的方法见第 5 节。

代码摘录 4.4 提供了一个示例测试程序，说明了 `implied_volatility` 的用法；结果如表 4.3 。

```cpp
double X, value, S[2], sigma, T, q;
long i, ifail;

ifail = 0;
S[0] = 10.0;
X = 10.5;
r = 0.3;
sigmat = 0.244;
q = 0.0;
printf("  %f option value implied volatility (Error%f)\n",
for(i = 0; i < 6; i++) {
    T = (double)i;
    black_scholes(value, NULL, S, sigma, T, q, &flag);
    sigma[0] = sigma;
    sigma[1] = 1.0;
    implied_volatility(value, S, X, sigma, r, q, &flag);
    printf("%.4f $15.4f (%.4f)\n", sigma[0], fabs(sigma-sigma[0]));
}
sigma = sigma + 0.1;
```

**代码摘录 4.4** 隐含波动率的示例测试程序。

**表 4.3** 从代码摘录 4.4 计算出的期权价值和隐含波动率

| 时间（年） | 期权价值 | 真值 $\sigma$ | 估计 $\sigma$ 的误差 |
|---|---|---|---|
| 0.5 | 0.1959 | 0.1 | 2.7756 $\times 10^{-16}$ |
| 1.0 | 0.8158 | 0.2 | 2.2204 $\times 10^{-16}$ |
| 1.5 | 1.5435 | 0.3 | 3.8858 $\times 10^{-16}$ |
| 2.0 | 2.3177 | 0.4 | 5.5511 $\times 10^{-17}$ |
| 2.5 | 3.1033 | 0.5 | 1.1102 $\times 10^{-16}$ |

## 4.4.5 使用 Microsoft Excel 为期权定价

在本节中，我们将展示如何使用 Excel 内部的 Visual Basic 基于 Black–Scholes 公式创建强大的衍生品定价应用。我们将解释如何使用 Excel 的 Visual Basic 创建一个应用程序，按下按钮即可为一组简单的欧式认跌权和认购权定价。

在 4.4.3 节中，我们推导了 Black–Scholes 公式：

```
$c(S, E, \tau) = SN_1(d_1) - e^{-r\tau}EN_1(d_2)$
```

以及

```
$p(S, E, \tau) = -SN_1(-d_1) + e^{-r\tau}EN_1(-d_2)$
```

其中

```
$d_1 = \frac{\log(S/E)(r + \sigma^2/2)\tau}{\sigma\sqrt{\tau}} = d_1 - \sigma\sqrt{\tau}$
```

$S$ 是资产的当前值，$\sigma$ 是资产的波动率，且 $N_1(x) = \frac{1}{\sqrt{2\pi}}\int_{-\infty}^x e^{-t^2/2}dx$。单变量标准正态分布 $N_1(x)$ 可以使用 Excel 内置的 NORMDIST 进行计算。该函数的定义如下：

```
NORMDIST(x, mean, standard_dev, cumulative)
```

该函数返回指定均值和标准差的正态累积分布。函数参数：

- x: 你想要分布的值。
- mean: 分布的算术平均值。
- standard_dev: 分布的标准差。
- cumulative: 决定函数形式逻辑值。如果为 TRUE，NORMDIST 返回累积分布函数；如果为 FALSE，则返回概率密度函数。

如果 mean = 0 且 standard_dev = 1，NORMDIST 返回标准正态分布。

该函数可以用于创建一个 Visual Basic 函数，在 Excel 内计算欧式期权价值，见代码 4.5。
一旦定义了函数，就可以通过 Excel 中的粘贴函数进行交互式访问，如图 4.1 所示。

函数 bs_opt 也可以整合到 Excel 中的其他 Visual Basic 代码中。代码摘录 4.6 定义了 Visual Basic 子程序 MANY_EUROPEANS_Click()。

## 欧式期权

```vb
Function bs_opt(S0 As Double,
ByVal X As Double, sigma As Double, T As Double,
r As Double, q As Double, ByVal putcall As Long) As Double
```

* 计算欧式认跌权或欧式认购权价值的 Visual Basic 程序。
* 作者：George Levy

```vb
Dim temp As Double
Dim d1 As Double
Dim d2 As Double
Dim value As Double
```

```vb
temp = Log (S0 / X) + (r - q + (sigma * sigma / 2)) * T
d1 = temp / (sigma * Sqrt (T))
d2 = d1 - sigma * Sqrt (T)
```

```vb
If (putcall = 0) Then ' 认购权
value = S0 * Exp(-q * T) * Worksheet.NormDist(d1, 0, True)
- Worksheet.NormDist(d2, 0, True) * X * Exp(-r * T)
```

```vb
Else ' 认跌权
value = -S0 * Exp(-q * T) * Worksheet.NormDist(-d1, 0, True) +
- X * Worksheet.NormDist(-d2, 0, True) * Exp(-r * T)
```

```vb
End If
End Function
```

```vb
bs_opt = value

# 代码 4.5 使用 Black-Scholes 公式为欧式期权定价的 Visual Basic 代码。![](img/603dc31da8bd8ca6afe29eaa_95_png)

图 4.1 在 Excel 中交互式使用函数 bs_opt。S = 10.0, X = 9.0, q = 0.0, T = 1.5, r = 0.1, 以及 sigma = 0.2。

# 使用 C# 进行计算金融计算

```vb
Private Sub MANY_EUROPEANS_Click()

Dim i As Long
Dim putcall As Long
Dim S As Double
Dim q As Double
Dim sigma As Double
Dim T As Double
Dim r As Double

```vb
q = 0
T = 1.5
sigma = 0.2

For i = 1 To 2

S = Sheet1.Cells(i + 1, 1).value
X = Sheet1.Cells(i + 1, 2).value
putcall = Sheet1.Cells(i + 1, 3).value
Sheet1.Cells(i + 1, 4).value = bs_opt(S, X, sigma, T, r, q, putcall)
Next

代码示例 4.6 Visual Basic 使用函数 bs_opt。(img/603dc31da8bd8ca6fe29eaa_96_png)

图 4.2 在 Excel 中交互式使用函数 bs_opt。S = 10.0, X = 9.0, q = 0.0, T = 1.5, r = 0.1, 以及 sigma = 0.2。

## 欧式期权

![](img/603dc31da8bd8ca6fe29eaa_97_0.png)

图 4.3 欧式期权。累积正态分布也可用于提供奇异期权（如 Lookback、Binary 等）的解析解。

## 4.5 障碍期权

障碍期权是收益取决于资产价格是否达到给定障碍的衍生品，如果资产价格达到障碍，则变得无效（停止）。

- **下触失效 (Down and out)**: 敲认购权，价值 $c_{do}$
- **上触失效 (Up and out)**: 敲认购权，价值 $c_{uo}$
- **下触生效 (Down and in)**: 触发认购权，价值 $c_{di}$
- **上触生效 (Up and in)**: 触发认购权，价值 $c_{ui}$

以下表达式成立：

## 4.5.2 下触失效期权的解析定价

如果我们考虑布朗运动（零漂移）$X_s \sim N(0, (s-t)\sigma^2)$，$t \le s \le T$，它始于 $X=0$ 并结束于点 $X$，那么（例如 Freedman, 1983），该运动在时间 $\tau = T-t$ 内不超过价值 $X=b$（$b > 0$）的概率密度函数为：

$$f(b \ge X_{max}^s, X) = \Omega \sqrt{\frac{2}{\pi}} \exp\left(-\frac{2b(X-b)}{\sigma^2\tau}\right)\exp\left(-\frac{X^2}{2\sigma^2\tau}\right) \quad (4.5.3)$$

其中为了方便，使用了 $\Omega = (2b-X)/(\sigma^3^{3/2})$，且 $X^{max}=max(X_s, t \le T)$。由于 $X_s$ 是没有漂移且波动率为 $\sigma$ 的布朗运动，$-X_s$ 是相同的布朗运动。因此，通过在方程中替换 $X \to -X$ 和 $b \to -b$，我们：

$$f(b \ge X_{min}^s, X) = \Omega \sqrt{\frac{2}{\pi}} \exp\left(-\frac{2b(X-b)}{\sigma^2\tau}\right)\exp\left(-\frac{X^2}{2\sigma^2\tau}\right) \quad (4.5.4)$$

其中我们使用了 $X_{min}^s=min(X_s, t \le T)$。方程 (4.5.4) 是 $-X_s$ 留在价值 $X=b$（$b<0$）之上的概率密度。这些结果可以推广到包含漂移（Musiela and Rutkowski, 1998, p. 212），通过 $N((r-q-\sigma^2/2)(s-t), \sigma(s-t))$，对于 $t \le s \le T$。

