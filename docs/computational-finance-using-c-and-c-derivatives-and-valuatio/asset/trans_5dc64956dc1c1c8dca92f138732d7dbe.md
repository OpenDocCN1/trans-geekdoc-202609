

## 资产价格运动的布朗模型

在这里，我们使用了事实（见附录 C.3.1）$Var[a+b]=b^2Var[X]$,其中 $a=\mu T$ 且 $b=1$。根据方程 (2.1.9) 和方程 (2.10,1)，我们得到

```
$$Var[X_T] = Var \left[ \sigma \sqrt{dt} \sum_{i=1}^n dZ_i \right] = T \sigma^2.$$
```

因此，在时间 $T$，颗粒的位置 $X_T$ 分布为 $X_T \sim N(\mu T, T \sigma^2)$。

我们刚刚证明了当改变布朗运动的漂移时，它的波动率保持不变。这是一个非常重要的性质（正如我们稍后看到的），在衍生品定价理论中被广泛使用。

## 2.2 资产价格运动的布朗模型

在上节中，我们展示了布朗运动可以描述悬浮在液体中的微粒运动。利用布朗运动描述金融资产价格运动的首次尝试是由 Bachelier (1900) 提出的。然而，这种尝试成功有限，因为资产价格特定变化的*显著性*取决于原始资产价格。例如，一只原始价格为 £1.10 的股票价值增加 £1，其*显著性*比原始价格为 £100 的股票价值增加 £1 要大得多。正因如此，资产价格运动通常用*相对*变化或百分比变化来描述。例如，如果 £1.10 的股票增加了 £11，而 £100 的股票也增加了（相应的比例的金额），这两种价格变化具有相同的显著性，并对应于价值增长了 10%。股票价值中相对价格变化的思想可以通过定义时间 $t$ 时股票的*收益率* $R_t$ 量来形式化。收益率 $R_t$ 的定义如下：

```
$$R_t = \frac{S_{t+dt}-S_t}{S_t} = \frac{dS_t}{S_t}, \quad (2.2.1)$$
```

其中 $S_{t+dt}$ 是时间 $t+dt$ 时股票的价值，$S_t$ 是时间 $t$ 时股票的价值，$dS_t$ 是股票在时间间隔 $dt$ 内价值的变化。时间间隔 $dt$ 内的百分比收益率 $R^*$ 简单定义为 $R^* = 100 \times R_t$。

现在我们就可以构建一个简单的资产价格运动布朗模型了，但关于金融领域布朗运动的更多信息可以在 Shreve et al. (1997) 中找到。
时间 $t$ 的资产收益率现在给出：

```
$$R_t = \frac{dS_t}{S_t} = \mu dt + \sigma dW_t, \quad dW_t \sim N(0,dt), \quad (2.2.2)$$
```

或等价于 $$dS_t = S_t \mu dt + S_t \sigma dW_t. \quad (2.2.3).$$

方程 (2.2.2) 和方程 (2.2.3) 给过程被称为几何布朗运动，我们简写为 GBM。这是因为相对（而非绝对）过程遵循布朗运动。

## 2.3 伊藤公式（或引理）

在本节中，我们将推导出伊藤公式，这比我们在 Karatas and Shreve (2000) 中看到的处理更严谨。

让我们考虑随机过程 $X$，

```
$dX = a dt + b dW =ad + b\sqrt{dt} dZ, \quad dZ \sim N(0,dt), \quad dW \sim N(0,dt). \quad (2.3.1)$
```

**其中** $a$ 和 $b$ 是常数。我们想要找到随机变量 $X$ 的函数遵循的过程，即 $\phi(X,t)$。这可以通过对变量 $X$ 和 $t$ 应用二阶泰勒展开来完成，如下：

```
$\phi^* = \phi + \frac{\partial \phi}{\partial t}dt + \frac{\partial \phi}{\partial X}dX + \frac{1}{2}\frac{\partial^2 \phi}{\partial X^2}dX^2 + \frac{1}{2}\frac{\partial^2 \phi}{\partial t^2}dt^2 + \frac{\partial^2 \phi}{\partial X\partial t}dXdt, \quad (2.3.2)$
```

$\phi^*$ 用于表示值 $\phi(X+dX)$

```
$dX^2 = (adt + b\sqrt{dt} dZ)(adt + b\sqrt{dt} dZ) = a^2dt^2 + 2ab dt^{3/2} dZ + b^2 dt^2$,
```

然后

```
$dXdt = a^2dt + b dt^{3/2} dZ$.
```

因此，当 $dt \to 0$ 时，忽略 $dt$ 中所有阶大于 1 的项，我们得到

```
$dX^2 \sim b^2 dt, \quad dt^2 \sim 0, \quad \text{and} dXdt \sim 0$.
```

因此，方程 (2.3.2) 可以重写为

```
$d\phi = \frac{\partial \phi}{\partial t}dt + \frac{\partial \phi}{\partial X}dX + \frac{1}{2}\frac{\partial^2 \phi}{\partial X^2} E[dX^2]. \quad (2.3.3)$
```

其中 $d\phi = \phi^* - \phi$，我们用 $dX^2$ 替换了它的期望值 $E[dX^2]$。现在

```
$E[dX^2] = b^2 dt,
```

我们使用了 $dZ \sim N(0,dt)$，$dZ$ 的方差为 1 的事实。将这些值代入方程 (2.3.3) 并从方程 (2.3.1) 代入 $dX$，我们得到

```
$d\phi = \frac{\partial \phi}{\partial t}dt + \frac{\partial \phi}{\partial X}(adt + bdW) + \frac{b^2}{2}\frac{\partial^2 \phi}{\partial X^2}dt. \quad (2.3.4)$
```

这给伊藤公式

```
$d\phi = (\frac{\partial \phi}{\partial t} + a\frac{\partial \phi}{\partial X} + \frac{b^2}{2}\frac{\partial^2 \phi}{\partial X^2})dt + b\frac{\partial \phi}{\partial X}dW. \quad (2.3.5)$
```

特别是，如果我们考虑几何布朗过程

```
$dS = \mu dt + \sigma S$
```

其中 $\mu$ 和 $\sigma$ 是常数，将 $X = S, a = \mu S, b = \sigma S$ 代入方程 (2.3.5) 得到

```
$df = \frac{\partial \phi}{\partial t}dt + \mu S \frac{\partial \phi}{\partial S} + \frac{\sigma^2 S^2}{2}\frac{\partial^2 \phi}{\partial S^2} dt + \sigma S dW.3.6$
```

(2.3.6) 描述了当随机变量 $S$ 遵循 GBM 时，在时间间隔 $dt$ 内函数 $\phi(S,t)$ 的变化。该结果在衍生品定价中具有非常重要的应用。这里，函数 $\phi(S,t)$ 被视为衍生品的价格，它取决于底层资产 $S$，该资产假设遵循 GBM。在第 4 章中，我们将使用方程 (2.3.6) 来推导由衍生品价格 $\phi = \log(S)$ 满足的 Black-Scholes 微分方程。我们还使用方程 (2.3.3) 来推导

```
$\frac{\partial \phi}{\partial S} = \frac{\partial \log(S)}{\partial S} - \frac{\sigma^2}{S^2}$.
$\frac{\partial \phi}{\partial t} = 0.
```

所以，

```
$d(\log(S)) = vdt + \sigma dW_t, \quad \text{where } v = \mu - \frac{\sigma^2}{2}. \quad (2.3.7)$
```

积分 (2.3.7) 得到

```
\int_{0}^T d(\log(S_t)) = \int_{0}^T vdt + \int_{0}^T \sigma dW_t,
```

所以

```
\log(S_T) - \log(S_0) = vT + \sigma W_T. \quad (2.3.8)
```

其中我们使用了 $t_0 = 0$ 和 $W_0 = 0$。

我们得到

```
\log(\frac{S_T}{S_0}) \sim N(vT, \sigma^2T). \quad (2.3.9)
```

因此

```
\log(\frac{S_T}{S_0}) = vT + \sigma W_T. \quad (2.3.10)
```

方程 (2.2.3) 中 GBM 的解为

```
$$S_T = S_0 \exp(vT + \sigma W_T), \quad \nu = \mu - \frac{\sigma^2}{2}. \quad (2.3.11)$$
```

因此，时间 $t+dt$ 的资产价值可以从其在时间 $t$ 的价值生成

```
$$S_{t+dt} = S_t \exp(vdt + \sigma dW_t)$$
```

我们已经证明，如果资产价格遵循 GBM，资产价格对数遵循标准布朗运动。这种另一种说法是，在时间 $dt$ 内，资产价格对数的变化是均值为 $[\mu - (\sigma^2/2)]$、方差为 $\sigma^2dt$ 的高斯分布。
这些结果可以推广到包含随时间变化的漂移和波动率。代替方程 (2.2.3)，我们有

```
$dS_t = S_t dt + \sigma_t dW_t$
```

导致

```
$d(\log(S_t)) = v_t dt + \sigma_t dW_t$
```

所以

```
$$\int_{t_0}^T d(\log(S_t)) = \int_{t_0}^T v_t dt + \int_{t_0}^T \sigma_t dW_t.$$
```

## 2.4 吉萨诺定理

该定理指出，对于任何满足 $\int_0^t k(s)^2 ds < \infty$ 的随机过程 $k(t)$，拉东-尼科姆导数 $dQ/d\mathbb{P} = \rho(t)$ 给出：

```
$$\rho(t) = \exp(\int_0^t k(s)dW_s - \frac{1}{2} \int_0^t k(s)^2ds),$$
```

其中 $W_t^P$ 在概率测 $\mathbb{P}$ 下也是布朗运动（可能带有漂移），我们参考 Baxter and Rennie (1996)。在概率测 $\mathbb{Q}$ 下，我们有

```
$W_t^Q = W_{t_0}^P - \int_0^t k(s)ds,$
```

## 2.5 多资产 GBM 的伊藤引理

我们现在考虑 n 维随机过程

```
$dX_i = a_i dt + b_i dW_i, \quad i = 1, \dots, n$.
```

