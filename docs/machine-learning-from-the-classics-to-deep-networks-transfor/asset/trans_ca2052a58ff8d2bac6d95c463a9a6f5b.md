
$J\left( \mathbf{\theta}^{(i - 1)} + \Delta\mathbf{\theta}^{(i)} \right) \approx J\left( \mathbf{\theta}^{(i - 1)} \right) + \left( \nabla J\left( \mathbf{\theta}^{(i - 1)} \right) \right)^{T}\Delta\mathbf{\theta}^{(i)} + \frac{1}{2}\left( \Delta\mathbf{\theta}^{(i)} \right)^{T}\nabla^{2}J\left( \mathbf{\theta}^{(i - 1)} \right)\Delta\mathbf{\theta}^{(i)}.$

![Equation](images/B9780443292385000123/si208.png)

回想一下，二阶导数 $\nabla^{2}J$ 是梯度向量的导数，是一个 $l \times l$ 矩阵（见附录 A）。假设 $\nabla^{2}J(\mathbf{\theta}^{(i-1)})$ 为正定矩阵（如果 $J(\mathbf{\theta})$ 是严格凸函数，则总是这种情况），$^{[41]}$

$$\Delta\mathbf{\theta}^{(i)} = -(\nabla^{2}J(\mathbf{\theta}^{(i-1)}))^{-1}\nabla J(\mathbf{\theta}^{(i-1)}).$$

![Equation](images/B9780443292385000123/si213.png)(6.49)

注意，这确实是一个下降方向，因为
