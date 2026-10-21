
等价地，

$$\dot{c}(t) = q(t) \cdot \exp\left( \int g(t) dt \right). \tag{97A.8}$$

因此，

$$c(t) = \int q(t) \cdot \exp\left( \int g(t) dt \right) dt. \tag{97A.9}$$

将方程 (97A.9) 代入方程 (97A.3)，我们得到方程 (97A.1) 的通解，

$$p(t) = \exp\left( - \int g(t) dt \right) \cdot \left[ \int q(t) \exp\left( \int g(t) dt \right) dt \right]. \tag{97A.10}$$

为求解方程 (97A.12)，我们将应用上述结果。令 $g(t) = \lambda \frac{\dot{n}(t)}{n(t)} - k$ 且 $q(t) = -H(t)$。由于

$$\begin{aligned}\exp\left( \int g(t) dt \right) &= \exp\left( \int \left( \lambda \frac{\dot{n}(t)}{n(t)} - k \right) dt \right) \\ &= \exp\left( \lambda \int \frac{\dot{n}(t)}{n(t)} dt - kt \right) \\ &= \exp\left( \lambda \ln(n(t)) - kt + c \right) \\ &= c_1 \cdot n(t)^{\lambda} \exp(-kt),\end{aligned}\tag{97A.11}$$

其中 $c_1 > 0$。

然后我们有

$$P(t) = c_2 \cdot n(t)^{-\lambda} \exp(kt) \cdot \left[ \int q(t) c_3 \cdot n(t)^{\lambda} \exp(-kt) dt \right], \tag{97A.12}$$

其中 $c_2 > 0$ 且 $c_3 > 0$ 或等价地，

$$P(t) = c_4 \cdot \frac{e^{kt}}{n(t)^{\lambda}} \cdot \left[ \int -H(t) \frac{n(t)^{\lambda}}{e^{kt}} dt \right], \tag{97A.13}$$

其中 $c_4 > 0$。

最后，我们有

$$P(t) = c \frac{e^{kt}}{n(t)^{\lambda}} \cdot \int H(t) n(t)^{\lambda} e^{-kt} dt, \tag{97A.14}$$

将不定积分改为定积分，方程 (97A.13) 可表示为

$$p(t) = \frac{e^{kt}}{n(t)^{\lambda}} \int_{t}^{T} H(s) n(s)^{\lambda} e^{-ks} ds,$$

这就是方程 (97.16)。

## 附录 97B：方程 (97.20) 的推导

本附录详细介绍了推导方程 (97.20) 的过程。遵循 Euler–Lagrange 条件（参见 Chiang, 1984），我们首先对方程 (97.17) 关于 t 求一阶条件，仅允许 n(t) 和 g(t) 随时间变化，并将一阶条件设为零。然后我们得到

$$\frac{\partial p(0)}{\partial t}\bigg|_{\dot{g}(t)=0} = (\lambda - 1) n(t)^{\lambda-2} \dot{n}(t) [r(t) - g(t)] A'(0) \exp\left(\int_0^t g(s) ds\right) - a' A'^2(0) \sigma^2(t) (\lambda - 2) n(t)^{\lambda-3} \dot{n}(t) \exp\left(2 \int_0^t g(s) ds\right) = 0, \qquad (97B.1)$$

$$\frac{\partial p(0)}{\partial t}\bigg|_{\dot{n}(t)=0} = \left[ n(t)^{\lambda-1} r(t) A'(0) g(t) \exp\left(\int_0^t g(s) ds\right) - n(t)^{\lambda-1} A'(0) \dot{g}(t) \exp\left(\int_0^t g(s) ds\right) - n(t)^{\lambda-1} A'(0) g(t)^2 \exp\left(\int_0^t g(s) ds\right) \right] - \left[ 2 a' A'^2(0) \sigma^2(t) n(t)^{\lambda-2} g(t) \exp\left(2 \int_0^t g(s) ds\right) \right] = 0. \qquad (97B.2)$$

重新排列方程 (97B.1) 和 (97B.2) 后，我们可以得到方程 (97.18) 和 (97.19)。

$$n(t) = \frac{(\lambda - 2) a' A'(0) \sigma^2(t) \exp\left(\int_0^t g(s) ds\right)}{(\lambda - 1) [r(t) - g(t)]}, \qquad (97.18)$$ $$n(t) = \frac{2 a' A'(0) \sigma^2(t) \exp\left(\int_0^t g(s) ds\right)}{r(t) - g(t) - \dot{g}(t)/g(t)}. \qquad (97.19)$$

因此，由方程 (97.18) 和 (97.19)，我们可以推导出以下众所周知的 logistic 微分方程为

$$\lambda g(t)^2 - \lambda r(t) g(t) + (2 - \lambda) \dot{g}(t) = 0. \qquad (97.20)$$

## 附录 97C：方程 (97.21) 的推导

本附录详细推导了方程 (97.21) 的解。偏微分方程，方程 (97.20)，是一个 logistic 方程（或 Verhulst 模型），由 Pierre Verhulst 于 1845、1847 年首次发表。为求解 logistic 方程，我们首先将方程 (97.20) 重写为 logistic 方程的标准形式。

dg(t)/dt = A g(t) (1 - g(t)/B). (97C.1)
where
A = λ r̄ / (2 - λ) and B = r̄.

使用变量分离法分离 g 和 t：
A dt = dg(t) / [g(t) (1 - g(t)/B)]
= dg(t)/g(t) + [dg(t)/B] / (1 - g(t)/B). (97C.2)

接下来我们对方程 (97C.2) 的两边积分，
At + C = ln(g(t)) - ln(1 - g(t)/B). (97C.3)

对方程 (97C.3) 的两边取指数，
C · exp(At) = g(t) / (1 - g(t)/B). (97C.4)

当 t = 0 时，g(t) = g0，方程 (97C.4) 可写为
C = g0 / (1 - g0/B) = B g0 / (B - g0). (97C.5)

将方程 (97C.5) 代入方程 (97C.4)，
(B g0)/(B - g0) · exp(At) = g(t) / (1 - g(t)/B). (97C.6)

求解 g(t)，
g(t) = [ (B g0)/(B - g0) exp(At) ] / [ 1 + ( (B g0)/(B - g0) exp(At) ) / B ]

= \frac{B g_0 \exp(At)}{B - g_0 + g_0 \exp(At)}

= \frac{B g_0}{g_0 + (B - g_0) \exp(-At)}. \tag{97C.7}

将 $A = \frac{\lambda \bar{r}}{(2 - \lambda)}$ 和 $B = \bar{r}$ 代入方程 (97C.7)，我们最终得到方程 (97.20) 的解，

$g(t) = \frac{\frac{\bar{r}}{(1 - L)}}{1 + \left(\frac{\bar{r}}{g_0} - 1\right) \exp\left(\frac{\lambda \bar{r} t}{\lambda - 2}\right)},$

这就是方程 (97.21)。

## 附录 97D：方程 (97.26) 的推导

本附录详细推导了方程 (97.26)。为了得到最优 $n(t)$ 的表达式，已知 $\bar{r}(t) = \bar{r}$，我们将方程 (97.21) 代入方程 (97.18) 并得到

$n(t) = \frac{(2 - \lambda) a' A'(0) \sigma^2(t) e^{\int_0^t g^*(s) ds}}{(1 - \lambda) (\bar{r} - g^*(t))}. \tag{97D.1}$

由方程 (97.15)、(97.18) 和 (97.21)，我们有

$H(t) = \frac{(\bar{r} - g^*(t))^2 (1 - \lambda)}{a' \sigma^2(t) (2 - \lambda)^2}. \tag{97D.2}$

将方程 (97D.1) 和 (97D.2) 代入方程 (97.16)，我们得到

$p(t) = \left( \frac{e^{k t}}{n(t)^\lambda} \frac{1 - \lambda}{a' (2 - \lambda)^2} \int_t^T \frac{n(s)^\lambda}{\sigma^2(s)} (\bar{r} - g^*(s))^2 e^{-k s} ds \right), \text{ or }$

$p(t) = \left[ \frac{e^{k t - \lambda \int_0^t g^*(s) ds} (1 - \lambda) (\bar{r} - g^*(t))^\lambda}{\sigma^2(t)^\lambda a' (2 - \lambda)^2} \right] W, \tag{97D.3}$

其中 $W = \int_t^T e^{\lambda \int_0^s g^*(u) du - k s} \sigma^2(s)^{\lambda - 1} (\bar{r} - g^*(s))^{2 - \lambda} ds.$

由方程 (97D.1)，我们有

$$\dot{n}(t) = \frac{(2 - \lambda) a' A'(0) \dot{\sigma}^2(t) e^{\int_0^t g^*(s) ds} + (2 - \lambda) a' A(0) \sigma^2(t) g^*(t) e^{\int_0^t g^*(s) ds}}{(1 - \lambda) (\bar{r} - g^*(t))} + \frac{(2 - \lambda) a' A'(0) \sigma^2(t) e^{\int_0^t g^*(s) ds} \dot{g}^*(t)}{(1 - \lambda) (\bar{r} - g^*(t))^2}.\tag{97D.4}$$

由方程 (97D.3) 和 (97D.4)，我们有新股发行产生的金额

$$\dot{n}(t) p(t) = \frac{A(0)}{\sigma^2(t)^{\lambda} (2 - \lambda)} \big[ (\dot{\sigma}^2(t) + \sigma^2(t) g^*(t)) (\bar{r} - g^*(t)) + \sigma^2(t) \dot{g}^*(t) \big] \cdot \big[ e^{k t - (\lambda -1) \int_0^t g^*(s) ds} (\bar{r} - g^*(t))^{\lambda -2} \big] W\tag{97D.5}$$

由方程 (97.1)、(97.6) 和 (97D.5)，我们可以得到 $\bar{D}(t) = n(t) \bar{d}(t)$ 且 $\bar{Y}(t) = \bar{r}(t) A(0) e^{\int_0^t g(s) ds}$。因此，最优支付比率可写为

$$\frac{\bar{D}(t)}{\bar{Y}(t)} = \left[ 1 - \frac{g^*(t)}{\bar{r}(t)} \right] \cdot \left[ 1 + \left[ e^{k t - \lambda \int_0^t g^*(s) ds} \right] \frac{\lambda \big[ (\dot{\sigma}^2(t) + \sigma^2(t) g^*(t)) (\bar{r} - g^*(t)) + \sigma^2(t) \dot{g}^*(t) \big]}{(2 - \lambda) \sigma^2(t)^{\lambda} (\bar{r} - g^*(t))^{3 - \lambda}} W \right]\tag{97.26}$$

其中 $W = \int_t^T e^{\int_0^s g^*(u) du - k s} \sigma^2(s)^{\lambda -1} (\bar{r} - g^*(s))^{2 - \lambda} ds.$

## 第 98 章

### 资产定价模型双重回归检验中的横截面相关测量误差*

Thomas Gramespacher、Armin Bänziger 和 Norbert Hilber

### 目录

- 98.1 引言 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3466
- 98.2 双重回归检验中的偏差 . . . . . . . . . . . . . . . . . . . . . . . 3470
- 98.2.1 模型及解析表达式的推导 . 3470
- 98.2.2 讨论 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3472
- 98.3 模拟 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3475
- 98.4 结论 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3481
- 参考文献 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3482
- 附录 98A：斜率估计量的泰勒展开 . . . . . 3483
- 附录 98B：双参数协方差矩阵的情况 . . . . 3486

Thomas Gramespacher
苏黎世应用科技大学
e-mail: grat@zhaw.ch
Armin Bänziger
苏黎世应用科技大学
e-mail: banz@zhaw.ch
Norbert Hilber
苏黎世应用科技大学
e-mail: hino@zhaw.ch

*本章是对论文“The bias in two-pass regression tests of asset-pricing models in presence of idiosyncratic errors with cross-sectional dependence,” Review of Pacific Basin Financial Markets and Policies, World Scientific Publishing Co. Pte. Ltd., vol. 22(02), pages 1–17, October 2019. 的更新和扩展。
