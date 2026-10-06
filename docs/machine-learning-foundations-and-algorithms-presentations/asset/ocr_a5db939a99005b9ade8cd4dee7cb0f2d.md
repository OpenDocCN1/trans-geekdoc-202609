# Support Vector Machines (continued...)

SVMs with features:

+   - Maximum margin principle
- Slack variables allow for margin violation
  $$\argmin_{\mathbf{w}, \xi} ||\mathbf{w}\|^2 + C \sum_{i=1}^{N} \xi_i,$$$
  $$\text{s.t.} \quad y_i(\mathbf{w}^T \phi(\mathbf{x}_i) + b) \ge 1-\xi_i, \quad \xi_i \ge 0$$
- Simpler formulation without slack variables
  $$\argmin_{\mathbf{w}} ||\mathbf{w}\|^2,$$$
  $$\text{s.t.} \quad y_i(\mathbf{w}^T \phi(\mathbf{x}_i) + b) \ge 1$$

![](bbox=[0.573, 0.225, 0.781, 0.603])

In order to apply the kernel trick, we need to apply Constrained Optimization!

+   - ... however, we do not have time for going into that
- See RL lecture