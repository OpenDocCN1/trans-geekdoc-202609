![](bbox=[0.325, 0.18, 0.506, 0.29])

(a) Constant kernel.

![](bbox=[0.533, 0.18, 0.686, 0.29])

(b) Linear kernel, $k(\mathbf{x}, \mathbf{y}) = 1 + \mathbf{x}^T\mathbf{y}$.

![](bbox=[0.325, 0.335, 0.506, 0.445])

(c) Quadratic kernel, $k(\mathbf{x}, \mathbf{y}) = (1 + \mathbf{x}^T\mathbf{y})^2$.

![](bbox=[0.533, 0.335, 0.686, 0.445])

(d) Gaussian kernel, $	heta = l = 1$.

![](bbox=[0.325, 0.489, 0.506, 0.599])

(e) Exponential kernel, $	heta = l = 1$.

![](bbox=[0.533, 0.489, 0.686, 0.599])

(f) Inverse multiquadric, $	heta = l = 1$.

Figure 8.12: Four draws from a Gaussian process with different kernels.

We assume that $f$ is drawn from a Gaussian process with kernel $k$ and mean zero. Therefore, the vector $(t_1, \dots, t_n, l_*)$ follows a normal distribution with mean zero and covariance matrix

> $$\begin{pmatrix} C \ k(\mathbf{x}_*)^T & c(\mathbf{x}_*) \end{pmatrix}$$

where the vector $k(\mathbf{x}_*)$ has elements $k(\mathbf{x}_n, \mathbf{x}_*)$ for $n = 1, \dots, N, c(\mathbf{x}_*) = k(\mathbf{x}_*, \mathbf{x}_*) + \sigma^2$, and the $(i, j)$ entry of $C$ is

```
$C_{ij} = k(\mathbf{x}_i, \mathbf{x}_j) + \sigma^2\delta_{ij},$
```

where $\delta_{ij}$ is zero for $i \neq j$ and one for $i = j$ and is known as the Kronecker delta.