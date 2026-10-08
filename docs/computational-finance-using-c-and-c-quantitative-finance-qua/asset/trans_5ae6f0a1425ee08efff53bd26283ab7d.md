
使用 C 和 C# 的计算金融学

与 $P(m_t^X \leqslant b, X_t \geqslant x)$ 相关的条件概率密度函数为：

```
$p(m_{t_2}^X \leqslant b, X_{t_2} | X_{t_1}) = \frac{1}{\sigma\sqrt{2\pi\Delta t}}\exp\left(\frac{2v(b-X_{t_1})}{\sigma^2}\right)\exp\left(-\frac{(X_{t_1} + X_{t_2} - 2b + \nu\Delta t)}{2\sigma^2\Delta t}\right) (H.1.10)$
```

其中 $t_2 \geqslant t_1$ 且 $\Delta t = t_2 - t_1$。

## H.2 公式 (H.1.2) 的证明

根据公式 (H.1.1)：

$X_t = \sigma\sqrt{t}, Z_t \sim N(0, 1)$

其中 $X_0 = 0$。我们将推导事件 $m_t^X \leqslant b$ 和 $X_t \geqslant x$ 发生的概率。对于每个事件 $m_\tau^X$ 的发生，必须存在一个时间 $\tau$ 使得 $X_\tau \leqslant b$，其中 $0 < \tau \leqslant t$。在时间 $\tau$，我们不再继续原有的布朗运动，而是考虑由以下定义的*反射*运动 $X_t^R$：

```
$X_s^R = X_s, \quad s < \tau$
X_s^R = 2b - X_s, \quad s \geqslant \tau$
```

因此，在时间 $\tau$ 之前，运动 $X_s$ 与事件 $X_s^R$相同。对于 $s \geqslant \tau$，$X_s^R$ 的*坐标*通过关于水平 $b$ 反射 $X_s$ 的值得到（记住 $b \leqslant x$）。此时事件 $X_t \geqslant x$ 等价于事件 $X_t^R \leqslant 2b-x$（记住 $b \leqslant 0$ 且 $x \geqslant 0$）。然而，事件 $X_\tau^R \leqslant 2b-x$ 只有在 $m_\tau^X \leqslant b$ 同时发生时才会发生，即：

```
$P(X_\tau^R \leqslant 2b-x) = P(m_\tau^X \leqslant b, X_\tau \leqslant x)$
```

在时间 $\tau$ 时

```
$X_\tau^R = 2b - X_\tau \quad(H.2.1)$
```

在时间 $\tau$ 之后

```
$X_{\tau+\gamma}^R = 2b - X_{\tau+\gamma}, \quad \gamma > 0 \quad(H.2.2)$
```

因此，从公式 (H.2.2) 减去公式 (H.2.1) 得：

```
$X_{\tau+\gamma}^R - X_\tau^R = X_\tau - X_{\tau+\gamma}$
X_{\tau+\gamma}^R - X_\tau^R = -(X_{\tau+\gamma} - X_\tau) \quad(H.2.3)$
```

然而，我们知道：

```
$(X_{\tau+\gamma} - X_\tau) \sim N(0, \sigma^2\gamma) \quad(H.2.4)$
```

所以

```
$(X_{\tau+\gamma}^R - X_\tau^R) \sim -N(0, \sigma^2\gamma)
```

# 附录 H：布朗运动：更多结果

这意味着：

```
$X_{t+\gamma}^R - X_t^R \sim N(0, \sigma^2\gamma) \quad (H.2.5)$
```

由于公式 (H.2.4) 和 (H.2.5) 的左侧具有相同的分布，且 $X_t$ 满足第 2.1 节给出的三个布朗属性，我们可以写道：

```
$P(X_t^R \le 2b-x) = P(X_t \le 2b-x) = N_1\left(\frac{2b-x}{\sigma\sqrt{t}}\right)$
```

因此：

```
$P(m_t^X \le b, X_t \ge x) = N_1\left(\frac{2b-x}{\sigma\sqrt{t}}\right)$
```

## H.3 公式 (H.1.4) 的证明

根据公式 (H.1.3) $\bar{X}_t = vt + \sigma\sqrt{t}Z_t, Z_t \sim N(0, 1)$。所以我们可以写道：

```
$P(\bar{X}_t \le K) = P(vt + \sigma\sqrt{t}Z_t \le K)$
= P\left(Z_t \le \frac{K-vt}{\sigma\sqrt{t}}\right)$
= N_1\left(\frac{K-vt}{\sigma\sqrt{t}}\right), Z_t \sim N(0, 1)$
```

## H.4 公式 (H.1.5) 的证明

我们知道 $P(\bar{X}_t \ge K) = 1 - P(\bar{X}_t \le K)$。代入公式 (H.1.4) 得：

```
$P(\bar{X}_t \ge K) = 1 - N_1\left(\frac{K-vt}{\sigma\sqrt{t}}\right)$
```

由于 $1 - N_1(x) = N_1(-x)$，我们得到：

```
$P(\bar{X}_t \ge K) = N_1\left(\frac{vt-K}{\sigma\sqrt{t}}\right)$
```

## H.5 公式 (H.1.6) 的证明

根据公式 (H.1.1)：

```
$dX_t = \sigma\sqrt{dt}Z_t, d_t \sim N(0, 1)$
```

这可以表示为概率测度 $P$ 下的零漂移布朗运动：

```
$dX_t = \sigma dW_t^P, \quad dW_t^P \sim N(0, dt) \quad (H.5.1)$
```

或者

```
$X_t = \sigma W_t^P, \quad W_t^P \sim N(0, t)$
```

现在我们可以选择另一个概率测度 $Q$， 使得：

```
$dW_t^P = dW_t^Q + \frac{\nu}{\sigma}dt \quad (H.5.2)$
```

其中 $\nu$ 是一个常数。在概率测度 $Q$ 下，公式 (H.5.1) 中的运动为：

```
$\widetilde{X}_t = \sigma \left(dW_t^Q + \frac{\nu}{\sigma}dt\right) \quad (H.5.3)$
```

所以

```
$\widetilde{X}_t = \nu dt + \sigma dW_t^Q \quad (H.5.4)$
```

从第 2.4 节可以看出，测度 $P$ 和 $Q$ 之间的变换可以通过 $k = \nu/\sigma$ 实现，相应的 Radon-尼科洛夫导数为：

```
$\frac{dQ}{dP} = \exp\left(kW_t^P - \frac{1}{2}k^2\right)$
$= \exp\left(\frac{\nu}{\sigma}W_t^P - \frac{1}{2}\left(\frac{\nu}{\sigma}\right)^2\right)$
$= \exp\left(\frac{\nu}{\sigma}X_t - \frac{\nu^2}{2t}\right) \quad (H.5.5)$
```

其中我们在概率测度 $P$ 下可以写道：

```
$\widetilde{W}_t^P = X_t/\sigma$
```

现在

```
$P(\widetilde{X}_t^P \le b, \widetilde{X}_t^P \ge x) = E^Q[\mathbb{I}_{\widetilde{X}_t^Q \le b}(\widetilde{X}_t^Q \ge x)] \quad (H.5.6)$
```

其中 $\mathbb{I}_{\{\widetilde{X}_t^P \le b\}}$ 是指示函数，在条件满足时取单位值，否则为 0——例如 $\mathbb{I}_{\{\widetilde{X}_t^P \le b\}}$ 在 $\widetilde{X}_t^P \le b$ 时为 1，在 $\widetilde{X}_t^P > b$ 时为 0。然而，对于 Baxter 和 Rennie (1996)，我们有：

```
$E^Q[\mathbb{I}_{\widetilde{X}_t^P \le b}(\widetilde{X}_t^P \ge x)] = E^P[\mathbb{I}_{\widetilde{X}_t^Q \le b}]\frac{dQ}{dP} \quad (H.5.7)$
```

所以从公式 (H.5.5) 代入 $\frac{dQ}{dP}$ 得：

```
$E^Q[\mathbb{I}_{\widetilde{X}_t^P \le b}(\widetilde{X}_t^P \ge x)] = E^P[\mathbb{I}_{\widetilde{X}_t^Q \le b}\exp\left(\frac{\nu X_t}{\sigma} - \frac{\nu^2 t}{2}\right)] \quad (H.5.8)$
```

# 附录 H：反射布朗运动

用反射布朗运动 $X_t^R = 2b - X_t$ 表示，公式 (H.5.8) 可以写为：

```
$P(m_t^X \le b, \bar{X}_t \ge x) = E^P[\mathbb{I}_{X_t^R \le b}(X_t^R \ge x)] \exp\left(\frac{\nu(X_t^R)}{\sigma} - \frac{\nu^2 t}{2}\right) \quad (H.5.9)$
```

由于 $\mathbb{I}_{X_t^R \le b} = \mathbb{I}_{2b-X_t \le b} = \mathbb{I}_{X_t \ge b}$（错误）且 $\mathbb{I}_{X_t^R \ge x} = \mathbb{I}_{2b-X_t \ge x} = \mathbb{I}_{X_t \le 2b-x}$，公式 (H.5.9) 变为：

```
$P(m_t^X \le b, \bar{X}_t \ge x) = \exp\left(\frac{2\nu b}{\sigma^2}\right) E^P[\mathbb{I}_{X_t < 2b-x} \exp\left(\frac{\nu X_t}{\sigma} - \frac{\nu^2 t}{2}\right)] \quad (H.5.10)$
```

其中，对于符号，我们现在用 $X_t^R$ 代替公式 (H.5.10) 的右侧：

```
$P(m_t^X \le b, \bar{X}_t \ge x) = \exp\left(\frac{2\nu b}{\sigma^2}\right) E^P[\mathbb{I}_{X_t^R \le b}(X_t^R \ge x)] \exp\left(\frac{\nu(X_t^R)}{\sigma} - \frac{\nu^2 t}{2}\right)$
```

对于符号，我们用 $X_t^R$ 代替 $X_t$：

```
$P(m_t^X \le b, \bar{X}_t \ge x) = \exp\left(\frac{2\nu b}{\sigma^2}\right) E^P[\mathbb{I}_{X_t^R \le b}(X_t^R \ge x)] \exp\left(\frac{\nu(X_t^R)}{\sigma} - \frac{\nu^2 t}{2}\right)$
```

因此：

```
$P(m_t^X \le b, \bar{X}_t \ge x) = \exp\left(\frac{2\nu b}{\sigma^2}\right) E^P[\mathbb{I}_{X_t < 2b-x} \exp\left(\frac{\nu X_t}{\sigma} - \frac{\nu^2 t}{2}\right)]$
```

（注：此处原文似乎存在大量重复和混乱，翻译文已根据逻辑进行了整理对齐）
