

## 随机过程简介

```
$d\phi = \left( \frac{\partial\phi}{\partial t} + \sum_{i=1}^n a_i\frac{\partial\phi}{\partial X_i} + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n b_{ij}b_j\rho_{ij}\frac{\partial^2\phi}{\partial X_i\partial X_j} \right)dt\+ \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}b_idW_i \quad (2.5.7)
```

如果我们考虑几何布朗运动：
$dS_i = \mu_i S_i dt + \sigma_i S_i dW_i, \quad i = 1,\dots,n$，

其中 $\mu_i$ 是第 $i$ 个资产的常数漂移，$\sigma_i$ 是将变量 $X_i = S_i, a_i = \mu_i S_i,$ 和 $b_i = \sigma_i S_i$ 代入方程 (2.5.7) 后的结果：

```
$d\phi = \left( \frac{\partial\phi}{\partial t} + \sum_{i=1}^n \mu_i S_i\frac{\partial\phi}{\partial X_i} + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j S_i S_j\rho_{ij}\frac{\partial^2\phi}{\partial X_i\partial X_j} \right)dt\+ \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}\sigma_i S_i dW_i \quad (2.5.8)
```

## 2.6 二维下的 Ito 积法则与除法则

现在我们将推导两个随机过程之积与除的表达式，其中 $\phi = \phi(X_1, X_2)$，

```
$dX_1 = a_1 dt + b_1 dW_1 \quad \quad dX_2 = a_2 dt + b_2 dW_2$
```

可以使用以下二维版本的 Ito 引理：

```
$d\phi = \frac{\partial\phi}{\partial X_1}dX_1 + \frac{\partial\phi}{\partial X_2}dX_2 + \frac{1}{2}E\sum_{i=1}^2\sum_{j=1}^2 \frac{\partial^2\phi}{\partial X_i\partial X_j}dX_i dX_j \quad (2.6.1)
```

其中我们使用了 $\frac{\partial\phi}{\partial t} = 0$ 这一事实。

### 2.6.1 Ito 积法则

这里 $\phi = \phi(X_1, X_2)$，偏导数如下：

```
$\frac{\partial\phi}{\partial X_1}=X_2, \quad\ \frac{\partial\phi}{\partial X_2}=X_1, \quad\ \frac{\partial^2\phi}{\partial X_1^2}=0, \quad\ \frac{\partial^2\phi}{\partial X_2^2}=0.\n\frac{\partial^2\phi}{\partial X_1\partial X_2}=1$
```

因此使用方程 (2.6.1)

```
$d\phi = X_2 dX_1 + X_1 dX_2 + \frac{2E[dX_1dX_2]}{2}
```

以及积法则：

$d(X_1X_2) = X_2 dX_1 + X_1 dX_2 + E[dX_1dX_2]$

单随机源的布朗运动

对于 $X_1$ 为布朗运动且 $X_2$ 无随机项的特殊情况，我们有：

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad dX_2 = X_2\mu_2 dt$

现在

$E[dX_1dX_2] = E[(X_1\mu_1 dt + X_1\sigma_1 dW_1)X_2\mu_2 dt] \\ \n = X_1X_2\mu_1\mu_2 dt^2 + X_1X_2\sigma_1\mu_2 dt dW_1 = 0$

其中我们忽略了阶数高于 1 的 $dt$ 项，并使用了 $E[dW_1] = 0$。

因此方程 (2.6.2) 变为：

$d(X_1X_2) = X_2 dX_1 + X_1 dX_2$

$d(X_1X_2) = X_2(X_1\mu_1 dt + X_1\sigma_1 dW_1) + X_1\mu_2 dt$

所以我们得到：

$d(X_1X_2) = (X_1X_2)(\mu_1 + \mu_2) dt + X_1X_2\sigma_1 dW_1$

### 2.6.2 Ito 除法则

这里 $\phi = \phi(X_1/X_2)$，偏导数是：

$\frac{\partial\phi}{\partial X_1} = \frac{1}{X_2}, \quad \frac{\partial\phi}{\partial X_2} = -\frac{X_1}{X_2^2}, \quad \frac{\partial^2\phi}{\partial X_1^2} = 0, \quad \frac{\partial^2\phi}{\partial X_2^2} = \frac{2X_1}{X_2^3}, \quad \frac{\partial^2\phi}{\partial X_1\partial X_2} = -\frac{1}{X_2^2}$

因此使用方程 (2.6.1)

$d\phi = \frac{\partial\phi}{\partial X_1}dX_1 + \frac{\partial\phi}{\partial X_2}dX_2 + \frac{1}{2}\frac{\partial^2\phi}{\partial X_1^2}dX_1^2 + \frac{1}{2}\frac{\partial^2\phi}{\partial X_2^2}dX_2^2 + \frac{\partial^2\phi}{\partial X_1\partial X_2}dX_1dX_2$

$d\phi = \frac{1}{X_2}dX_1 - \frac{X_1}{X_2^2}dX_2 + \frac{1}{2}\frac{2X_1}{X_2^3}dX_2^2 - \frac{1}{X_2^2}dX_1dX_2$

我们得到除法的表达式：

$d(\frac{X_1}{X_2}) = \frac{X_1}{X_2}\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2} + \frac{dX_2^2}{X_2^2} - \frac{dX_1dX_2}{X_1X_2}\right]$ 布朗运动

这里有

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad \text{and} \quad dX_2 = X_2\mu_2 dt$

或者

$\frac{dX_1}{X_1} = \mu_1 dt + \sigma_1 dW_1 \quad \text{and} \quad \frac{dX_2}{X_2} = \mu_2 dt + \sigma_2 dW_2$

因此

$E\left[\frac{dX_2}{X_2}\right]\left(\frac{dX_2}{X_2}\right) = E[(\mu_2 dt + \sigma_2 dW_2)(\mu_2 dt + \sigma_2 dW_2)]$
$= E[\mu_2^2 dt^2] + E[\sigma_2^2(dW_2)^2] + 2E[\mu_2\sigma_2 dt dW_2]$
$= \mu_2^2 dt^2 + \sigma_2^2 dt + 2\dots$ 

这导致了

$E\left[\frac{dX_2}{X_2}\right]\left(\frac{dX_2}{X_2}\right) = \sigma_2^2 dt \quad (2.6.5)$ 其中我们忽略了阶数高于 1 的 $dt$ 项，并使用了 $E[dW_2] = 0$。

以类似的方式

$E\left[\frac{dX_1}{X_1}\right]\left(\frac{dX_2}{X_2}\right) = E[(\mu_1 dt + \sigma_1 dW_1)(\mu_2 dt + \sigma_2 dW_2)]$
$= E[\mu_1\mu_2 dt^2] + E[\mu_1\sigma_2 dt dW_2] + E[\sigma_1\mu_2 dt dW_1] + E[\sigma_1\sigma_2 dW_1dW_2]$
$= \sigma_1\sigma_2 E[dW_1dW_2]$

这得到了

$E\left[\frac{dX_1}{X_1}\right]\left(\frac{dX_2}{X_2}\right) = \sigma_1\sigma_2 dt \quad (2.6.6)$ 其中我们像之前一样使用了 $E[dW_1 dW_2] = \rho_{12} dt$。

将这些代入方程 (2.4)，我们有

$d[\frac{X_1}{X_2}] = \frac{X_1}{X_2}\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2} + \sigma_2^2 dt - \sigma_1\sigma_2\rho_{12} dt\right]$ 产生了：

$d(\frac{X_1}{X_2}) = \frac{X_1}{X_2}\left[\mu_1 - \mu_2 + \sigma_2^2 - \sigma_1\sigma_2\rho_{12}\right]dt + \left(\frac{X_1}{X_2}\right)[\sigma_1 dW_1 - \sigma_2 dW_2] \quad (2.6.7)$ 单随机源的布朗运动

我们有

$dX_1 = X_1\mu_1 dt + X_1\sigma_1 dW_1 \quad dX_2 = X_2\mu_2 dt$

如之前

$E\left[\frac{dX_2}{X_2}\right]\left(\frac{dX_2}{X_2}\right) = E[\mu_2^2 dt] \rightarrow 0$

$E\left[\frac{dX_1}{X_1}\right]\left(\frac{dX_2}{X_2}\right) = E[(\mu_1 dt + \sigma_1 dW_1)\mu_2 dt] = E[\mu_1\mu_2 dt^2 + \sigma_1\mu_2 dt dW_1] = \mu_1\mu_2 dt^2 + \sigma_1\mu_2 dt E[dW_1] \rightarrow 0$

因此

$d(\frac{X_1}{X_2}) = \frac{X_1}{X_2}\left[\frac{dX_1}{X_1} - \frac{dX_2}{X_2}\right] = \left(\frac{X_1}{X_2}\right)(\mu_1 dt + \sigma_1 dW_1 - \mu_2 dt)$

所以最终表达式是：

$d(\frac{X_1}{X_2}) = \left(\frac{X_1}{X_2}\right)[\mu_1 - \mu_2]dt + \left(\frac{X_1}{X_2}\right)[\sigma_1 dW_1] \quad (2.6.8)$

## 2.7 n 维下的 Ito 积

使用方程 (2.5.7)，现在我们将推导 $n$ 个随机过程之积的表达式。在这种情况下 $\phi \rightarrow \prod_{i=1}^n X_i$，偏导数如下：

$\frac{\partial\phi}{\partial X_i} = \phi\frac{dX_i}{X_i} \text{ 对于 } i=1, \dots, n$

$\frac{\partial^2\phi}{\partial X_i^2} = 0 \text{ 对于 } i=1, \dots, n$

$\frac{\partial^2\phi}{\partial X_i\partial X_j} = \phi\frac{dX_i}{X_i}\frac{dX_j}{X_j} \text{ 对于 } i \neq j$

$\frac{\partial\phi}{\partial t} = 0$

将其代入方程 (2.5.7)，我们有

$d\phi = \sum_{i=1}^n \frac{\partial\phi}{\partial X_i}dX_i + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \frac{\partial^2\phi}{\partial X_i\partial X_j}dX_i dX_j$

$d\phi = \sum_{i=1}^n \phi\frac{dX_i}{X_i}dX_i + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \phi\frac{dX_i}{X_i}\frac{dX_j}{X_j}dX_i dX_j$

$d\phi = \phi \sum_{i=1}^n \frac{dX_i^2}{X_i} + \frac{1}{2}\phi \sum_{i=1}^n\sum_{j=1}^n \frac{dX_i dX_j}{X_i X_j}$

由于 $dX_i^2 = \sigma_i^2 X_i^2 dt$，且 $dX_i dX_j = \sigma_i\sigma_j X_i X_j \rho_{ij} dt$，

$d\phi = \phi \sum_{i=1}^n \sigma_i^2 X_i dt + \frac{1}{2}\phi \sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j \rho_{ij} dt$

$d\phi = \phi \left( \sum_{i=1}^n \sigma_i^2 X_i + \frac{1}{2}\sum_{i=1}^n\sum_{j=1}^n \sigma_i\sigma_j \rho_{ij} \right) dt$

## 2.8 布朗桥

设布朗过程在 $t_0$ 时刻有 $W_{t0}$，在 $t_1$ 时刻有 $W_{t1}$。我们想找到 $W_t$ 的条件分布，其中 $t_0 < t < t_1$。该分布将记为 $P(W_t|W_{t0}, W_{t1})$，表示 $W_t$ 依赖于边界值 $W_{t0}$ 和 $W_{t1}$。我们把 $W_{t0}$ 和 $W_{t1}$ 写为：

$W_t = W_{t0} + \sqrt{t-t_0}X_t, \quad X_t \sim N(0, 1),$ $(2.8.1)$

$W_t = W_{t1} - \sqrt{t_1-t}Y_t, \quad Y_t \sim N(0, 1)$ $(2.8.2)$

其中 $X_t$ 和 $Y_t$ 是独立的正态变量。结合方程 (2.8.1) 和 (2.8.2)，我们有：

$W_{t0} + \sqrt{t-t_0}X_t = W_{t1} - \sqrt{t_1-t}Y_t$

重写为：

$W_{t1} - W_{t0} = \sqrt{t-t_0}X_t + \sqrt{t_1-t}Y_t$

解出 $X_t$：

$X_t = \frac{W_{t1} - W_{t0} + \sqrt{t_1-t}Y_t}{\sqrt{t-t_0}}$

由于 $W_{t1}-W_{t0}$ 是均值为 0，方差为 $t_1-t_0$ 的正态分布，且 $Y_t$ 与之独立，因此 $X_t$ 服从正态分布：

$X_t \sim N\left( \frac{W_{t1} - W_{t0}}{\sqrt{t-t_0}}, \frac{t_1-t}{t-t_0} \right)$

这就是布朗桥。

