

## 定理 5.2

考虑一个由 $K$ 个节点组成的网络，每个节点都能访问一个状态向量 $\mathbf{x}_k$。考虑递归

![Equation](images/B9780443292385000111/fx020.jpg)

其中

$$\boldsymbol{\theta}_k^{(0)} = \mathbf{x}_k, \quad k = 1, 2, \dots, K.$$

![Equation](images/B9780443292385000111/si587.png)

定义 $\mathbf{A} \in \mathbb{R}^{K \times K}$ 为其元素为

$$[\mathbf{A}]_{mk} = a_{mk}, \quad m, k = 1, 2, \dots, K,$$

![Equation](images/B9780443292385000111/si589.png)

的矩阵，其中 $a_{mk} \ge 0$，若 $m \notin \mathcal{N}_k$ 则 $a_{mk} = 0$。

![Equation](images/B9780443292385000111/si590.png)

如果 $\mathbf{A}$ 是一致性矩阵，则

$$\boldsymbol{\theta}_k^{(i)} \longrightarrow \frac{1}{K}\sum_{k=1}^{K} \mathbf{x}_k.$$

![Equation](images/B9780443292385000111/si591.png)

反之亦然。如果收敛*总是*得到保证，则 $\mathbf{A}$ 是一致性矩阵。

换句话说，该定理表明：通过用适当的权重凸组合其邻域内的当前估计值来更新每个节点，网络将按一致性原理收敛到平均值（问题 [5.16](#Chp005_177-248_B9780443292385000111.xhtml#o0085)）。

## 习题

1.  **5.1** 证明梯度向量垂直于等值曲线上某点的切线。

2.  **5.2** 证明如果

    $$\sum_{i=1}^{\infty} \mu_i^2 < \infty, \quad \sum_{i=1}^{\infty} \mu_i = \infty,$$

    ![Equation](images/B9780443292385000111/si592.png)

    则对于 MSE 代价函数和迭代相关步长情况，梯度下降法收敛到最优解。

3.  **5.3** 推导复值情况下的最速梯度下降方向。

4.  **5.4** 设 $\theta, x$ 为两个联合分布的随机变量。另设函数（回归）

    $$f(\theta) = \mathbb{E}[x|\theta],$$

    ![Equation](images/B9780443292385000111/si594.png)

    假设为单调递增函数。证明在 [(5.29)](#Chp005_177-248_B9780443292385000111.xhtml#deq53) 条件下，递归

    $$\theta[n] = \theta[n-1] - \mu[n]x[n]$$

    ![Equation](images/B9780443292385000111/si595.png)

