

### 引理 1.2.3（具有一个隐藏层的完全连接前馈人工神经网络）

设 $\mathcal{I}, \mathcal{H} \in \mathbb{N}$，$\theta = (\theta_1, \theta_2, \dots, \theta_{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}) \in \mathbb{R}^{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}$，$x = (x_1, x_2, \dots, x_\mathcal{I}) \in \mathbb{R}^{\mathcal{I}}$，并设 $\psi : \mathbb{R} \to \mathbb{R}$ 为一个函数。则

$$
\mathcal{N}^{\theta, \mathcal{I}}_{\mathfrak{M}_{\psi, \mathcal{H}, \mathrm{id}_{\mathcal{I}}}}(x) = \left[ \sum_{k=1}^{\mathcal{H}} \theta_{\mathcal{H}\mathcal{I}+k+k} \psi \left( \sum_{i=1}^{\mathcal{I}} x_i \theta_{(k-1)\mathcal{I}+i} + \theta_{\mathcal{H}\mathcal{I}+k} \right) \right] + \theta_{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}. \tag{1.24}
$$

*(参见定义 1.1.1、1.1.3 和 1.2.1)*。

**引理 1.2.3 的证明。** 注意到 (1.5) 和 (1.18) 表明

$$
\begin{align}
&\mathcal{N}^{\theta, \mathcal{I}}_{\mathfrak{M}_{\psi, \mathcal{H}, \mathrm{id}_{\mathcal{I}}}}(x) \\
&= \left( \mathrm{id}_{\mathbb{R}} \circ \mathcal{A}^{0, \mathcal{H}\mathcal{I}+\mathcal{H}}_{1, \mathcal{H}} \circ \mathfrak{M}_{\psi, \mathcal{H}} \circ \mathcal{A}^{\theta, 0}_{\mathcal{H}, \mathcal{I}} \right)(x) \\
&= \mathcal{A}^{0, \mathcal{H}\mathcal{I}+\mathcal{H}}_{1, \mathcal{H}} \left( \mathfrak{M}_{\psi, \mathcal{H}} \left( \mathcal{A}^{\theta, 0}_{\mathcal{H}, \mathcal{I}}(x) \right) \right) \\
&= \left[ \sum_{k=1}^{\mathcal{H}} \theta_{\mathcal{H}\mathcal{I}+k+k} \psi \left( \sum_{i=1}^{\mathcal{I}} x_i \theta_{(k-1)\mathcal{I}+i} + \theta_{\mathcal{H}\mathcal{I}+k} \right) \right] + \theta_{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}. \tag{1.25}
\end{align}
$$

因此，引理 1.2.3 得证。$\Box$

## 1.2.3 整流线性单元（ReLU）激活函数

在本小节中，我们将表述 ReLU 函数，它是深度学习应用中最常用的激活函数之一（例如参见 LeCun 等人 [263]）。

**定义 1.2.4（ReLU 激活函数）。** 我们用 $\mathfrak{r} : \mathbb{R} \to \mathbb{R}$ 表示满足对所有 $x \in \mathbb{R}$ 有

$$
\mathfrak{r}(x) = \max \{x, 0\} \tag{1.26}
$$

的函数，并称 $\mathfrak{r}$ 为 ReLU 激活函数（我们也称 $\mathfrak{r}$ 为整流函数）。

![](img/dec290f673e6357c31893c67b579ffe1_29_0.png)

图 1.4 (plots/relu.pdf)：ReLU 激活函数的图像

**源代码 1.1** (code/activation_functions/plot_util.py)：本小节代码清单中使用的 PLOT_UTIL 模块的 PYTHON 代码

```python
import matplotlib.pyplot as plt

def setup_axis(xlim, ylim):
    _, ax = plt.subplots()
    
    ax.set_aspect("equal")
    ax.set_xlim(xlim)
    ax.set_ylim(ylim)
    ax.spines["left"].set_position("zero")
    ax.spines["bottom"].set_position("zero")
    ax.spines["right"].set_color("none")
    ax.spines["top"].set_color("none")
    for s in ax.spines.values():
        s.set_zorder(0)
    return ax
```

**源代码 1.2** (code/activation_functions/relu_plot.py)：用于生成图 1.4 的 PYTHON 代码

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-2, 2), (-.5, 2))

x = np.linspace(-2, 2, 100)

ax.plot(x, tf.keras.activations.relu(x))

plt.savefig("../../plots/relu.pdf", bbox_inches='tight')
```

**定义 1.2.5（多维 ReLU 激活函数）。** 设 $d \in \mathbb{N}$。则我们用 $\Re_d: \mathbb{R}^d \rightarrow \mathbb{R}^d$ 表示由

$$
\Re_d = \mathfrak{M}_{\epsilon_d} \tag{1.27}
$$

给出的函数，并称 $\Re_d$ 为 $d$ 维 ReLU 激活函数（我们也称 $\Re_d$ 为 $d$ 维整流函数）（参见定义 1.2.1 和 1.2.4）。

**引理 1.2.6**（以 **ReLU** 激活函数作为激活函数的**人工神经网络**）。设 $W_1 = w_1 = 1$，$W_2 = w_2 = -1$，$b_1 = b_2 = B = 0$。则对所有 $x \in \mathbb{R}$，有

$$
x = W_1 \max\{w_1 x + b_1, 0\} + W_2 \max\{w_2 x + b_2, 0\} + B. \tag{1.28}
$$

**引理 1.2.6 的证明。** 注意到对所有 $x \in \mathbb{R}$，有

$$
\begin{split}
W_1&\max\{w_1 x + b_1, 0\} + W_2 \max\{w_2 x + b_2, 0\} + B \\
&= \max\{w_1 x + b_1, 0\} - \max\{w_2 x + b_2, 0\} = \max\{x, 0\} - \max\{-x, 0\} \\
&= \max\{x, 0\} + \min\{x, 0\} = x. \tag{1.29}
\end{split}
$$

因此，引理 1.2.6 得证。$\Box$

*练习 1.2.3*（实数恒等映射）。证明或反驳以下陈述：存在 $\mathfrak{d}, H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^{\mathfrak{d}}$，且 $\mathfrak{d} \geq 2 l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + l_H + 1$，使得对所有 $x \in \mathbb{R}$ 有

$$(\mathcal{N}_{\mathfrak{g}_{l_1}, \mathfrak{g}_{l_2}, \dots, \mathfrak{g}_{l_H}, \mathrm{id}_{\mathfrak{d}}}^{\theta, l})(x) = x \tag{1.30}$$

（参见定义 1.1.3 和 1.2.5）。

下一个引理（引理 1.2.7）的陈述为练习 1.2.3 提供了部分答案。引理 1.2.7 由引理 1.2.6 的应用得出，引理 1.2.7 的详细证明留作练习。

**引理 1.2.7**（实数恒等映射）。设 $\theta = (1, -1, 0, 0, 1, -1, 0) \in \mathbb{R}^{7}$。则对所有 $x \in \mathbb{R}$ 有

$$(\mathcal{N}_{\mathfrak{g}_2, \mathrm{id}_{\mathfrak{g}}}^{\theta, 1})(x) = x \tag{1.31}$$

（参见定义 1.1.3 和 1.2.5）。

*练习 1.2.4*（绝对值）。证明或反驳以下陈述：存在 $\mathfrak{d}, H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^{\mathfrak{d}}$，且 $\mathfrak{d} \geq 2 l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + l_H + 1$，使得对所有 $x \in \mathbb{R}$ 有

$$(\mathcal{N}_{\mathfrak{g}_{l_1}, \mathfrak{g}_{l_2}, \dots, \mathfrak{g}_{l_H}, \mathrm{id}_{\mathfrak{d}}}^{\theta, l})(x) = |x| \tag{1.32}$$

（参见定义 1.1.3 和 1.2.5）。

*练习 1.2.5*（指数）。证明或反驳以下陈述：存在 $\mathfrak{d}, H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^{\mathfrak{d}}$，且 $\mathfrak{d} \geq 2 l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + l_H + 1$，使得对所有 $x \in \mathbb{R}$ 有

$$(\mathcal{N}_{\mathfrak{g}_{l_1}, \mathfrak{g}_{l_2}, \dots, \mathfrak{g}_{l_H}, \mathrm{id}_{\mathfrak{d}}}^{\theta, l})(x) = e^x \tag{1.33}$$

*练习 1.2.6*（二维最大值）。证明或反驳以下陈述：存在 $\boldsymbol{d}$，$H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^d$，且 $\boldsymbol{d} \geq 3l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + l_H + 1$，使得对所有 $x, y \in \mathbb{R}$ 有

$$\big(\mathcal{N}^{\boldsymbol{d, 2}}_{\mathfrak{N}_{l_1}, \mathfrak{N}_{l_2}, \dots, \mathfrak{N}_H, \text{id}_\mathbb{R}}\big)(x, y) = \max\{x, y\} \tag{1.34}$$

（参见定义 1.1.3 和 1.2.5）。

*练习 1.2.7*（具有两个隐藏层的实数恒等映射）。证明或反驳以下陈述：存在 $\boldsymbol{d}$，$l_1, l_2 \in \mathbb{N}$，$\theta \in \mathbb{R}^d$，且 $\boldsymbol{d} \geq 2l_1 + l_1 l_2 + 2l_2 + 1$，使得对所有 $x \in \mathbb{R}$ 有

$$\big(\mathcal{N}^{\boldsymbol{d, 1}}_{\mathfrak{N}_{l_1}, \mathfrak{N}_{l_2}, \text{id}_\mathbb{R}}\big)(x) = x \tag{1.35}$$

（参见定义 1.1.3 和 1.2.5）。

下一个引理（引理 1.2.8）的陈述为练习 1.2.7 提供了部分答案。引理 1.2.8 的证明留作练习。

**引理 1.2.8**（具有两个隐藏层的实数恒等映射）。设 $\theta = (1, -1, 0, 0, 1, -1, -1, 1, 0, 0, 1, -1, 0) \in \mathbb{R}^{13}$。则对所有 $x \in \mathbb{R}$ 有

$$\big(\mathcal{N}^{\boldsymbol{d, 1}}_{\mathfrak{N}_{2}, \mathfrak{N}_{2}, \text{id}_\mathbb{R}}\big)(x) = x \tag{1.36}$$

（参见定义 1.1.3 和 1.2.5）。

*练习 1.2.8*（三维最大值）。证明或反驳以下陈述：存在 $\boldsymbol{d}$，$H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^d$，且 $\boldsymbol{d} \geq 4l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + l_H + 1$，使得对所有 $x, y, z \in \mathbb{R}$ 有

$$\big(\mathcal{N}^{\boldsymbol{d, 3}}_{\mathfrak{N}_{l_1}, \mathfrak{N}_{l_2}, \dots, \mathfrak{N}_H, \text{id}_\mathbb{R}}\big)(x, y, z) = \max\{x, y, z\} \tag{1.37}$$

（参见定义 1.1.3 和 1.2.5）。

*练习 1.2.9*（多维最大值）。证明或反驳以下陈述：对每个 $k \in \mathbb{N}$，存在 $\boldsymbol{d}$，$H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^d$，且 $\boldsymbol{d} \geq (k+1)l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + l_H + 1$，使得对所有 $x_1, x_2, \dots, x_k \in \mathbb{R}$ 有

$$\big(\mathcal{N}^{\boldsymbol{d, k}}_{\mathfrak{N}_{l_1}, \mathfrak{N}_{l_2}, \dots, \mathfrak{N}_H, \text{id}_\mathbb{R}}\big)(x_1, x_2, \dots, x_k) = \max\{x_1, x_2, \dots, x_k\} \tag{1.38}$$

（参见定义 1.1.3 和 1.2.5）。

*练习 1.2.10*. 证明或反驳以下陈述：存在 $\boldsymbol{d}$，$H \in \mathbb{N}$，$l_1, l_2, \dots, l_H \in \mathbb{N}$，$\theta \in \mathbb{R}^d$，且 $\boldsymbol{d} \geq 2l_1 + [\sum_{k=2}^{H} l_k(l_{k-1} + 1)] + (l_H + 1) + 1$，使得对所有 $x \in \mathbb{R}$ 有

$$\big(\mathcal{N}^{\boldsymbol{d, 1}}_{\mathfrak{N}_{l_1}, \mathfrak{N}_{l_2}, \dots, \mathfrak{N}_H, \text{id}_\mathbb{R}}\big)(x) = \max\{x, \frac{x}{2}\} \tag{1.39}$$

（参见定义 1.1.3 和 1.2.5）。

