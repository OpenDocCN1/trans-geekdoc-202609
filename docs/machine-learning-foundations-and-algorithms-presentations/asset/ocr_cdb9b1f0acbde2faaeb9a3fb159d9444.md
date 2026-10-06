# # Reformulation into an unconstrained problem

Constrained optimization: Slack variables

```
$\text{argmin}_{\mathbf{w}, \xi} ||\mathbf{w}||^2 + C \sum_{i=1}^{N} \xi_i, \quad \text{s.t.} \quad y_i(\mathbf{w}^T \mathbf{x}_i + b) \geq 1-\xi_i, \quad \xi_i \geq 0$
Regularization parameter
```

SVMs can be reformulated into an unconstrained optimization problem

+   - Rewrite constraints: $\xi_i \geq 1-y_i(\mathbf{w}^T \mathbf{x}_i + b) = 1-y_i f(\mathbf{x}_i)$

+   - Together with $\xi_i \geq 0$ this results in $\xi_i = \max(0, 1-y_i f(\mathbf{x}_i))$ (Why?)

Unconstrained optimization (over w):

```
$\text{argmin}_{\mathbf{w}} ||\mathbf{w}||^2 + C \sum_{i=1}^{N} \max(0, 1-y_i f(\mathbf{x}_i))$
regularization loss function
```