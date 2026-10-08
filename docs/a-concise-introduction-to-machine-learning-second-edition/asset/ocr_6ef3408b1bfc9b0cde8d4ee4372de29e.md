![](bbox=[0.307, 0.175, 0.692, 0.417])

Figure 4.9: Objective function, constraints and gradients.

**Figure 4.9** illustrates the quadratic programming problem. The circles are the isolines of $||\mathbf{w}\|^2/2$, that is, lines where it takes a constant value. In the white region, no constraints are satisfied, in the light gray region, one constraint is satisfied, while in the medium gray region, two constraints are satisfied. In the dark gray region, all constraints are satisfied. This is known as the **feasible** set. The minimum value subject to the constraints lies at the point where the gradient of the feasible set closest to the circles. At this point, the gradient of $||\mathbf{w}\|^2/2$ is a linear combination of the gradients of the active constraints. In the illustration of **Figure 4.9**, these constraints are active and one is inactive.

The **Lagrangian function** combines the objective function and the constraints into one. Its form is given by

```
L(\mathbf{w}, \alpha) = \frac{1}{2}|\mathbf{w}\|^2 - \sum_{n} \alpha_n (c_n\mathbf{w}^T\mathbf{v}_n - 1),
```

where $\alpha = (\alpha_1, \dots, \alpha_n)^T$ are known as **Lagrange multipliers** which are required to be non-negative. For a particular $\mathbf{w}$, if the constraint $c_n\mathbf{w}^T\mathbf{v}_n - 1 \geq 0$ is satisfied as a strict inequality, it is zero and does not contribute to the sum. If it is satisfied as a strict inequality, we subtract from the objective function, but if it is not satisfied, we add to it. Thus, if $\mathbf{w}$ lies outside the feasible set, it is penalized by increasing the objective function which needs to be minimized.
In **Figure 4.9** the arrows perpendicular to the constraints are the gradients of the constraints multiplied by $\alpha_n$. The dotted lines illustrate that these add to form the gradient vector of the objective function at the constrained minimum.