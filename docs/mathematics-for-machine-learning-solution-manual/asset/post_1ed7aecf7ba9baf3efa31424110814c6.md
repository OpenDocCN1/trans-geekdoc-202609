
Looking at (6.11), it remains to compute the cross-covariance term \(\Sigma_{xy}\) (the marginal distributions \(p(x)\) and \(p(y)\) are known and \(\Sigma_{yx} = \Sigma_{xy}^\top\)):

\[
\Sigma_{xy} = \mathrm{Cov}[x, y] = \mathbb{E}_{X,Y}[x y^\top] - \mathbb{E}_X[x] \mathbb{E}_Y[y]^\top = \mathbb{E}_{X,Y}[x y^\top] - \mu_x \mu_y^\top,
\]

where \(\mu_x\) and \(\mu_y\) are known. Hence, it remains to compute

\[
\mathbb{E}_{X,Y}[x y^\top] = \mathbb{E}_X[x (A x + b + w)^\top] = \mathbb{E}_X[x x^\top] A^\top + \mathbb{E}_X[x] b^\top = \mathbb{E}_X[x x^\top] A^\top + \mu_x b^\top.
\]

With

\[
\mu_x \mu_y^\top = \mu_x \mu_x^\top A^\top + \mu_x b^\top
\]

we obtain the desired cross-covariance

\[
\Sigma_{xy} = \mathbb{E}_X[x x^\top] A^\top + \mu_x b^\top - \mu_x \mu_x^\top A^\top - \mu_x b^\top = (\mathbb{E}_X[x x^\top] - \mu_x \mu_x^\top) A^\top = \Sigma_x A^\top.
\]

And finally

\[
\mu_{x|y} = \mu_x + \Sigma_x A^\top (A \Sigma_x A^\top + Q)^{-1} (y - A \mu_x - b), \qquad
\Sigma_{x|y} = \Sigma_x - \Sigma_x A^\top (A \Sigma_x A^\top + Q)^{-1} A \Sigma_x.
\]

## 6.13 Probability Integral Transformation

Given a continuous random variable \(x\), with cdf \(F_X(x)\), show that the random variable \(y = F_X(x)\) is uniformly distributed.

**Proof.** We need to show that the cumulative distribution function of \(Y\) defines a distribution of a uniform random variable. Recall that by the axioms of probability (Section 6.1) probabilities must be non-negative and sum/integrate to one. Therefore, the range of possible values of \(Y = F_X(x)\) is the interval \([0, 1]\). For any \(F_X(x)\), the inverse \(F_X^{-1}\) exists because we assumed that \(F_X(x)\) is strictly monotonically increasing, which we will use in the following.

Given any continuous random variable \(X\), the definition of a cdf gives

\[
F_Y(y) = P(Y \le y) = P(F_X(x) \le y) \quad \text{(transformation of interest)}
\]
\[
= P(X \le F_X^{-1}(y)) \quad \text{(inverse exists)}
\]
\[
= F_X(F_X^{-1}(y)) \quad \text{(definition of cdf)}
\]
\[
= y,
\]

where the last line is due to the fact that \(F_X(x)\) composed with its inverse results in an identity transformation. The statement \(F_Y(y) = y\) along with the fact that \(y\) lies in the interval \([0, 1]\) means that \(F_Y(y)\) is the cdf of the uniform random variable on the unit interval.

## Continuous Optimization

### Exercises

**7.1** Consider the univariate function

\[
f(x) = x^3 + 6x^2 - 3x - 5.
\]

Find its stationary points and indicate whether they are maximum, minimum, or saddle points.

Given the function \(f(x)\), we obtain the following gradient and Hessian,

\[
\frac{df}{dx} = 3x^2 + 12x - 3
\]
\[
\frac{d^2 f}{dx^2} = 6x + 12.
\]

We find stationary points by setting the gradient to zero, and solving for \(x\). One option is to use the formula for quadratic functions, but below we show how to solve it using completing the square. Observe that

\[
(x + 2)^2 = x^2 + 4x + 4
\]

and therefore (after dividing all terms by 3),

\[
(x^2 + 4x) - 1 = ((x + 2)^2 - 4) - 1.
\]

By setting this to zero, we obtain that

\[
(x + 2)^2 = 5,
\]

and hence

\[
x = -2 \pm \sqrt{5}.
\]

Substituting the solutions of \(\frac{df}{dx} = 0\) into the Hessian gives

\[
\frac{d^2 f}{dx^2}(-2 - \sqrt{5}) \approx -13.4 \quad \text{and} \quad \frac{d^2 f}{dx^2}(-2 + \sqrt{5}) \approx 13.4.
\]

This means that the left stationary point is a maximum and the right one is a minimum. See Figure 7.1 for an illustration.

**7.2** Consider the update equation for stochastic gradient descent (Equation (7.15)). Write down the update when we use a mini-batch size of one.

\[
\boldsymbol{\theta}_{i+1} = \boldsymbol{\theta}_i - \gamma_i (\nabla L(\boldsymbol{\theta}_i))^\top = \boldsymbol{\theta}_i - \gamma_i \nabla L_k(\boldsymbol{\theta}_i)^\top
\]

where \(k\) is the index of the example that is randomly chosen.

**7.3** Consider whether the following statements are true or false:

**7.7** Consider the quadratic program illustrated in Figure 7.4:

\[
\min_{x \in \mathbb{R}^2} \frac{1}{2}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}^\top
\begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
+
\begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
\]

subject to

\[
\begin{bmatrix} 1 & 0 \\ -1 & 0 \\ 0 & 1 \\ 0 & -1 \end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \end{bmatrix}
\le
\begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}.
\]

Derive the dual quadratic program using Lagrange duality.

Let

\[
Q = \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix}, \quad
c = \begin{bmatrix} 5 \\ 3 \end{bmatrix}, \quad
A = \begin{bmatrix} 1 & 0 \\ -1 & 0 \\ 0 & 1 \\ 0 & -1 \end{bmatrix}, \quad
b = \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}.
\]

Then by (7.45) and (7.52) the dual optimization problem is

\[
\max_{\lambda \in \mathbb{R}^4} -\frac{1}{2} \left( \begin{bmatrix} 5 \\ 3 \end{bmatrix} + A^\top \lambda \right)^\top Q^{-1} \left( \begin{bmatrix} 5 \\ 3 \end{bmatrix} + A^\top \lambda \right) - \lambda^\top b
\]

subject to \(\lambda \ge 0\),

which expands to

\[
\max_{\lambda \in \mathbb{R}^4} -\frac{1}{14} \left( 88 + \begin{bmatrix} 33 \\ -35 \\ 1 \\ -3 \end{bmatrix}^\top \lambda + \lambda^\top \begin{bmatrix} 4 & -4 & -1 & 1 \\ -4 & 4 & 1 & -1 \\ -1 & 1 & 2 & -2 \\ 1 & -1 & -2 & 2 \end{bmatrix} \lambda \right)
\]

subject to \(\lambda \ge 0\).

### Alternative derivation

Write down the Lagrangian:

\[
L(x, \lambda) = \frac{1}{2} x^\top \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix} x + \begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top x + \lambda^\top (A x - b).
\]

Differentiate with respect to \(x\) and set to zero:

\[
\nabla_x L = x^\top \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix} + \begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top + \lambda^\top A = 0.
\]

Solve for \(x\):

\[
x^\top = -\left( \begin{bmatrix} 5 \\ 3 \end{bmatrix}^\top + \lambda^\top A \right) Q^{-1}.
\]

product.

*Hint: Take the gradient of an appropriate function and set the gradient to zero.*

From the definition of the Legendre–Fenchel conjugate,

\[
f^*(s) = \sup_{x \in \mathbb{R}^D} \sum_{d=1}^{D} s_d x_d - x_d \log x_d.
\]

Define a function, for notational convenience,

\[
g(x) = \sum_{d=1}^{D} s_d x_d - x_d \log x_d.
\]

The gradient of \(g(x)\) with respect to \(x_d\) is

\[
\frac{\partial g(x)}{\partial x_d} = s_d - \frac{x_d}{x_d} - \log x_d = s_d - 1 - \log x_d.
\]

Setting the gradient to zero gives

\[
x_d = \exp(s_d - 1).
\]

Substituting the optimum value of \(x_d\) back into \(f^*(s)\) gives

\[
f^*(s) = \sum_{d=1}^{D} \left[ s_d \exp(s_d - 1) - (s_d - 1)\exp(s_d - 1) \right] = \sum_{d=1}^{D} \exp(s_d - 1).
\]

**7.10** Consider the function

\[
f(x) = \frac{1}{2} x^\top A x + b^\top x + c,
\]

where \(A\) is strictly positive definite, which means that it is invertible. Derive the convex conjugate of \(f(x)\).

*Hint: Take the gradient of an appropriate function and set the gradient to zero.*

From the definition of the Legendre–Fenchel transform,

\[
f^*(s) = \sup_{x \in \mathbb{R}^D} s^\top x - \frac{1}{2} x^\top A x - b^\top x - c.
\]

Define a function, for notational convenience,

\[
g(x) = s^\top x - \frac{1}{2} x^\top A x - b^\top x - c.
\]

The gradient of \(g(x)\) with respect to \(x\) is

\[
\frac{\partial g(x)}{\partial x} = s^\top - x^\top A - b^\top.
\]

Setting the gradient to zero gives, noting that \(A^\top = A\),

\[
s^\top - x^\top A - b^\top = 0,
\]

and therefore \(A^\top x = s - b\), so

\[
x = A^{-1}(s - b).
\]
