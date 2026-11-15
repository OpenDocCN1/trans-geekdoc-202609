by the latest state.

\(\hat{x}_t^{\text{FTL}} = \arg \min \text{LP}_{t-1}(x) \quad (4.2)\)

Intuitively, this approach is applicable and effective in cases where the round durations are chosen to be small enough that the system barely changes across successive rounds. In such cases, using slightly stale state should not make much of a difference. Formally, it can be shown (Theorem 4.1) that the dynamic regret suffered by the FTL algorithm scales as \(\mathcal{O}(\mathcal{P}_x(T))\)—if the change in solutions across rounds is small, the dynamic regret stays small.

**Theorem 4.1** (Simplified Theorem 3, [146]). *Let the linear objectives* \(f_t(x) = c_t^T x\) *be such that* \(\|c_t\|_2\) *is bounded, and let* \(\mathcal{X}_t\) *denote the set of feasible solutions in step t. Then the greedy FTL strategy in Equation (4.2) satisfies*,

\(D\text{-Reg}(\{\hat{x}_t\}_{t=1}^T) = \sum_{t=1}^T f_t(\hat{x}_t) - \sum_{t=1}^T f_t(x_t^*) \leq \mathcal{O}(\min\{\mathcal{P}_x(T), \mathcal{P}_x^{\frac{1}{2}}(T)\}),\)

*where* \(\mathcal{P}_x(T) = \sum_{t=2}^T \|x_t^* - x_{t-1}^*\|^2\) *and* \(\mathcal{P}_x^{\frac{1}{2}}(T) = \sum_{t=2}^T \|x_t^* - x_{t-1}^*\|.\)

Note however, that the small dynamic regret does not imply that the time to find \(\hat{x}_t\) is small, or, even dependent on the path length. The time to find optimum depends on the choice of optimization algorithm used, even when starting from good initializations. For instance, algorithms such as Simplex do not necessarily benefit from initializing close in terms of \(\ell_2\) norm, while algorithms like ADMM spend most of the iterations in the vicinity of the optimum anyway, and need not show meaningful advantages in practice. We now discuss how the PPA algorithm we use in COPTER can be warm-started.

# ## 4.4.3 Warm Starting Proximal Point Algorithm (PPA)

Given a linear program in standard form,

\(\begin{aligned} \min & \quad c^T x \\ \text{s.t.} & \quad Ax \le 0, x \ge 0, \end{aligned}\)

we can rewrite the program as the sum of a smooth and two non-smooth terms as follows:

\(\min \quad c^T x + \mathcal{I}_{Ax \le b}(x) + \mathcal{I}_{x \ge 0}(x),\)