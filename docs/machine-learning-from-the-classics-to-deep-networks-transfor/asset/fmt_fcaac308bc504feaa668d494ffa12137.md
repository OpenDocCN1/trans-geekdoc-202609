
## 数学推导

### 梯度与海森矩阵

$$
-\nabla J(\boldsymbol{\theta}) = \mathbf{p} - \Sigma_x \boldsymbol{\theta} = \mathbb{E}[\mathbf{x}y] - \mathbb{E}[\mathbf{x}\mathbf{x}^T]\boldsymbol{\theta} = \mathbb{E}[\mathbf{x}(y - \mathbf{x}^T\boldsymbol{\theta})] = \mathbb{E}[\mathbf{x}e]
$$

![Equation](images/B9780443292385000123/si228.png)

and

$$
\nabla^2 J(\boldsymbol{\theta}) = \Sigma_x.
$$

![Equation](images/B9780443292385000123/si229.png)

### 牛顿迭代

Newton's iteration becomes

$$
\boldsymbol{\theta}^{(i)} = \boldsymbol{\theta}^{(i-1)} + \mu_i \Sigma_x^{-1} \mathbb{E}[\mathbf{x}e].
$$

![Equation](images/B9780443292385000123/si230.png)

Following stochastic approximation arguments and replacing iteration steps with time updates and expectations with observations, we obtain

$$
\boldsymbol{\theta}[n] = \boldsymbol{\theta}[n-1] + \mu_n \Sigma_x^{-1} \mathbf{x}[n] e[n].
$$

![Equation](images/B9780443292385000123/si231.png)

### 近似设定

Let us now adopt the approximation,

$$
\Sigma_x \approx \frac{1}{n + 1}\Phi_n = \left( \frac{1}{n + 1}\lambda\beta^{n + 1}I + \frac{1}{n + 1}\sum_{i = 0}^{n}\beta^{n - i}\mathbf{x}_i\mathbf{x}_i^T \right),
$$

![Equation](images/B9780443292385000123/si232.png)

and set
