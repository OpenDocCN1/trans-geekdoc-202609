
# 1.2.13 RePU activation

![](img/dec290f673e6357c31893c67b579ffe1_47_0.png)

Figure 1.14 (plots/repU.pdf): A plot of the RePU activation function with power 2 and the ReLU activation function

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-2,2), (-.5,3))
ax.set_ylim(-.5, 3)

x = np.linspace(-2, 2, 100)

ax.plot(x, tf.keras.activations.relu(x), linewidth=3, label='ReLU')
ax.plot(x, tf.keras.activations.relu(x)**2, label='RePU')
ax.legend()

plt.savefig("../../plots/repU.pdf", bbox_inches='tight')
```

Source code 1.12 (code/activation_functions/repu_plot.py): PYTHON code used to create Figure 1.14

> **Definition 1.2.38 (Multidimensional RePU activation function).** Let $d,p \in \mathbb{N}$ and let $a$ be the RePU activation function with power $p$ (cf. Definition 1.2.37). Then we say that $A$ is the $d$-dimensional RePU activation function with power $p$ if and only if $A = \mathfrak{W}_{a,d}$ (cf. Definition 1.2.1).

# 1.2.14 Sine activation

The sine function has been proposed as activation function in Sitzmann et al. [380]. This is formulated in the next notation.

**Definition 1.2.39 (Sine activation function).** We say that $a$ is the sine activation function if and only if it holds that $a : \mathbb{R} \rightarrow \mathbb{R}$ is the function from $\mathbb{R}$ to $\mathbb{R}$ which satisfies for all $x \in \mathbb{R}$ that

$$a(x) = \sin(x).\tag{1.72}$$

![](img/dec290f673e6357c31893c67b579ffe1_48_0.png)

Figure 1.15 (plots/sine.pdf): A plot of the sine activation function

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-2*np.pi,2*np.pi), (-1.5,1.5))

x = np.linspace(-2*np.pi, 2*np.pi, 100)

ax.plot(x, np.sin(x))

plt.savefig("../../plots/sine.pdf", bbox_inches='tight')
```

Source code 1.13 (code/activation_functions/sine_plot.py): PYTHON code used to create Figure 1.15

**Definition 1.2.40 (Multidimensional sine activation functions).** Let $d \in \mathbb{N}$ and let $a$ be the sine activation function (cf. Definition 1.2.39). Then we say that $A$ is the $d$-dimensional sine activation function if and only if $A = \mathfrak{M}_{a, a}$ (cf. Definition 1.2.1).

# 1.2.15 Heaviside activation

**Definition 1.2.41 (Heaviside activation function).** We say that $a$ is the Heaviside activation function (we say that $a$ is the Heaviside step function, we say that $a$ is the unit step function) if and only if it holds that $a: \mathbb{R} \rightarrow \mathbb{R}$ is the function from $\mathbb{R}$ to $\mathbb{R}$ which satisfies for all $x \in \mathbb{R}$ that

$$a(x)=\mathbb{I}_{[0, \infty)}(x)=\left\{\begin{array}{ll} 1 & : x \geq 0 \\ 0 & : x<0 . \end{array}\right.\tag{1.73}$$

![](img/dec290f673e6357c31893c67b579ffe1_49_0.png)

Figure 1.16 (**plots/heaviside.pdf**): A plot of the Heaviside activation function and the standard logistic activation function

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-3, 3), (-.5, 1.5))

x = np.linspace(-3, 3, 100)
ax.plot(x[0:50], [0]*50, 'C0')
ax.plot(x[50:100], [1]*50, 'C0', label='Heaviside')
ax.plot(x, tf.keras.activations.sigmoid(x), 'C1',
        label='standard logistic')
ax.legend()

plt.savefig("../plots/heaviside.pdf", bbox_inches='tight')
```

Source code 1.14 (**code/activation\_functions/heaviside\_plot.py**): PYTHON code used to create Figure 1.16

**Definition 1.2.42 (Multidimensional Heaviside activation functions).** Let $d \in \mathbb{N}$ and let $a$ be the Heaviside activation function (cf. Definition 1.2.41). Then we say that $A$ is the $d$-dimensional Heaviside activation function (we say that $A$ is the $d$-dimensional Heaviside step function, we say that $A$ is the $d$-dimensional unit step function) if and only if $A = \mathfrak{M}_{a, d}$ (cf. Definition 1.2.1).

# 1.2.16 Softmax activation

**Definition 1.2.43 (Softmax activation function).** Let $d \in \mathbb{N}$. Then we say that $A$ is the $d$-dimensional softmax activation function if and only if it holds that $A: \mathbb{R}^d \rightarrow \mathbb{R}^d$ is the function from $\mathbb{R}^d$ to $\mathbb{R}^d$ which satisfies for all $x=(x_1, x_2, \ldots, x_d) \in \mathbb{R}^d$ that

$$A(x)=\left(\frac{\exp(x_1)}{\sum_{i=1}^{d} \exp(x_i)}, \frac{\exp(x_2)}{\sum_{i=1}^{d} \exp(x_i)}, \ldots, \frac{\exp(x_d)}{\sum_{i=1}^{d} \exp(x_i)}\right). \tag{1.74}$$

**Lemma 1.2.44.** Let $d \in \mathbb{N}$ and let $A=(A_1, A_2, \ldots, A_d)$ be the $d$-dimensional softmax activation function (cf. Definition 1.2.43). Then

- (i) it holds for all $x \in \mathbb{R}^d$, $k \in \{1, 2, \ldots, d\}$ that $A_k(x) \in (0, 1]$ and
- (ii) it holds for all $x \in \mathbb{R}^d$ that

$$\sum_{k=1}^{d} A_k(x)=1. \tag{1.75}$$

**Proof of Lemma 1.2.44.** Observe that (1.74) demonstrates that for all $x=(x_1, x_2, \ldots, x_d) \in \mathbb{R}^d$ it holds that

$$\sum_{k=1}^{d} A_k(x)=\sum_{k=1}^{d} \frac{\exp(x_k)}{\sum_{i=1}^{d} \exp(x_i)}=\frac{\sum_{k=1}^{d} \exp(x_k)}{\sum_{i=1}^{d} \exp(x_i)}=1. \tag{1.76}$$

The proof of Lemma 1.2.44 is thus complete. $\square$

# 1.3 Fully-connected feedforward ANNs (structured description)

In this section we present an alternative way to describe the fully-connected feedforward ANNs introduced in Section 1.1 above. Roughly speaking, in Section 1.1 above we defined a *vectorized description* of fully-connected feedforward ANNs in the sense that the trainable parameters of a fully-connected feedforward ANN are represented by the components of a single Euclidean vector (cf. Definition 1.1.3 above). In this section we introduce a *structured description* of fully-connected feedforward ANNs in which the trainable parameters of a fully-connected feedforward ANN are represented by a tuple of matrix-vector pairs corresponding to the weight matrices and bias vectors of the fully-connected feedforward ANNs (cf. Definitions 1.3.1 and 1.3.4 below).

## 1.3.1 Structured description of fully-connected feedforward ANNs

**Definition 1.3.1 (Structured description of fully-connected feedforward $ANNs$).** We denote by $\mathbf{N}$ the set given by

$$\mathbf{N} = \bigcup_{L \in \mathbb{N}} \bigcup_{l_0, l_1, \dots, l_L \in \mathbb{N}} \left( \bigtimes_{k=1}^L (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k}) \right)$$

For every $L \in \mathbb{N}$, $l_0, l_1, \dots, l_L \in \mathbb{N}$, $\Phi \in \left( \bigtimes_{k=1}^L (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k}) \right) \subseteq \mathbf{N}$ we denote by $\mathcal{P}(\Phi)$, $\mathcal{L}(\Phi)$, $\mathcal{I}(\Phi)$, $\mathcal{O}(\Phi) \in \mathbb{N}$, $\mathcal{H}(\Phi) \in \mathbb{N}_0$ the numbers given by

$$\mathcal{P}(\Phi) = \sum_{k=1}^L l_k(l_{k-1}+1), \quad \mathcal{L}(\Phi) = L, \quad \mathcal{I}(\Phi) = l_0, \quad \mathcal{O}(\Phi) = l_L, \quad \text{and} \quad \mathcal{H}(\Phi) = L-1$$

For every $n \in \mathbb{N}_0$, $L \in \mathbb{N}$, $l_0, l_1, \dots, l_L \in \mathbb{N}$, $\Phi \in \left( \bigtimes_{k=1}^L (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k}) \right) \subseteq \mathbf{N}$ we denote by $\mathbb{D}_n(\Phi) \in \mathbb{N}_0$ the number given by

$$\mathbb{D}_n(\Phi) = \begin{cases} l_n & : n \leq L \\ 0 & : n > L, \end{cases}$$

For every $\Phi \in \mathbf{N}$ we denote by $\mathcal{D}(\Phi) \in \mathbb{N}^{\mathcal{L}(\Phi)+1}$ the tuple given by

$$\mathcal{D}(\Phi) = (\mathbb{D}_0(\Phi), \mathbb{D}_1(\Phi), \dots, \mathbb{D}_{\mathcal{L}(\Phi)}(\Phi))$$

And for every $L \in \mathbb{N}$, $l_0, l_1, \dots, l_L \in \mathbb{N}$, $\Phi = ((W_1, B_1), \dots, (W_L, B_L)) \in \left( \bigtimes_{k=1}^L (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k}) \right) \subseteq \mathbf{N}$, $n \in \{1, 2, \dots, L\}$ we denote by $\mathcal{W}_{n, \Phi} \in \mathbb{R}^{l_n \times l_{n-1}}$, $\mathcal{B}_{n, \Phi} \in \mathbb{R}^{l_n}$ the matrix and the vector given by

$$\mathcal{W}_{n, \Phi} = W_n \quad\text{ and}\quad \mathcal{B}_{n, \Phi} = B_n.$$

**Definition 1.3.2 (Fully-connected feedforward $ANNs$).** We say that $\Phi$ is a fully-connected feedforward $ANN$ if and only if it holds that

$$\Phi \in \mathbf{N}$$

(cf. Definition 1.3.1).

**Lemma 1.3.3.** Let $\Phi \in \mathbf{N}$ (cf. Definition 1.3.1). Then

- (i) it holds that $\mathcal{D}(\Phi) \in \mathbb{N}^{\mathcal{L}(\Phi)+1}$,
- (ii) it holds that

$$\mathcal{I}(\Phi) = \mathbb{D}_0(\Phi) \quad\text{ and}\quad \mathcal{O}(\Phi) = \mathbb{D}_{\mathcal{L}(\Phi)}(\Phi),$$

