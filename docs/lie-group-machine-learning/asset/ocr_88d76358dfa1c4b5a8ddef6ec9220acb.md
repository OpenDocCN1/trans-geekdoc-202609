In this experiment, for the image in the MNIST database, set $R = F$, and $\phi(I, x, y)$ is given by

```
$$\phi(I, x, y) = \begin{pmatrix} x, y, I(x, y), \left|\frac{\partial}{\partial x}I(x, y)\right|, \left|\frac{\partial}{\partial y}I(x, y)\right| \end{pmatrix}^{T} \quad (9.75)$$

$$\phi(I, x, y) = \begin{pmatrix} x, y, I(x, y), \left|\frac{\partial}{\partial x}I(x, y)\right|, \left|\frac{\partial}{\partial y}I(x, y)\right|, \sqrt{\left|\frac{\partial}{\partial x}I(x, y)\right|^{2} + \left|\frac{\partial}{\partial y}I(x, y)\right|^{2}} \end{pmatrix}^{T} \quad (9.76)$$

$$\phi(I, x, y) = \begin{pmatrix} x, y, I(x, y), \left|\frac{\partial}{\partial x}I(x, y)\right|, \left|\frac{\partial}{\partial y}I(x, y)\right|, \left|\frac{\partial^{2}}{\partial x^{2}}I(x, y)\right|, \left|\frac{\partial^{2}}{\partial y^{2}}I(x, y)\right| \end{pmatrix}^{T} \quad (9.77)$$

$$\phi(I, x, y) = \begin{pmatrix} x, y, I(x, y), \left|\frac{\partial}{\partial x}I(x, y)\right|, \left|\frac{\partial}{\partial y}I(x, y)\right|, \left|\frac{\partial^{2}}{\partial x^{2}}I(x, y)\right|, \left|\frac{\partial^{2}}{\partial y^{2}}I(x, y)\right|, \\ 	an^{-1}\left(\left(\frac{\partial}{\partial x}I(x, y)/\frac{\partial}{\partial y}I(x, y)\right)\right) \end{pmatrix}^{T} \quad (9.78)$$
```

In $(9.75) - (9.78)$, $I(x, y)$ is the luminance value at $(x, y)$, $\partial/\partial xI(x, y)$ is the first-order gradient in the transverse direction at $(x, y)$, $\partial^{2}/\partial x^{2}I(x, y)$ is the second-order gradient, $\sqrt{|\partial/\partial xI(x, y)|^{2} + |\partial/\partial yI(x, y)|^{2}}$ is the length of first-order gradient vector, and $\tan^{-1}(\partial/\partial xI(x, y)/\partial/\partial yI(x, y))$ is the arc tangent of the ratio of the first-order gradient vector. After modelling, we can get that $Z$ is a 5-dimensional, 6-dimensional, 7-dimensional, and 8-dimensional real vector for the four functions $(9.75) - (9.78)$. For $(9.78)$, the calculated $C_{R}$ is an $8 \times 8$ real symmetric matrix. Since $C_{R}$ is a symmetric matrix, $\sum_{i = 1}^{n} i |_{n = 8} = 36$ dimensions, which are lower than those for many image features. The covariance matrix is a real symmetric positive definite matrix. Many achievements have been made in the study of the spatial structure, metric, mean, and other properties of such matrices $[14, 22, 25]$.

The covariance matrix of the image becomes a tensor space, and each matrix is a point within the space. The distance between any two points $C_{1}$, $C_{2}$ is given by $[53]$

$$\rho\left(C_{1}, C_{2}\right) = \sqrt{\sum_{i = 1}^{n} \ln^{2} \lambda_{i}\left(C_{1}, C_{2}\right)} \quad (9.79)$$

and $\{\lambda_{i}\left(C_{1}, C_{2}\right)\}_{i = 1}^{n}$ are generalised eigenvalues of $C_{1}$, $C_{2}$, which can be calculated by

$$\lambda_{i} C_{1} x_{i} - C_{2} x_{i} = 0, \quad i = 1, \dots, d \quad (9.80)$$

where $x_{i} \neq 0$.

The vector satisfying $x_{i} \neq 0$ is a generalised eigenvector. It can be proved that $\rho$ satisfies the axioms of the second chapter about the metric in $(9.79)$. This metric also satisfies the Lie group structure of positive definite matrices, which can be derived from the Lie algebra of positive definite matrices.