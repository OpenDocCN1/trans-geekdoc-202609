![](bbox=[0.345, 0.115, 0.628, 0.273])

**Fig. 3.10** Example of a non-linear separation between two classes.

Let us illustrate the basic idea with an example in two-dimensions. A linear function with two attributes that span the 2-dimensional feature space is given by

```
$y = w_0 + w_1x_1 + w_2x_2 = \mathbf{w}^T\mathbf{x},$
```

with

```
$$\mathbf{x} = \begin{pmatrix} x_1 \ x_2 \end{pmatrix}$
```

and weight vector

```
$$\mathbf{w}^T = (w_0, w_1, w_2).$
```

Let us say that we cannot separate the data with this linear function but that we could separate it with a polynomial that would include second-order terms like

```
$y = \tilde{w}_0 + \tilde{w}_1x_1 + \tilde{w}_2x_2 + \tilde{w}_3x_1x_2 + \tilde{w}_4x_1^2 + \tilde{w}_5x_2^2 = \tilde{\phi}(\mathbf{x}).$.
```

We can view the second equation as a linear separation on a feature vector

```
$$\mathbf{x} \rightarrow \phi(\mathbf{x}) = \begin{pmatrix} x_1 \ x_2 \ x_1x_2 \ x_1^2 \ x_2^2 \end{pmatrix}$
```

This can be seen as mapping the attribute $(1, x_1, x_2)$ to a higher-dimensional space with the mapping function $\phi(\mathbf{x})$. We call this a feature map. The separating hyperplane is then linear in this higher-dimensional space. Thus, we can use the linear maximum classification method in non-linear cases if we replace all occurrences of the attribute $\mathbf{x}$ with the mapped feature $\phi(\mathbf{x})$.

There are only three problems remaining. One is that we don't know the mapping function should be. The somewhat ad-hoc solution to this problem will be that we try out some functions and see which works best. We will discuss this further later in this chapter. The second problem is that we have the problem of overfitting