![](bbox=[0.2, 0.17, 0.8, 0.48])

Figure 5.2 (plots/gradient_plot2.pdf): Illustration of negative gradients in a two-dimensional example. The plot shows contour lines of the function $\mathbb{R}^{2} \ni(x, y) \mapsto \frac{1}{2}\left|x-1\right|^{2}+5\left|y-1\right|^{2} \in \mathbb{R}$ with arrows indicating the direction and magnitude of the negative gradient at several points along these contour lines. The PYTHON code used to produce this plot is given in Source code 5.2.

```
```
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
```
```