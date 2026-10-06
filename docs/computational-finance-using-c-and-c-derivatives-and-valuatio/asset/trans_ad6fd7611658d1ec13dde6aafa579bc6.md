

所以

$$\lambda_{min} > 1 + \Delta t \left(r + \frac{\sigma^2}{\Delta Z^2}\right) - \frac{\sigma^2 \Delta t}{\Delta Z^2}$$

因此，我们有

$|\lambda_{min}| > 1 + r\Delta t$

由于 $r > 0$，我们有

$|\lambda_{min}| > 1$。

## 录录 G

### 布桥：另一种推导方法

在这里，我们对第2章给出的布桥方程提供另一种推导方法。

假设布朗过程在时间 $t_0$ 的取值为 $W_{t_0}$，在时间 $t_1$ 的取值为 $W_{t_1}$。我们想要找到给定 $W_{t_0}$ 时 $W_t$ 的条件分布，其中 $t_0 < t < t_1$。该分布记为 $P(W_t|\{W_{t_0}\})$，其中 $W_t$ 条件于端值 $W_{t_0}$ 和 $W_{t_1}$。我们有

$$P(W_t|W_{t_0}) = \frac{1}{\sqrt{2\pi(t-t_0)}} \exp\left(\frac{(W_t-W_{t_0})^2}{2(t-t_0)}\right)$$

给定 $W_{t_0}$ 时，$W_{t_0}$ 和 $W_{t_1}$ 的联合分布为

$$P(\{W_{t_0},W_{t_1}\}|W_{t_0}) = P(W_{t_0}|W_{t_0})P(W_{t_1}|W_{t_0}) = \frac{1}{\sqrt{2\pi(t-t_0)(t_1-t)}} \exp\left(\left(\frac{(W_t-W_{t_0})^2}{2(t-t_0)} - \frac{(W_{t_1}-W_{t_0})^2}{2(t_1-t)}\right)\right) = \frac{1}{\sqrt{2\pi(t-t_0)(t_1-t)}} \exp\left(\left(-\frac{1}{2}\left(\frac{(W_t-W_{t_0})^2}{2(t-t_0)} + \frac{(W_{t_1}-W_{t_0})^2}{2(t_1-t)}\right)\right)\right)$$

相似地，

$$P(W_{t_1}|W_{t_0}) = \frac{1}{\sqrt{2\pi(t_1-t_0)}} \exp\left(\frac{(W_{t_1}-W_{t_0})^2}{2(t_1-t_0)}\right)$$

现在我们有

$$P(W_t|{W_{t_0},W_{t_1}\}) = \frac{P(W_{t_0},W_{t_1}|W_{t_0})}{P(W_{t_0}|W_{t_0})} = \frac{1}{\sqrt{2\pi(t-t_0)(t_1-t)}} \times \exp\left(\left(-\frac{1}{2}\left(\frac{(W_t-W_{t_0})^2}{2(t-t_0)} + \frac{(W_{t_1}-W_{t_0})^2}{2(t_1-t)}\right)\right\right.$$

为了方便引用，我们将该方程写为

$$P(W_t|{W_{t_0},W_{t_1}}) = \frac{1}{\sqrt{2\pi(t_1-t_0)(t_1-t)}} \exp\left\{A\right\}$$

## 附录 G 布桥：另一种推导方法

我们考虑指数 A 中的项，

$$A = -\frac{1}{2} \left( \frac{(X_1-X_0)^2(t_1-t)(t-t_0)}{(t-t_0)(t_1-t)(t_1-t_0)} + \frac{(X_1-X_0)^2(t-t_0)}{(t-t_0)(t_1-t)(t_1-t_0)} \right) - \frac{(X_1-X_0)^2(t-t_0)(t_1-t)}{(t-t_0)(t_1-t)(t_1-t_0)}$$

将表达式 A 的分子和分母除以 $(t_1-t_0)^2$，我们得到

$$A = -\frac{1}{2V} \left( (W_{t_1}^2 + W_{t_0}^2 - 2W_{t_1}W_{t_0}) \frac{(t_1-t_0)}{(t_1-t_0)^2} + (W_{t_1}^2 + W_{t_0}^2 - 2W_{t_1}W_{t_0}) \frac{(t-t_0)}{(t_1-t_0)^2} \right) - (W_{t_1}^2 + W_{t_0}^2 - 2W_{t_1}W_{t_0}) \frac{(t-t_0)(t_1-t)}{(t_1-t_0)^2}$$

其中 $V = \frac{(t-t_0)(t_1-t)}{(t_1-t_0)^2}$

所以

$$A = -\frac{1}{2V} \left( \frac{(t_1-t)}{(t_1-t_0)} \frac{(t-t_0)}{(t_1-t_0)} \right) + W_{t_1}^2 \frac{(t_1-t)}{(t_1-t_0)^2} + W_{t_0}^2 \frac{(t-t_0)}{(t_1-t_0)^2} - 2W_{t_1}W_{t_0} \frac{(t_1-t)(t-t_0)}{(t_1-t_0)^2}$$

我们证明 A 可以表示为二次型

$$B = -\frac{1}{2V}(W_{t_1}-\mu)^2 = -\frac{1}{2V}(W_{t_1}^2+\mu^2-2\mu)$$

其中 $V = \frac{(t-t_0)(t_1-t)}{(t_1-t_0)^2} \quad \mu = W_{t_0} \frac{(t_1-t)}{(t_1-t_0)} + W_{t_1} \frac{(t-t_0)}{(t_1-t_0)}$

因此我们有

$$B = -\frac{1}{2V} \left( W_{t_0} \frac{(t_1-t)}{(t_1-t_0)} + W_{t_1} \frac{(t-t_0)}{(t_1-t_0)} \right)^2 - 2W_{t_1} \left( W_{t_0} \frac{(t_1-t)}{(t_1-t_0)} + W_{t_1} \frac{(t-t_0)}{(t_1-t_0)} \right)$$

展开并合并项，我们得到

$$B = -\frac{1}{2V} \left( W_{t_0}^2 \frac{(t_1-t)^2}{(t_1-t_0)^2} + W_{t_1}^2 \frac{(t-t_0)^2}{(t_1-t_0)^2} + 2W_{t_1}W_{t_0} \frac{(t_1-t)(t-t_0)}{(t_1-t_0)^2} \right) - 2W_{t_1} \left( W_{t_0} \frac{(t_1-t)}{(t_1-t_0)} + W_{t_1} \frac{(t-t_0)}{(t_1-t_0)} \right)$$

比较 A 和 B 的系数，我们得到：

$W_t^2$ 的系数：

$A : \frac{1}{2V} \left( \frac{(t_1-t)}{(t_1-t_0)} + \frac{(t-t_0)}{(t_1-t_0)} \right) = \frac{1}{2V} \left( \frac{t_1-t_0}{t_1-t_0} \right) = \frac{1}{2V}$，$B : $

$W_{t_0}^2$ 的系数：

$A : \frac{1}{2V} \left( \frac{(t_1-t)^2}{(t_1-t_0)^2} \right) = \frac{1}{2V} \frac{(t_1-t)^2}{(t_1-t_0)^2}$，$B : $

$W_{t_1}^2$ 的系数：

$A : \frac{1}{2V} \left( \frac{(t-t_0)^2}{(t_1-t_0)^2} \right) = \frac{1}{2V} \frac{(t-t_0)^2}{(t_1-t_0)^2}$，$B : $

$W_{t_1}W_{t_0}$ 的系数：

$A : \frac{1}{2V} \left( \frac{2(t_1-t)(t-t_0)}{(t_1-t_0)^2} \right) = \frac{1}{V} \frac{(t_1-t)(t-t_0)}{(t_1-t_0)^2}$，$B : $

A 和 B 中剩余 $W_{t_0}W_{t_1}, W_{t_1}W_t, W_{t_0}W_t$ 的系数是完全相同的。

我们已经证明 $P(W_t|{W_{t_0}, W_{t_1}}) = \frac{1}{\sqrt{2\pi}} \left( \frac{(t_1-t)}{(t_1-t_0)} \right) \exp\left\{ -\frac{(W_t - \mu)^2}{2V} \right\} = \frac{1}{\sqrt{2\pi V}} \exp\left\{ \frac{(W_t - \mu)^2}{2V}\right\}$。因此，$W_t$ 的条件分布是均值为 $\mu = W_{t_0} \frac{(t_1-t)}{(t_1-t_0)} + W_{t_1} \frac{(t-t_0)}{(t_1-t_0)}$ 方差为 $V = \frac{(t-t_0)(t_1-t)}{(t_1-t_0)^2}$的高斯分布，我们可以从该分布中得到变量 $\hat{W}_t$：$\hat{W}_t = W_{t_0} \frac{(t_1-t)}{(t_1-t_0)} + W_{t_1} \frac{(t-t_0)}{(t_1-t_0)} + \sqrt{\frac{(t-t_0)(t_1-t)}{(t_1-t_0)^2}} Z$，其中 $Z \sim N(0,1)$。

## 附录 H

### 布朗运动：更多结果

### H.1 关于布朗运动的性质

在这里，我们将证明关于布朗运动的一些事实。

如果布朗运动具有零漂移，

$$dX_t = \sigma \sqrt{dt} dZ_t, \quad dZ_t \sim N(0,1)$$

$$P(m_t^X \leq b, X_t \geq x) = N_1 \left(\frac{2b-x}{\sigma\sqrt{dt}}\right)$$

其中 $m_t^X$ 表示 $X_t$ 在区间 $[0,t]$ 最小值，$b \leq 0$ 且 $x \geq 0$。

当布朗运动具有非零漂移时，

$$dX_t = vt + \sigma \sqrt{dt} dZ_t, \quad dZ_t \sim N(0,1)$$

且 $m_t^X$ 和 $\tilde{X}_t$ 满足以下方程，

$$P(\tilde{X}_t \leq K) = N_1 \left(\frac{K-vt}{\sigma\sqrt{dt}}\right)$$

$$P(\tilde{X}_t \geq K) = N_1 \left(\frac{vt-K}{\sigma\sqrt{dt}}\right)$$

$$P(m_t^X \leq b, \tilde{X}_t \geq x) = N_1 \left(\frac{2b-x+vt}{\sigma\sqrt{dt}}\right)$$

$$P(m_t^X \leq b, \tilde{X}_t \leq x) = N_1 \left(\frac{2b-x-vt}{\sigma\sqrt{dt}}\right)$$

$$P(m_t^X \leq b) = N_1 \left(\frac{2b-vt}{\sigma\sqrt{dt}}\right)$$

$$P(m_t^X \geq b) = N_1 \left(\frac{vt-2b}{\sigma\sqrt{dt}}\right)$$

其中 $K$ 是常数，$\tilde{X} \geq 0, b \leq 0$ 且 $x \geq 0$，$(condition)$ 表示对应条件的概率，例如 $\tilde{X}_t \geq K, m_t^X \geq b$ 等。

