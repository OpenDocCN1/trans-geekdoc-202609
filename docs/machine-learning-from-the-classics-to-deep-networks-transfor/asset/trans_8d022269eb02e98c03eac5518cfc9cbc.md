

### 优化问题推导

$$
\mathbf{\theta}^{(i)} = \arg\min_{\mathbf{\theta} \in \mathbb{R}^{l}} \left\{ J\left( \mathbf{\theta}^{(i - 1)} \right) + \left( \mathbf{\theta} - \mathbf{\theta}^{(i - 1)} \right)^{T} \frac{\partial J\left( \mathbf{\theta}^{(i - 1)} \right)}{\partial \mathbf{\theta}} + \frac{1}{2\mu} \left\| \mathbf{\theta} - \mathbf{\theta}^{(i - 1)} \right\|_{2}^{2} + \lambda \left\| \mathbf{\theta} \right\|_{1} \right\}
$$

![Equation](images/B9780443292385000160/si83.png)

忽略常数项后，等价写为：

$$
\mathbf{\theta}^{(i)} = \arg\min_{\mathbf{\theta} \in \mathbb{R}^{l}} \left\{ \frac{1}{2} \left\| \mathbf{\theta} - \widetilde{\mathbf{\theta}} \right\|_{2}^{2} + \lambda \mu \left\| \mathbf{\theta} \right\|_{1} \right\}
$$

![Equation](images/B9780443292385000160/si84.png) (10.4)

其中

$$
\widetilde{\mathbf{\theta}} := \mathbf{\theta}^{(i - 1)} - \mu \frac{\partial J\left( \mathbf{\theta}^{(i - 1)} \right)}{\partial \mathbf{\theta}}
$$

![Equation](images/B9780443292385000160/si85.png) (10.5)

