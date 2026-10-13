
$$
\min_{\{\theta_i, u_i\}_{i=1}^l} \quad (\mathbf{y} - X\mathbf{\theta})^T(\mathbf{y} - X\mathbf{\theta}) + \lambda\sum_{i=1}^l u_i, \quad \text{s.t.} \quad \left\{ \begin{aligned} & -u_i \leq \theta_i \leq u_i, \\ & u_i \geq 0, \end{aligned} \quad i = 1,2,\ldots,l \right.
$$

![Equation](images/B9780443292385000159/si53.png)

which can be solved by any standard convex optimization method (e.g., [14,101]). The reason that developing algorithms for the LASSO task has been at the center of an intense research activity is due to the emphasis on obtaining *efficient* algorithms by exploiting the specific nature of this task, especially for cases where *l* is very large, as is often the case in practice.

In order to get better insight into the nature of the solution that is obtained by LASSO, let us assume that the regressors are mutually orthogonal and of unit norm, hence $X^T X = I$.

![Equation](images/B9780443292385000159/si54.png)

Orthogonality of the input matrix helps to decouple the coordinates and results to *l* one-dimensional problems that can be solved analytically. For this case, the LS estimate becomes

$$
\widehat{\mathbf{\theta}}_{\text{LS}} = (X^T X)^{-1} X^T \mathbf{y} = X^T \mathbf{y},
$$

![Equation](images/B9780443292385000159/si55.png)

and the ridge regression gives

$$
\widehat{\mathbf{\theta}}_R = \frac{1}{1 + \lambda} \widehat{\mathbf{\theta}}_{\text{LS}},
$$

![Equation](images/B9780443292385000159/si56.png) (9.9)

that is, every component of the LS estimate is simply shrunk by the *same* factor, $\frac{1}{1 + \lambda}$;

![Equation](images/B9780443292385000159/si57.png)

see, also, Section [6.5](#Chp006_249-291_B9780443292385000123.xhtml).
