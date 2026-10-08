**Definition 1.2.10** (Multidimensional clipping activation functions). *Let $d \in \mathbb{N}$, $u \in [ - \infty, \infty )$, $v \in (u, \infty]$. Then we denote by $\mathfrak{C}_{u, v, d}: \mathbb{R}^{d} \rightarrow \mathbb{R}^{d}$ the function given by*

$$\mathfrak{C}_{u, v, d} = \mathfrak{M}_{\mathfrak{C}_{u, v}, d} \tag{1.46}$$

*and we call $\mathfrak{C}_{u, v, d}$ the $d$-dimensional $(u, v)$-clipping activation function (cf. Definitions 1.2.1 and 1.2.9).*

# ## 1.2.5 Softplus activation

**Definition 1.2.11** (Softplus activation function). *We say that $a$ is the softplus activation function if and only if it holds that $a: \mathbb{R} \rightarrow \mathbb{R}$ is the function from $\mathbb{R}$ to $\mathbb{R}$ which satisfies for all $x \in \mathbb{R}$ that*

$$a(x) = \ln(1 + \exp(x)). \tag{1.47}$$

![](bbox=[0.29, 0.39, 0.68, 0.54])

Figure 1.6 (plots/softplus.pdf): A plot of the softplus activation function and the ReLU activation function

```
```python
import numpy as np
import tensorwlow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-4, 4), (-.5, 4))

x = np.linspace(-4, 4, 100)

ax.plot(x, tf.keras.activations.relu(x), label='ReLU')
ax.plot(x, tf.keras.activations.softplus(x), label='softplus')
ax.legend()

plt.savefig('../../plots/softplus.pdf', bbox_inches='tight')
```
```