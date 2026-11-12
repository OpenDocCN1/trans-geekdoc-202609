![](bbox=[0.26, 0.1, 0.74, 0.4])

Figure 3.32: Computational graph of e = c*d for UG and LG

$$
\frac{\partial d}{\partial b} = \frac{\partial}{\partial b}(b + 1)
$$
$$
\frac{\partial d}{\partial b} = 1
$$

Also,

$$
\frac{\partial e}{\partial d} = \frac{\partial}{\partial d}(c * d)
$$
$$
\frac{\partial e}{\partial d} = c = 3
$$
$$
\frac{\partial e}{\partial c} = \frac{\partial}{\partial c}(c * d)
$$
$$
\frac{\partial e}{\partial c} = d = 2
$$

And,

$$
\frac{\partial c}{\partial a} = \frac{\partial}{\partial a}(a + b)
$$
$$
\frac{\partial c}{\partial a} = b = 1
$$