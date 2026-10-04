In the dual problem, we replace the scalar multiplication

```
$$\mathbf{x}_i^T \mathbf{x}_j = \langle\mathbf{x}_i, \mathbf{x}_j\rangle$
```

by the kernel

```
$k(\mathbf{x}_i, \mathbf{x}_j),$
```

everything stays the same. So, given the training sample $\{\mathbf{x}_i, t_i\}_{i=1}^N$, with $t_i \in \{-1, +1\}$ we want to find the Lagrange multipliers $\{\alpha_i\}_{i=1}^N$ that maximize

```
$Q(\alpha) = \sum_{i=1}^N \alpha_i - \frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N \alpha_i \cdot \alpha_j \cdot t_i \cdot t_j \cdot k(\mathbf{x}_i, \mathbf{x}_j) \quad (1.32)
```

subject to constraints

```
$$\sum_{i=1}^N \alpha_i \cdot t_i = 0 \quad (1.33)
```

```
$0 \leq \alpha_i \leq C, \quad i = 1, 2, \cdots, N \quad (1.34)
```

where $C$ is a user specified positive parameter. To compute the output

+   1. First we determine the bias
$$b = \frac{1}{N_i} \left(t_i - \sum_{j=1}^{N_i} \alpha_j \cdot t_j \cdot k(\mathbf{x}_i, \mathbf{x}_j) \right) \quad (1.35)$

+   2. then the output
$$o = \text{sgn}\left(\sum_{i=1}^{N_s} \alpha_i \cdot t_i \cdot k(\mathbf{x}_i, \mathbf{x}_i) + b\right) \quad (1.36)$

# 1.3.7.1 Example: XOR Problem

The XOR Problem is described by four vectors [41], instead of 0 we will use $\{-1\)

```
$$\mathbf{x}_1 = \begin{pmatrix} 1 \ -1 \end{pmatrix}, \mathbf{x}_2 = \begin{pmatrix} 1 \ 1 \end{pmatrix}, \mathbf{x}_3 = \begin{pmatrix} -1 \ -1 \end{pmatrix}, \mathbf{x}_4 = \begin{pmatrix} 1 \ 1 \end{pmatrix}$
```

and the corresponding target of the two classes is indicated as

```
$t_1 = -1, t_2 = 1, t_3 = 1, t_4 = -1$.
```

We will use a polynomial kernel

```
$k(\mathbf{x}_i, \mathbf{x}_j) = (1 + \mathbf{x}_i^T \mathbf{x}_j)^2$
```

with

```
$k(\mathbf{x}_i, \mathbf{x}_j) = 1 + x_{i1}^2 \cdot x_{j1}^2 + 2 \cdot x_{i1} \cdot x_{i2} \cdot x_{j1} \cdot x_{j2} + x_{i2}^2 \cdot x_{j2}^2 + 2 \cdot x_{i1} \cdot x_{j1} + 2 \cdot x_{i2} \cdot x_{j2}$
```