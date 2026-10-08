

$\Delta\Pi = -\sum_{i=1}^n \mu_i S_i\Delta t\frac{\partial f}{\partial S_i}-\Delta t\frac{\partial f}{\partial t}-\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j\rho_{ij}S_i S_j\frac{\partial^2 f}{\partial S_i\partial S_j}$

```
\sum_{i=1}^n \sigma_i S_i\Delta t\frac{\partial f}{\partial S_i}+\sum_{i=1}^n \mu_i S_i\Delta t\frac{\partial f}{\partial S_i}
```

```
\sum_{i=1}^n \sigma_i S_i\Delta t\frac{\partial f}{\partial S_i} \quad (4.4.21)
```

消去项后，我们得到：

```
\Delta\Pi = -\Delta t\left(\frac{\partial f}{\partial t}+\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j\rho_{ij}S_i S_j\frac{\partial^2 f}{\partial S_i\partial S_j}\right) \quad (4.4.22)
```

如果该投资组合处于无风险利率 $r$ 下，则有：

$r\Delta t = \Delta\Pi$

因此根据方程 (4.4.22)，我们有：

```
\Delta\Pi = -\Delta t\left(\frac{\partial f}{\partial t}+\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j\rho_{ij}S_i S_j\frac{\partial^2 f}{\partial S_i\partial S_j}\right) \quad (4.4.23)
```

代入 $\Pi$ 我们得到：

```
$r\Delta t = f-\sum_{i=1}^n S_i\frac{\partial f}{\partial S_i}-\Delta t+\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j\rho_{ij}S_i S_j\frac{\partial^2 f}{\partial S_i\partial S_j} \quad (4.4.24)
```

重组方程 (4.4.24) 得到：

```
\frac{\partial f}{\partial t}+\sum_{i=1}^n S_i\frac{\partial f}{\partial S_i}+\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j\rho_{ij}S_i S_j\frac{\partial^2 f}{\partial S_i\partial S_j}=rf \quad (4.4.25)
```

这就是 $n$ 维 Black–Scholes 偏微分方程。

## 4.4.3 Black–Scholes 公式

Black-Scholes 模型包含两种资产：无风险资金账户和股票。它可以被写为以下二维 Ito 方程：

```
$dS_t=\mu_S S_t dt+\sigma_S S_t dW^P \quad (4.4.26)
```

```
$dB_t=rB_t dt
```

其中 $W^P$ 是测度 $\mathbb{P}$ 下的布朗运动（无漂移），因此 $dW^P \sim N(0,dt)$。

当前时间用 $t_0$ 表示，期权到期时间用 $T$ 表示。货币市场账户在 $t_0$ 的价值为 $B_{t_0}=1$，在 $T$ 的价值为 $B_T = \exp(r(T - t_0))$。

现在考虑相对价值 $\phi(S_t, B_t) = S_t/B_t$ 的过程。

使用 2.6.2 节描述的 Ito 商法则，并在方程 (2.6.8) 中代入 $X_1 = S_t$ 和 $X_2 = B_t$，我们得到：

```
$d\left(\frac{S_t}{B_t}\right) = \left(\frac{S_t}{B_t}\right)(\mu - r)dt + \left(\frac{S_t}{B_t}\right)\sigma dW^P
```

最后我们可以写成：

```
$dS_t^* = S_t^*(\mu - r)dt + S_t^*\sigma dW^P$ (4.4.27)
```

其中 $S_t^* = S_t/B_t$。参考 2.4 节的 Girsanov定理，我们可以选择概率测度 $Q$：

```
$dW^P = dW^Q - \left(\frac{\mu - r}{\sigma}\right)dt \quad (4.4.28)
```

在方程 (2.4.3) 中我们有 $k(t) = -((\mu - r)/\sigma)$ 以及：

```
$\frac{dQ}{dP} = \exp\left\{-\left(\frac{\mu - r}{\sigma}\right)W^P - \frac{1}{2}\left(\frac{\mu - r}{\sigma}\right)^2 t\right\}$ (4.4.29)
```

参考 Musiela (1998) 第 114 页，在方程 (4.4.27) 中代入 $dW^P$ 得到：

```
$dS_t^* = S_t^*(\mu - r)dt + S_t^*\sigma\left(\frac{\mu - r}{\sigma}\right)dW^Q
```

简化为：

```
$dS_t^* = S_t^*\sigma dW^Q$ (4.4.30)
```

方程 (4.4.30) 过程 $S_t^*$ 在概率 $Q$ 下是鞅的。

将 (4.4.26) 中的 $dW^P$ 替换为方程 (4.4.28) 中的值得到：

```
$dS_t = \mu_t S_t dt + S_t\sigma dW^P
$= \mu_t S_t dt + S_t\sigma\left\{dW^Q - \left(\frac{\mu - r}{\sigma}\right)dt\right\}$
$= \left\{S_t\mu_t dt - S_t\sigma\left(\frac{\mu - r}{\sigma}\right)dt\right\} + S_t\sigma dW^Q
```

所以在风险中性测度 $Q$ 下，$S_t$ 的动力学过程为：

```
$dS_t = r dt + S_t\sigma dW^Q$ (4.4.31)
```

比较 (4.4.31) 和原始方程 (4.4.26)，我们看到从真实测度到风险中性测度只需将 $dW^P$ 替换为 $dW^Q$，并将 $\mu$ 替换为 $r$。

## 欧期权

现在我们可以通过方程 (2.3) 的结果求解方程 (4.4.31)。我们有：

```
$S_T = S \exp(v(T-t_0))$
```

其中 $S$ 是 $t_0$ 时刻，$v = r - \sigma^2/2$。到期于 $T$ 的期货价格记为 $S(t_0, T)$。根据附录 D，我们有：

```
$S(t_0, T) = E[S_T] = S \exp(r(T-t_0))$ (4.4.32)
```

使用方程 (2.3)，在 $T$ 时刻资产的分布为：

```
$\log \frac{S_T}{S} \sim N(v(T-t_0), \sigma^2(T-t_0))$ (4.4.33)
```

我们想要考虑执行价为 $E$、在时间 $T$ 到期的欧期权，期限为 $\tau$。我们在这里采用的方法首先推导出看涨期权的价值表达式，然后使用第 2 节的看跌看涨平价获得欧期权的价值。参考 (2.1)，我们有：

```
$V_0 = B_0 E\left[\frac{H_T}{B_T}\right]$ (4.4.34)
```

代入 $B_0 = 1, B_T = \exp(r\tau)$ 且 $H_T = \max(S_T-E, 0)$，我们得到：

```
$V_0 = \frac{1}{\exp(r\tau)} E[\max(S_T-E, 0)]$ (4.4.35)
```

并将看涨期权的价值记为 $c(S, E, \tau)$，得到：

```
$c(S, E, \tau) = \exp(-r\tau) E[\max(S_T-E)]$ (4.4.36)
```

从方程 (4.4.36) 可以看出，欧期权的价值是到期收益的期望值，通过无风险利率 $r$ 折现到当前时间 $t_0$。这意味着看涨期权的价值可以写为：

```
$c(S, E, \tau) = \exp(-r\tau) \int_{S_T=E}^{\infty} f(S_T)(S_T-E) dS_T$ (4.4.37)
```

其中 $f(S_T)$ 是 $S_T$ 的概率密度函数。我们不对 $S_T$ 积分，而是使用变量 $X = \log(S_T/S)$ 计算 (4.4.37)。从方程 (4.4.33) 中我们知道 $X$ 的密度函数为：

```
$f(X) = \frac{1}{\sigma\sqrt{2\pi}} \exp\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)$ (4.4.38)
```

因此期权的价值为：

```
$c(S, E, \tau) = \exp(-r\tau) \int_{X=\log(E/S)}^{\infty} \{Se^X - E\}f(X)dX$ (4.4.39)
```

其中我们使用了 $S_T = S\exp(X)$。方程 (4.4.39) 中的下限对应 (4.4.37) 中的 $S_T = E$，通过设置 $E = S\exp(X)$ 得到下限 $X = \log(E/S)$。方程 (4.4.39) 的积分通过拆分为两部分来计算：

```
$c(S, E, \tau) = I_A - I_B$ (4.4.40)
```

其中：

```
$I_A = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{X=\log(E/S)}^{\infty} e^X \exp\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) dX
```

为了计算这些积分，我们利用累积正态函数 $N(x)$ 的性质：

```
$N(x) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{x} \exp\left(-\frac{u^2}{2}\right) du
```

根据对称性我们有 $N(-x) = 1 - N(x)$。我们先考虑 $I_B$，它是更容易的积分：

```
$I_B = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{-\infty}^{\log(E/S)} \exp\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) dX
```

如果使用 $u = \frac{X-(r-\sigma^2/2)\tau}{\sqrt{\tau}}$，则 $dX = \sigma\sqrt{\tau}$。所以：

```
$I_B = E\exp(-r\tau) \int_{-\infty}^{\frac{\log(E/S)-(r-\sigma^2/2)\tau}{\sqrt{\tau}}} \exp\left(-\frac{u^2}{2}\right) du
```

其中积分下限为 $\frac{\log(E/S)-(r-\sigma^2/2)\tau}{\sqrt{\tau}} = -d_2$。因此 $I_B = E\exp(-r\tau) N(d_2)$。

现在考虑 $I_A$：

```
$I_A = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} e^X \exp\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) dX
```

使用代换 $u = \frac{X-(r-\sigma^2/2)\tau}{\sqrt{\tau}}$，则 $dX = \sigma\sqrt{\tau}$ 且 $X = u\sqrt{\tau} + (r-\sigma^2/2)\tau$。

```
$I_A = S\exp(-r\tau)e^{(r-\sigma^2/2)\tau} \frac{1}{\sqrt{2\pi}} \int_{-d_2}^{\infty} e^{u\sqrt{\tau}} \exp\left(-\frac{u^2}{2}\right) du
```

在指数部分完成配方法：$u^2-2u\sqrt{\tau} = (u-\sqrt{\tau})^2 - \tau$。

```
$I_A = S\exp(-r\tau)e^{r\tau-\frac{\sigma^2\tau}{2}} e^{\frac{\sigma^2\tau}{2}} \frac{1}{\sqrt{2\pi}} \int_{-d_2}^{\infty} \exp\left(-\frac{(u-\sqrt{\tau})^2}{2}\right) du
```

```

```
$I_A = S \frac{1}{\sqrt{2\pi}} \int_{-d_2}^{\infty} \exp\left(-\frac{(u-\sqrt{\tau})^2}{2}\right) du
```

令 $v = u-\sqrt{\tau}$，则 $dv=du$。下限变为 $-d_2-\sqrt{\tau} = -d_1$。

```
$I_A = S \frac{1}{\sqrt{2\pi}} \int_{v=-d_1}^{\infty} \exp\left(-\frac{v^2}{2}\right) dv = S N(d_1)
```

其中 $d_1 = \frac{\log(S/E)+(r+\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$ 且 $d_2 = d_1-\sigma\sqrt{\tau}$。最后 Black-Scholes 公式为：

```
$c(S, E, \tau) = SN(d_1) - E\exp(-r\tau)N(d_2)$
```

