x ∈ ℝ² with x constrained to have exactly unit L² norm, we can instead minimize g(θ) = f([cos θ, sin θ]ᵀ) with respect to θ, then return [cos θ, sin θ] as the solution to the original problem. This approach requires creativity; the transformation between optimization problems must be designed specifically for each case we encounter.

The **Karush–Kuhn–Tucker** (KKT) approach¹ provides a very general solution to constrained optimization. With the KKT approach, we introduce a new function called the **generalized Lagrangian** or **generalized Lagrange function**.

To define the Lagrangian, we first need to describe 𝕊 in terms of equations and inequalities. We want a description of 𝕊 in terms of m functions g⁽ⁱ⁾ and n functions h⁽ʲ⁾ so that 𝕊 = {x | ∀i, g⁽ⁱ⁾(x) = 0 and ∀j, h⁽ʲ⁾(x) ≤ 0}. The equations involving g⁽ⁱ⁾ are called the **equality constraints**, and the inequalities involving h⁽ʲ⁾ are called **inequality constraints**.

We introduce new variables λᵢ and αⱼ for each constraint, these are called the KKT multipliers. The generalized Lagrangian is then defined as

$$L(x, λ, α) = f(x) + \sum_{i} λ_i g^{(i)}(x) + \sum_{j} α_j h^{(j)}(x). \tag{4.14}$$

We can now solve a constrained minimization problem using unconstrained optimization of the generalized Lagrangian. As long as at least one feasible point exists and f(x) is not permitted to have value ∞, then

$$\min_{x} \max_{λ} \max_{α, α ≥ 0} L(x, λ, α) \tag{4.15}$$

has the same optimal objective function value and set of optimal points x as

$$\min_{x ∈ 𝕊} f(x). \tag{4.16}$$

This follows because any time the constraints are satisfied,

$$\max_{λ} \max_{α, α ≥ 0} L(x, λ, α) = f(x), \tag{4.17}$$

while any time a constraint is violated,

$$\max_{λ} \max_{α, α ≥ 0} L(x, λ, α) = ∞. \tag{4.18}$$

These properties guarantee that no infeasible point can be optimal, and that the optimum within the feasible points is unchanged.

¹The KKT approach generalizes the method of **Lagrange multipliers**, which allows equality constraints but not inequality constraints.