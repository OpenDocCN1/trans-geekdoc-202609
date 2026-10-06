
## 欧式期权与布莱克-斯科尔斯模型章节 | 4.4 67

我们不再对 $S_T$ 进行积分，而是通过使用变量 $X = \log(S_T/S)$ 来对 (4.4.37) 进行求。从方程 (4.4.33) 中，我们知道 $X$ 的概率密度函数为：

```
$f(X) = \frac{1}{\sigma \sqrt{2\pi}} \exp \left( \frac{-(X - (r - \sigma^2/2)\tau)^2}{2\sigma^2\tau} \right). \quad (4.4.38)$
```

因此，期权的价值为：

```
$c(S, E, \tau) = \exp(-r\tau) \int_{\log(E/S)}^{\infty} {S\exp(X) - E} dX, \quad (4.4.39)$
```

其中我们使用了 $S = S\exp(X)$。(4.4.39) 中对应于方程 (4.4.37) 中 $S_T = E$ 的下限是通过令 $E = \exp(X)$ 得到的；这得出了下限 $X = \log(E/S)$。(4.4.39) 中的积分通过将其分为两部分来计算：

```
$c(S, E, \tau) = I_A - I_B. \quad (4.4.40)$
```

其中：

```
$I_A = \frac{S\exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \exp(X) \exp \left( \frac{\{X - (r - \sigma^2/2)\tau)^2}{2\sigma^2\tau} \right) dX. \quad (4.4.41)$
```

以及：

```
$I_B = \frac{E\exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \exp \left( \frac{\{X - (r - \sigma^2/2)\tau)^2}{2\sigma^2\tau} \right) dX. \quad (4.4.42)$
```

为了计算这些积分，我们将利用单变量累积正态分布函数 $N_1(x)$ 为：

```
$N_1(x) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{x} \exp \left( \frac{-u^2}{2} \right) du.$
```

根据对称性，我们有 $N_1(x) = 1 - N_1(-x)$ 以及：

```
$$\frac{1}{\sqrt{2\pi}} \int_{x}^{\infty} \exp \left( \frac{-u^2}{2} \right) du = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{-x} \exp \left( \frac{-u^2}{2} \right) du = N_1(-x).$$
```

我们首先考虑 $I_B$，它是两个积分中较的一个。

```
$I_B = \frac{E\exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \exp \left( \frac{\{X - (r - \sigma^2/2)\tau)^2}{2\sigma^2\tau} \right) dX.$
```

如果我们令 $u = \frac{X - (r - \sigma^2/2)\tau}{\sigma \sqrt{\tau}}$，则 $dX = \sigma \sqrt{\tau}$。

```
$I_B = \frac{E\exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{k_2}^{\infty} \exp \left( \frac{-u^2}{2} \right) du.$
```

其中积分下限为 $k_2 = [\log(E/S) - (r - \sigma^2/2)\tau]/\sigma \sqrt{\tau}$。

## 68 第 4 章 欧式期权

因此我们有：

$I_B = E \exp(-r\tau)N_1(-k_2). \quad (4.4.43)$

我们现在考虑积分 $I_A$：

```
$I_A = \frac{S \exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \exp(X) \exp\left( \frac{\{X - (r - \sigma^2/2)\tau)^2}{2\sigma^2\tau} \right) dX.
```

重排积函数：

```
$I_A = \frac{S \exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \exp\left( \frac{\{\{X - (r - \sigma^2/2)\tau)^2 - 2\sigma^2\tau X\}}{2\sigma^2\tau} \right) dX. \quad (4.4.44)$
```

展开指数项中的项：

```
$\{X - (r - \sigma^2/2)\tau)^2 - 2\sigma^2\tau X = X^2 - 2\{(r - \sigma^2/2)\tau X\} + \{(r - \sigma^2/2)\tau\}^2$,
$= \{X - (r - \sigma^2/2)\tau\}^2 + \{(r - \sigma^2/2)\tau\}^2 - \{(r + \sigma^2/2)\tau\}^2$,
```

结果为：

```
$\{X - (r - \sigma^2/2)\tau)^2 - 2\sigma^2\tau X = \{X - (r + \sigma^2/2)\tau\}^2 - 2\sigma^2\tau. \quad (4.4.45)$
```

将方程 (4.4.45) 代入方程的积函数中，我们有：

```
$\exp(X) \exp\left( \frac{\{X - (r + \sigma^2/2)\tau\}^2}{2\sigma^2\tau} \right) = \exp(r\tau) \exp\left( \frac{\{X - (r + \sigma^2/2)\tau\}^2}{2\sigma^2\tau} \right)$
```

积分 $I_A$ 可以表示为：

```
$I_A = \frac{S \exp(-r\tau) \exp(-r\tau)}{\sigma \sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \exp\left( \frac{\{X - (r + \sigma^2/2)\tau\}^2}{2\sigma^2\tau} \right) dX.$
```

如果我们令 $u = \frac{X - (r + \sigma^2/2)\tau}{\sigma \sqrt{\tau}}$，则 $dX = \sigma \sqrt{\tau} du$。

所以：

```
$I_A = \frac{S \sqrt{\tau}}{\sigma \sqrt{2\pi}} \int_{u_1}^{\infty} \exp\left( -\frac{u^2}{2} \right) du.$
```

其中积分下限为 $k_1 = [\log(E/S) - (r + \sigma^2/2)\tau]/\sigma \sqrt{\tau}$。（注：原文此处逻辑混乱，根据 $I_A = SN_1(-k_1)$ 逻辑推导）

我们有：

```
$I_A = SN_1(-k_1). \quad (4.4.46)$
```

因此，欧式看涨权的价值为：

```
$c(S, E, \tau) = SN_1(-k_1) - E \exp(-r\tau)N_1(-k_2),$
```

## 欧式期权与布莱克-斯科尔斯模型章节 | 4.4 69

这给出了欧式看涨权布莱克-斯科尔斯公式的常用形式：

```
$c(S,E,\tau) = SN_1(d_1) - E \exp(-r\tau)N_1(d_2), \quad (4.4.47)$
```

其中：

```
$d_1 = \frac{\log(E/S) + (r + \sigma^2/2)\tau}{\sigma\sqrt{\tau}} \text{ and } d_2 = \frac{\log(E/S) + (r - \sigma^2/2)\tau}{\sigma\sqrt{\tau}} = d_1 - \sigma\sqrt{\tau}. \quad (4.4.48)$
```

为了深入理解上述方程，我们将其重写为以下形式：

```
$c(S,E,\tau) = \exp(-r\tau) \{SN_1(d_1)\exp(r\tau) - EN_1(d_2)\}. \quad (4.4.49)$
```

项 $N_1(d_2)$ 是在风险中性世界中行权的概率，其中 $EN_1(d_2)$ 是行权价格乘以支付行权的概率。项 $SN_1(d_1)\exp(r\tau)$ 是一个变量在风险中性世界中的期望，当 $S_T > E$ 时等于 $S_T$，否则为零。

相应的看跌公式可以使用看跌平价关系（见第4.3节）导出：

```
$p(S,E,\tau) = E\exp(-r\tau)N_1(-d_2) - SN_1(-d_1). \quad (4.4.50)$
```

或者等价地 $N_1(-x) = 1 - N_1(x)$，我们有：

```
$p(S,E,\tau) = E\exp(-r\tau) \{1 - N_1(d_2)\} - S\{1 - N_1(d_1)\}. \quad (4.4.51)$
```

## 连续红利的引入

红利对欧式期权的影响可以通过假设资产价格为风险部分、期权内支付的已知红利以及风险（随机）部分之和来处理，参见 Hull (2003)。

当支付连续红利 $q$ 时，股票价格减少相应的金额，当欧式期权到期时，所有红利都已支付，只剩下资产价格的风险部分。

从方程 (4.4.26) 中，我们有：

```
$dS = \dots$
```
