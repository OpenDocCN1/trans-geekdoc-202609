# Linear Classification: regression loss (2nd attempt)

We can use same loss as in regression
$L_{reg}(\mathbf{w}) = \sum_{i} (f(\mathbf{x}_i) - c_i)^2$

+   - Minimize the squared error: Easy!
- However: we ignored the fact that $c_i$ is restricted to $\{0,1\}$

Not robust to outliers

![](bbox=[0.315, 0.584, 0.933, 0.982])