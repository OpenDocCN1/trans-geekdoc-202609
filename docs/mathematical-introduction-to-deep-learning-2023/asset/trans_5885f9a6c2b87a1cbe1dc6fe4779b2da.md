
证明了对于所有 $\mathbf{z} = (z_1, \dots, z_d) \in [0, \infty)^d$，若满足 $\sum_{i=1}^d z_i = \sum_{i=1}^d y_i$ 且 $\forall i \in J: z_i = y_i$，则恒有 $\mathbf{z} = \mathbf{y}$。因此，假设 $\sum_{i=1}^d x_i = \sum_{i=1}^d y_i$ 且 $\mathbf{x} \neq \mathbf{y}$ 确保了存在 $i \in J$ 使得 $x_i \neq y_i > 0$。将此与 (5.60) 结合表明，对于所有 $h \in [0, 1)$，恒有

$$g''(h) > 0. \tag{5.62}$$

微积分基本定理进而表明，对于所有 $h \in (0, 1)$，恒有

$$g'(h) = g'(0) + \int_0^h g''(b) \, \mathrm{d}b > g'(0). \tag{5.63}$$

此外，注意到 (5.59) 以及假设 $\sum_{i=1}^d x_i = \sum_{i=1}^d y_i$ 证明了

$\begin{align*} g'(0) &= -\sum_{i \in J} \frac{y_i (x_i - y_i)}{y_i} = \sum_{i \in J} (y_i - x_i) = \left[ \sum_{i \in J} y_i \right] - \left[ \sum_{i \in J} x_i \right] \\ &= \left[ \sum_{i \in \{1,2,\dots,d\}} y_i \right] - \left[ \sum_{i \in J} x_i \right] = \left[ \sum_{i \in \{1,2,\dots,d\}} x_i \right] - \left[ \sum_{i \in J} x_i \right] = \left[ \sum_{i \in \{1,2,\dots,d\} \setminus J} x_i \right] \ge 0. \end{align*} \tag{5.64}

将此与 (5.63) 结合，确立了对于所有 $h \in (0, 1)$，恒有

$$g'(h) > 0. \tag{5.65}$$

因此，我们得到 $g$ 是严格递增的。这一点以及 (5.55) 证明了 $f|_{[0,1]}$ 是严格递减的。接下来注意到，(5.55) 和 (5.58) 确保了对于所有 $h \in (0, 1]$，恒有

$$f(h) = -\sum_{i \in J} \ln(y_i + (1-h)(x_i - y_i)) y_i = -\sum_{i \in J} \ln(x_i + h(y_i - x_i)) y_i \in \mathbb{R}. \tag{5.66}$$

此外，注意到引理 5.4.6 中的第 (i) 项和第 (ii) 项表明

$$\left[ f(0) = \infty \right] \lor \left[ f(0) = -\sum_{i \in J} \ln(x_i + 0(y_i - x_i)) y_i \in \mathbb{R} \right]. \tag{5.67}$$

将此与 (5.66) 结合可推得

$$\left[ f(0) = \infty \right] \lor \left[ \forall h \in [0, 1]: f(h) \in \mathbb{R} \right] \land \left( [0, 1] \ni h \mapsto f(h) \in \mathbb{R} \right) \in C([0, 1], \mathbb{R}]). \tag{5.68}$$

这一点以及 $f|_{[0,1]}$ 严格递减的事实证明了 $f$ 是严格递减的。由此，引理 5.4.7 的证明完成。

**推论 5.4.8。** *设 $d \in \mathbb{N} \setminus \{1\}$，设 $A = \{ \mathbf{x} = (x_1, \dots, x_d) \in [0, 1]^d: \sum_{i=1}^d x_i = 1 \}$，设 $\mathbf{L}$ 为 $d$ 维交叉熵损失函数，且设 $\mathbf{y} \in A$（参见定义 5.4.5）。则*

*(i)* 恒有

$\{x \in A: \mathbf{L}(x, y) = \inf_{z \in A} \mathbf{L}(z, y)\} = \{y\}$

并且

*(ii)* 恒有

$\inf_{z \in A} \mathbf{L}(z, y) = \mathbf{L}(y, y) = -\sum_{i \in \{1, 2, \ldots, d\}, \; y_i \neq 0} \ln(y_i)y_i.$

推论 5.4.8 的证明。注意到引理 5.4.7 表明，对于所有 $x \in A \setminus \{y\}$，恒有

$\mathbf{L}(x, y) = \mathbf{L}(x + 0(y - x), y) > \mathbf{L}(x + 1(y - x), y) = \mathbf{L}(y, y).$

这一点以及引理 5.4.6 中的第 (ii) 项确立了第 (i) 项和第 (ii) 项。由此，推论 5.4.8 的证明完成。 $\square$

# 5.4.5 库拉巴-莱布勒散度损失

引理 5.4.9. 设 $z \in (0, \infty)$。则

*(i)* 恒有

$\liminf_{x \downarrow 0} [\ln(x)x] = 0 = \limsup_{x \downarrow 0} [\ln(x)x]$

并且

*(ii)* 对于所有 $y \in [0, \infty)$，恒有

$\liminf_{x \uparrow y} [\ln(\frac{x}{y})x] = \begin{cases} 0 & : y = 0 \\ \ln(\frac{y}{y})y & : y > 0 \end{cases} = \limsup_{x \uparrow y} [\ln(\frac{x}{y})x].$

引理 5.4.9 的证明。在整个证明过程中，设 $f: (0, \infty) \to \mathbb{R}$ 和 $g: (0, \infty) \to \mathbb{R}$ 满足对于所有 $x \in (0, \infty)$

$f(x) = \ln(x^{-1}) \quad \text{且} \quad g(x) = x.$

注意到链式法则证明对于所有 $x \in (0, \infty)$，$f$ 是可微的，且

$f'(x) = -x^{-2}(x^{-1})^{-1} = -x^{-1}.$

结合这一点、事实 $\lim_{x \to \infty} |f(x)| = \infty = \lim_{x \to 0} |g(x)|$、事实 $g$ 是可微的、事实对于所有 $x \in (0, \infty)$ 恒有 $g'(x) = 1 \neq 0$，以及事实 $\lim_{x \to \infty} \frac{-x^{-1}}{1} = 0$，洛必达法则确保

$\lim_{x \to \infty} \frac{f(x)}{g(x)} = 0 = \lim_{x \to \infty} \frac{f(x)}{g(x)}.$

这证明了

$$\lim_{{x \searrow 0}} \inf \frac{{f({x^{ - 1}})}}{{g({x^{ - 1}})}} = 0 = \lim_{{x \searrow 0}} \sup \frac{{f({x^{ - 1}})}}{{g({x^{ - 1}})}} .\qquad (5.77)$$

事实：对于所有 $x \in (0, \infty)$，恒有 $\frac{{f({x^{ - 1}})}}{{g({x^{ - 1}})}} = \ln (x)x$，从而确立了第 **(i)** 项。注意到第 **(i)** 项以及事实：对于所有 $x \in (0, \infty)$，恒有 $\ln (\frac{z}{x})x = \ln (z)x - \ln (x)x$，证明了第 **(ii)** 项。由此，引理 5.4.9 的证明完成。 $\square$

**定义 5.4.10.** *设* $d \in \mathbb{N}\backslash\{1\}$*。称* $\mathbf{L}$ *为* $d$ *维库拉巴-莱布勒散度损失函数，当且仅当它满足* $\mathbf{L}\colon [0, \infty)^d \times [0, \infty)^d \rightarrow ( - \infty, \infty]$ *是从* $[0, \infty)^d \times [0, \infty)^d$ *到* $( - \infty, \infty]$ *的函数，且满足对于所有* $x = (x_1, \ldots, x_d)$， $y = (y_1, \ldots, y_d) \in [0, \infty)^d$ *恒有*

$$\mathbf{L}(x, y) = - \sum_{i = 1}^{d}\lim_{z \searrow x_i}\lim_{w \searrow y_i}\ln (\frac{z}{w})u\qquad (5.78)$$

（参见引理 5.4.9）。

![](img/dec290f673e6357c31893c67b579ffe1_192_0.png)

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((0,1), (0,3))

ax.set_aspect(.3)

x = np.linspace(0, 1, 100)

kld_loss = tf.keras.losses.KLDivergence(
    reduction=tf.keras.losses.Reduction.NONE)
cce_loss = tf.keras.losses.CategoricalCrossentropy(
    reduction=tf.keras.losses.Reduction.NONE)
y = tf.constant([[0.3, 0.7]] * 100, shape=(100, 2))

X = tf.stack([x,1-x], axis=1)

ax.plot(x, kld_loss(y,X), label='Kulback-Leibler divergence')
ax.plot(x, cce_loss(y,X), label='Cross-entropy')
ax.legend()

plt.savefig("../../plots/kldloss.pdf", bbox_inches='tight')
```

源代码 5.7 (code/loss_functions/kldloss_plot.py): 用于创建图 5.7 的 PYTHON 代码

**引理 5.4.11.** 设 $d \in \mathbb{N} \setminus \{1\}$，设 $\mathbf{L}_{\mathrm{CE}}$ 为 $d$ 维交叉熵损失函数，设 $\mathbf{L}_{\mathrm{KLD}}$ 为 $d$ 维库拉巴-莱布勒散度损失函数（参见定义 5.4.5 和 5.4.10）。则对于所有 $x,y \in [0,\infty)^d$，恒有

$\mathbf{L}_{\mathrm{CE}}(x, y) = \mathbf{L}_{\mathrm{KLD}}(x, y) + \mathbf{L}_{\mathrm{CE}}(y, y).$ (5.79)

**引理 5.4.11 的证明。** 注意到引理 5.4.9 意味着对于所有 $a,b \in [0,\infty)$，恒有

$\begin{aligned} \lim_{z\searrow a} \lim_{u\searrow b} \left[\ln \left(\frac{z}{u}\right) u\right] &= \lim_{z\searrow a} \lim_{u\searrow b} [\ln(z)u - \ln(u)u] \\
&= \lim_{z\searrow a} \left[\ln(z)b - \lim_{u\searrow b}[\ln(u)u]\right] \\
&= \left(\lim_{z\searrow a}[\ln(z)b]\right) - \left(\lim_{u\searrow b}[\ln(u)u]\right). \end{aligned}$ (5.80)

这一点以及 (5.78) 表明，对于所有 $x = (x_1,\dots,x_d)$， $y = (y_1,\dots,y_d) \in [0,\infty)^d$，恒有

$\begin{aligned} \mathbf{L}_{\mathrm{KLD}}(x,y) &= -\sum_{i=1}^{d} \lim_{z\searrow x_i} \lim_{u\searrow y_i} \left[\ln \left(\frac{z}{u}\right) u\right] \\
&= -\left(\sum_{i=1}^{d} \lim_{z\searrow x_i} [\ln(z)y_i]\right) + \left(\sum_{i=1}^{d} \lim_{u\searrow y_i} [\ln(u)u]\right). \end{aligned}$ (5.81)

此外，注意到引理 5.4.9 确保了对于所有 \( b \in [0, \infty) \)，恒有

$$\lim_{u \searrow b} [\ln(u)b] = \begin{cases} 0 & : b = 0 \\ \ln(b) & : b > 0 \end{cases} . \tag{5.82}$$

将此与 (5.81) 结合表明，对于所有 \( x = (x_1, \ldots, x_d) \)， \( y = (y_1, \ldots, y_d) \in [0, \infty)^d \)，恒有

$$\mathbf{L}_{\mathrm{KLD}}(x, y) = -\left( \sum_{i=1}^{d} \lim_{z \searrow x_i} [\ln(z)x_i] \right) + \left( \sum_{i=1}^{d} \lim_{u \searrow y_i} [\ln(u)y_i] \right) = \mathbf{L}_{\mathrm{CE}}(x, y) - \mathbf{L}_{\mathrm{CE}}(y, y). \tag{5.83}$$

因此，我们得到 (5.79)。由此，引理 5.4.11 的证明完成。

**引理 5.4.12.** 设 \( d \in \mathbb{N} \setminus \{1\} \)，设 \( \mathbf{L} \) 为 $d$ 维库拉巴-莱布勒损失函数，设 \( x = (x_1, \ldots, x_d) \)， \( y = (y_1, \ldots, y_d) \in [0, \infty)^d \) 满足 \( \sum_{i=1}^{d} x_i = \sum_{i=1}^{d} y_i \) 且 \( x \neq y \)，并设 \( f \) : \([0, 1] \rightarrow (-\infty, \infty] \) 满足对于所有 \( h \in [0, 1] \) 恒有

$$f(h) = \mathbf{L}(x + h(y - x), y) \tag{5.84}$$

（参见定义 5.4.10）。则 \( f \) 是严格递减的。

引理 5.4.12 的证明。注意到引理 5.4.7 和引理 5.4.11 确立了 (5.84)。由此，引理 5.4.12 的证明完成。

**推论 5.4.13.** 设 \( d \in \mathbb{N} \setminus \{1\} \)，设 \( A = \{x = (x_1, \ldots, x_d) \in [0, 1]^d \) : \( \sum_{i=1}^{d} x_i = 1 \}\)，设 \( \mathbf{L} \) 为 $d$ 维库拉巴-莱布勒散度损失函数，且设 \( y \in A \)（参见定义 5.4.10）。则

- (i) 恒有

$$\{ x \in A \) : \( \mathbf{L}(x, y) = \inf_{z \in A} \mathbf{L}(z, y) \} = \{y\} \tag{5.85}$$

- 并且
- (ii) 恒有 \( \inf_{z \in A} \mathbf{L}(z, y) = \mathbf{L}(y, y) = 0 \)。

推论 5.4.13 的证明。注意到推论 5.4.8 和引理 5.4.11 证明了第 (i) 项和第 (ii) 项。由此，推论 5.4.13 的证明完成。

# 5.5 人工神经网络训练中的 GF 优化

例 5.5.1. 设 \( d, L, \mathfrak{d} \in \mathbb{N} \)，\( l_1, l_2, \ldots, l_L \in \mathbb{N} \) 满足 \( \mathfrak{d} = l_1(d+1) + [\sum_{k=2}^{L} l_k(l_{k-1} + 1)] \)，设 \( \alpha \) : \( \mathbb{R} \rightarrow \mathbb{R} \) 可微，设 \( M \in \mathbb{N} \)，\( x_1, x_2, \ldots, x_M \in \mathbb{R}^d \)，\( y_1, y_2, \ldots, y_M \in \mathbb{R}^{l_L} \)，设

