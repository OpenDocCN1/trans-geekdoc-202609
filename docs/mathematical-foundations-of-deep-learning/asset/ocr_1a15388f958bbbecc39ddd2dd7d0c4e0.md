# 13.3 Optimization Techniques

# 13.3.1 Gradient Descent (GD)

Gradient Descent is an iterative optimization algorithm used to minimize a differentiable function. The goal is to find the point where the function achieves its minimum value. Mathematically, it can be formulated as follows. Given a differentiable objective function \( f : \mathbb{R}^n \rightarrow \mathbb{R} \), the gradient descent update rule is:

```
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \nabla f(\mathbf{x}_k)
```

where:

+   - \(\mathbf{x}_k \in \mathbb{R}^n\) is the current point in the \(n\)-dimensional space (iteration index \(k\)),
+   - \(\nabla f(\mathbf{x}_k)\) is the gradient of the objective function at \(\mathbf{x}_k\),
+   - \(\eta\) is the learning rate (step size).

To analyze the convergence of gradient descent, we assume \(f\) is **convex** and **differentiable** with a **Lipschitz continuous gradient**. That is, there exists a constant \(L > 0\) such that:

```
\|\nabla f(\mathbf{x}) - \nabla f(\mathbf{y})\| \leq L\|\mathbf{x} - \mathbf{y}\|, \quad \forall \mathbf{x}, \mathbf{y} \in \mathbb{R}^n.
```

This property ensures the gradient of \(f\) does not change too rapidly, which allows us to bound the convergence rate. The following is an upper bound on the decrease in the function value at each iteration:

```
f(\mathbf{x}_{k+1}) - f(\mathbf{x}^*) \leq (1 - \eta L)(f(\mathbf{x}_k) - f(\mathbf{x}^*)),
```

where \(\mathbf{x}^*\) is the global minimum. Thus, we have the following convergence rate:

```
f(\mathbf{x}_k) - f(\mathbf{x}^*) \leq (1 - \eta L)^k(f(\mathbf{x}_0) - f(\mathbf{x}^*)).
```

For this to converge, we require \(\eta L < 1\). Hence, the step size \(\eta\) must be chosen carefully to ensure convergence.

# 13.3.2 Stochastic Gradient Descent (SGD)

Stochastic Gradient Descent is a variant of gradient descent that approximates the gradient of the objective function using a randomly chosen subset (mini-batch) of the data at each iteration. This can significantly reduce the computational cost when the dataset is large.

Let the objective function be the sum of individual functions \(f_i(\mathbf{x})\) corresponding to each data point:

```
f(\mathbf{x}) = \frac{1}{m} \sum_{i=1}^m f_i(\mathbf{x}),
```

where \(m\) is the number of data points. In **Stochastic Gradient Descent**, the update rule becomes:

```
\mathbf{x}_{k+1} = \mathbf{x}_k - \eta \nabla f_{i_k}(\mathbf{x}_k),
```

where \(i_k\) is a randomly chosen index at the \(k\)-th iteration, and \(\nabla f_{i_k}(\mathbf{x})\) is the gradient of the function \(f_{i_k}(\mathbf{x})\) corresponding to that randomly selected data point. The stochastic gradient is given by:

```
\nabla f_{i_k}(\mathbf{x}_k) = \nabla f_{i_k}(\mathbf{x}_k).
```

Given that the gradient is stochastic, the convergence analysis of SGD is more complex. Assuming that each \(f_i\) is convex and differentiable, and using the strong convexity assumption (i.e., there exists a constant \(m > 0\) such that \(f\) satisfies the inequality):

```
f(\mathbf{x}) - f(\mathbf{y}) \geq m\|\mathbf{x} - \mathbf{y}\|^2, \quad \forall \mathbf{x}, \mathbf{y} \in \mathbb{R}^n,
```