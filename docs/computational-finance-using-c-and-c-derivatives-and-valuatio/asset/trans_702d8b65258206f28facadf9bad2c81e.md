

# 22 章 | 2 随机过程简介

## 无条件平均

无条件平均为：

$E[Y_{w,t}] = E\left[\exp(-\alpha t) W\left(\frac{\sigma^2 \exp(2\alpha t)}{2\alpha}\right)\right], \text{ 其中 } \alpha > 0 \text{ 且 } t \to \infty. (2.9.16)$

因此，

$E[Y_{w,t}] = 0. (2.9.17)$

## 无条件方差与协方差

设

$Y_{w,t} = \exp(-\alpha t) \Psi_t, \text{ 其中 } \psi_t = \left(\frac{\sigma^2 \exp(2\alpha t)}{2\alpha}\right). (2.9.18)$

且

$Y_{w,s} = \exp(-\alpha s) \Psi_s, \text{ 其中 } \psi_s = \left(\frac{\sigma^2 \exp(2\alpha s)}{2\alpha}\right). (2.9.19)$

协方差为

$Cov[Y_{w,s}, Y_{w,t}] = E[Y_{w,t} Y_{w,s}] - E[Y_{w,t}] E[Y_{w,s}] = E[Y_{w,t} Y_{w,s}]. (2.9.20)$

因为 $E[Y_{w,t}] = E[Y_{w,t}] = 0$。

将 $Y_{w,t}$ 的符号简化为 $Y_t$，我们得到

$Cov[Y_s, Y_t] = E[\exp(-\alpha t) \Psi_t \Psi_s] = \exp(-\alpha(t + s)) E\{\Psi_t \Psi_s\}$.

根据方程 (2.1.2)，

$E[W_s, W_t] = s \wedge t. (2.9.21)$

因此，如果 $s \le t$，

$E[\Psi_t \Psi_s] = \Psi_s. (2.9.22)$

且

$Cov[Y_s, Y_t] = \frac{\exp(-\alpha(t + s)) \sigma^2 \exp(2\alpha s)}{2\alpha} = \frac{\sigma^2}{2\alpha}\exp(-\alpha(t - s)). (2.9.23)$

无条件方差（通过令 $s = t$ 得到）为

$Var[Y_t] = \frac{\sigma^2}{2\alpha}. (2.9.24)$

## 2.10 ORNSTEIN UHLENBEC 过程

Ornstein Uhlenbeck 过程由于其均值回归性质，常用于建模利率。它由以下方程定义

$dX_t = -\alpha X_t dt + \sigma dW_t. (2.10.1)$

$\E\left[ \{X_t - X_{t_0} \exp(-\alpha t)\}^2 \right].$

然而根据方程 (2.10.5)，

$X_t - X_{t_0} \exp(-\alpha t) = \sigma \exp(-\alpha t) \int_{s=0}^{s=t} \exp(\alpha s) ds$

将上述表达式代入方程 (2.10.8)，

$Var[X_t] = E \left[\{\exp(-\alpha t) \sigma \int_{s=0}^{s=t} \exp(\alpha s) dW_s\}^2\right] (2.10.9)$

$Var[X_t] = \sigma^2 \exp(-2\alpha t) E \left\{\int_{s=0}^{s=t} \exp(\alpha s) dW_s\}^2\right] (2.10.10)$

使用 Ito 等距性（见 2.12.2 节），

$E \left\{\{\int_{s=0}^{s=t} \exp(\alpha s) dW_s\}^2\right] = E \left[\int_{s=0}^{s=t}\{\exp(\alpha s)\}^2 ds\right]$

利用 Fubini 定理（见 2.12.1 节），

$E \left[\int_{s=0}^{s=t}\{\exp(\alpha s)\}^2 ds\right] = \int_{s=0}^{s=t} \exp(2\alpha s) ds = \left\{\frac{\exp(2\alpha s)}{2\alpha}\right]_{s=0}^{s=t} = \frac{\exp(2\alpha t)-1}{2\alpha}$

将上述结果代入方程 (2.10.10)，

$Var[X_t] = \sigma^2 \left\{\frac{\exp(2\alpha t)-1}{2\alpha}\right\} (2.10.11)$

得到方差的表达式

$Var[X_t] = \sigma^2 \left\{\frac{\exp(-2\alpha t)}{2\alpha}\right\} (2.10.11)$

方程 (2.10.7) 和 (2.10.11) 中导出的均值和方差允许我们写出 $X_t$ 的分布为

$X_t \sim N(X_{t_0} \exp(-\alpha t), \sigma^2 \left\{\frac{\exp(-2\alpha t)}{2\alpha}\right\}) (2.10.12)$

如果 $X_{t_0} = 0$，则简化为

$X_t \sim N(0, \sigma^2 \left\{\frac{\exp(-2\alpha t)}{2\alpha}\right\}) (2.10.13)$

## Ornstein Uhlenbeck Bridge

从 $X_0$ 到 $X_t$ 的转移密度为

$P(X_t|X_0) = \sqrt{\frac{K}{2\pi(1-y^2)}} \exp\left\{ \frac{K(X_t - X_0) \exp(-\alpha(t-t_0))}{1-y^2}\right\} (2.10.14)$

其中 $K = 2\alpha/\sigma^2$ 且 $y = \exp(-\alpha(t-t_0))$。Ornstein Uhlenbeck 随机路径可以使用以下模拟

$X_{t+dt} = X_t \exp(-\alpha dt) + \sigma \sqrt{\frac{1-\exp(-2\alpha dt)}{2\alpha}} dZ. (2.10.15)$

根据方程 (2.10.14)，我们可以写出

$E[X_{t+dt}|X_t] = X_t \exp(-\alpha dt)$
$Var[X_{t+dt}|X_t] = \sigma^2 \left\{\frac{1-\exp(-2\alpha dt)}{2\alpha}\right\}$

我们现在证明当 $dt \to 0$ 时方程 (2.10.15) 退化为 GBM。我们可以对指数项取一阶展开得到

$X_{t+dt} = X_t (1-\alpha dt) + \sigma \sqrt{dt} dZ = X_t - \alpha X_t dt + \sigma dZ,$

这是一个具有漂移 $-\alpha$ 和波动率 $\sigma$ 的 GBM。

$dX_t = -\alpha X_t dt + \sigma dW_t.$

## ORNSTEIN UHLBEC BRIDGE

设 Ornstein Uhlenbeck 过程在 $t_0$ 处的值为 $X_0$，在 $t_1$ 处的值为 $X_1$。我们对中间点 $X_t$ 的分布感兴趣，即 $P(X_t|X_0, X_1)$，其中 $t_0 < t < t_1$。我们将证明 $X_t$ 是高斯分布，其均值为

$\mu_t = X_0 \exp(-\alpha(t-t_0)) \left\{\frac{1-\exp(-2\alpha(t_1-t))}{1-y^2}\right\} + X_1 \exp(-\alpha(t_1-t)) \left\{\frac{1-\exp(-2\alpha t)}{1-y^2}\right\} (2.11.1)$

且条件方差

$V_t = \frac{(1-\exp(-2\alpha(t-t_0)))(1-\exp(-2\alpha(t_1-t)))}{2\alpha (1-\exp(-2\alpha(t_1-t_0)))} (2.11.2)$

证明。标准 Ornstein Uhlenbeck 过程 $(\sigma = 1)$ 定义为

$dX_t = -\alpha X_t dt + \sqrt{dt} dZ. (2.11.3)$

根据 2.10，

$X_t = X_{t_0} \exp(-\alpha(t-t_0)) + \left\{\frac{1-\exp(-2\alpha(t-t_0))}{2\alpha}\right\} d_t, (2.11.4)$

且从 $X_0$ 到 $X_t$ 的转移密度为

$P(X_t|X_0) = \frac{\sqrt{2\alpha}}{\sqrt{2\pi(1-\exp(-2\alpha(t-t_0))}} \exp \left\{\frac{-\alpha (X_t - X_0) \exp(-\alpha(t-t_0))}{1-\exp(-2\alpha(t-t_0))}\right\} (2.11.5)$

给定 $X_0$ 下，$X_t$ 和 $X_1$ 的联合密度为

$P(X_t, X_1|X_0) = P(X_t|X_0) P(X_1|X_0). (2.11.6)$

我们有

$P(X_t, X_1|X_0) = \kappa \exp \left\{\frac{\alpha (X_t - X_0) \exp(-\alpha(t-t_0))}{1-\exp(-2\alpha(t-t_0))}\right\} \times \exp \left\{\frac{\alpha (X_1 - X_0) \exp(-\alpha(t_1-t_0))}{1-\exp(-2\alpha(t_1-t_0))}\right,$

其中 $\kappa = (1/2)\pi \times \alpha / \left[ \frac{1}{1-\exp(-2\alpha(t-t_0))} (1 - \exp(-2\alpha(t_1-t))) \right]$。给定 $X_0$ 和 $X_1$ 下 $X_t$ 的分布 $P(X_t|X_0, X_1)$ 为

$P(X|\{X_{t_0}, X_1\}) = \frac{P(X_1,X|X_0)}{P(X_1|X_0)} (2.11.7)$

其中

$P(X_1|X_0) = \frac{\sqrt{2\alpha}}{\sqrt{2\pi(1-\exp(-2\alpha(t_1-t_0))}} \exp \left\{\frac{-\alpha (X_1 - X_0) \exp(-\alpha(t_1-t_0))}{1-\exp(-2\alpha(t_1-t_0))}\right\} (2.11.8)$

通过一些代数运算，我们可以重新表达

$P(X_t|X_0, X_1) = \dots$ (2.11.9)$

