Recall that we arrived at the Linear Discriminant Analysis by assuming $\mathbf{\Sigma}_0 = \mathbf{\Sigma} = \mathbf{\Sigma}$. In this case,

```
$$\begin{aligned} \mathbf{A} &= 0, \ \mathbf{b} &= \mathbf{\Sigma}^{-1}(\mu_0 - \mu_1), \ \mathbf{c} &= \frac{1}{2}(\mu_0^{\intertext{T}}\mathbf{\Sigma}^{-1}\mu_1 - \mu_0^{\intertext{T}}\mathbf{\Sigma}^{-1}\mu_0) \end{aligned}$
```

This is the equation of the line in the Linear Discriminant Analysis.
In this section, we look at the Quadratic Discriminant Analysis from a different angle by introducing artificial features and extending the feature space this way.

# ## 5.2 Kernel Trick

In the quadratic

```
$$\mathbf{v}^{\intertext{T}}\mathbf{A}\mathbf{v} + \mathbf{v}^{\intertext{T}}\mathbf{b} + c = 0$
```

the matrix $\mathbf{A}$ is symmetric, as $\mathbf{A}$ is the difference of covariance matrices which are symmetric. Assuming $M=2$ and writing

```
$$\mathbf{A} = \begin{pmatrix} A_{11} & A_{12} \ A_{12} & A_{22} \end{pmatrix}, \mathbf{b} = \begin{pmatrix} b_1 \ b_2 \end{pmatrix}$
```

the boundary equation can be written as

```
$$A_{11}v_1^2 + 2A_{12}v_1v_2 + A_{22}v_2^2 + b_1v_1 + b_2v_2 + c = 0$
```

Now we can rearrange this as

```
$$\begin{pmatrix} A_{11} & A_{12} & A_{22} & b_1 & b_2 \end{pmatrix} \begin{pmatrix} v_1^2 \ v_2^2 \end{pmatrix} + c = 0$
```

Let $\mathbf{w}^{\intertext{T}} = \begin{pmatrix} A_{11} & A_{12} & A_{22} & b_1 & b_2 \end{pmatrix}$ and $\mathbf{\{v}} = \begin{pmatrix} v_1^2 \ v_2^2 \ v_1 \ v_2 \end{pmatrix}$, this de-

cribes a linear boundary in a five-dimensional feature space.

```
$$\mathbf{w}^{\intertext{T}}\mathbf{\{v}} + c = 0$
```

In other words, we have augmented the feature space by three artificial features

```
$$v_1^2, v_2^2$
```