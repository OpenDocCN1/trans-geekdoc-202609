
## Proof of Lemma 5.4.3

Note that (5.40) implies that for all $x = (x_1, \ldots, x_d)$, $y = (y_1, \ldots, y_d) \in \mathbb{R}^d$ it holds that

$$\mathbf{L}(x,y) = \|x-y\|_2^2 = \langle x-y, x-y\rangle = \sum_{i=1}^{d} (x_i - y_i)^2. \tag{5.42}$$

Hence, we obtain that for all $x,y \in \mathbb{R}^d$ it holds that $\mathbf{L} \in C^1(\mathbb{R}^d \times \mathbb{R}^d, \mathbb{R})$ and

$$(\nabla \mathbf{L})(x,y) = (2(x-y), -2(x-y)) \in \mathbb{R}^{2d}. \tag{5.43}$$

This implies that for all $x,y,h,k \in \mathbb{R}^d$ it holds that

$$\mathbf{L}'(x,y)(h,k) = \langle 2(x-y), h\rangle + \langle -2(x-y), k\rangle = 2\langle x-y, h-k\rangle. \tag{5.44}$$

Furthermore, observe that (5.43) implies that for all $x,y \in \mathbb{R}^d$ it holds that $\mathbf{L} \in C^2(\mathbb{R}^d \times \mathbb{R}^d, \mathbb{R})$ and

$$(\mathrm{Hess}_{(x,y)} \mathbf{L}) = \begin{pmatrix} 2I_d & -2I_d \\ -2I_d & 2I_d \end{pmatrix}. \tag{5.45}$$

Therefore, we obtain that for all $x,y,h,k \in \mathbb{R}^d$ it holds that

$$\mathbf{L}^{(2)}(x,y)(\langle h,k\rangle, \langle h,k\rangle) = 2\langle h,h\rangle - 2\langle h,k\rangle - 2\langle k,h\rangle + 2\langle k,k\rangle = 2\|h-k\|_2^2. \tag{5.46}$$

Combining this with (5.43) shows that for all $x,y \in \mathbb{R}^d$, $h,k \in \mathbb{R}^d$ it holds that $\mathbf{L} \in C^\infty(\mathbb{R}^d \times \mathbb{R}^d, \mathbb{R})$ and

$$\begin{split}\mathbf{L}(x,y) + \mathbf{L}'(x,y)(h,k) + \tfrac{1}{2}\mathbf{L}^{(2)}(x,y)(\langle h,k\rangle, \langle h,k\rangle) \\ \quad \quad = \|x-y\|_2^2 + 2\langle x-y, h-k\rangle + \|h-k\|_2^2 \\ \quad \quad = \|x-y+(h-k)\|_2^2 \\ \quad \quad = \mathbf{L}(x+h, y+k). \end{split} \tag{5.47}$$

This implies items (i) and (ii). The proof of Lemma 5.4.3 is thus complete.

### 5.4.3 Huber error loss

**Definition 5.4.4.** Let $d \in \mathbb{N}$, let $\delta \in [0,\infty)$, and let $\|\cdot\| : \mathbb{R}^d \to [0,\infty)$ be a norm. We say that $\mathbf{L}$ is the $\delta$-Huber-error loss function based on $\|\cdot\|$ if and only if it holds that $\mathbf{L} : \mathbb{R}^d \times \mathbb{R}^d \to \mathbb{R}$ is the function from $\mathbb{R}^d \times \mathbb{R}^d$ to $\mathbb{R}$ which satisfies for all $x,y \in \mathbb{R}^d$ that

$$\mathbf{L}(x,y) = \begin{cases} \frac{1}{2}\|x-y\|^2 & : \|x-y\| \leq \delta \\ \delta(\|x-y\| - \frac{\delta}{2}) & : \|x-y\| > \delta. \end{cases} \tag{5.48}$$

![](img/dec290f673e6357c31893c67b579ffe1_186_0.png)

Figure 5.5 (**plots/huber_loss.pdf**): A plot of the functions $\mathbb{R} \ni x \mapsto \mathbf{L}_{i}(x, 0) \in [0, \infty)$, $i \in \{1, 2, 3\}$, where $\mathbf{L}_{0}$ is the mean squared error loss function based on $\mathbb{R} \ni x \mapsto |x| \in [0, \infty)$, where $\mathbf{L}_{1}: \mathbb{R}^{d} \times \mathbb{R}^{d} \to [0, \infty)$ satisfies for all $x, y \in \mathbb{R}^{d}$ that $\mathbf{L}_{1}(x, y)=\frac{1}{2} \mathbf{L}_{0}(x, y)$, where $\mathbf{L}_{2}$ is the $\ell^{1}$-error loss function based on $\mathbb{R} \ni x \mapsto |x| \in [0, \infty)$, and where $\mathbf{L}_{3}$ is the 1-Huber loss function based on $\mathbb{R} \ni x \mapsto |x| \in [0, \infty)$.

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((-3,3), (-.5,4))

x = np.linspace(-3, 3, 100)

mse_loss = tf.keras.losses.MeanSquaredError(
    reduction=tf.keras.losses.Reduction.NONE)
mae_loss = tf.keras.losses.MeanAbsoluteError(
    reduction=tf.keras.losses.Reduction.NONE)
huber_loss = tf.keras.losses.Huber(
    reduction=tf.keras.losses.Reduction.NONE)

zero = tf.zeros([100,1])

ax.plot(x, mse_loss(x.reshape([100,1]),zero)/2.,
    label='Scaled mean squared error')
ax.plot(x, mae_loss(x.reshape([100,1]),zero),
    label='$\ell$-error')
ax.plot(x, huber_loss(x.reshape([100,1]),zero),
    label='1-Huber-error')
ax.legend()
plt.savefig(".../plots/huberloss.pdf", bbox_inches='tight')
```

Source code 5.5 (code/loss_functions/huberloss_plot.py): PYTHON code used to create Figure 5.5

## 5.4.4 Cross-entropy loss

**Definition 5.4.5.** Let $d \in \mathbb{N} \setminus \{1\}$. We say that $\mathbf{L}$ is the $d$-dimensional cross-entropy loss function if and only if it holds that $\mathbf{L} : [0, \infty)^d \times [0, \infty)^d \to (-\infty, \infty]$ is the function from $[0, \infty)^d \times [0, \infty)^d$ to $(-\infty, \infty)$ which satisfies for all $x = (x_1, \dots, x_d)$, $y = (y_1, \dots, y_d) \in [0, \infty)^d$ that

$$
\mathbf{L}(x, y) = - \sum_{i = 1}^{d} \lim_{z \searrow x_i} [ \ln(z) y_i ]. \tag{5.49}
$$

![](img/dec290f673e6357c31893c67b579ffe1_187_0.png)

Figure 5.6 (plots/crossentropyloss.pdf): A plot of the function $(0, 1) \ni x \mapsto \mathbf{L}((x, 1 - x), (\frac{3}{10}, \frac{7}{10})) \in \mathbb{R}$ where $\mathbf{L}$ is the 2-dimensional cross-entropy loss function (cf. Definition 5.4.5).

```python
import numpy as np
import tensorflow as tf
import matplotlib.pyplot as plt
import plot_util

ax = plot_util.setup_axis((0, 1), (0, 3))
ax.set_aspect(.3)

x = np.linspace(0, 1, 100)

cce_loss = tf.keras.losses.CategoricalCrossentropy(
    reduction=tf.keras.losses.Reduction.NONE)
y = tf.constant([[0.3, 0.7]] * 100, shape=(100, 2))

X = tf.stack([x,1-x], axis=1)

ax.plot(x, cce_loss(y,X), label='Cross-entropy')
ax.legend()

plt.savefig("../../plots/crossentropyloss_plot.pdf", bbox_inches='tight')
```

Source code 5.6 (code/loss_functions/crossentropyloss_plot.py): PYTHON code used to create Figure 5.6

**Lemma 5.4.6.** Let $d \in \mathbb{N} \setminus \{1\}$ and let $\mathbf{L}$ be the $d$-dimensional cross-entropy loss function (cf. Definition 5.4.5). Then

(i) it holds for all $x = (x_1, \dots, x_d), y = (y_1, \dots, y_d) \in [0, \infty)^d$ that

$$(\mathbf{L}(x, y) = \infty) \leftrightarrow (\exists i \in \{1, 2, \dots, d\} : [(x_i = 0) \wedge (y_i \neq 0)]) , \tag{5.50}$$

(ii) it holds for all $x = (x_1, \dots, x_d), y = (y_1, \dots, y_d) \in [0, \infty)^d$ with $\forall i \in \{1, 2, \dots, d\} : [(x_i \neq 0) \vee (y_i = 0)]$ that

$$\mathbf{L}(x, y) = - \sum_{\substack{i \in \{1,2, \dots, d\}, \\ y_i \neq 0}} \ln(x_i) y_i \in \mathbb{R} , \tag{5.51}$$

and

(iii) it holds for all $x = (x_1, \dots, x_d) \in (0, \infty)^d, y = (y_1, \dots, y_d) \in [0, \infty)^d$ that

$$\mathbf{L}(x, y) = - \sum_{i=1}^{d} \ln(x_i) y_i \in \mathbb{R} . \tag{5.52}$$

**Proof of Lemma 5.4.6.** Note that (5.49) and the fact that for all $a, b \in [0, \infty)$ it holds that

$$\lim_{z \searrow a} [\ln(z) b] = \begin{cases} 0 & : b = 0 \\ \ln(a) b & : (a \neq 0) \wedge (b \neq 0) \\ -\infty & : (a = 0) \wedge (b \neq 0) \end{cases} \tag{5.53}$$

prove items (i), (ii), and (iii). The proof of Lemma 5.4.6 is thus complete. $\quad \square$

**Lemma 5.4.7.** Let $d \in \mathbb{N} \backslash \{1\}$, let $\mathbf{L}$ be the $d$-dimensional cross-entropy loss function, let $x = (x_1, \dots, x_d)$, $y = (y_1, \dots, y_d)$ in $[0, \infty)^d$ satisfy $\sum_{i=1}^d x_i = \sum_{i=1}^d y_i$ and $x \neq y$, and let $f: [0, 1] \to (-\infty, \infty]$ satisfy for all $h$ in $[0, 1]$ that

$$f(h) = \mathbf{L}(x + h(y - x), y) \tag{5.54}$$

(cf. Definition 5.4.5). Then $f$ is strictly decreasing.

**Proof of Lemma 5.4.7.** Throughout this proof, let $g: [0, 1) \to (-\infty, \infty]$ satisfy for all $h \in [0, 1)$ that

$$g(h) = f(1 - h) \tag{5.55}$$

and let $J = \{i \in \{1, 2, \dots, d\}: y_i \neq 0\}$. Observe that (5.54) shows that for all $h \in [0, 1]$ it holds that

$$g(h) = \mathbf{L}(x + (1 - h)(y - x), y) = \mathbf{L}(y + h(x - y), y). \tag{5.56}$$

Furthermore, note that the fact that for all $i \in J$ it holds that $x_i \in [0, \infty)$ and $y_i \in (0, \infty)$ ensures that for all $i \in J$, $h \in [0, 1)$ it holds that

$$y_i + h(x_i - y_i) = (1 - h)y_i + hx_i \geq (1 - h)y_i > 0. \tag{5.57}$$

This, (5.56), and item (ii) in Lemma 5.4.6 imply that for all $h \in [0, 1)$ it holds that

$$g(h) = -\sum_{i \in J} \ln(y_i + h(x_i - y_i))y_i \in \mathbb{R}. \tag{5.58}$$

The chain rule hence demonstrates that for all $h \in [0, 1)$ it holds that $([0, 1) \ni z \mapsto g(z) \in \mathbb{R}) \in C^\infty([0, 1), \mathbb{R})$ and

$$g'(h) = -\sum_{i \in J} \frac{y_i(x_i - y_i)}{y_i + h(x_i - y_i)}. \tag{5.59}$$

This and the chain rule establish that for all $h \in [0, 1)$ it holds that

$$g''(h) = \sum_{i \in J} \frac{y_i(x_i - y_i)^2}{(y_i + h(x_i - y_i))^2}. \tag{5.60}$$

Moreover, observe that the fact that for all $z = (z_1, \dots, z_d) \in [0, \infty)^d$ with $\sum_{i=1}^d z_i = \sum_{i=1}^d y_i$ and $\forall i \in J: z_i = y_i$ it holds that

$$\begin{aligned} \sum_{i \in \{1, 2, \dots, d\} \setminus J} z_i &= \left[ \sum_{i \in \{1, 2, \dots, d\}} z_i \right] - \left[ \sum_{i \in J} z_i \right] \\
&= \left[ \sum_{i \in \{1, 2, \dots, d\}} y_i \right] - \left[ \sum_{i \in J} z_i \right] \\
&= \sum_{i \in J} (y_i - z_i) = 0 \end{aligned} \tag{5.61}$$
