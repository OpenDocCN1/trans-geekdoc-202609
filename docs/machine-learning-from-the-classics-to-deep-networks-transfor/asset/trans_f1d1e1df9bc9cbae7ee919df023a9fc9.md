

$$
\mathbf{\theta}^{(i)} = \arg\min_{\mathbf{\theta} \in \mathbb{R}^{l}}\left\{ J\left( \mathbf{\theta}^{(i - 1)} \right) + \left( \mathbf{\theta} - \mathbf{\theta}^{(i - 1)} \right)^{T}\frac{\partial J\left( \mathbf{\theta}^{(i - 1)} \right)}{\partial\mathbf{\theta}} + \frac{1}{2\mu}\left\| \mathbf{\theta} - \mathbf{\theta}^{(i - 1)} \right\|_{2}^{2} \right\}.
$$

![Equation](images/B9780443292385000160/si81.png) (10.3)

可以采用这种梯度下降理念的观点作为出发点，以迭代方式最小化以下 LASSO 任务：

$$
\min_{\mathbf{\theta} \in \mathbb{R}^{l}}\left\{ L(\mathbf{\theta},\lambda) = \frac{1}{2}\left\| \mathbf{y} - X\mathbf{\theta} \right\|_{2}^{2} + \lambda\left\| \mathbf{\theta} \right\|_{1} = J(\mathbf{\theta}) + \lambda\left\| \mathbf{\theta} \right\|_{1} \right\}.
$$

![Equation](images/B9780443292385000160/si82.png)

现在的区别在于损失函数包含两项：一项是光滑的（可微的），另一项是非光滑的。令当前估计为 **θ**^((*i* − 1))。更新后的估计通过以下方式获得

