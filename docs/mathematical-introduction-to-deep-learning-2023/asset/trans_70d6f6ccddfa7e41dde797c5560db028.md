

(iii) 对于所有 $\Xi \in C^1([0, \infty), \mathbb{R}^9)$, $\tau \in (0, \infty)$ 且满足 $\Xi(\tau) = \Theta(\tau)$ 以及 $\|\Xi'(\tau)\|_2 = \|\Theta'(\tau)\|_2$，均有

$$(\mathcal{L} \circ \Theta)^\top(\tau) \le (\mathcal{L} \circ \Xi)^\top(\tau) \quad (5.20)$$

成立（参见定义 3.3.4）。

**推论 5.2.4 的证明。** 注意，引理 5.2.3 和微积分基本定理蕴含了第 (i) 项和第 (ii) 项。值得注意的是，引理 5.2.2 表明，对于所有 $\Xi \in C^1([0, \infty), \mathbb{R}^9)$ 和 $t \in (0, \infty)$，均有

$$(\mathcal{L} \circ \Xi)^\top(t) = [\mathcal{L}'(\Xi(t))](\Xi'(t))$$
$$\ge \inf_{v \in \{i \in \mathbb{R}^9 : \|i\|_2 = \|\Xi'(i)\|_2\}} [\mathcal{L}'(\Xi(t))](v)$$
$$= -\|\Xi'(t)\|_2 \|(\nabla \mathcal{L})(\Xi(t))\|_2 \quad (5.21)$$

成立（参见定义 3.3.4）。因此，引理 5.2.3 确保对于所有满足 $\Xi(\tau) = \Theta(\tau)$ 且 $\|\Xi'(\tau)\|_2 = \|\Theta'(\tau)\|_2$ 的 $\Xi \in C^1([0, \infty), \mathbb{R}^9)$ 和 $\tau \in (0, \infty)$，均有

$$(\mathcal{L} \circ \Xi)^\top(\tau) \ge -\|\Xi'(\tau)\|_2 \|(\nabla \mathcal{L})(\Xi(\tau))\|_2 \ge -\|\Theta'(\tau)\|_2 \|(\nabla \mathcal{L})(\Theta(\tau))\|_2$$
$$= -\| (\nabla \mathcal{L})(\Theta(\tau)) \|_2^2 = (\mathcal{L} \circ \Theta)^\top(\tau). \quad (5.22)$$

结合第 (ii) 项，由此建立了第 (iii) 项。至此，推论 5.2.4 的证明完成。 $\square$

![](img/dec290f673e6357c31893c67b579ffe1_176_0.png)

**图 5.1** ([plots/gradient_plot1.pdf](plots/gradient_plot1.pdf))：一维示例中负梯度的图示。该图展示了函数 ${[-2,2]\supseteq x\mapsto x^{4}-3x^{2}\in\mathbb{R}}$ 的图像，并用水平箭头标出了若干点处负梯度的值。用于生成此图的 PYTHON 代码见源代码 5.1。

![](img/dec290f673e6357c31893c67b579ffe1_177_0.png)

**图 5.2** ([plots/gradient_plot2.pdf](plots/gradient_plot2.pdf))：二维示例中负梯度的图示。该图展示了函数 $\mathbb{R}^{2} \ni(x, y) \mapsto \frac{1}{2}\left|x-1\right|^{2}+5\left|y-1\right|^{2} \in \mathbb{R}$ 的等高线，箭头指示了沿这些等高线若干点处负梯度的方向和大小。用于生成此图的 PYTHON 代码见源代码 5.2。

```python
1 import numpy as np
2 import matplotlib.pyplot as plt
3
4 def f(x):
5     return x**4 - 3 * x**2
6
7 def nablaf(x):
8     return 4 * x**3 - 6 * x
9
10 plt.figure()
11
12 # Plot graph of f
13 x = np.linspace(-2,2,100)
14 plt.plot(x,f(x))
15
16 # Plot arrows
17 for x in np.linspace(-1.9, 1.9, 21):
18     d = nabla_f(x)
19     plt.arrow(x, f(x), -.05 * d, 0,
20             length_includes_head=True, head_width=0.08,
21             head_length=0.05, color='b')
22 
23 plt.savefig("../plots/gradient_plot1.pdf")
```

**源代码 5.1** ([code/gradient_plot1.py](code/gradient_plot1.py))：用于创建图 5.1 的 PYTHON 代码

```python
1 import numpy as np
2 import matplotlib.pyplot as plt
3 
4 K = [1., 10.]
5 vartheta = np.array([1., 1.])
6 
7 def f(x, y):
8     result = K[0] / 2. * np.abs(x - vartheta[0])**2 \
9             + K[1] / 2. * np.abs(y - vartheta[1])**2
10     return result
11 
12 def nabla_f(x):
13     return K * (x - vartheta)
14 
15 plt.figure()
16 
17 # Plot contour lines of f
18 x = np.linspace(-3., 7., 100)
19 y = np.linspace(-2., 4., 100)
20 X, Y = np.meshgrid(x, y)
21 Z = f(X, Y)
22 
23 cp = plt.contour(X, Y, Z, colors="black",
24                 levels=[0.5, 2, 4, 8, 16],
25                 linestyles=":")
26 
27 # Plot arrows along contour lines
28 for i in [0.5, 2, 4, 8, 16]:
29     for d in np.linspace(0, 2.*np.pi, 10, endpoint=False):
30         x = np.cos(d) / ((K[0] / (2*1))**0.5) + vartheta[0]
31         y = np.sin(d) / ((K[1] / (2*1))**0.5) + vartheta[1]
32         grad = nabla_f(np.array([x, y]))
33         plt.arrow(x, y, -.05 * grad[0], -.05 * grad[1],
34                 length_includes_head=True, head_width=.08,
35                 head_length=.1, color='b')
36 
37 plt.savefig("../plots/gradient_plot2.pdf")
```

**源代码 5.2** ([code/gradient_plot2.py](code/gradient_plot2.py))：用于创建图 5.2 的 PYTHON 代码

## 5.3 人工神经网络的正则性性质

### 5.3.1 关于参数化函数组合的可微性

**引理 5.3.1.** 设 $\mathbf{0}_1, \mathbf{0}_2, l_1, l_2 \in \mathbb{N}$，设 $A_1 : \mathbb{R}^{l_1} \to \mathbb{R}^{l_1} \times \mathbb{R}^{l_2}$ 和 $A_2 : \mathbb{R}^{l_2} \to \mathbb{R}^{l_1} \times \mathbb{R}^{l_2}$ 满足对于所有 $x_1 \in \mathbb{R}^{l_1}$ 和 $x_2 \in \mathbb{R}^{l_2}$，有 $A_1(x_1) = (x_1, \mathbf{0})$ 且 $A_2(x_2) = (\mathbf{0}, x_2)$；对于每个 $k \in \{1, 2\}$，设 $B_k : \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \to \mathbb{R}^{l_k}$ 满足对于所有 $x_1 \in \mathbb{R}^{l_1}$ 和 $x_2 \in \mathbb{R}^{l_2}$，有 $B_k(x_1, x_2) = x_k$；对于每个 $k \in \{1, 2\}$，设 $F_k : \mathbb{R}^{l_k} \to \mathbb{R}^{l_k}$ 是可微的；设 $f : \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \to \mathbb{R}^{l_1} \times \mathbb{R}^{l_2}$ 满足对于所有 $x_1 \in \mathbb{R}^{l_1}$ 和 $x_2 \in \mathbb{R}^{l_2}$，有

$$f(x_1, x_2) = (F_1(x_1), F_2(x_2)).\tag{5.23}$$

*那么*
- (i) 有 $f = A_1 \circ F_1 \circ B_1 + A_2 \circ F_2 \circ B_2$ 成立，且
- (ii) $f$ 是可微的。

*引理 5.3.1 的证明。* 注意，(5.23) 蕴含对于所有 $x_1 \in \mathbb{R}^{l_1}$ 和 $x_2 \in \mathbb{R}^{l_2}$，均有

$$(A_1 \circ F_1 \circ B_1 + A_2 \circ F_2 \circ B_2)(x_1, x_2) = (A_1 \circ F_1)(x_1) + (A_2 \circ F_2)(x_2)$$
$$= (F_1(x_1), \mathbf{0}) + (\mathbf{0}, F_2(x_2))\tag{5.24}$$
$$= (F_1(x_1), F_2(x_2)).$$

结合这一点以及 $A_1$、$A_2$、$F_1$、$F_2$、$B_1$ 和 $B_2$ 均可微的事实，利用链式法则可知 $f$ 是可微的。至此，引理 5.3.1 的证明完成。 $\square$

**引理 5.3.2.** 设 $\mathbf{0}_1, \mathbf{0}_2, l_0, l_1, l_2 \in \mathbb{N}$，设 $A : \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \times \mathbb{R}^{l_0} \to \mathbb{R}^{l_2} \times \mathbb{R}^{l_1+l_0}$ 和 $B : \mathbb{R}^{l_2} \times \mathbb{R}^{l_1+l_0} \to \mathbb{R}^{l_2} \times \mathbb{R}^{l_1}$ 满足对于所有 $\theta_1 \in \mathbb{R}^{l_1}$、$\theta_2 \in \mathbb{R}^{l_2}$ 和 $x \in \mathbb{R}^{l_0}$，有

$$A(\theta_1, \theta_2, x) = (\theta_2, (\theta_1, x)) \quad\text{且}\quad B(\theta_2, (\theta_1, x)) = (\theta_2, F_1(\theta_1, x)),\tag{5.25}$$

对于每个 $k \in \{1, 2\}$，设 $F_k : \mathbb{R}^{l_k} \times \mathbb{R}^{l_k-1} \to \mathbb{R}^{l_k}$ 是可微的；设 $f : \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \times \mathbb{R}^{l_0} \to \mathbb{R}^{l_2}$ 满足对于所有 $\theta_1 \in \mathbb{R}^{l_1}$、$\theta_2 \in \mathbb{R}^{l_2}$ 和 $x \in \mathbb{R}^{l_0}$，有

$$f(\theta_1, \theta_2, x) = (F_2(\theta_2, \cdot) \circ F_1(\theta_1, \cdot))(x).\tag{5.26}$$

*那么*
- (i) 有 $f = F_2 \circ B \circ A$ 成立，且
- (ii) $f$ 是可微的。

*引理 5.3.2 的证明。* 注意，(5.25) 和 (5.26) 确保对于所有 $\theta_{1} \in \mathbb{R}^{l_{1}}$、$\theta_{2} \in \mathbb{R}^{l_{2}}$ 和 $x \in \mathbb{R}^{l_{0}}$，均有

$$f(\theta_{1},\theta_{2},x)=F_{2}(\theta_{2},F_{1}(\theta_{1},x))=F_{2}(B(\theta_{2},\theta_{1},x))=F_{2}(B(A(\theta_{1},\theta_{2},x))). \qquad (5.27)$$

观察可知，引理 5.3.1（在引理 5.3.1 的记号下，取 $l_{1} \mapsto l_{2}$、$l_{2} \mapsto l_{1}+l_{0}$、$F_{1} \mapsto (\mathbb{R}^{l_{2}} \ni \theta_{2} \mapsto \theta_{2} \in \mathbb{R}^{l_{2}})$、$F_{2} \mapsto (\mathbb{R}^{l_{1}+l_{0}} \ni (\theta_{1},x) \mapsto F_{1}(\theta_{1},x) \in \mathbb{R}^{l_{1}})$）蕴含 $B$ 是可微的。结合这一点、$A$ 是可微的事实、$F_{2}$ 是可微的事实以及 (5.27)，利用链式法则可知 $f$ 是可微的。至此，引理 5.3.2 的证明完成。

### 5.3.2 关于人工神经网络实现的可微性

*引理 5.3.3* (*人工神经网络* 实现函数的可微性)。设 $L \in \mathbb{N}$，$l_{0}$、$l_{1}$、...、$l_L \in \mathbb{N}$；对于每个 $k \in \{1, 2, ..., L\}$，设 $d_k = l_k(l_k + 1)$；对于每个 $k \in \{1, 2, ..., L\}$，设 $\Psi_{k} : \mathbb{R}^{l_{k}} \rightarrow \mathbb{R}^{l_{k}}$ 是可微的；对于每个 $k \in \{1, 2, ..., L\}$，设 $F_k: \mathbb{R}^{d_{k}} \times \mathbb{R}^{l_{k-1}} \rightarrow \mathbb{R}^{l_{k}}$ 满足对于所有 $\theta \in \mathbb{R}^{d_{k}}$ 和 $x \in \mathbb{R}^{l_{k-1}}$，有

$$F_{k}(\theta,x)=\Psi_{k}(A_{l_{k},l_{k-1}}^{\theta,0}(x)) \qquad (5.28)$$

*(参见定义 1.1.1)*。那么

- (i) 对于所有 $\theta_{1} \in \mathbb{R}^{d_{1}}$、$\theta_{2} \in \mathbb{R}^{d_{2}}$、...、$\theta_{L} \in \mathbb{R}^{d_{L}}$ 和 $x \in \mathbb{R}^{l_{0}}$，均有

$$\big(\mathcal{N}_{\Psi_{1},\Psi_{2},\ldots,\Psi_{L}}^{\theta_{1},\theta_{2},\ldots,\theta_{L},l_{0}}\big)(x)=\big(F_{L}(\theta_{L},\cdot) \circ F_{L-1}(\theta_{L-1},\cdot) \circ \cdots \circ F_{1}(\theta_{1},\cdot)\big)(x) \qquad (5.29)$$

- (ii) 函数

$$\mathbb{R}^{d_{1}+d_{2}+\cdots+d_{L}} \times \mathbb{R}^{l_{0}} \ni (\theta,x) \mapsto \big(\mathcal{N}_{\Psi_{1},\Psi_{2},\ldots,\Psi_{L}}^{\theta,l_{0}}\big)(x) \in \mathbb{R}^{l_{L}} \qquad (5.30)$$

是可微的

*(参见定义 1.1.3)*。

*引理 5.3.3 的证明。* 注意，(1.1) 表明对于所有 $\theta_{1} \in \mathbb{R}^{d_{1}}$、$\theta_{2} \in \mathbb{R}^{d_{2}}$、...、$\theta_{L} \in \mathbb{R}^{d_{L}}$ 和 $k \in \{1, 2, ..., L\}$，均有

$$\mathcal{A}_{l_{k},l_{k-1}}^{(\theta_{1},\theta_{2},\ldots,\theta_{L}),\sum_{j=1}^{k-1}d_{j}}=\mathcal{A}_{l_{k},l_{k-1}}^{\theta_{k},0}. \qquad (5.31)$$

因此，我们得到对于所有 $\theta_{1} \in \mathbb{R}^{d_{1}}$、$\theta_{2} \in \mathbb{R}^{d_{2}}$、...、$\theta_{L} \in \mathbb{R}^{d_{L}}$ 和 $k \in \{1, 2, ..., L\}$，均有

$$F_{k}(\theta_{k},x)=\big(\Psi_{k} \circ \mathcal{A}_{l_{k},l_{k-1}}^{(\theta_{1},\theta_{2},\ldots,\theta_{L}),\sum_{j=1}^{k-1}d_{j}}\big)(x). \qquad (5.32)$$

