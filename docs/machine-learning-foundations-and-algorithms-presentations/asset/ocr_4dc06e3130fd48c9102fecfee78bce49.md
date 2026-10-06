# Soft Max-Margin

Optimization problem:

$$\text{argmin}_{\mathbf{w},\xi} \quad ||\mathbf{w}||^2 + C\sum_{i}^N \xi_i,$$
$\text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \ge 1-\xi_i, \quad \xi_i \ge 0$$

Punish large slack variables

Condition for soft-margin

+   - C is a (inverse) regularization parameter
    - Small C: Constraints have little influence -> large margin -> large regularization
    - Large C: Constraints have large influence -> small margin -> small regularization
    - C infinite: Constraints are enforced-> hard margin -> no regularization