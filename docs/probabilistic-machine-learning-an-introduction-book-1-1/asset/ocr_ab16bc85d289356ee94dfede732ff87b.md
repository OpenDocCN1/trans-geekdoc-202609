precisely, at a saddle point, the eigenvalues of the Hessian will be both positive and negative. However, if the Hessian at a point is positive semi-definite, then some directions may point uphill, while others are flat. This means that the objective function can not be decreased in the neighbourhood of this point, implying that it is necessarily a local minimum. Moreover, if the Hessian is strictly positive definite, then we are at the bottom of a “bowl”, and all directions point uphill, which is sufficient for this to be a minimum.

# 5.1.2 Constrained vs unconstrained optimization

In **unconstrained optimization**, we define the optimization task as finding any value in the parameter space Θ that minimizes the loss. However, we often have a set of **constraints** on the allowable values. It is standard to partition the set of constraints 𝒞 into **inequality constraints**, g_j(θ) ≤ 0 for j ∈ ℐ and **equality constraints**, h_k(θ) = 0 for k ∈ ℰ. For example, we can represent a sum-to-one constraint as an equality constraint h(θ) = (1 − ∑_{i=1}^D θ_i) = 0, and we can represent a non-negativity constraint on the parameters by using D inequality constraints of the form g_i(θ) = −θ_i ≤ 0.

We define the **feasible set** as the subset of the parameter space that satisfies the constraints:

𝒞 = {θ : g_j(θ) ≤ 0 : j ∈ ℐ, h_k(θ) = 0 : k ∈ ℰ} ⊆ ℝ^D  (5.4)

Our **constrained optimization** problem now becomes

θ* ∈ argmin_{θ ∈ 𝒞} ℒ(θ)  (5.5)

If 𝒞 = ℝ^D, it is called **unconstrained optimization**.

The addition of constraints can change the number of optima of a function. For example, a function that was previously unbounded (and hence had no well-defined global maximum or minimum) can “acquire” multiple maxima or minima when we add constraints, as illustrated in Fig. 5.2. However, if we add too many constraints, we may find that the feasible set becomes empty. The task of finding any point (regardless of its cost) in the feasible set is called a **feasibility problem**; this can be a hard subproblem in itself.

A common strategy for solving constrained problems is to create penalty terms that measure how much we violate each constraint. We then add these terms to the objective and solve an unconstrained optimization problem. The **Lagrangian** is a special case of such a combined objective (see Sec. 5.5 for details).

# 5.1.3 Convex vs nonconvex optimization

In **convex optimization**, we require the objective to be a convex function defined over a convex set (see Appendix B.4 for definitions of these terms). In such problems, every local minimum is also a global minimum. If ℒ is a *strictly* convex function, then the optimal solution (assuming it exists) is unique. Furthermore, we can usually devise methods to efficiently find such minima, as we will see. Thus many models are designed so that their training objectives are convex.