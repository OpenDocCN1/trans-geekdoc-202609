

## 234 章 | 7 其他金融衍生品

其他金融衍生品

我们首先将 $(X_d^B/B_d)$ 写为 $(S_f^B/B_f)(X_d^B/B_d)$。使用伊藤 乘积法则，我们得到：

```
$d\left(\frac{S_f^B}{B_f}\frac{X_d^B}{B_d}\right)=\left(E\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)+\sigma_x\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right)+E\left[d\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right]\quad(7.5.15)$
```

将方程 (7.5.14) 中的 $(X_d^B/B_d)$ 代入方程 (7.5.15) 得到：

```
$d\left(\frac{S_f^B}{B_f}\frac{X_d^B}{B_d}\right)=\left(\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)+\sigma_x\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right)dW_x^Q+E\left[d\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right]\quad(7.5.16)$
```

使用具有单一随机源的伊藤 商法则（见 2.6.2 节），方程 (7.5.13) 和方程 (7.5.10) 得到：

```
$d\left(\frac{S_f^B}{B_f}\right)=\alpha dt+d\left(\frac{S_f^B}{B_f}\right)\sigma_x dW_x^Q.\quad(7.5.17)$
```

我们现在考虑方程 (7.5.16)中的项 $E\left[d\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right]$：

```
$E\left[d\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right]=\left\left(\frac{S_f^B}{B_f}\right)\left(\alpha dt+d\left(\frac{S_f^B}{B_f}\right)\sigma_x dW_x^Q\right)\sigma_x\left(\frac{X_d^B}{B_d}\right)+\left\left(\frac{X_d^B}{B_d}\right)\left(\alpha dt+d\left(\frac{X_d^B}{B_d}\right)\sigma_x dW_x^Q\right)\sigma_x\left(\frac{S_f^B}{B_f}\right)-\left\left(\frac{X_d^B}{B_d}\right)d\left(\frac{X_d^B}{B_d}\right)\right)\sigma_x\sigma_x\left(\frac{S_f^B}{B_f}\right)\left(\frac{X_d^B}{B_d}\right)\right]$
```

由于 $[dW_x^Q]=0$ 且 $E[dW_x^Q dW_x^Q]=\rho_{xs}dt$，我们有：

```
$E\left[d\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right]=\left\left(\frac{S_f^B}{B_f}\right)\left(\frac{X_d^B}{B_d}\right)\right)\sigma_x\sigma_x\rho_{xs}dt.\quad(7.5.18)$
```

将方程 (7.5.17) 和 (7.5.18) 中的 $(S_f^B/B_f)$ 和 $E\left[d\left(\frac{S_f^B}{B_f}\right)d\left(\frac{X_d^B}{B_d}\right)\right]$ 的值代入方程 (7.5.16) 得到：

```
$d\left(\frac{S_f^B}{B_f}\frac{X_d^B}{B_d}\right)=\left\left(\frac{S_f^B}{B_f}\right)\left\left(\frac{X_d^B}{B_d}\right)\right)\alpha dt+\left\left(\frac{S_f^B}{B_f}\right)\left\left(\frac{X_d^B}{B_d}\right)\right)\sigma_x\sigma_x dW_x^Q+\sigma_x\left(\frac{X_d^B}{B_d}\right)\left(\frac{S_f^B}{B_f}\right)\sigma_x\sigma_x\rho_{xs}dt.$
```

## 股票衍生品章节

重新整理得：

```
$d\left(\frac{S_f^B}{B_d}\right)=\left(\frac{S_f^B}{B_d}\right)\{\alpha+\sigma_s\sigma_x\rho_{xs}\}dt+\left(\frac{S_f^B}{B_d}\right)(\sigma_s dW_s+\sigma_x dW_x).\quad(7.5.19)$
```

$(\frac{S_f^B}{B_d})$ 在测度 $Q$ 下是马鞅的，因此方程 (7.5.19) 中的漂移项为零。这意味着：

```
$\alpha=-\sigma_s\sigma_x\rho_{xs},$
```

其中 $\sigma_s$ 是股票波动率，$\sigma_x$ 是汇率波动率，$\rho_{xs}$ 是 $dW_s$ 和 $dW_x$ 之间的相关性。方程 (7.5.13) 可以写为：

```
$dS\F=\{rf-\sigma_s\sigma_x\rho_{xs}\}S^F dt+\sigma_s S^F dW_s.\quad(7.5.20)$
```

## 股票 Quanto 期货

到期为 $T$ 的本币股票期货合约（时间 $t$）：

```
$F(t)=DF^d(t,T)\{S^d(t,T)-K^d\},
```

其中 $K^d$ 是本币计的行权价。要对股票 Quanto 期货定价，需要知道股票的期货价格 $S^F$。从方程 (4.4.31)、(4.4.32) 和 (7.5.20) 可以看出该期货价格为：

```
$S^F(t,T)=S^F(t)\exp((rf-\sigma_s\sigma_x\rho_{xs})(T-t)).\quad(7.5.21)$
```

其中 $S^F(t)$ 是当前价格，$T$ 是期货到期。在股票 Quanto 期货中，收益以外币计价，但按预定汇率（此处用 $X$ 表示）转换为本币。Quanto 期货的价值为：

```
$PF(t)=DF^d(t,T)\{S^d(t,T)-K^f\}X,$
```

其中 $X$ 是指定汇率，$K^f$ 是外币单位行权价，$S^F(T)$ 是期货价格。

## 股票 Quanto 期权

在第 4 章中，方程 (4.4.58) 和 (4.4.59) 表示了标准欧式看跌和看涨期权的价值：

```
$Call(t)=\exp(-rd(T-t))\{S^d(t,T)N_1(d_1)-EN_1(d_2)\},$
```

```
$Put(t)=\exp(-rd(T-t))\{-S^d(t,T)N_1(-d_1)+EN_1(-d_2)\},$
```

其中我们使用上标表示本币，到期为 $T$ 的当前股票期货价格为：

```
$S^d(t,T) = S^d \exp(r^d(T-t)), \quad t \le T.$
```

任何股票期权的价值可以通过将上述方程中的 $S^d$ 替换为 $f^d$ 来得到：

```
$QCall(t) = \exp(-r^d(T-t)) \{S^d(t,T)N_1(d_1) - E^f N_1(d_2)\},$
```

```
$QPut(t) = \exp(-r^d(T-t)) \{-S^f(t,T)N_1(-d_1) + E^f N_1(d_2)\}, X.$
```

```
$d_1 = \frac{\log(S^f(t,T)/E^f) + \sigma^2/2T}{\sigma_s \sqrt{T-t}}, \quad d_2 = \frac{\log(S^f(t,T)/E^f) - \sigma^2/2T}{\sigma_s \sqrt{T-t}}$
```

其中 $E^f$ 是外币单位行权价，$S^f(t,T)$ 是外币股票期货价格（从方程 7.5.21 得到），$X$ 是指定汇率（每单位外币对应的本币数量）。

## 7. 选定期权

-   1. 令 $F(t_i), i=1$ 为期货曲线，令 $S(t_i)$ 为现价。期货价格 $F(t_i)$ 是今天购买资产并在未来日期 $t_i$ 交付的。。

-   2. 令 $S(t)$ 为遵循随机微分方程 SDE 的随机过程：
$dS(t) = \mu S(t)dt + \sigma S(t)dW(t),$
其中 $\mu$ 是漂移系数，$\sigma$ 是波动率，$W(t)$ 是标准布朗运动。

-   3. 考虑以下带有跳跃的过程：
```
dS(t) = \mu S(t)dt + \sigma S(t)dW(t) + S(t-)dJ(t),
```
其中 $J(t)$ 是强度为 $\lambda$ 的复合泊松过程。

-   4. Hull-White 随机微分方程用于：
```
$dr_t = (\Theta_t - ar_t)dt + \sigma dW_t,$
```
其中 $a$ 是回归速率，$\Theta_t$ 是时间变化的均值$\sigma$ 是波动率。

-   5. 短利率 $r$ 的 Vasicek 模型定义为：
```
$dr_t = \alpha(\beta-r_t)dt+\sigma dW_t,$
```
其中 $\alpha$ 是均值回归速率，$\beta$ 是长期均值$\sigma$ 是波动率。

