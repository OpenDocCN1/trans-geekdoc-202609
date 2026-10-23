![](bbox=[0.05, 0.05, 0.95, 0.32])

![](bbox=[0.05, 0.32, 0.95, 0.6])

For example, consider the absolute value function f(x) = |x|. Its subdifferential is given by

∂f(x) = \begin{cases} \{-1\} & \text{if } x < 0 \\\ [-1,1] & \text{if } x = 0 \\\ \{+1\} & \text{if } x > 0 \end{cases}

(B.63)

where the notation [-1, 1] means any value between -1 and 1 inclusive. See Fig. B.11 for an illustration.

# B.4.5 Taylor series approximation

In many cases, the function is not convex, but it may be locally convex around a point. In particular, we may be able to compute a linear or quadratic approximation in some neighborhood. This is called a (first or second order) Taylor series expansion.

In more detail, let f : \mathbb{R}^n \to \mathbb{R} be a function that is second order differentiable. We can compute a linear approximation around the point a \in \mathbb{R}^n using

\hat f(x) = f(a) + \nabla f(a)^\top (x - a)

(B.64)