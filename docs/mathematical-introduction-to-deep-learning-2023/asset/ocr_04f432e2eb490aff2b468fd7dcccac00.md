Chapter 5: *Optimization through ODEs*

```
26|  27|  plt.savefig(".../plots/huberloss.pdf", bbox_inches='tight')
```

Source code 5.5 (code/loss_functions/huberloss_plot.py): PYTHON code used to create Figure 5.5

# 5.4.4 Cross-entropy loss

> **Definition 5.4.5.** Let $d \in \mathbb{N}\{1\}$. We say that $\mathbf{L}$ is the $d$-dimensional cross-entropy loss function if and only if it holds that $\mathbf{L} : [0, \infty)^d \times [0, \infty)^d \to (-\infty, \infty]$ is the function from $[0, \infty)^d \times [0, \infty)^d$ to $(-\infty, \infty)$ which satisfies for all $x = (x_1, \dots, x_d)$, $y = (y_1, \dots, y_d) \in [0, \infty)^d$ that

$$
\mathbf{L}(x, y) = - \sum_{i = 1}^{d} \lim_{z \searrow x_i} [ \ln(z) y_i ]. \tag{5.49}
$$

![](bbox=[0.32, 0.39, 0.7, 0.63])

Figure 5.6 (plots/crossentropyloss.pdf): A plot of the function $(0, 1) \ni x \mapsto \mathbf{L}((x, 1 - x), (\frac{3}{10}, \frac{7}{10})) \in \mathbb{R}$ where $\mathbf{L}$ is the 2-dimensional cross-entropy loss function (cf. Definition 5.4.5).

```
```python
1  import numpy as np
2  import tensorflow as tf
3  import matplotlib.pyplot as plt
4  import plot_util
5
6  ax = plot_util.setup_axis((0, 1), (0, 3))
```
```