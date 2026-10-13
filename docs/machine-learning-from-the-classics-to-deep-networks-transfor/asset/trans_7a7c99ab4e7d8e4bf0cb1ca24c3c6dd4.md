
$AZ = \left\lbrack \mathbf{a}_{1},\ldots,\mathbf{a}_{m} \right\rbrack\left\lbrack \mathbf{z}_{1}^{r},\ldots,\mathbf{z}_{m}^{r} \right\rbrack^{T} = \sum\limits_{i = 1}^{m}\mathbf{a}_{i}\mathbf{z}_{i}^{rT},$

![Equation](images/B9780443292385000263/si277.png)(20.68)

其中 $\mathbf{z}_{i}^{rT}$，$i=1,2,\ldots,m$，是 $Z$ 的*行*。请注意，在上述求和中，索引 $i=1,2,\ldots,k-1$ 对应的向量在当前迭代步骤的第二阶段固定为其最近更新的值，而对应 $i=k+1,\ldots,m$ 的向量则固定为上一迭代步骤可用的值。这种策略允许使用最近更新的信息。我们现在将针对秩一外积矩阵 $\mathbf{a}_{k}\mathbf{z}_{k}^{rT}$ 进行最小化。观察到该乘积除了涉及 $A$ 的第 $k$ 列外，还涉及 $Z$ 的第 $k$ 行；两者都将被更新。秩一矩阵的估计旨在使以下式子最小化：

$\|\mathbf{E}_{k}-\mathbf{a}_{k}\mathbf{z}_{k}^{rT}\|_{F}^{2},$

![Equation](images/B9780443292385000263/si282.png)(20.69)

其中

$E_{k} := X - \sum\limits_{i = 1,i \neq k}^{m}\mathbf{a}_{i}\mathbf{z}_{i}^{rT}.$

![Equation](images/B9780443292385000263/si283.png)

换句话说，我们寻求在 Frobenius 范数意义下 $E_{k}$ 的最佳秩一近似。回顾第 [6](#Chp006_249-291_B9780443292385000123.xhtml) 章（第 [6.4](#Chp006_249-291_B9780443292385000123.xhtml) 节），其解由 $E_{k}$ 的 SVD 给出。然而，如果那样做，无法保证从第一阶段更新中嵌入 $\mathbf{z}_{k}^{r}$ 的任何稀疏结构会被保留。根据 $k$-SVD，这是通过聚焦于活动集来绕过的，即仅涉及其非零系数。因此，我们首先搜索 $\mathbf{z}_{k}^{r}$ 中非零系数的位置，并令
