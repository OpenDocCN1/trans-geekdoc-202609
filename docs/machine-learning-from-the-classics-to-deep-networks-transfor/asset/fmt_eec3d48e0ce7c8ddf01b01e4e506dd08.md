
The `focal underdetermined system solver` (FOCUSS) algorithm [64] was the first one to use the concept of `iterative-reweighted-least-squares` to represent ℓ[*p*], *p* ≤ 1, as a weighted ℓ[2] norm in order to find a sparse solution to an underdetermined system of equations. This algorithm is also of historical importance, because it is among the very first ones to emphasize the importance of sparsity; moreover, it provides comprehensive convergence analysis as well as a characterization of the stationary points of the algorithm. Variants of this basic iterative weighting scheme have also been proposed (see, e.g., [35] and the references therein).

In [126], the `elastic net` regularization penalty was introduced, which combines the ℓ[2] and ℓ[1] concepts together in a tradeoff fashion, that is,

```
$\lambda\sum\limits_{i = 1}^{l}\left( \alpha\theta_{i}^{2} + (1 - \alpha)|\theta_{i}| \right),$
```

where *α* is a user-defined parameter controlling the influence of each individual term. The idea behind the elastic net is to combine the advantages of the LASSO and the ridge regression. In problems where there is a group of variables in ***x*** that are highly correlated, LASSO tends to select one of the corresponding parameters in ***θ***, and set the rest to zero in a rather arbitrary fashion. This can be understood by looking carefully at how the greedy algorithms work. When sparsity is used to select the most important of the variables in ***x*** (feature selection), it is better to select all the relevant components in the group. If one knew which of the variables are correlated, he/she could form a group and then use the group LASSO. However, if this is not known, involving the ridge regression offers a remedy to the problem. This is because the ℓ[2] penalty in ridge regression tends to shrink the parameters associated with correlated variables toward each other (e.g., [68]). In such cases, it would be better to work with the elastic net rationale that involves LASSO and ridge regression in a combined fashion.

In [23], the LASSO task is modified by replacing the squared error term with one involving correlations, and the minimization task becomes

```
$\widehat{\mathbf{\theta}}:\ \ \ \ \ \min\limits_{\mathbf{\theta} \in \mathbb{R}^{l}}\left\| \mathbf{\theta} \right\|_{1},\text{s.t.}\ \ \ \ \left\| X^{T}(\mathbf{y} - X\mathbf{\theta}) \right\|_{\infty} \leq \epsilon,$
```

where *ϵ* is related to *l* and the noise variance. This task is known as the `Dantzig selector`. That is, instead of constraining the energy of the error, the constraint now imposes an upper limit to the correlation of the error vector with any of the columns of *X*. In [5,15], it is shown that under certain conditions, the LASSO estimator and the Dantzig selector become identical.

`Total variation` (TV) [107] is a closely related to ℓ[1] sparsity promoting notion that has been widely used in image processing. Most of the grayscale image arrays, *I* ∈ ℝ^(*l* × *l*), consist of slowly varying pixel intensities except at the edges. As a consequence, the discrete gradient of an image array will be approximately sparse (compressible). The discrete directional derivatives of an image array are defined pixel-wise as
