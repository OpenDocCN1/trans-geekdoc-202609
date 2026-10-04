```
$w_{opt}^T \cdot \mathbf{x}_i + b_{opt} = \pm 1 \quad (1.24)$
```

and

```
$b_{opt} = 1 - w_{opt}^T \cdot \mathbf{x}^{(s)}, \quad t^{(s)} = 1 \quad (1.25)$
```

since

```
$b_{opt} = 1 - \left(\sum_{i=1}^{N} \alpha_{opt,i} \cdot t_i \cdot \mathbf{x}_i^T\right) \cdot \mathbf{x}^{(s)}, \quad t^{(s)} = 1.$
```

# 1.3.7 Support Vector Machine as a Kernel Machine

Let $\mathbf{x}$ be a vector from the input space of $D$ and let $\{\phi(\mathbf{x})\}_{i=1}^N$ be a set of nonlinear functions, from $D$ dimension to infinite dimension. In feature space, the hyperplane would be defined as

```
$\mathbf{w}^T \cdot \Phi(\mathbf{x}) + b = 0 \quad (1.26)$
```

With $\Phi(\mathbf{x})$ being a feature vector with infinite dimension and $\mathbf{w}$ being the weight vector with infinite dimension. With $N_s$ being the number of support vectors, we can represent the weight vector as

```
$\mathbf{w} = \sum_{i=1}^{N_s} \alpha_i \cdot t_i \cdot \Phi(\mathbf{x}_i). \quad (1.27)$
```

We do not need the weight vector itself, all we need is the boundary or decision surface and we can represent it by

```
$\sum_{i=1}^{N_s} \alpha_i \cdot t_i \cdot \Phi^T(\mathbf{x}_i)\Phi(\mathbf{x}) = 0. \quad (1.28)$
```

All we need are inner products between support vectors $\langle\Phi(\mathbf{x}_i)|\Phi(\mathbf{x}_j)\rangle$. We can look at these inner products as the result of a kernel function

```
$k(\mathbf{x}_i, \mathbf{x}_j) = \Phi^T(\mathbf{x}_i)\Phi(\mathbf{x}_j) = \langle\Phi(\mathbf{x}_i)|\Phi(\mathbf{x}_j)\rangle \quad (1.29)$
```

Specifying the kernel $k(\mathbf{x}_i, \mathbf{x}_j)$ is sufficient, we need not explicitly compute the weight vector $w_{opt}$ [98]. Having the kernel we can take full advantage of the fact that

```
$\sum_{j=1}^{\infty} w_j \cdot \Phi(\mathbf{x}_j) + b = \sum_{j=1}^{\infty} \alpha_j \cdot t_j \cdot k(\mathbf{x}_k, \mathbf{x}_j) + b = 0. \quad (1.30)$
```

We can compute kernel matrix or Gram matrix where $k(\mathbf{x}_i, \mathbf{x}_j)$ is the $ij$-element of the $N \times N$ matrix. Resulting in something like

```
$K = \begin{pmatrix} k(\mathbf{x}_1, \mathbf{x}_1) & k(\mathbf{x}_1, \mathbf{x}_2) & k(\mathbf{x}_1, \mathbf{x}_3) & \dots & k(\mathbf{x}_1, \mathbf{x}_N) \ k(\mathbf{x}_2, \mathbf{x}_1) & k(\mathbf{x}_2, \mathbf{x}_2) & k(\mathbf{x}_2, \mathbf{x}_3) & \dots & k(\mathbf{x}_2, \mathbf{x}_N) \ \vdots & \vdots & \vdots & \ddots & \vdots \ k(\mathbf{x}_N, \mathbf{x}_1) & k(\mathbf{x}_N, \mathbf{x}_2) & k(\mathbf{x}_N, \mathbf{x}_3) & \dots & k(\mathbf{x}_N, \mathbf{x}_N) \end{pmatrix} \quad (1.31)$
```