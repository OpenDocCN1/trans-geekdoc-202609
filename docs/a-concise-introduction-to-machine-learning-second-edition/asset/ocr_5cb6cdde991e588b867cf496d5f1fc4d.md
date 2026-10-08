![](bbox=[0.363, 0.189, 0.636, 0.335])

Figure 2.26: The shaded area is where $x_1 + x_2 \le y$ for the given $y$.

to be less than or equal to $y$ (note that $a_i$ could be $-\infty$ and $b_i$ could be $+\infty$).

+   - Calculate $F_y(y)$ as a sum over these intervals,

```
$F_y(y) = \sum_{i=1}^{k} \int_{-\infty}^{b_i(y)} f_x(x)dx - \int_{-\infty}^{a_i(y)} f_x(x)dx$$
```

+   - Use integration by substitution.

+   - Differentiate $F_y(y)$ with respect to $y$.

In the above example, there was only one where $a_1(y) = -\sqrt{y}$ and $b_1(y) = \sqrt{y}$.

This can be extended to $y$ being a function of multiple random variables $x_1, \dots, x_K$ which are summarized as $\mathbf{x} = (x_1, \dots, x_K)^T$ and follow a joint probability distribution $f_{\mathbf{x}}(\mathbf{x})$. The first step is to find the region $R(y)$ where $\mathbf{x} \in R(y)$ results in $g(\mathbf{x}) \le y$. Then calculate

```
$F_y(y) = \int_{R(y)} f_{\mathbf{x}}(\mathbf{x})d\mathbf{x}.$$
```

and with respect to $y$. However, this task might not be straightforward, found no closed solution for the integral, which is in several cases. We might illustrate with some examples.

Let $y = g(x_1, x_2) = x_1 + x_2$, where $x_1$ and $x_2$ are independent variables. Because of dependence, this simplifies as $f_{\mathbf{x}}(\mathbf{x}) = f_1(x_1)f_2(x_2)$. The condition $g(x_1, x_2) = x_1 + x_2 \le y$ can be written as $x_1 \le y$ and $x_2 \le y - x_1$, where all inequalities have to hold at the same time. While the interval of $x_1$ only depends on $y$, the interval of $x_2$ depends on both $y$ and $x_1$. The shaded area in Figure 2.26 shows where $x_1$ and $x_2$ lie to have $x_1 + x_2 \le y$.