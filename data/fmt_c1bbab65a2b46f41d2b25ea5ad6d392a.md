
```
$E[\epsilon_i^2] = 2\mathcal{K} \int_{0}^{\infty} \frac{\epsilon_i^2 d_i}{(1+\epsilon_i^2/h_i(v-2))^{(v+1)/2}} = 2\mathcal{K}h_i(v-2)^{\frac{(v+1)}{2}} \int_{0}^{\infty} \frac{\epsilon_i^2 d_i}{(h_i(v-2)+\epsilon_i^2)^{(v+1)/2}}$
```

使用附录 E.1 中的标准积分，取 $a=4, b=2, c=(v+1)/2$, 且 $m=(v-2)h_i$，得到

```
$$\frac{m}{h_i}\frac{a+1-bc}{b} = \frac{(h_i(v-2))^{\frac{2-v}{2}}}{2}, \Gamma\left(\frac{a+1}{b}\right) = \Gamma(5/2),\\ \Gamma\left(c-\frac{a+1}{b}\right) = \Gamma\left(\frac{v}{2}\right), \Gamma(c)=\Gamma\left(\frac{v+1}{2}\right)$$
```

## 330 附录 | D 统计函数

以及

```
$E[\epsilon_i^4] = 2\mathcal{K}(h_i(v-2))^{\frac{v+1}{2}} \left\{ \frac{(h_i(v-2))^{\frac{4-v}{2}} \sqrt{\pi}\Gamma((v-2))Gamma((v+1)/2)} \right\}$
```

代入 $\mathcal{K}$ 并简化，我们得到

```
$E[\epsilon_i^4] = \frac{3h_i^2(v-2)}{v(v+4)} (D.2.5)$
```

但是

因此，

```
$$\Gamma\left(\frac{v-2}{2}\right)\Gamma\left(\frac{v-1}{2}\right) = \Gamma\left(\frac{v-1}{2}+1\right) = \Gamma\left(\frac{v}{2}\right)$$
```

```
$E[\epsilon_i^4] = \frac{3h_i^2(v-2)}{v(v+4)}$
```

峰度为

```
$\kappa = \frac{E[\epsilon_i^4]}{(E[\epsilon_i^2])^2} = \frac{3(v-2)}{v(v+4)} (D.3.1)$
```

## 误差分布

本节证明了广误差分布的各种关系。广误差分布的密度函数为

```
$f(\epsilon_i) = \mathcal{K}\exp\left(-\frac{\epsilon_i^2}{2\lambda}\right), \quad \text{where} \mathcal{K} = \frac{1}{\sqrt{2\pi\lambda}} (D.4.1)$
```

## D.4.1 方差 $h_i$ 的 $\lambda$ 值

计算均值为0、方差为 $h_i$ 的误差分布所需的缩放因子 $\lambda$。分布的方差 $E(\epsilon_i^2)$ 给出

```
$E(\epsilon_i^2) = \mathcal{K}\int_{-\infty}^{\infty} \epsilon_i^2\exp\left(-\frac{\epsilon_i^2}{2\lambda}\right)d\epsilon_i = 2\mathcal{K}\int_{0}^{\infty}\epsilon_i^2\exp\left(-\frac{\epsilon_i^2}{2\lambda}\right)d\epsilon_i.$
```

## 节

使用附录 E.1 中的标准积分，取 $n=2, p=a,$ 且 $b=1/2$，得到

```
$h_i = \frac{2\mathcal{K}}{a} \Gamma\left(\frac{3}{2}\right) \left\{\frac{1}{2\lambda}\right\}^$
```

经过一些简化后得到

```
$h_i = \frac{2\mathcal{K}}{a} \Gamma\left(\frac{3}{2}\right) \lambda$
```

代入 $\mathcal{K}$ 并简化得到

```
$h_i = \frac{2\mathcal{K}}{a} \Gamma\left(\frac{3}{2}\right) \lambda$
```

因此，所需的 $\lambda$ 值为

```
$\lambda = \left( h_i 2^{-2/a} \frac{\Gamma(1/a)}{\Gamma(3/a)} \right)^{1/2}$
```

## D.4.2 峰度

```
$E[\epsilon_i^4] = \int_{-\infty}^{\infty} \epsilon_i^4 \exp\left(-\frac{\epsilon_i^2}{2\lambda}\right)d\epsilon_i = 2\mathcal{K}\int_{0}^{\infty} \epsilon_i^4 \exp\left(-\frac{\epsilon_i^2}{2\lambda}\right)d\epsilon_i.$
```

然而，从标准表上

```
$E[\epsilon_i^4] = \frac{1}{(2\lambda)^a} \exp(-b\epsilon_i^a) = \frac{\Gamma(k)}{p^k}$
```

其中 $p=a, b=1/2$ 且 $k=5/a$ 得到

```
$E[\epsilon_i^4] = 2\mathcal{K}(h_i(v-2))^{\frac{v+1}{2}} \frac{5}{a} \Gamma\left(\frac{v}{2}\right)$
```

从附录 E.1 得到

```
$E[\epsilon_i^2] = h_i \frac{2^{-2/a} \Gamma(1/a)}{\Gamma(3/a)}$
```

因此，

```
$E[\epsilon_i^4] = \frac{3h_i^2(v-2)}{v(v+4)}$
```

峰度为

```
$\kappa = \frac{E[\epsilon_i^4]}{(E[\epsilon_i^2])^2} = \frac{3(v-2)}{v(v+4)} \left(\frac{\Gamma(3/a)}{2^{2/a} \Gamma(1/a)}\right)^2$
```

## D.4.3 形状参数 a 的分布

如果分布的方差为 $h_i$，则根据附录 D.4.1

```
$$\lambda = \left( h_i 2^{-2/a} \frac{\Gamma(1/a)}{\Gamma(3/a)} \right)^{1/2}$$
```

现在对于 $0 < x < 1$，我们有 $\Gamma(1+x) = 1+a_1x+a_2x^2+a_3x^3$，其中系数 $|a_i| < 1$，Abramowitz and Steegun (1968)。由于 $x\Gamma(x) = \Gamma(1+x)$，到 $x$ 的三阶得到：

到 $x$ 的三阶得到 $x\Gamma(x) = 1+a_1x+a_2x^2+a_3x^3$。

# 附录 E

# 数学参考

## E.1 标准积分

```
$$\int_{0}^{\infty} exp(-ay^2) dy = \frac{1}{2} \sqrt{\frac{\pi}{a}}, \quad (i)$$
$\int_{0}^{\infty} y \exp(-ay^2) dy = \frac{1}{2}, \quad (ii)$$
$\int_{0}^{\infty} y^2 \exp(-ay^2) dy = \frac{1}{4a} \sqrt{\frac{\pi}{a}}, \quad (iii)$$
$\int_{0}^{\infty} y^3 \exp(-ay^2) dy = \frac{3}{8a^2} \sqrt{\frac{\pi}{a}}, \quad (iv)$$
$\int_{0}^{\infty} y^{2n} \exp(-ay^2) dy = \frac{1 \times 3 \times 5 \dots (2n-1)}{2^{2n+1}a^n} \sqrt{\frac{\pi}{a}}, \quad (v)$$
$\int_{0}^{\pi} \epsilon^n \exp(-b\epsilon^p) = \frac{\Gamma(k)}{p b^k}, \quad n > -p, b > 0, \text{ and } k = \frac{n+1}{p} \quad (vi)$$
$\int_{0}^{\infty} \frac{\epsilon^a d\epsilon}{(m + \epsilon^b)^c} = \frac{1}{b} \frac{\Gamma((\frac{a+1}{b}))}{\Gamma(c-(a+1)/b)} \quad (vii)$
```

其中 $a > -1, b > 0, \text{ 且 } c > (a+1)/b$。

## E.2 Gamma 函数

更多详情请参阅 Abramowitz and Stegun (1968)

```
$$\Gamma(1+x) = x!$$
$x\Gamma(x) = \Gamma(x+1),$$
$\Gamma(\frac{1}{2}) = \sqrt{\pi},$$
$\Gamma(\frac{3}{2}) = \frac{\sqrt{\pi}}{2},$$
$\Gamma(\frac{5}{2}) = \frac{3\sqrt{\pi}}{4},,$$
$\frac{\frac{\partial \log(\Gamma(x))}{\partial x} = \psi(x).$
```

对于 $0 \le x \le 1,$ 我们有

```
$$\Gamma(1+x) = 1 + a_1x + a_2x^2 + a_3x^3 + a_4x^4 + a_5x^5.$
```

其中 $a_1 = -0.5748, a_2 = 0.9512, a_3 = -0.6998, a_4 = 0.4245, \text{ 且 } a_5 = -0.1010$。

## E.3 正态累积分布函数

在本节中，我们展示了正态累积分布函数 $N_1(x)$ 与互补误差函数 erfc(x) 满足以下方程：

```
$N_1(x) = \frac{1}{2}\text{erfc}(-x/\sqrt{2}). \quad (E.3.1)$
```

如果我们令误差函数表示为 erf(x)，则有

```
$$\text{erf}(x) = \frac{2}{\sqrt{\pi}}\int_{0}^{x}\exp(-t^2)dt.$
```

现在我们有以下关系：

erfc(x) = $1 - \text{erf}(x)$, erfc(-x) = $-\text{erf}(x)$, erfc($\infty$) = 1, 以及 erfc(-$x$) = 2 - \text{erf}(x)$。

我们将考虑积分：

```
$I(x) = \frac{2}{\sqrt{\pi}}\int_{-\infty}^{x}\exp(-t^2)dt = \frac{2}{\sqrt{\pi}}\int_{-\infty}^{0}\exp(-t^2)dt + \frac{2}{\sqrt{\pi}}\int_{0}^{x}\exp(-t^2)dt.$
```

由于

```
$$\frac{2}{\sqrt{\pi}}\int_{-\infty}^{0}\exp(-t^2)dt = 1.
```

因此有

```
$I(x) = 1 + \text{erf}(x) = 1 + \{1 - \text{erfc}(x)\} = 2 - \text{erfc}(x).$
```

代入 erf(x)，得到

```
$N_1(x) = 2 - \{2 - \text{erfc}(-x)\} = \text{erfc}(-x).$
```

所以有

```
$$\text{erfc}(-x) = \frac{2}{\sqrt{\pi}}\int_{-\infty}^{x}\exp(-t^2)dt. \quad (E.3.2)$
```

正态分布定义为：

```
$N_1(x) = \frac{1}{\sqrt{\pi}}\int_{-\infty}^{x}\exp(-t^2)dt.$
```

令 $u = t\sqrt{2}$，则 $du = \sqrt{2}dt$，对于上限有 $x = t\sqrt{2}$ 或 $t = x/\sqrt{2}$。该积分变为：

```
$N_1(x) = \frac{1}{\sqrt{\pi}}\int_{-\infty}^{x/\sqrt{2}}\exp(-t^2)dt. \quad (E.3.3)$
```

所以根据方程 (E.3.2)，我们有

```
$N_1(x) = \frac{1}{2}\text{erfc}(-x/\sqrt{2}). \QED$
```

我们还注意到

```
$N_1(-x) = 1 - N_1(x).$```

## E.4 等差数列与等比数列

### 等差数列

等差数列的前 n 项之和为

```
$s_n = \frac{n}{2}\{2a_1 + (n-1)d\}, \quad (E.4.1)$
```

其中 $a_1$ 是首项，$d$ 是公差，即数列中的项为 $a_1, a_1+d, a_1+2d, a_1+3d,\dots$

### 等比数列

等比数列的前 n 项之和为

```
$s_n = \frac{a_1(1-r^n)}{1-r}, \quad (E.4.2)$
```

其中 $a_1$ 是首项，$r$ 是公比，即数列中的项为 $a_1, a_1r, a_1r^2, a_1r^3,\dots$

# 附录 F

## Black-Scholes 有限差分格式

### F.1 一般情况

在本节中，我们考虑第5节描述的有限差分格式的稳定性。假设网格包含 $n_s$ 个点，我们将用 $n_{s-2}$ 维向量 $X^i$ 和 $X^{i+1}$ 表示 $i$ 刻和 $i+1$ 刻的时间依赖值。因此我们可以写道：

```
$X^i = T_1 X^{i+1}, \quad (F.1)$
```

其中 $T_1$ 和 $T_2$ 是 $n_{s-2} \times n_{s-2}$ 的三对角矩阵，$x^i_k = 1, \dots, n_{s-2}$ 用于表示向量 $X^i$ 的元素。

```
$X^i = T_1^{-1} X^{i+1}. \quad (F.2)$
```

然而，方程 (F.2) 只有当 $n_{s-2} \times n_{s-2}$ 矩阵 $T_1^{-1}T_2$ 的特征值模均小于 1 时才是稳定的，参见 Smith (1985)。

### F.2 对数变换与均匀网格

我们将证明隐式差分法 $\theta_m = 0$ 用于均匀网格的对数变换 Black-Scholes 方程是非稳定的，这意味着稳定性不于 $\sigma, \Delta t, \Delta Z$ 的值。

根据第5节，有限差分格式由以下三对角方程组描述：

$$\begin{pmatrix} B & C & 0 & 0 & \dots & 0 \\ A & B & C & 0 & \dots & 0 \\ 0 & A & B & C & \dots & 0 \\ \vdots & \vdots & \ddots & \ddots & \ddots & \vdots \\ 0 & 0 & \dots & A & B & C \\ 0 & 0 & \dots & 0 & A & B \end{pmatrix} \begin{pmatrix} x^{i+1}_1 \\ x^{i+1}_2 \\ x^{i+1}_3 \\ \dots \\ x^{i+1}_{s-2-1} \\ x^{i+1}_{s-2} \end{pmatrix}$$

（注：原文此处存在严重的文本错乱和重复，已根据标准差分格式逻辑进行还原）

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
