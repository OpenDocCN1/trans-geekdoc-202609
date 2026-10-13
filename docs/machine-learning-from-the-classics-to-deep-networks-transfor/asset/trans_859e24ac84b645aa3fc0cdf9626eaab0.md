
$||\mathbf{x}_{n} - \mathbf{x}||^{2} \approx ||\widehat{\mathbf{x}}_{n} - \widehat{\mathbf{x}}||^{2} = \left\| \sum\limits_{i = 1}^{m}z_{ni}\mathbf{u}_{i} - \sum\limits_{i = 1}^{m}z_{i}\mathbf{u}_{i} \right\|^{2} = ||\mathbf{z}_{n}^{(m)} - \mathbf{z}||^{2}$

![Equation](images/B9780443292385000263/si64.png)

其中 **z** : = [$z_{1}$, …, $z_{m}$]^{(T)}

![Equation](images/B9780443292385000263/si65.png)。换句话说，欧氏距离是在低维子空间中计算的，这带来了显著的计算增益（例如，参见 [22,63,160] 及其参考文献）。此方法也称为*潜在语义索引*。

### PCA 的正交化特性与特征生成

我们现在将从另一个角度阐述 PCA。我们刚刚在信息检索应用的背景下讨论过，PCA 也可以被视为一种特征生成方法，它生成一组新的特征向量 **z**，其分量沿主轴描述一种模式。现在让我们假设（为了简化问题）*N* 足够大，并且样本协方差矩阵是（满秩）协方差矩阵 $\Sigma = \mathbb{E}[\mathbf{x}\mathbf{x}^{(T)}]$

![Equation](images/B9780443292385000263/si66.png) 的良好近似。我们知道，任意向量 $\mathbf{x} \in \mathbb{R}^{(l)}$

![Equation](images/B9780443292385000263/si67.png) 都可以用 $\mathbf{u}_{1}$, …, $\mathbf{u}_{l}$

![Equation](images/B9780443292385000263/si68.png) 来描述，即

$\mathbf{x} = \sum\limits_{i = 1}^{l}z_{i}\mathbf{u}_{i} = \sum\limits_{i = 1}^{l}(\mathbf{u}_{i}^{T}\mathbf{x})\mathbf{u}_{i}.$

![Equation](images/B9780443292385000263/si69.png)

我们现在的关注点转向随机向量 **z** 的协方差矩阵，当 **x** 随机变化时。考虑到
