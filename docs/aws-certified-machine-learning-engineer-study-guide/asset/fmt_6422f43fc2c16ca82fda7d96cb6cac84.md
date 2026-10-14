
## Gradient Descent

The gradient of a function $f(x_1, x_2, \dots, x_n)$ is the vector of partial derivatives:

$$
\nabla f(x_1, x_2, \dots, x_n) = \left[ \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2}, \dots, \frac{\partial f}{\partial x_n} \right]
$$

For example, for $f(x_1, x_2) = x_1^2 + x_2^2$:

$$
\nabla f(x_1, x_2) = \left[ \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2} \right] = [2x_1, 2x_2]
$$

In ML, the gradient is used to calculate the direction to adjust model parameters during optimization.

### Gradient Descent

Gradient descent is an optimization algorithm that iteratively adjusts parameters to minimize a function (e.g., loss function). It uses the gradient to determine the direction and magnitude of parameter updates.

$$
x_{\text{new}} = x_{\text{old}} - \eta \nabla f(x_{\text{old}})
$$

where

*   $\eta$ (eta) is the learning rate hyperparameter (step size).
*   $\nabla f(x)$ is the gradient of the function.

This process is repeated until convergence: i.e., when updates become negligible or the function reaches its minimum.

[Figure A.9](#a02.xhtml#c0-fig-9) visually illustrates the gradient descent convergence process for the single-variable function $f(x) = x^2$.

![FIGURE A.9 Gradient descent convergence process ($f(x) = x^2$).](images/cappf009.png)

[FIGURE A.9](#a02.xhtml#rc0-fig-9) Gradient descent convergence process ($f(x) = x^2$).

In [Figure A.9](#a02.xhtml#c0-fig-9):

*   Steps 0, 1, and 2 are explicitly annotated with $x_{\text{old}}$ and $f'(x)$.
*   All steps beyond 3 are visually marked on the function line but are not annotated to maintain readability.
*   Starting from $x = 8$ with $\eta = 0.2$, the algorithm takes 10 iterations to converge, based on the number of steps shown.
*   By the 10th step, the changes in $x$ and $f(x)$ are small enough to indicate convergence near the global minimum ($x = 0$).

For your reference, the following Python code shows the plot illustrated in [Figure A.9](#a02.xhtml#c0-fig-9):
