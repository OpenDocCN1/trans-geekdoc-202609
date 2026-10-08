

通过此，我们可以简化 $\mathcal{L}$ 中的项。首先，

$$\log |C| = \log |C_{-j}| + \log (1 + \sigma^{-2}\mathbf{w}_j^T\mathbf{w}_j). \quad (7.4)$$

使用 **A2.1** 对其 $\mathbf{w}_j$ 求导得到：

$$\frac{\partial}{\partial\mathbf{w}_j}\log |C| = \frac{1}{1+\sigma^{-2}\mathbf{w}_j^T\mathbf{w}_j}\sigma^{-2}\mathbf{w}_j = \frac{2}{\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j}\mathbf{w}_j.$$

另一方面，

$tr(C^{-1}\Sigma) = tr(C_{-j}\Sigma)\frac{\sigma^{-2}}{\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j}tr(\mathbf{w}_j^T\Sigma) = tr(C_{-j}\Sigma)\frac{\sigma^{-2}}{\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j}\mathbf{w}_j,$

这里我们使用了迹的循环变换性质。利用乘法法则、**A.2** 和 **A2.3**，对 $\mathbf{w}_j$ 的导数为：

$$\frac{\partial}{\partial\mathbf{w}_j}tr(C^{-1}\Sigma) = \frac{\sigma^{-2}}{\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j}[(\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j)\Sigma\mathbf{w}_j - (\mathbf{w}_j^T\Sigma)2\mathbf{w}_j].$$

因此，似然函数对 $\mathbf{w}_j$ 的导数为：

$$\frac{\partial}{\partial\mathbf{w}_j}\mathcal{L} = \frac{\sigma^{-2}}{\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j}[(\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j)\mathbf{w}_j - \Sigma\mathbf{w}_j].$$

如果 $\mathbf{w}_j$ 是 $\Sigma$ 的特征值为 $\lambda_j$ 的特征向量，且 $\mathbf{w}_j$ 的长度满足

则该项为零：

$$\frac{\sigma^{-2}\mathbf{w}_j}{\sigma^{-2}+\mathbf{w}_j^T\mathbf{w}_j} = \lambda_j,$$

使用 $\mathbf{w}_j = \lambda_j\mathbf{w}_j$，我们得到 $\mathbf{w}_j^T\mathbf{w}_j = \lambda_j$，或者等价于 $\mathbf{w}_j^T\mathbf{w}_j = \lambda_j$；由于 $\Sigma$ 有一组相互正交的特征向量，这与我们的假设一致。

图 7.5 显示了二维数据，主成分 $\mathbf{w}_1$ 被绘制为从样本均值开始长度为 $\sqrt{\lambda_1}\sigma^{-2}$ 的红色箭头，其中 $\lambda_1$ 是协方差矩阵的长度。在接下来我们将看到，选择最大的特征向量是最大化对数似然正确选择。

令 $\mathbf{w}_k, k=1, \dots, K$ 为 $\Sigma$ 的某些特征向量，其长度平方为 $\mathbf{w}_k^T\mathbf{w}_k = \lambda_k - \sigma^{-2}$ 并将其代入 (7.4)，得到：

$$\|C| = |C_{-j}|(1+\sigma^{-2}(\lambda_j-\sigma^{-2})) = (\sigma^{-2})^{D-K}\prod_{k=1}^K |\lambda_k|^2\prod_{k=1}^K \lambda_k.$$

![](img/c6c76bf52016db7e78a5e30d4766ef81_233_0.png)

同样将此应用于 (7.3)，我们得到：

$$C^{-1} = \sigma^2 \left(I - \sum_{k=1}^{K} \frac{\mathbf{w}_k\mathbf{w}_k^T}{\lambda_k}\right),$$

以及

$$tr(\mathbf{C}^{-1}\mathbf{\Sigma}) = \sigma^{-2} \left(tr(\mathbf{\Sigma}) - \sum_{k=1}^{K} \frac{\mathbf{w}_k^T\mathbf{\Sigma}\mathbf{w}_k}{\lambda_k}\right) = \sigma^{-2} \left(tr(\mathbf{\Sigma}) - \sum_{k=1}^{K} \lambda_k\right) + K,$$

这里我们使用了迹的循环变换以及 $\mathbf{w}_k$ 是 $\mathbf{\Sigma}$ 的特征向量且长度平方为 $\mathbf{w}_k^T\mathbf{w}_k = \lambda_k - \sigma^2$ 的事实。

利用这些结果，对数似然函数的表达式为：

$$\mathcal{L} = -\frac{N}{2} \left[ D\log(2\pi) + (D-K)\log\sigma^2 + \sum_{k=1}^{K} \log\lambda_k + \sigma^{-2} \left( \sum_{k=K+1}^{D} \lambda_k \right) \right]$$

因为矩阵的迹是其特征值的和。我们对其对 $\sigma^2$ 求导以对噪声差进行优化。

$$\frac{\partial}{\partial\sigma^2}\mathcal{L} = -\frac{N}{2} \left( (D-K)(\sigma^2)^{-1} - \sigma^{-2} \sum_{k=K+1}^{D} \lambda_k \right)$$

在下式下为零：

$$\sigma^2 = \frac{1}{D-K} \sum_{k=K+1}^{D} \lambda_k.$$

![](img/c6c76bf52016db7e78a5e30d4766ef81_234.png)

(a) 由主成分定义的平面。
(b) 沿着主成分观察数据。

图 7.6：三维数据的概率成分分析。

换句话说，$\sigma^2$ 是 $\lambda_1,...,lambda_K$ 之外的所有特征值的平均值。如前所述，$\sigma^2$ 解释了 $K$ 维之外的数据。因此 $\lambda_1,...,lambda_K$ 被选取为 $\Sigma$ 的最大特征值。似然取值为：

$$\mathcal{L} = -\frac{N}{2}[D\log(2\pi) + (D-K)\log(\frac{1}{D-K}\sum_{k=K+1}^D \lambda_k) + \sum_{k=1}^K \log \lambda_k]$$

图 7.6 说明了这些概念。从两个角度观察数据：首先由主成分定义的平面，其次沿着主成分。后者显示所有数据点位于主成分平面。噪声差 $\sigma^2$ 解释了偏差并等于协方差矩阵的最小特征值。

在本节中，我们通过极大化似然推导了 PCA。更一般地，Bishop 等 (203) 显示许多降维技术优化了似然的下界。下一节将利用该下界迭代极大化似然。

## 7.3 期望极大化

上一节基于假设，数据样本 $\mathbf{v}_1,...,mathbf{v}_N$ 通过 (7.2) 给出的线性映射到低维空间，均值为零且协方差矩阵为 $\sigma^2I$。因此，每个 $\mathbf{v}_n$ 服从均值为 $\mathbf{Wu}_n + \mu$ 协方差矩阵为 $\sigma^2I$ 的条件分布，其中 $n=1,...,N$，隐藏变量服从正态分布。上一节的解通过对隐藏变量求边缘分布有效地计算了 $\mathbf{v}_n$ 的边缘分布。然后对 $\mu$ 和 $\sigma^2$ 极大化数据集的似然。当 $m=\mu$ 为样本均值时，似然极大。对 $\mathbf{W}$ 和 $\sigma^2$ 的极大化涉及寻找协方差矩阵的最大特征值和特征向量，这本身是一个计算密集型问题。计算协方差矩阵并寻找 $K$ 最大特征值的复杂度为 $\mathcal{O}(ND^2)$（参见 [16]）。

接下来我们将使用结果 $m=\mu$ 并采用 6.4 节引入的期望极大化技术来寻找 $\mathbf{W}$ 和 $\sigma^2$，利用 $\mathbf{u}, a$ 的联合分布以及给定 $\mathbf{v}$ 的分布。注意在 6.4 中隐藏变量是离散的，在这里它们是连续的。原理是相同的。

根据乘法法则，联合概率为：

$$p(v, \mathbf{u}) = p(u)p(v|u) \times (2\pi)^{-K/2} \exp(-\frac{1}{2}\mathbf{u}^T\mathbf{u}) \times (2\pi\sigma^2)^{-D/2} \exp(-\frac{1}{2}\sigma^{-2}(v-\mathbf{W}u-\mu)^T(v-\mathbf{W}u-\mu))$$

合并指数项得到指数：

$$-\frac{1}{2}\sigma^{-2}(v-\mathbf{W}\mu)^T(v-\mathbf{W}\mu)^T\mathbf{W}-\mathbf{u}^T\mathbf{W}^T(v-\mu)+\mathbf{u}^T(\mathbf{W}^T\mathbf{W}+\sigma^2\mathbf{I}) \quad (7.5)$$

这可以写为：

$$-\frac{1}{2}(\begin{pmatrix} v \\ \mu \end{pmatrix})^T \sigma^{-2} \begin{pmatrix} \mathbf{I} & -\mathbf{W} \\ -\mathbf{W}^T & \mathbf{W}^T\mathbf{W}+\sigma^2\mathbf{I} \end{pmatrix} \begin{pmatrix} v \\ \mu \end{pmatrix}$$

因此，联合分布的均值为 $(\mu, 0)^T$，而带有标量因子 $\sigma^{-2}$ 的方差是精度矩阵，即协方差矩阵的逆。因此，使用 A.1.1 中的块矩阵逆公式，联合分布的协方差矩阵为：

$$\begin{pmatrix} \mathbf{I} & \mathbf{W} \\ \mathbf{W}^T & \mathbf{W}^T\mathbf{W}+\sigma^2\mathbf{I} \end{pmatrix}$$

使用 A.1.2 中块矩阵行列式的计算公式，联合协方差矩阵的行列式为 $(\sigma^2)^D$，与联合概率分布的因子一致。

