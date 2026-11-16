For example, in Figure 6.1b, we see that \( f_{x_0}^1(z^*) = f_{x_0}^1(0.5) = 1.0 \), so \( f^1(x_0) = 1.0 \). This is shown by the blue circle. The dotted line is the locus of blue points as we vary \( x_0 \), i.e., the Moreau envelope of \( f \).

We see that the Moreau envelope is a smooth lower bound on \( f \), and has the same minimum location as \( f \). Furthermore, it has domain \( \mathbb{R}^n \), even when \( f \) does not, and it is continuously differentiable, even when \( f \) is not. This makes it easier to optimize. For example, the Moreau envelope of \( f(r) = |r| \) is the **Huber loss** function, which is used in robust regression.

# 6.1.1.2 Prox operator on a linear approximation yields gradient update

Suppose we make a linear approximation of \( f \) at the current iterate \( \boldsymbol{x}_t \):

\( \hat{f}(\boldsymbol{x}) = f(\boldsymbol{x}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{x} - \boldsymbol{x}_t) \quad (6.10) \)

where \( \boldsymbol{g}_t = \nabla f(\boldsymbol{x}_t) \). To compute the prox operator, note that

\( \nabla_z \hat{f}_x^\eta(\boldsymbol{z}) = \nabla_z \left[ f(\boldsymbol{x}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{z} - \boldsymbol{x}) + \frac{1}{2\eta}||\boldsymbol{z} - \boldsymbol{x}_t||_2^2 \right] = \boldsymbol{g}_t + \frac{1}{\eta}(\boldsymbol{z} - \boldsymbol{x}_t) \quad (6.11) \)

Solving \( \nabla_z \hat{f}_x^\eta(\boldsymbol{z}) = \boldsymbol{0} \) yields the standard gradient update:

\( \text{prox}_{\eta f}(\boldsymbol{x}) = \boldsymbol{x} - \eta \boldsymbol{g}_t \quad (6.12) \)

Thus a prox step is equivalent to a gradient step on a linearized objective.

# 6.1.1.3 Prox operator on a quadratic approximation yields regularized Newton update

Now suppose we use a second order approximation at \( \boldsymbol{x}_t \):

\( \hat{f}(\boldsymbol{x}) = f(\boldsymbol{x}_t) + \nabla \boldsymbol{g}_t(\boldsymbol{x} - \boldsymbol{x}_t) + \frac{1}{2}(\boldsymbol{x} - \boldsymbol{x}_t)^\mathsf{T} \mathbf{H}_t (\boldsymbol{x} - \boldsymbol{x}_t) \quad (6.13) \)

The prox operator for this is

\( \text{prox}_{\eta \hat{f}}(\boldsymbol{x}) = \boldsymbol{x} - (\mathbf{H}_t + \frac{1}{\eta}\mathbf{I})^{-1} \boldsymbol{g}_t \quad (6.14) \)

# 6.1.1.4 Prox operator as gradient descent on a smoothed objective

Prox operators are arguably most useful for nonsmooth functions for which we cannot make a Taylor series approximation. Instead, we will optimize the Moreau envelope, which is a smooth approximation.

In particular, from Equation (6.9), we have

\( f^\eta(\boldsymbol{x}) = f(\text{prox}_{\eta f}(\boldsymbol{x})) + \frac{1}{2\eta} || \boldsymbol{x} - \text{prox}_{\eta f}(\boldsymbol{x}) ||_2^2 \quad (6.15) \)

Hence the gradient of the Moreau envelope is given by

\( \nabla_x f^\eta(\boldsymbol{x}) = \frac{1}{\eta} (\boldsymbol{x} - \text{prox}_{\eta f}(\boldsymbol{x})) \quad (6.16) \)

Thus we can rewrite the prox operator as

\( \text{prox}_{\eta f}(\boldsymbol{x}) = \boldsymbol{x} - \eta \nabla f^\eta(\boldsymbol{x}) \quad (6.17) \)

Thus a prox step is equivalent to a gradient step on the smoothed objective.

# 6.1.2 Computing proximal operators

In this section, we briefly discuss how to compute proximal operators for various functions that are useful in ML, either as regularizers or constraints. More examples can be found in [PB+14; PSW15].