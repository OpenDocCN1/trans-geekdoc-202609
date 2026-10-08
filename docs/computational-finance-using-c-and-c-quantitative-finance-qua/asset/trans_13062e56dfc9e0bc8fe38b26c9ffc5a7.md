
现在由于 $\phi$ 在 $Q^{k+1}$ 下是一个阶鞅过程，我们知道 $D = 0$，因此方程 (7.2.65) 得到：

```
$$(1 + F_{k+1})F_k\mu_k \, dt = -\rho_{k,k+1}\sigma_k\sigma_{k+1}F_k F_{k+1} \, dt$$
```

这意味着漂移项为：

```
$$\mu_k = -\frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}}{1 + F_{k+1}}$$ $$(7.2.66)$$
```

在方程 (7.2.61) 中代入 $\mu_k$ 得到：

```
$$dF_k = F_k\sigma_k \left\{ \frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{1 + F_{k+1}} \, dt + dW^{k+1} \right\}$ $$(7.2.67)$$
```

比较方程 (7.2.67) 和方程 (7.2.40)我们得到：

```
$$dW^k = -\frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{1 + F_{k+1}} \, dr + dW^{k+1}$$ $$(7.2.68)$$
```

这是布朗运动 $dW^k$ 与 $dW^{k+1}$ 之间的关系。

$i \geq k+2$
设 $F_k$ 在 $Q^{k+1}$ 下遵循的随机过程为：

```
$$dF_k = F_k\mu_k \, dt + F_k\sigma_k \, dW^{k+2}$$ $$(7.2.69)$$
```

其中 $W^k$ 是概率测度 $Q^{k+2}$ 下的布朗运动，漂移项 $\mu_k$ 待求。
在方程 (7.2.68) 中将 $k$ 替换为 $k+1$ 得到：

```
$$dW^{k+1} = -\frac{\rho_{k+1,k+2}\sigma_{k+1}\sigma_{k+2}F_{k+2}}{1 + F_{k+2}} \, dr + dW^{k+2}$$ $$(7.2.70)$$
```

使用方程 (7.2.70) 代入方程 (7.2.68) 中的 $dW^{k+1}$ 得到：

```
$$dW^k = -F_k\sigma_k \left\{ \frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{1 + F_{k+1}} \, dt - \frac{\rho_{k+1,k+2}\sigma_{k+1}\sigma_{k+2}F_{k+2}}{1 + F_{k+2}} \, dt \right\}$$ $$(7.2.71)$$
```

在方程 (7.2.40) 中代入 $dW^k$ 得到：
因此漂移项为：

```
$$\mu_k = -\frac{\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{1 + F_{k+1}} - \frac{\rho_{k+1,k+2}\sigma_{k+1}\sigma_{k+2}F_{k+2}}{1 + F_{k+2}}$$ $$(7.2.72)$$
```

可以以类似的方法推导出以下通用表达式：

```
$$dF_k = -F_k\sigma_k \sum_{j=k+1}^i \frac{\rho_{k,j}\sigma_k\sigma_j}{1 + F_j} \, dt + \sigma_k F_k \, dW^i$ $$(7.2.73)$$
```

其中所有符号含义与之前相同，但现在 $i$ 可以取任何大于 $k$ 的整数值。

## 7.2.4 利率量化

本节考虑价值取决于外币利率收益率曲线但以本币结算的衍生品。我们使用与第 7.3 节（处理外汇衍生品）相同的符号。

例如，标准的利率上限期（rate cap）以本币结算，并且取决于本币的远期利率。在 $t_k$ 时刻支付且期限从 $t_{k-1}$ 延伸到 $t_k$ 的上限期（caplet）在 $t_0$ 时刻的价值为：

```
$Caplet(t_0) = P\tau D^p(t_0, t_k)E^Q[max(F^d_k - K, 0)]$
```

其中 $P$ 是本金，$K$ 是执行价格，$\tau = t_{k-1}-t_k$，$F^d$ 是本币远期利率 $F^d(t_0, t_k, t_{k-1})$。方程 (7.2.74) 可以使用 Black–Scholes 公式求值为：

```
$Caplet(t_0) = P\tau D^p(t_0, t_k)\{F^d(t_0, t_k, t_{k-1})N_1(d_1) - KN_1(d_2)\}$
```

其中 $\sigma_d$ 是 $F^d$ 的波动率，且：

$d_1 = \frac{\log(F^d(t_0, t_k)/K) + \frac{\sigma_d^2}{2}(t_{k-1}-t_0)}{\sigma_d\sqrt{t_{k-1}-t_0}}$
$d_2 = \frac{\log(F^d(t_0, t_k)/K) - \frac{\sigma_d^2}{2}(t_{k-1}-t_0)}{\sigma_d\sqrt{t_{k-1}-t_0}}$

在 7.2.3 节中，我们证明了当使用 $DF^p(t, t_k)$ 作为计价基时，$(F^d(t, t_{k-1}, t_k)/DF^p(t, t_k))$ 是一个鞅，且漂移为零：

```
$dF^d(t, t_{k-1}, t_k) = \sigma_d F^d(t, t_{k-1})dW_t$
```

## 量化期 (Quanto caplet)

在使用本币远期利率 $F^d(t_0, t_k)$ 的量化期中，我们使用外币远期利率 $F^f(t, t_{k-1}, t_k)$。在外币零息债券 $DF^f(t, t_k)$ 相关的概率测度 $\mathbb{F}$ 下，外币远期利率是一个鞅，并由以下方程描述：

```
$dF^f(t, t_{k-1}, t_k) = \sigma_f F^f(t, t_{k-1})dW_t^{\mathbb{F}}$
```

然而，当我们使用 $DF^d(t, t_k)$ 作为计价基时，过程 $(F^f(t, t_{k-1}, t_k)/DF^d(t, t_k))$ 具有漂移，并遵循过程：

```
$dF^f(t, t_{k-1}, t_k) = F^f(t, t_{k-1}, t_k)\alpha dt + \sigma_f F^f(t, t_{k-1}, t_k)dW_t^{\mathbb{Q}}$
```

我们的目标是找到 $\alpha$ 的值并为量化期定价：

```
$QCaplet(t_0) = P\tau D^p(t_0, t_k)\times\{F^f(t_0, t_{k-1})\exp(\alpha(t_{k-1}-t_0))N_1(d_1) - KN_1(d_2)\}$
```

其中 $P$ 是本金，$K$ 是执行价格，$\tau = t_{k-1} - t_k$，$F^f(t_0, t_{k-1}, t_k)$ 是外币远期利率，$\sigma_f$ 是 $F^f(t_0, t_{k-1}, t_k)$ 的波动率，且：

$d_1 = \frac{\log(F^f(t_0, t_{k-1}, t_k)/K) + (\alpha + \frac{\sigma_f^2}{2})(t_{k-1}-t_0)}{\sigma_f\sqrt{t_{k-1}-t_0}}$
$d_2 = \frac{\log(F^f(t_0, t_{k-1}, t_k)/K) + (\alpha - \frac{\sigma_f^2}{2})(t_{k-1}-t_0)}{\sigma_f\sqrt{t_{k-1}-t_0}}$

我们现在推导 $\alpha$ 的值。
首先定义两个过程 $X_1(t)$ 和 $X_2(t)$ 如下：

```
$X_1(t) = \left(\frac{DF^f(t, t_{k-1}) - DF^f(t, t_k)}{DF^f(t, t_k)}\right)X_d^f(t) \quad (7.2.80)$
```

并且：

```
$X_2(t) = \tau X_d^f(t)\frac{DF^f(t, t_k)}{DF^f(t, t_k)} = \tau X_d^f(t, t_k) \quad (7.2.81)$
```

$X_d^f(t, t_k)$ 是远期外汇率（第 7.3 节）。因此：

```
$X_1(t) = \frac{DF^f(t, t_{k-1}) - DF^f(t, t_k)}{\tau DF^f(t, t_k)} = F^f(t, t_{k-1}, t_k) \quad (7.2.82)$
```

现在 $X_1$ 和 $X_2$ 在 $\mathbb{Q}$ 下是鞅，因此我们：

```
$dX_1 = \sigma_1 X_1 dW_1^{\mathbb{Q}} \quad (7.2.83)$
```

并且：

```
$dX_2 = \sigma_2 X_2 dW_2^{\mathbb{Q}} \quad (7.2.84)$
```

方程 (7.2.84) 可以表示为：

```
$d\left(\frac{\tau X_d^f(t, t_k)}{\tau X_d^f(t, t_k)}\right) = \sigma_x dW_x^{\mathbb{Q}} \quad (7.2.85)$
```

利用它得到：

```
$d\left(\frac{X_1}{X_2}\right) = \frac{X_1}{X_2}[\sigma_1 dW_1^{\mathbb{Q}} - \sigma_2 dW_2^{\mathbb{Q}}] + \frac{X_1}{X_2}[E[(\sigma_1 dW_1^{\mathbb{Q}})^2] - E[(\sigma_1 dW_1^{\mathbb{Q}})(\sigma_2 dW_2^{\mathbb{Q}})] \quad (7.2.86)$
```

以及 $\log(X_1)$ 和 $\log(X_2)$ 的以下过程：

```
$d\log(X_1) = -\frac{\sigma_1^2}{2}dt + \sigma_1 dW_1^{\mathbb{Q}}$
$d\log(X_2) = -\frac{\sigma_2^2}{2}dt + \sigma_2 dW_2^{\mathbb{Q}} \quad (7.2.87)$
```

## 其他衍生品

利用方程 (7.2.85) 我们可以将方程 (7.2.87) 写成：

```
$d\log(\tau X_d^f(t, t_k)) = -\frac{\sigma_x^2}{2} dt + \sigma_x dW_x^{\mathbb{Q}} \quad (7.2.88)$
```

现在，我们忽略了大于 1 的 $dt$ 项。此外：

```
$E[d\log(X_2) - d\log(X_1)] = -E[d\log(X_2) d\left(\frac{X_1}{X_2}\right)] = -E[d\log(X_2) d(F^f(t, t_{k-1}, t_k))] = -\sigma_x\sigma_f\rho_{x,f} dt
```

其中 $\sigma_x$ 是外汇率 $X_d^f(t, t_k)$ 的波动率，$\sigma_f$ 是远期利率 $F^f(t, t_{k-1}, t_k)$ 的波动率，而 $\rho_{x,f}$ 是 $dW_x^Q$ 与 $dW_f^Q$ 之间的相关性。
因此方程 (7.2.86) 可以写为：

```
$d\left(\frac{X_1}{X_2}\right) = -\frac{X_1}{X_2}(\sigma_x\sigma_f\rho_{x,f}) dt + \frac{X_1}{X_2}\{\sigma_1 dW_1^{\mathbb{Q}} - \sigma_2 dW_2^{\mathbb{Q}}\}$
```

这意味着：

```
$D^f(t, t_{k-1}, t_k) = -F^f(t, t_{k-1}, t_k)(\sigma_x\sigma_f\rho_{x,f}) dt + \sigma_f F^f(t, t_{k-1}, t_k) dW^Q \quad (7.2.89)$
```

且 $\alpha = -\sigma_x\sigma_f\rho_{x,f}$。

## 量化下期 (Quanto floorlet)

量化下期的定价方法可以与量化期的方法类似。在 $t_k$ 时刻支付且期限从 $t_{k-1}$ 延伸到 $t_k$ 的标准下期（floorlet）在 $t_0$ 时刻的价值为：

```
$Floorlet(t_0) = P\tau DF^d(t_0, t_k)E^{Q^d}[\max(K - F_d^d, 0)]$
```

其中 $P$ 是本金，$K$ 是执行价格，$\tau = t_{k-1}-t_k$，$F_k$ 是远期利率 $F(t_0, t_{k-1}, t_k)$。方程 (7.2.90) 可以使用 Black-Scholes 公式求值为：

```
$Floorlet(t_0) = P\tau DF^d(t_0, t_k)[-F^d(t_0, t_{k-1}, t_k)N_1(d_1) + KN_1(d_2)]$
```

其中符号含义与对应的量化期相同。

```
$d_1 = \frac{\log(F^d(t_0, t_{k-1}, t_k)/K) + \frac{\sigma_d^2}{2}(t_{k-1}-t_0)}{\sigma_d\sqrt{t_{k-1}-t_0}}$
$d_2 = \frac{\log(F^d(t_0, t_{k-1}, t_k)/K) - \frac{\sigma_d^2}{2}(t_{k-1}-t_0)}{\sigma_d\sqrt{t_{k-1}-t_0}}$
```

在量化下期中，我们不使用本币远期利率 $F^d(t_0, t_{k-1}, t_k)$，而是使用外币远期利率 $F^f(t, t_{k-1}, t_k)$：

```
$Floorlet(t_0) = P\tau DF^f(t_0, t_k)\times\{-F^f(t_0, t_{k-1}, t_k)\exp(\alpha(t_{k-1}-t_0))N_1(d_1) + KN_1(d_2)\}$
```

其中 $P$ 是本金，$K$ 是执行价格，$\tau = t_{k-1} - t_k$，$F^f(t_0, t_{k-1}, t_k)$ 是外币远期利率，$\sigma_f$ 是 $F^f(t_0, t_{k-1}, t_k)$ 的波动率。

