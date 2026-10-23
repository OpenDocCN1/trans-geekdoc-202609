![](bbox=[0.15, 0.12, 0.9, 0.36])

Figure 5.13: Illustration of some constrained optimization problems. Red contours are the level sets of the objective function L(θ). Optimal constrained solution is the black dot, (a) Blue line is the equality constraint h(θ)=0. (b) Blue lines denote the inequality constraints |θ1|+|θ2| ≤ 1. (Compare to Fig. 11.10 (left).)

# 5.4.6.4 Issues with adaptive learning rates

When using diagonal scaling methods, the overall learning rate is determined by η0 M_t^{-1}, which changes with time. Hence these methods are often called adaptive learning rate methods. However, they still require setting the base learning rate η0.

Since the EWMA methods are typically used in the stochastic setting where the gradient estimates are noisy, their learning rate adaptation can result in non-convergence even on convex problems [RKK18]. Various solutions to this problem have been proposed, including AMSGrad [RKK18], PADAM [CG18; Zho+18], and YOGI [Zah+18].

# 5.5 Constrained optimization

In this section, we consider the following constrained optimization problem:

θ* = arg min_{θ ∈ C} L(θ) (5.83)

where the feasible set, or constraint set, is

C = {θ ∈ R^D : h_i(θ) = 0, i ∈ E, g_j(θ) ≤ 0, j ∈ I} (5.84)

where E is the set of equality constraints, and I is the set of inequality constraints, and C = I ∪ E is the set of all constraints. (We define the constraints in this way, rather than as boolean membership of some set, so it gives us a measure of how far from feasible any given proposed solution is.)

For example, suppose we have a quadratic objective, L(θ) = θ1^2 + θ2^2, subject to a linear equality constraint, h(θ) = 1 − θ1 − θ2 = 0. Fig. 5.13(a) plots the level sets of f, as well as the constraint surface. What we are trying to do is find the point θ* that lives on the line, but which is closest to the origin. It is clear from the geometry that the optimal solution is θ = (0.5, 0.5), indicated by the solid black dot.