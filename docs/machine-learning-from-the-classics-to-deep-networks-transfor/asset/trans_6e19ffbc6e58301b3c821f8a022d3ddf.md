
## 假设观测值相互独立，求未知均值向量的 ML 估计

对于 $N$ 个统计独立的观测值，联合对数似然函数由下式给出：

$$
L(\boldsymbol{\mu}) = \ln\prod_{n=1}^{N}p(\mathbf{x}_n;\boldsymbol{\mu}) = - \frac{N}{2}\ln\left( (2\pi)^l|\Sigma| \right) - \frac{1}{2}\sum_{n=1}^{N}(\mathbf{x}_n - \boldsymbol{\mu})^T\Sigma^{-1}(\mathbf{x}_n - \boldsymbol{\mu}).
$$

![Equation](images/B9780443292385000093/si313.png)

对 $\boldsymbol{\mu}$ 求梯度，我们得到^[^12]。
