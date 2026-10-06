# # Binary Classification: Previous Definition

![](bbox=[0.116, 0.287, 0.822, 0.532])

Given the training data $(x_i, y_i)$, $i = 1...N$, with $x_i \in \mathbb{R}^d$ and $y_i \in \{0, 1\}$ , learn a classifier $f(oldsymbol{x})$ such that:

```
$f(\boldsymbol{x}_i) = \begin{cases} > 0, & \text{if } y_i = 1 \ < 0, & \text{if } y_i = 0 \end{cases}$
```