

# 2008年金融危机章节 | 9.8

在评级下调后的第二天，AIG采取了最后的努力来筹集额外资金。管理层与高盛、摩根士大通以及纽约联邦储备银行（纽约联储）的代表会面，讨论建立一个由各金融机构承销的总额为750亿美元的担保贷款机制。然而，私营部门并未提供贷款，美国政府决定介入。

2008年9月16日，官方宣布纽约联储将通过850亿美元的信贷额度来救助AIG。

2009年3月，《纽约时报》发表了一篇基于AIG为监管机构准备的21页机密文件的文章，该文件标题为《A.I.G.：风险具有系统性吗？》。文中提到，AIG旗下的保险子公司在美国发行了3.75亿保单，面值高达19万亿美元。

没有人能确切知道AIG破产将造成的损害范围。其规模和互联性，加上金融市场已经处于严重困境的事实，引发了人们的担忧，即AIG的失败将导致整个金融系统的崩溃。联邦政府不愿承担这一风险，因此通过超过1825亿美元的救助方案救助了AIG。

## 附录 A

## 欧式末期期权的希腊字母

### A.1 引言

在本节中，我们将介绍一些有用的结果，这些结果以后将用于导出希腊字母的表达式。

微积分的一个基本结果是：

```
$$\frac{\partial}{\partial x} \int f(x)dx = f(x).$ (A.1.1)$$
```

此外，不定积分 $\int f(x)dx$ 可以表示为具有变量上界的定积分：

```
$$\int f(x)dx = \int_{a}^{x} f(x)dx + c.
```

所以

```
$$\frac{\partial}{\partial x} \int_{y=a}^{y=x} f(y)dy = f(x).$ (A.1.2)$$
```

我们现在可以使用这个结果来获得累积分布函数的导数：

```
$N_1(x) = \frac{1}{\sqrt{2\pi}} \int_{y=-\infty}^{y=x} exp(-y^2/2)dy.$
```

得到：

```
$$\frac{\partial N_1(x)}{\partial x} = n(x),$ (A.1.3)$$
```

其中

```
$n(x) = \frac{1}{\sqrt{2\pi}} exp(-x^2/2).$
```

我们现在为Black-Scholes方程中出现的参数 $d_1$ 和 $d_2$ 推出各种结果：

```
$d_1 = \frac{\log(S/E) + (r - q + \sigma^2/2)(T - t)}{\sigma \sqrt{T - t}}$ (A.1.4)$
```

以及

```
$d_2 = \frac{\log(S/E) + (r - q - \sigma^2/2)(T - t)}{\sigma \sqrt{T - t}} = d_1 - \sigma \sqrt{T - t}}.$ (A.1.5)$
```

我们有

```
$$\frac{\partial d_2}{\partial S} = \frac{\partial d_1}{\partial S}-\frac{1}{S\sqrt{T-t}}, \quad (A.1.6)$$
```

```
$$\frac{\partial d_2}{\partial \sigma} = \frac{\partial d_1}{\partial \sigma}-\sqrt{T-t}, \quad (A.1.7)$$
```

```
$$\frac{\partial d_1}{\partial r} = \frac{\partial d_2}{\partial r}-\frac{\sqrt{T-t}}{\sigma}, \quad (A.1.8)$$
```

```
$$\frac{\partial d_2}{\partial t} = \frac{\partial d_1}{\partial t}-\frac{\sigma}{2(T-t)}, \quad (A.1.9)$$
```

此外

```
$n(d_2) = \frac{1}{\sqrt{2\pi}}exp(-d_2^2/2)
= \frac{1}{\sqrt{2\pi}}exp(-d_1^2/2)\exp\{d_1\sqrt{T-t}-\sigma^2(T-t)/2\}
= n(d_1)\exp\{log(S/E)+(r-q+\sigma^2/2)(T-t)-\sigma^2(T-t)/2\}$
```

所以

```
$n(d_2) = \frac{S}{E}n(d_1)\exp(r(T-t))exp(-q(T-t)).\quad (A.1.10)$
```

我们注意到

```
$$\frac{\partial N(d_1)}{\partial S} = \frac{\partial N(d_1)}{\partial d_1}\frac{\partial d_1}{\partial S} = n(d_1)\frac{1}{S\sqrt{T-t}}$$

这种技术将用于计算希腊字母。

### A.2 GAMMA

Gamma定义为期权价格对标的的的二阶导数。这意味着（见A3）它是Delta的变化率。对于欧式看涨期权，Gamma值为：

```
$$\Gamma_c = \frac{\partial^2\Delta_c}{\partial S^2}=\frac{\partial\Delta_c}{\partial S}\frac{\partial}{\partial S}\{N_1(d_1)\exp(-q(T-t))\}$
```

$\Delta_c$ 的值在附录A3给出。因此，欧式看跌期权的Gamma值可以相似计算：

```
$$\Gamma_p = \frac{\partial^2\Delta_p}{\partial S^2}=\frac{\partial\Delta_p}{\partial S}\frac{\partial}{\partial S}\{(1-N_1(d_1))\exp(-q(T-t))\}$
```

其中我们使用了 $\Delta_p$ 的值。因此，

```
$$\Gamma_p = \Gamma_c = \frac{n(d_1)}{S\sqrt{T-t}} \exp(-q(T-t)).\quad (A.2.2)$$
```

所以看跌期权看涨期权的Gamma是相同的。

### A.3 DELTA

Delta定义为期权价格对标的的变化率。对于欧式看涨期权，我们有：

```
$\Delta_c = \frac{\partial c}{\partial S} = \frac{\partial}{\partial S}\{S\exp(-q(T-t))N_1(d_1) - E\exp(-r(T-t))N_1(d_2)\}$
```

所以

```
$\Delta_c = \exp(-q(T-t)) \left(N_1(d_1) + Sn(d_1)\frac{\partial d_1}{\partial S}\right) - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial S}.\quad (A.3.1)$
```

代入 $n(d_2)$ 和 $\partial d_2/\partial S$，得到：

```
$\Delta_c = \exp(-q(T-t))N_1(d_1).\quad (A.3.2)$
```

同样，对于欧式看跌期权有：

```
$\Delta_p = \frac{\partial p}{\partial S} = \frac{\partial}{\partial S}\{E\exp(-r(T-t))(1-N_1(d_2)) - S\exp(-q(T-t))(1-N_1(d_1))\}$
```

所以

```
$\Delta_p = -E\exp(-r(T-t))n(d_2) - \exp(-q(T-t))\left\{1-N_1(d_1) + Sn(d_1)\frac{\partial d_1}{\partial S}\right\}\quad (A.3.3)$
```

代入 $n(d_2)$ 和 $\partial d_2/\partial S$，得到：

```
$\Delta_p = \exp(-q(T-t))N_1(d_1) - 1.\quad (A.3.4)$
```

### A.4 THETA

Theta定义为期权价格随时间的变化率。对于欧式看涨期权，我们有：

```
$\Theta_c = \frac{\partial c}{\partial t} = \frac{\partial}{\partial t}\{S\exp(-q(T-t))N_1(d_1) - E\exp(-r(T-t))N_1(d_2)\}$
```

```
= q\exp(-q(T-t))SN_1(d_1) + \exp(-q(T-t))Sn(d_1)\frac{\partial d_1}{\partial t} - E\exp(-r(T-t))N_1(d_2) - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial t};$
```

代入 $n(d_2)$ 和 $\partial d_2/\partial t$，得到：

```
$\Theta_c = q\exp(-q(T-t))SN_1(d_1) - rE\exp(-r(T-t))N_1(d_2) - \frac{Sn(d_1)\sigma\exp(-q(T-t))}{2\sqrt{T-t}}$
```

因此，Theta值为：

```
$\Theta_c = \exp(-q(T-t))\left\{q - SN_1(d_1)\frac{Sn(d_1)\sigma}{2\sqrt{T-t}}\right{\ - rE \exp(-r(T-t))N_1(d_2).$ (A.4.1)$
```

对于看跌期权，我们可以相似地展示：

```
$\Theta_p = \frac{\partial p}{\partial t} = \frac{\partial}{\partial t} \left\{E\exp(-r(T-t))(1-N_1(d_2)) - S\exp(-q(T-t))(1-N_1(d_1))\right\},$
```

```
$\Theta_p = r\exp(-r(T-t))(1-N_1(d_2)) - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial t} - S\exp(-q(T-t))(1-N_1(d_1)) + S\exp(-q(T-t))n_1(d_1)\frac{\partial d_1}{\partial t};$
```

代入 $n(d_2)$ 和 $\partial d_2/\partial t$，得到：

```
$\Theta_p = r\exp(-r(T-t))N_1(-d_2) - S\exp(-q(T-t))N_1(-d_2) - E\exp(-r(T-t))\exp(r(T-t))\exp(-q(T-t))n(d_2)\left{\frac{S}{E}\frac{\partial d_1}{\partial t} + \frac{\sigma}{2(T-t)}\right{\} + S\exp(-q(T-t))n_1(d_1)\frac{\partial d_1}{\partial t}.$
```

所以我们有

$\Theta_p = \exp(-q(T-t))\left\{qSN_1(-d_1) + \frac{Sn(d_1)\sigma}{2\sqrt{T-t}}\right{\ + rE \exp(-r(T-t))N_1(-d_2).$ (A.4.2)$

