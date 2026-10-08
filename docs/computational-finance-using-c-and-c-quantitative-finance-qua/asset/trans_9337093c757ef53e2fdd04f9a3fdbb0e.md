
等效地：

$dS_t = S_t \mu dt + S_t \sigma dW_t$

公式 (2.2.2) 和 (2.2.3) 中的过程被称为几何布朗运动；我们将其缩写为 GBM。这是因为相对（而非绝对）价格变化遵循布朗运动。

## 2.3 伊藤公式（或伊藤引理）

在本节中，我们将推导伊藤公式；关于更严谨的处理，可以在 Karatzas 和 Shreve (1991) 中找到。

让我们考虑随机过程 X：

$dX = a dt + b dW = a dt + b \sqrt{dt} dZ, \quad dZ \sim N(0, 1), \quad dN \sim N(0, dt)$

其中 $a$ 和 $b$ 是常数。我们想要找到随机变量 $X$ 的函数所遵循的过程，即 $\phi(X,t)$。这可以通过对两个变量 $X$ 和 $t$ 进行直至二阶的泰勒展开来实现，如下：

$\phi^* = \phi + \frac{\partial \phi}{\partial t} dt + \frac{\partial \phi}{\partial X} dX + \frac{1}{2} \frac{\partial^2 \phi}{\partial X^2} dX^2 + \frac{1}{2} \frac{\partial^2 \phi}{\partial t^2} dt^2 + \frac{\partial \phi}{\partial X} dX dt$

$\phi^*$ 用于表示值 $\phi(X+dX, t+dt)$，而 $\phi$ 表示值 $\phi(X,t)$。我们现在考虑当 $dt \to 0$ 时，$dX^2$dX dt$ 和 $dt^2$ 项的量级。首先

$dX^2 = (a dt + b \sqrt{dt} dZ)(a dt + b \sqrt{dt} dZ) = a^2 dt^2 + 2ab dt^{3/2} dZ + b^2 dt^2$

然后

$dX dt = a dt^2 + b dt^{3/2} dZ$

因此当 $dt \to 0$ 时，忽略所有 $dt$ 阶数大于 1 的项，我们得到：
$dX^2 \sim b^2 dt^2 \quad dt^2 \sim 0, \quad dX dt \sim 0$

因此公式 (2.3.2) 可以重写为：

$d\phi = \frac{\partial \phi}{\partial t} dt + \frac{\partial \phi}{\partial X} dX + \frac{1}{2} \frac{\partial^2 \phi}{\partial X^2} E[dX^2]$

其中 $d\phi = \phi^* - \phi$，我们已经将 $dX^2$ 替换为它的期望值 $E[dX^2]$。现在

$E[dX^2] = E[b^2 dt^2 dZ^2] = b^2 dt$

## 随机过程简介

这里我们使用了 $dZ \sim N(0, 1)$ 的事实，即 $dZ$ 的方差 $E[dZ^2]$ 根据定义等于 1。将这些值代入公式 (2.3.3) 并代入公式 (2.3.1) 中的 $dX$，我们得到：

```
$d\phi = \frac{\partial \phi}{\partial t}dt + \frac{\partial \phi}{\partial X}(a\dt + b\dW) + \frac{b^2}{2}\frac{\partial^2 \phi}{\partial X^2}dt$ (2.3.4)
```

这得到了伊藤公式

```
$d\phi = (\frac{\partial \phi}{\partial t} + a\frac{\partial \phi}{\partial X} + \frac{b^2}{2}\frac{\partial^2 \phi}{\partial X^2})dt + \frac{\partial \phi}{\partial X}b\dW$ (2.3.5)
```

特别是我们正在考虑几何布朗过程：
$dS = \mu S dt + \sigma dW$

其中 $\mu$ 和 $\sigma$ 是常数，将 $X=S, a=\mu S,$ 和 $b=\sigma S$ 代入公式 (2.3.5) 得到：

```
$d\phi = (\frac{\partial \phi}{\partial t} + \mu S\frac{\partial \phi}{\partial S} + \frac{\sigma^2}{2}\frac{\partial^2 \phi}{\partial S^2})dt + \frac{\partial \phi}{\partial S}\sigma dW$ (2.3.6)
```

公式 (2.3.6) 描述了函数 $\phi(S,t)$ 在时间间隔 $dr$ 内的值变化，其中随机 $S$ 遵循 GBM。这一结果在金融衍生品的定价中有许多重要应用。这里函数 $\phi(S,t)$ 被视为金融衍生品的价格 $f(S,t)$，它取决于标的资产 $S$ 的值，该标的资产被假设遵循 GBM。在第 4 章中，我们使用公式 (2.3.3) 来推导出 $\phi = \log(S_t)$ 所遵循的过程。我们有：

```
$$\frac{\partial \log(S_t)}{\partial t} = 0$$
$$\frac{\partial \log(S_t)}{\partial S_t} = \frac{1}{S_t}, \quad \frac{\partial^2 \log(S_t)}{\partial S_t^2} = -\frac{1}{S_t^2}$$
```

所以

```
$d(\log(S_t)) = \nu dt + \sigma dW \quad \text{where } \nu = \mu - \frac{\sigma^2}{2}$ (2.3.7)
```

积分公式 (2.3.7) 得到：

```
$$\int_{t_0}^T d(\log(S_t)) = \int_{t_0}^T \nu dt + \int_{t_0}^T \sigma dW$$
```

所以

```
$$\log(S_T) - \log(S_{t_0}) = \nu T + \sigma W_T$ (2.3.8)
```

这里我们使用了 $t_0 = 0$ 和 $W_0 = 0$。
我们得到

$\log\left(\frac{S_T}{S_{t0}}\right) \sim N(\nu T, \sigma^2 T) \quad (2.3.9)$

并且

$\log\left(\frac{S_T}{S_{t0}}\right) = \nu T + \sigma W_T \quad (2.3.10)$

公式 (2.2.3) 中几何布朗运动 (GBM) 的解为：

$S_T = S_{t0} \exp(\nu T + \sigma W_T), \quad \nu = \mu - \frac{\sigma^2}{2} \quad (2.3.11)$

$t+dt$ 时的资产值可以通过其在 $t$ 刻的值生成：

$S_{t+dt} = S_t \exp(\nu dt + \sigma dW)$

我们已经证明如果资产价格遵循几何运动，那么资产对数遵循标准运动。另一种说法是，在时间间隔 $dt$ 内，资产对数的变化是均值为 $(\mu - \sigma^2/2)dt$，方差为 $\sigma^2 dt$ 的高斯分布。

这些结果很容易推广到包含随时间变化的漂移和波动率。现在不是公式 (2.2.3)，我们有：

$dS_t = S_t \mu dt + \sigma_t dW_t \quad (2.3.12)$

导致

$d(\log(S_t)) = \nu_t dt + \sigma_t dW_t \quad (2.3.13)$

所以

$\int_{t_0}^T d(\log(S_t)) = \int_{t_0}^T \nu_t dt + \int_{t_0}^T \sigma_t dW_t$ 导致 $S_T$ 的以下解：

$S_T = S_{t0} \exp\left(\int_{t_0}^T \nu_t dt + \int_{t_0}^T \sigma_t dW_t\right)$ 其中 $\nu_t = \mu - \frac{\sigma_t^2}{2} \quad (2.3.14)$

公式 (2.3.11) 和 (2.3.14) 中的结果非常重要，稍后引用。

## 2.4 Girsanov 定理

该定理指出对于满足 $\int_0^t k(s)^2 ds < \infty$ 的任意随机 $k(t)$，Radon-Nikodym 导数 $\frac{dQ}{dP} = \rho(t)$ 给出：

$\rho(t) = \exp\left(\int_0^t k(s) dW_s - \frac{1}{2}\int_0^t k(s)^2 ds\right) \quad (2.4.1)$

## 随机过程简介

其中 $W_t^P$ 是概率测度 $P$ 下的布朗运动（可能带有漂移）。在概率测度 $Q$ 下，我们有：

$W_t^Q = W_t^P - \int_0^t k(s) ds \quad (2.4.2)$

其中 $W_t^Q$ 也是布朗运动（可能带有漂移）。我们也可以写为：

$dW_t^P = dW_t^Q + k(t) dt \quad (2.4.3)$

Girsanov 定理提供了一种改变布朗运动漂移的机制。

## 2.5 多资产几何布朗运动的伊藤引理

我们现在考虑 n 维随机过程：

$dX_i = a_i dt + b_i \sqrt{dt} dZ_i = a_idt + b_idW_i, \quad i = 1, \dots, n \quad (2.5.1)$

或者向量形式：

$dX = Ad + \sqrt{dt} BDZ = Ad + BDW \quad (2.5.2)$

其中 $A$ 和 $B$ 分别是包含常数 $a_i, i = 1, \dots, n,$ 和 $b_i = 1, \dots, n$ 的 n 元素向量。随机向量 $dX$ 包含 n 个随机变量 $X_i, i = 1, \dots, n$。

我们假设 n 元素随机向量 $dZ$ 提取自均值为零且协方矩阵为 $\tilde{C}$ 的多元正态分布。即，我们可以写为：

$dZ \sim N(0, \tilde{C})$

由于 $\tilde{C}_{ii} = Var[dW_i] = 1, i = 1, \dots, n$，$\tilde{C}$ 的对角线元素均为单位，且矩阵 $C$ 实际上是一个*相关矩阵*，其非对角线元素给出：

$\tilde{C}_{ij} = E[dW_i dW_j] = \rho_{ij}, \quad i = 1, \dots, n, j = 1, \dots, n, i \neq j,$

其中 $\rho_{ij}$ 是向量 $dZ$ 的 $i$ 个和 $j$ 个元素之间的相关系数。同样，n 元素随机向量 $dW$ 提取自均值为零且协方矩阵为 $C$ 的多元分布。我们可以写为：

$dW \sim N(0, C)$

$C$ 的对角线元素为 $C_{ii} = Var[dW_i] = dt, i = 1, \dots, n$，非对角线元素为

$C_{ij} = E[dW_i dW_j] = \rho_{ij} dt, \quad i = 1, \dots, n, j = 1, \dots, n, i \neq j$

## 14 使用 C 和 C# 进行计算金融

如第 2.3 节所示，我们需要找到随机向量 $X$ 的函数的过程，即 $\phi(X, t)$ 所遵循的过程。这可以通过对变量 $X$ 和 $t$ 进行 $n$ 维直至二阶的泰勒展开来实现，如下：

$$\phi^* = \phi + \frac{\partial\phi}{\partial t}dt + \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}dX_i + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \frac{\partial^2\phi}{\partial X_i\partial X_j}dX_id_j + \frac{1}{2}\frac{\partial^2\phi}{\partial t^2}dt^2 + \sum_{i=1}^n \frac{\partial^2\phi}{\partial X_i\partial t}dX_idt$$

$\phi^*$ 用于表示值 $\phi(X+dX, t+dt)$，而 $\phi$ 表示值 $\phi(X,t)$。我们现在考虑当 $dt \to 0$ 时，$dX^2,dX dt$ 和 $dt^2$ 项的量级。首先

$dX^2 = (a dt + b \sqrt{dt} dZ)(a dt + b \sqrt{dt} dZ) = a^2 dt^2 + 2ab dt^{3/2} dZ + b^2 dt^2$

然后

$dX dt = a dt^2 + b dt^{3/2} dZ$

所以当 $dt \to 0$ 时，忽略所有 $dt$ 阶数大于 1 的项，我们得到：
$dX^2 \sim b^2 dt^2, \quad dt^2 \sim 0, \quad dX dt \sim 0$

因此公式 (2.3.2) 可以重写为：

$d\phi = \frac{\partial \phi}{\partial t} dt + \frac{\partial \phi}{\partial X} dX + \frac{1}{2} \frac{\partial^2 \phi}{\partial X^2} E[dX^2]$

其中 $d\phi = \phi^* - \phi$，我们已经将 $dX^2$ 替换为它的期望值 $E[dX^2]$。现在

$E[dX^2] = E[b^2 dt^2 dZ^2] = b^2 dt$

这里我们使用了 $dZ \sim N(0, 1)$ 的事实，即 $dZ$ 的方差 $E[dZ^2]$ 根据定义等于 1。将这些值代入公式 (2.3.3) 并代入公式 (2.3.1) 中的 $dX$，我们得到：

```
$d\phi = \frac{\partial \phi}{\partial t}dt + \frac{\partial \phi}{\partial X}(a\dt + b\dW) + \frac{b^2}{2}\frac{\partial^2 \phi}{\partial X^2}dt$ (2.3.4)
```

这得到了伊藤公式

```
$d\phi = (\frac{\partial \phi}{\partial t} + a\frac{\partial \phi}{\partial X} + \frac{b^2}{2}\frac{\partial^2 \phi}{\partial X^2})dt + \frac{\partial \phi}{\partial X}b\dW$ (2.3.5)
```

特别是我们正在考虑几何布朗过程：
$dS = \mu S dt + \sigma dW$

其中 $\mu$ 和 $\sigma$ 是常数，将 $X=S, a=\mu S,$ 和 $b=\sigma S$ 代入公式 (2.3.5) 得到：

```
$d\phi = (\frac{\partial \phi}{\partial t} + \mu S\frac{\partial \phi}{\partial S} + \frac{\sigma^2}{2}\frac{\partial^2 \phi}{\partial S^2})dt + \frac{\partial \phi}{\partial S}\sigma dW$ (2.3.6)
```

公式 (2.3.6) 描述了函数 $\phi(S,t)$ 在时间间隔 $dr$ 内的值变化，其中随机 $S$ 遵循 GBM。这一结果在金融衍生品的定价中有许多重要应用。这里函数 $\phi(S,t)$ 被视为金融衍生品的价格 $f(S,t)$，它取决于标的资产 $S$ 的值，该标的资产被假设遵循 GBM。在第 4 章中，我们使用公式 (2.3.3) 来推导出 $\phi = \log(S_t)$ 所遵循的过程。我们有：

```
$$\frac{\partial \log(S_t)}{\partial t} = 0$$
$$\frac{\partial \log(S_t)}{\partial S_t} = \frac{1}{S_t}, \quad \frac{\partial^2 \log(S_t)}{\partial S_t^2} = -\frac{1}{S_t^2}$$
```

所以

```
$d(\log(S_t)) = \nu dt + \sigma dW \quad \text{where } \nu = \mu - \frac{\sigma^2}{2}$ (2.3.7)
```

积分公式 (2.3.7) 得到：

```
$$\int_{t_0}^T d(\log(S_t)) = \int_{t_0}^T \nu dt + \int_{t_0}^T \sigma dW$$
```

所以

```
$$\log(S_T) - \log(S_{t_0}) = \nu T + \sigma W_T$ (2.3.8)
```

这里我们使用了 $t_0 = 0$ 和 $W_0 = 0$。
我们得到

$\log\left(\frac{S_T}{S_{t0}}\right) \sim N(\nu T, \sigma^2 T) \quad (2.3.9)$

并且

$\log\left(\frac{S_T}{S_{t0}}\right) = \nu T + \sigma W_T \quad (2.3.10)$

公式 (2.2.3) 中几何布朗运动 (GBM) 的解为：

$S_T = S_{t0} \exp(\nu T + \sigma W_T), \quad \nu = \mu - \frac{\sigma^2}{2} \quad (2.3.11)$

$t+dt$ 时的资产值可以通过其在 $t$ 刻的值生成：

$S_{t+dt} = S_t \exp(\nu dt + \sigma dW)$

我们已经证明如果资产价格遵循几何运动，那么资产对数遵循标准运动。另一种说法是，在时间间隔 $dt$ 内，资产对数的变化是均值为 $(\mu - \sigma^2/2)dt$，方差为 $\sigma^2 dt$ 的高斯分布。

这些结果很容易推广到包含随时间变化的漂移和波动率。现在不是公式 (2.2.3)，我们有：

$dS_t = S_t \mu dt + \sigma_t dW_t \quad (2.3.12)$

导致

$d(\log(S_t)) = \nu_t dt + \sigma_t dW_t \quad (2.3.13)$

所以

$\int_{t_0}^T d(\log(S_t)) = \int_{t_0}^T \nu_t dt + \int_{t_0}^T \sigma_t dW_t$ 导致 $S_T$ 的以下解：

$S_T = S_{t0} \exp\left(\int_{t_0}^T \nu_t dt + \int_{t_0}^T \sigma_t dW_t\right)$ 其中 $\nu_t = \mu - \frac{\sigma_t^2}{2} \quad (2.3.14)$

公式 (2.3.11) 和 (2.3.14) 中的结果非常重要，稍后引用。

## 2.4 Girsanov 定理

该定理指出对于满足 $\int_0^t k(s)^2 ds < \infty$ 的任意随机 $k(t)$，Radon-Nikodym 导数 $\frac{dQ}{dP} = \rho(t)$ 给出：

$\rho(t) = \exp\left(\int_0^t k(s) dW_s - \frac{1}{2}\int_0^t k(s)^2 ds\right) \quad (2.4.1)$

## 随机过程简介

其中 $W_t^P$ 是概率测度 $P$ 下的布朗运动（可能带有漂移）。在概率测度 $Q$ 下，我们有：

$W_t^Q = W_t^P - \int_0^t k(s) ds \quad (2.4.2)$

其中 $W_t^Q$ 也是布朗运动（可能带有漂移）。我们也可以写为：

$dW_t^P = dW_t^Q + k(t) dt \quad (2.4.3)$

Girsanov 定理提供了一种改变布朗运动漂移的机制。

## 2.5 多资产几何布朗运动的伊藤引理

我们现在考虑 n 维随机过程：

$dX_i = a_i dt + b_i \sqrt{dt} dZ_i = a_idt + b_idW_i, \quad i = 1, \dots, n \quad (2.5.1)$

或者向量形式：

$dX = Ad + \sqrt{dt} BDZ = Ad + BDW \quad (2.5.2)$

其中 $A$ 和 $B$ 分别是包含常数 $a_i, i = 1, \dots, n,$ 和 $b_i = 1, \dots, n$ 的 n 元素向量。随机向量 $dX$ 包含 n 个随机变量 $X_i, i = 1, \dots, n$。

我们假设 n 元素随机向量 $dZ$ 提取自均值为零且协方矩阵为 $\tilde{C}$ 的多元正态分布。即，我们可以写为：

$dZ \sim N(0, \tilde{C})$

由于 $\tilde{C}_{ii} = Var[dW_i] = 1, i = 1, \dots, n$，$\tilde{C}$ 的对角线元素均为单位，且矩阵 $C$ 实际上是一个*相关矩阵*，其非对角线元素给出：

$\tilde{C}_{ij} = E[dW_i dW_j] = \rho_{ij}, \quad i = 1, \dots, n, j = 1, \dots, n, i \neq j,$

其中 $\rho_{ij}$ 是向量 $dZ$ 的 $i$ 个和 $j$ 个元素之间的相关系数。同样，n 元素随机向量 $dW$ 提取自均值为零且协方矩阵为 $C$ 的多元分布。我们可以写为：

$dW \sim N(0, C)$

$C$ 的对角线元素为 $C_{ii} = Var[dW_i] = dt, i = 1, \dots, n$，非对角线元素为

$C_{ij} = E[dW_i dW_j] = \rho_{ij} dt, \quad i = 1, \dots, n, j = 1, \dots, n, i \neq j$
