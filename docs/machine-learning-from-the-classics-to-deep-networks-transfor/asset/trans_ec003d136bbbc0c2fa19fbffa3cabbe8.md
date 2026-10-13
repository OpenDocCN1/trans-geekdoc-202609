
$$
\mathcal{Q}(\Theta,\Theta^{(t)}) = \sum\limits_{k = 1}^{K}\gamma(x_{1,k} = 1;\Theta^{(t)})\ln P_{k}\quad + \sum\limits_{n = 2}^{N}\sum\limits_{i = 1}^{K}\sum\limits_{j = 1}^{K}\xi(x_{n - 1,j} = 1,x_{n,i} = 1;\Theta^{(t)})\ln P_{ij}\quad + \sum\limits_{n = 1}^{N}\sum\limits_{k = 1}^{K}\gamma(x_{n,k} = 1;\Theta^{(t)})\ln p(\mathbf{y}_{n}|k;\mathbf{\theta}_{k}).
$$

![Equation](images/B9780443292385000226/si292.png)(16.55)

### 最大化步骤

在此步骤中，只需求出关于 `P[k]`、`P[ij]` 和 `θ[k]` 的导数/梯度并将它们设为零，即可获得新的估计值，这些估计值将构成 `Θ^(t+1)`。请注意，`P[k]` 和 `P[ij]` 是概率；因此，它们的最大化应受到约束，以便
