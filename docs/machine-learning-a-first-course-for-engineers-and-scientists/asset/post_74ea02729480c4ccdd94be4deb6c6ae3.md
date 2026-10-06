
## 8.4 Kernel theory

The kernel plays an important role in determining the influence of each training data point when making a prediction.

- Even though we started introducing kernels via the inner product $\phi(x)^T\phi(x')$, we do not have to bother about inner product...

In addition to this, the kernel also plays a somewhat more important role in methods that use the representer term (such as kernel regression, support vector regression and support vector classification, but not $k$-NN).

The $L^2$-regularization $\lambda||\theta||_2^2$ ensures we do not solve the primal formulation when using kernels (we solve the dual), it is nonetheless of equivalent representation...

- The choice of kernel corresponds to a role of a regularization function. That is, the kernel implies a preference for certain functions in the space of all functions that are spanned by the feature vector.

Using a kernel method is quite simple, and one could perceive that it would suffer from overfitting. However, the regularizing role of the kernel explains why that is rarely the case in practice.

All three points above are central to understanding the usefulness and versatility of kernel methods. They also highlight the importance for the machine learning engineer to choose the kernel wisely, and not resort to "default" choices.

## Valid choices of kernels

We introduced kernels as a way to work with nonlinear feature transformations as in (8.11). A direct consequence of that is it is not sufficient to consider $\kappa(x,x')$ and $\phi(x)$ independently.

```
$\kappa(x,x') = \phi(x)^T\phi(x')$
```

Before answering the question, we have to be aware that the question is primarily of theoretical nature. As long as we use $\kappa(x,x')$ computing its predictions is sure, no matter if it is factorization (8.21) or not.

That said, we will now have a closer look at the important family of positive semidefinite kernels. A kernel is said to be positive definite if the Gram matrix $K(X,X)$ as defined in (8.12b) is positive semidefinite...

## 8 Nonlinear transformations and kernels

First, it holds that a kernel $\kappa(x, x')$ defined as an inner product between feature vector $\phi(x)$, as in (8.21), is always positive semidefinite. It can be, for example, shown by the equivalent definition of positive semidefinite $\mathbf{v}^T \mathbf{K} \mathbf{v} \geq 0$ for any vector $\mathbf{v} = [v_1 \dots v_n]^T$. By using (8.2b), the definition of matrix multiplication (first equality) and property of the inner product (second equality below) we can indent:

```
$$\mathbf{v}^T \mathbf{K} \mathbf{v} = \sum_{i=1}^n \sum_{j=1}^n v_i \phi(x_i)^T \phi(x_j) v_j = \sum_{i=1}^n v_i \phi(x_i)^T \sum_{j=1}^n v_j \phi(x_j) \geq 0. (8.22)
```

Less trivial than the other holds that, for any positive semidefinite $\kappa(x,x')$ there exists a feature vector $\phi(x)$ such that $\kappa(x,x')$ can be written as an inner product (8.21). Technically it can be shown that for any positive semidefinite kernel $\kappa(x,x')$ it is possible to construct a function map, more specifically a Hilbert space, which is spanned by a feature vector $\phi(x)$ by which 8.21 holds. The dimensionality of the Hilbert space, and also the dimension of $\phi(x)$, can be infinite.

Given a kernel $\kappa(x,x')$ there are many ways to construct a Hilbert space spanned by $\phi(x)$, and we will only mention some others. One alternative is the so-called reproducing kernel map. The reproducing kernel map is obtained by one argument, say that, $\kappa(x,x')$ fixed and $x'$ span the Hilbert space with an inner product $\langle \cdot, \cdot \rangle$ such that $\langle \kappa(x,''), x' \rangle = \kappa(x,x')$. This inner product has a reproducing property, and alternatively the so-called Mercer kernel method which constructs the Hilbert space using an integral operator which is related to the kernel.

A given Hilbert space uniquely defines a kernel, but for a given kernel there exist multiple Hilbert spaces which correspond to it. In fact this means that a kernel $\kappa(x,x')$ representing the feature vector $\phi(x)$ is not unique, in fact not its dimensionality either. A simple example consider the linear kernel $\kappa(x,x') = \mathbf{x}^T \mathbf{x}'$, which can be expressed as an inner product between $\phi(x) = \mathbf{x}$ (one-dimensional $\phi(x)$) or as an inner product between $\phi(x) = \frac{1}{\sqrt{2}} [1, x^T]^T$ (two-dimensional $\phi(x)$).

### Examples of kernels

We will give a list of some commonly used kernels, which we have introduced above. These examples are only for the case when $x$ is a numeric value. For other types of input (such as in Example 8.4), we refer to the more specific application literature. We start with some positive semidefinite kernels, where the linear kernel is the simplest one:

```
$$\kappa(x,x') = \mathbf{x}^T \mathbf{x}'. (8.23)
```

A generalization thereof, still positive semidefinite, the polynomial kernel:

```
$$\kappa(x,x') = (c + \mathbf{x}^T \mathbf{x}')^d. (8.24)
```

with hyperparameter $c \geq 0$ and order $d$ (integer). The polynomial kernel corresponds to finite-dimensional feature vector $\phi(x)$. On the other hand, we have previously mentioned the squared kernel:

```
$$\kappa(x,x') = \exp\left(-\frac{||x-x'||^2}{2\ell}\right). (8.25)
```

with hyperparameter $\ell>0$ (lengthscale). This is the most commonly used because.
