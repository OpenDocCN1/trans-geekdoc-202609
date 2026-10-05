# Kernel Ridge Regression

In ridge regression, we give a vector $\mathbf{y} \in \mathbb{R}^n$ and a matrix $\mathbf{X} \in \mathbb{R}^{n \times l}$, where $n$ is the number of training points and $l$ is the dimension of the raw data points. In most settings we don't want to work with the raw feature space, so we augment features to the data points and replace $\mathbf{X}$ with $\mathbf{\Phi} \in \mathbb{R}^{n \times d}$, where $\phi_i = \phi(\mathbf{x}_i) \in \mathbb{R}^d$. Then we solve a well-defined optimization problem that involves $\mathbf{\Phi}$ and $y$, where the parameters $\mathbf{w} \in \mathbb{R}^d$. Note the problem that arises here. If we use polynomial features of degree $p$ in the raw $l$ dimensional space, then there are $d = \binom{l+p}{p}$ terms that we need to optimize, which can be very, large (much larger than the number of training points $n$). Wouldn't it be better, instead of solving an optimization problem over $d$ variables, could we solve an equivalent problem over (potentially smaller) $n$ variables, and achieve a computational runtime independent of the number of augmented features? As it turns out, the concept of kernels (in addition to a technique called the kernel trick) will allow us to achieve this goal. Consider the solution to ridge regression:

```
\mathbf{w} =(\mathbf{\Phi}^T\mathbf{\Phi} + \lambda\mathbf{I})^{-1}\mathbf{\Phi}^T\mathbf{y}
```

This operation involves calculating $\mathbf{\Phi}^T\mathbf{\Phi}$, which is a $d \times d$ matrix and takes $O(d^2n)$ time to compute. The matrix inversion takes an additional $O(d^3)$ time to compute. What we really like is to have an $n \times n$ matrix that takes $O(n^3)$ to invert: if we flip the order of $\mathbf{\Phi}$ and $\mathbf{\Phi}$, we end up with an $n \times n$ matrix $\mathbfmathbf{\Phi}^T\mathbf{\Phi}$. In fact, $\mathbf{\Phi}^T\mathbf{\Phi}$ has a intuitive meaning: it is the matrix of inner products between all of the augmented datapoints, which in terms measures the 'similarity' of all the datapoints and captures their representation. Now let's see if we could somehow express the solution to ridge regression using the matrix $\mathbfmathbf{\Phi}^T$.

# Derivation

For simplicity of notation, let's revert back to using $\mathbf{X}$ instead of $\mathbfmathbf{\Phi}$ (pretend that we are only working with raw features, our analysis of kernel ridge regression still holds if we use just the raw data). Rearranging the terms of the original regression solution we have

```
\mathbf{w}=(\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})^{-1}\mathbf{X}^T\mathbf{y}
\n(\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})\mathbf{w}=\mathbf{X}^T\mathbf{y}
\n\mathbf{X}^T\mathbf{Xw}+\lambda\mathbf{w}=\mathbf{X}^T\mathbf{y}
\n\lambda\mathbf{w}=\mathbf{X}^T\mathbf{y}-\mathbf{X}^T\mathbf{Xw}=\mathbf{X}^T(\mathbf{y}-\mathbf{Xw})
\n\mathbf{w}=\frac{1}{\lambda}(\mathbf{X}^T\mathbf{y}-\mathbf{X}^T\mathbf{Xw})
\n\mathbf{w}=\mathbf{X}^T\mathbf{y}/\lambda
```

which says that whatever $\mathbf{w}$ is, it is some linear combination of the training points $\mathbf{x}_i$, (because anything of the form $\mathbfmathbf{X}^T\mathbf{v}$ is a linear combination of the columns of $\mathbfmathbf{X}^T$, which are the training points). To find $\mathbfmathbf{w}$ it suffices to find $\mathbfmathbf{v}$, where $\mathbfmathbf{w}=\mathbf{X}^T\mathbf{v}$.

Recall that the relationship we have to satisfy is $\mathbfmathbf{X}^T\mathbf{X}-\lambda\mathbf{w}=\mathbf{X}^T\mathbf{y}$. Let's assume that we have $\mathbfmathbf{v}$, and substitute $\mathbfmathbf{v}$ in $\mathbf{w}$ for all the $\mathbfmathbf{w}$.

```
\mathbf{X}^T(\mathbf{X}\mathbf{v}) +\lambda(\mathbf{X}^T\mathbf{v})=\mathbf{X}^T\mathbf{y}
```