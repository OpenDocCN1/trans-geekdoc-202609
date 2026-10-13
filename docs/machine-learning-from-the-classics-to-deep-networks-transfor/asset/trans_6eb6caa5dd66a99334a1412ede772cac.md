

$$
\mathbf{\theta}_{n} = \begin{cases} 
\mathbf{\theta}_{n - 1} + X_{n}{(X_{n}^{T}X_{n})}^{- 1}(\mathbf{e}_{n} - \mathbf{y}_{n}), & \text{if } |e_{n}| > \epsilon, \\ 
\mathbf{\theta}_{n - 1}, & \text{otherwise}, 
\end{cases}
$$

其中 `X[n] = [x[n], x[n-1], ..., x[n-q+1]]`，`y[n] = [y[n], y[n-1], ..., y[n-q+1]]^T`，且 `e[n] = [e[n], e[n-1], ..., e[n-q+1]]^T`，满足 `e[n] = y[n] - x[n]^T \theta[n-1]`。集成员 APA 的随机分析 [34] 确立了其均方误差 (MSE) 性能，该分析通过采用能量守恒论证进行（第 [5](#Chp005_177-248_B9780443292385000111.xhtml) 章）。

### 示例 8.2

本示例旨在演示 NLMS、APA、APSM 和递归最小二乘 (RLS) 算法的比较收敛性能。实验在两种不同的噪声设置下进行，一种用于低噪声电平，另一种用于高噪声电平，以展示 APA 相对于 APSM 的敏感性。数据根据我们熟悉的模型生成：

$$
y[n] = \mathbf{\theta}_{o}^{T}\mathbf{x}[n] + \eta[n].
$$

