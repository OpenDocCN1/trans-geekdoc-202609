

## 1.2. 激活函数

**定义 1.2.26**（多维双曲正切激活函数）。设 \(d \in \mathbb{N}\)。若且仅若 \(A = \mathfrak{M}_{\tanh,d}\)（参见定义 1.2.1 和 1.2.25），则称 \(A\) 为 *d* 维双曲正切激活函数。

**引理 1.2.27**。设 *a* 为标准逻辑激活函数（参见定义 1.2.18）。则对于所有 \(x \in \mathbb{R}\)，有

\[
\tanh(x) = 2a(2x) - 1 \tag{1.63}
\]

*（参见定义 1.2.18 和 1.2.25）。*

**引理 1.2.27 的证明**。注意 (1.52) 和 (1.62) 保证了对于所有 \(x \in \mathbb{R}\)，有

\[
\begin{align}
2a(2x) - 1 & = 2 \left( \frac{\exp(2x)}{\exp(2x)+1} \right) - 1 = \frac{2\exp(2x) - (\exp(2x)+1)}{\exp(2x)+1} \\
& = \frac{\exp(2x)-1}{\exp(2x)+1} = \frac{\exp(x)(\exp(x)-\exp(-x))}{\exp(x)(\exp(x)+\exp(-x))} \\
& = \frac{\exp(x)-\exp(-x)}{\exp(x)+\exp(-x)} = \tanh(x). \tag{1.64}
\end{align}
\]

引理 1.2.27 得证。

**练习 1.2.16。** 设 *a* 为标准逻辑激活函数（参见定义 1.2.18）。证明或反驳以下陈述：存在 \(L \in \{2, 3, \ldots\}\)，\(\boldsymbol{l}, l_1, l_2, \ldots, l_{L-1} \in \mathbb{N}\)，以及满足 \(\boldsymbol{\theta} \geq 2l_1 + [\sum_{k=2}^{L-1} l_k(l_{k-1}+1)] + (l_{L-1}+1)\) 的 \(\boldsymbol{\theta} \in \mathbb{R}^{\boldsymbol{\theta}}\)，使得对于所有 \(x \in \mathbb{R}\) 有

\[
\left( \mathcal{N}^{\boldsymbol{g}, 1}_{\mathfrak{A}_{a,l_1}, \mathfrak{A}_{a,l_2}, \ldots, \mathfrak{A}_{a,l_{L-1}}, \mathrm{id}_{\mathbb{R}}} \right)(x) = \tanh(x) \tag{1.65}
\]

*（参见定义 1.1.3, 1.2.1 和 1.2.25）。*

### 1.2.10 Softsign 激活

**定义 1.2.28**（Softsign 激活函数）。*我们称* *a* *为 softsign 激活函数，当且仅当* \(a \colon \mathbb{R} \rightarrow \mathbb{R}\) *是从* \(\mathbb{R}\) *到* \(\mathbb{R}\) 的函数，且对于所有* \(x \in \mathbb{R}\) *满足*

\[
a(x) = \frac{x}{|x|+1}. \tag{1.66}
\]

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util
```

![](img/dec290f673e6357c31893c67b579ffe1_43_0.png)

```python
ax = plot_util.setup_axis((-5,5), (-1.5,1.5))

x = np.linspace(-5, 5, 100)

ax.plot(x, tf.keras.activations.tanh(x), label='tanh')
ax.plot(x, tf.keras.activations.softsign(x), label='softsign')
ax.legend()
plt.savefig("../plots/softsign.pdf", bbox_inches='tight')
```

源代码 1.9 (code/activation_functions/softsign_plot.py)：用于生成图 1.11 的 PYTHON 代码

**定义 1.2.29**（多维 softsign 激活函数）。设 $d \in \mathbb{N}$，且设 $a$ 为 softsign 激活函数（参见定义 1.2.28）。若且仅若 $A = \mathfrak{M}_{a,d}$（参见定义 1.2.1），则称 $A$ 为 $d$ 维 softsign 激活函数。

### 1.2.11 泄漏整流线性单元 (Leaky ReLU) 激活

**定义 1.2.30**（Leaky ReLU 激活函数）。设 $\gamma \in [0,\infty)$。若且仅若 $a: \mathbb{R} \rightarrow \mathbb{R}$ 是从 $\mathbb{R}$ 到 $\mathbb{R}$ 的函数，且对于所有 $x \in \mathbb{R}$ 满足

$$
a(x)= \left\{\begin{array}{cl} x & : x>0 \\ \gamma x & : x \leq 0 .\end{array}\right. \tag{1.67}
$$

则称 $a$ 为具有泄漏因子 $\gamma$ 的 leaky ReLU 激活函数。

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-2,2), (-5,2))

x = np.linspace(-2, 2, 100)
```

![](img/dec290f673e6357c31893c67b579ffe1_44_0.png)

图 1.12 (plots/leaky_relu.pdf)：泄漏因子为 1/10 的 leaky ReLU 激活函数与 ReLU 激活函数的图像

```python
ax.plot(x, tf.keras.activations.relu(x), linewidth=3, label='ReLU')
ax.plot(x, tf.keras.activations.relu(x, alpha=0.1), 
        label='leaky ReLU')
ax.legend()
plt.savefig("../plots/leaky_relu.pdf", bbox_inches='tight')
```

源代码 1.10 (code/activation_functions/leaky_relu_plot.py)：用于生成图 1.12 的 PYTHON 代码

**引理 1.2.31。** *设 $\gamma \in [0,1]$，且设 $a: \mathbb{R} \rightarrow \mathbb{R}$ 为一个函数。则 $a$ 是具有泄漏因子 $\gamma$ 的 leaky ReLU 激活函数，当且仅当对于所有 $x \in \mathbb{R}$ 有*

$$
a(x) = \max \{x, \gamma x \} \tag{1.68}
$$

*（参见定义 1.2.30）。*

*引理 1.2.31 的证明。* *注意到事实 $\gamma \leq 1$ 以及 (1.67) 确立了 (1.68)。引理 1.2.31 得证。* $\square$

**引理 1.2.32。** *设 $u, \beta \in \mathbb{R}$，$v \in (u, \infty)$，$\alpha \in (-\infty, 0]$，设 $a_1$ 为 softplus 激活函数，设 $a_2$ 为 GELU 激活函数，设 $a_3$ 为标准逻辑激活函数，设 $a_4$ 为参数为 $\beta$ 的 swish 激活函数，设 $a_5$ 为 softsign 激活函数，且设 $l$ 为泄漏参数为 $\gamma$ 的 leaky ReLU 激活函数（参见定义 1.2.11, 1.2.15, 1.2.18, 1.2.22, 1.2.28 和 1.2.30）。则*

- (i) 对于所有 $f \in \{\mathbf{c}, \mathbf{u}, \mathbf{v}, \mathbf{tanh}, a_1, a_2, \dots, a_5\}$，有 $\lim_{x \rightarrow -\infty} |f'(x)| = 0$，且

- (ii) 有 $\lim _ { x \rightarrow - \infty } l ^ { \prime } ( x ) = \gamma$

*（参见定义 1.2.4, 1.2.9 和 1.2.25）。*

**引理 1.2.32 的证明**。注意到 $(1.26)$、$(1.45)$、$(1.47)$、$(1.51)$、$(1.52)$、$(1.60)$、$(1.62)$ 和 $(1.66)$ 证明了第 (i) 项。观察到 $(1.67)$ 确立了第 (ii) 项。引理 1.2.32 得证。

**定义 1.2.33**（多维 leaky ReLU 激活函数）。设 $d \in \mathbb { N }$，$\gamma \in [0, \infty)$，且设 $a$ 为具有泄漏因子 $\gamma$ 的 leaky ReLU 激活函数（参见定义 1.2.30）。若且仅若 $A = \mathfrak { M } _ { a , d }$（参见定义 1.2.1），则称 $A$ 为具有泄漏因子 $\gamma$ 的 $d$ 维 leaky ReLU 激活函数。

### 1.2.12 指数线性单元 (ELU) 激活

另一种流行的激活函数是所谓的指数线性单元（ELU）激活函数，它由 Clevert 等人 [83] 提出。此激活函数是下一个概念的主题。

**定义 1.2.34**（ELU 激活函数）。设 $\gamma \in ( - \infty , 0 ]$。若且仅若 $a \colon \mathbb { R } \rightarrow \mathbb { R }$ 是从 $\mathbb { R }$ 到 $\mathbb { R }$ 的函数，且对于所有 $x \in \mathbb { R }$ 满足

$$
a ( x ) = \left\{ \begin{array}{cl} x & : x > 0 \\ \gamma ( 1 - \exp ( x ) ) & : x \leq 0 . \end{array} \right. \tag{1.69}
$$

则称 $a$ 为具有渐近值 $\gamma$ 的 ELU 激活函数。

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-2,2), (-1,2))

x = np.linspace(-2, 2, 100)

ax.plot(x, tf.keras.activations.relu(x), linewidth=3, label='ReLU')
ax.plot(x, tf.keras.activations.relu(x, alpha=0.1), linewidth=2,
        label='leaky ReLU')
ax.plot(x, tf.keras.activations.elu(x), linewidth=0.9, label='ELU')
ax.legend()
plt.savefig("../../../plots/elu.pdf", bbox_inches='tight')
```

源代码 1.11 (code/activation_functions/elu_plot.py)：用于生成图 1.13 的 PYTHON 代码

![](img/dec290f673e6357c31893c67b579ffe1_46_0.png)

图 1.13 (plots/elu.pdf)：渐近值为 $-1$ 的 ELU 激活函数、泄漏因子为 $1/10$ 的 leaky ReLU 激活函数以及 ReLU 激活函数的图像

**引理 1.2.35**。设 $\gamma \in (−\infty, 0]$，且设 $a$ 为具有渐近值 $\gamma$ 的 *ELU* 激活函数（参见定义 1.2.34）。则

$$
\limsup _ { x \to -\infty} a(x) = \liminf _ { x \to -\infty} a(x) = \gamma. \qquad (1.70)
$$

*引理 1.2.35 的证明。* 观察到 (1.69) 确立了 (1.70)。引理 1.2.35 得证。

**定义 1.2.36**（多维 *ELU* 激活函数）。设 $d \in \mathbb{N}$，$\gamma \in (−\infty, 0]$，且设 $a$ 为具有渐近值 $\gamma$ 的 *ELU* 激活函数（参见定义 1.2.34）。若且仅若 $A = \mathfrak{M}_{a,d}$（参见定义 1.2.1），则称 $A$ 为具有渐近值 $\gamma$ 的 $d$ 维 *ELU* 激活函数。

### 1.2.13 整流幂单元 (RePU) 激活

另一种流行的激活函数是所谓的*整流幂单元*（RePU）激活函数。此概念是下一个定义的主题。

**定义 1.2.37**（RePU 激活函数）。设 $p \in \mathbb{N}$。若且仅若 $a: \mathbb{R} \to \mathbb{R}$ 是从 $\mathbb{R}$ 到 $\mathbb{R}$ 的函数，且对于所有 $x \in \mathbb{R}$ 满足

$$
a(x) = (\max \{x, 0\})^{p}. \qquad (1.71)
$$

则称 $a$ 为具有幂次 $p$ 的 *RePU* 激活函数。

