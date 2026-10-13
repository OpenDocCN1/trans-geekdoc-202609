

## 命题 8.3

设 $J$ 为凸代价函数。假设所有点的次梯度均有界，即

$$
\|J'(\mathbf{x})\| \le G, \quad \forall \mathbf{x} \in \mathbb{R}^l.
$$

再假设步长序列为递减序列，使得

$$
\sum_{i=1}^{\infty} \mu_i = \infty, \quad \sum_{i=1}^{\infty} \mu_i^2 < \infty.
$$

则

$$
\lim_{i \to \infty} J_*^{(i)} = J(\mathbf{\theta}_*),
$$

其中 $\mathbf{\theta}_*$ 为极小值点，假设极小值点集合非空。

### 证明

我们有

