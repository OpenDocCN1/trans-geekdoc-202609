

## 看涨看跌平价章节 | 4.3 59

投资组合 B：

一份欧式看跌期权，$p(S, E, \tau)$ 和一份价值为 $S$ 的股票。

到期时，看涨和看跌期权的价值分别为 $c(S_T, E, 0)$ 和 $p(S_T, E, 0)$；同时在时间 $T$，期权存续期间支付的股利价值为 $D \exp(r\tau)$。

我们现在考虑在所有可能的情况下时间 $T$ 时两个组合的价值。

如果 $S_T \ge E$

投资组合 A 的价值为：

$$\max(S_T - E, 0) + E \exp(-r\tau) + D = S_T - E + E \exp(r\tau) = S_T + D \exp(r\tau).$$

投资组合 B 的价值为：

$$\max(E - S_T, 0) + S_T + D \exp(r\tau) = 0 + S_T + D \exp(r\tau) = S_T + D \exp(r\tau).$$

如果 $S_T < E$

投资组合 A 的价值为：

$$\max(S_T - E, 0) + \exp(r\tau) + D = 0 + E + D \exp(r\tau) = E + D \exp(r\tau).$$

投资组合 B 的价值为：

$$\max(E - S_T, 0) + S_T + D \exp(r\tau) = E - S_T + S_T + D \exp(r\tau) = E + D \exp(r\tau).$$

我们已经证明，在所有情况下，投资组合 A 的价值与投资组合 B 相同。

## 4.3.2 连续股利

在这里，我们考虑单一资产的欧式看跌和看涨期权，并导出以下关系：

$$c(S, E, \tau) + E \exp(-r\tau) = p(S, E, \tau) + S \exp(-q\tau),$$

其中 $q$ 是期权存续期间支付的资产连续股利率。该结果可以通过考虑以下两个投资来证明：

投资组合 A：

一份欧式看涨期权，$c(S, E, \tau)$ 和价值为 $E \exp(-r\tau)$ 的现金。

投资组合 B：

一份欧式看跌期权，$p(S, E, \tau)$ 和一份价值为 $S \exp(-q\tau)$ 的股票。

在到期时，看涨和看跌期权的价值分别为 $c(S_T, E, 0)$ 和 $p(S_T, E, 0)$。同时，如果时间 $t$ 的股票价值标记为 $S$，则时间 $T$ 时股票和股利的组合价值为 $S \exp(q\tau)$：注意 $q$ 的处理方式与连续复利无风险利率 $r$ 。

## 4 欧式期权

如果 $S_T \geq E$
投资组合 A 的价值为：

$\max(S_T - E, 0) + \exp(r\tau)E\exp(-r\tau) = S_T - E + E = S_T.$

投资组合 B 的价值为：

$\max(S_T - E, 0) + S_T\exp(-q\tau)\exp(q\tau) = 0 + S_T = S_T,$

其中 $S\exp(-q\tau)\exp(q\tau)$ 是期权到期时股票和股利的组合价值。

如果 $S_T < E$
投资组合 A 的价值为：

$\max(S_T - E, 0) + \exp(r\tau)E\exp(-r\tau) = 0 + E = E.$

投资组合 B 的价值为：

$\max(S_T - E, 0) + S_T\exp(-q\tau)\exp(q\tau) = E - S_T + S_T = E.$

因此，我们已经证明了在所有情况下，投资组合 A 的价值与投资组合 B 相同。

## 4.4 普通期权与布莱-舒尔斯模型

### 4.4.1 期权定价微分方程

在本节中，我们将推导出单一资产期权所遵循的（布莱-舒尔斯）微分方程。

之前，在第 2.3 和 2.5 节中，我们推导了伊藤引（Ito's lemma），它提供了函数 $\phi(X,t)$ 值变化的表达式，其中 $X$ 是随机变量。当随机变量 $X$ 遵循几何布朗运动（GBM）时，$\phi$ 的变化可以通过 (2.3,6) 证明。在这里，我们假设函数 $\phi(S,t)$ 是金融期权的价值，且底层资产价格 $S$ 遵循 GBM。

如果我们将金融衍生品的价值标记为 $f$，它在时间间隔 $dt$ 内的价值 $df$ 给出：

$$df=(\mu S\frac{\partial f}{\partial S} + \frac{\partial f}{\partial t} + \frac{\sigma^2 S^2}{2}\frac{\partial^2 f}{\partial S^2})dt + \sigma S\frac{\partial f}{\partial S}dW \sim N(0,dt).$$

该方程的离散化版本为：

$$\Delta f=(\mu S\frac{\partial f}{\partial S} + \frac{\partial f}{\partial t} + \frac{\sigma^2 S^2}{2}\frac{\partial^2 f}{\partial S^2})\Delta t + \sigma S\frac{\partial f}{\partial S}\Delta W \sim N(0,\Delta t), (4.4.1)$$

其中时间间隔为 $\Delta t$，期权价值的变化为 $\Delta f$。如果资产价格 $S$ 遵循 GBM，我们还有：

$$\Delta S = \mu S\Delta t + \sigma S\Delta W \sim N(0,\Delta t), (4.4.2)$$

普通期权与布莱-舒尔斯模型

其中 $\mu$ 是漂移，定义如前。现在让我们考虑一个由 -1 份期权和 $\partial f/\partial S$ 份股票组成的组合。换句话说，我们卖空了一份期权并持有 $\partial f/\partial S$ 份股票。组合的价值 $\Pi$ 因此为：

$$\Pi = -f + \frac{\partial f}{\partial S}S,$$ (4.4.3)$$

并且在时间 $\Delta t$ 内组合价值的变化 $\Delta\Pi$ 为：

$$\Delta\Pi = -\Delta f + \frac{\partial f}{\partial S}\Delta S,$$ (4.4.4)$$

将 (4.4.1) 和 (4.4.2) 代入 (4.4.4)，得到：

$$\Delta\Pi = -(\mu S\frac{\partial f}{\partial S} + \frac{\partial f}{\partial t} + \frac{\sigma^2 S^2}{2}\frac{\partial^2 f}{\partial S^2})\Delta t - \sigma S\frac{\partial f}{\partial S}\Delta W$$

