

这种数据生成方法被称为*中国餐厅过程*（Chinese Restaurant Process, CRP）。许多中国餐厅都有带有可以旋转的中心的圆桌。各种菜肴摆放在那里，食客可以通过旋转中心来共享食物。数据生成被比作一家假设的中国餐厅，那里有无限种桌子，每张桌子都可以坐下任意数量的顾客。第一个顾客坐在第一张桌子上并点了各种食物，这决定了分布。他们吃的内容对应于一个样本数据。第二个顾客可能选择坐在同一张桌子上。他们将享用相同的食物选择，但并不与第一个顾客完全相同。他们采样了一组不同的食物。另一方面，他们可能会选择坐在一张新桌子上并点一套不同的菜肴，这构成了第二个过程的分布。随着新顾客的到来，他们要么坐在空桌子上，要么新开一张桌子。

由于最终顾客人数 $V$ 是有限的，桌子数量 $K$ 也是有限的。最终达到的配置在重新标记桌子的情况下是唯一的。这意味着有 $K!$ 种等价的方式达到这种配置。在这种情况下，顾客到达的顺序并不重要。如果改变顺序，使得第一个顾客坐在不同的桌子上并成为第一张桌子，我们将这张桌子重新标记为 1 并更改所有标签。

## 6.7 利克过程

在考虑了数据集生成的过程后，我们需要改变视角，推导出聚类的数量以及哪些样本属于哪些数据。与之前的贝叶斯混合模型一样，我们选择一个浓度参数 $\alpha$ 和先验概率分布，并使用 Gibbs 采样（Gibbs sampling）从数据中推导出后验概率。然而，现在 $K$ 是当前的聚类数量且是变量。使用参数为 $m, \Psi$ 和 $\nu$ 的正态逆 Wishart 分布作为先验来进行说明。

在初始化阶段，按随机顺序考虑样本。假设首先考虑 $\mathbf{v}_1$。它也构成了第一个聚类。该聚类的后验正态逆 Wishart 分布从先验计算得出：

$$ \begin{aligned} \mathbf{m}_1 &= \frac{\mathbf{v}_1}{\lambda + 1} \\ \lambda_1 &= \lambda \\ \nu_1 &= \nu + 1 \\ \Psi_1 &= \Psi + \frac{\lambda}{\lambda + 1}(\mathbf{v}_1 - \mathbf{m})(\mathbf{v}_1 - \mathbf{m})^T \end{aligned} $$

从该聚类的分布中抽取出协方差矩阵 $\mathbf{\Sigma}_1$ 和均值 $\boldsymbol{\mu}_1$。

![](img/c6c76bf52016db7e78a5e30d4766ef81_213_0.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_213_1.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_213_2.png)

(a) 初始聚类分配。
(b) 10 次迭代后的聚类分配。
(c) 20 次迭代后的聚类分配。
6.12: 利克过程方法示例。

$v_n$ 是被考虑的第 $n$ 个样本，$\mathcal{D}_n = \{v_1, \dots, v_{n-1}\}$。也就是说 $\mathcal{D}_n$ 是目前为止被考虑的所有样本及其聚类分配。
对于 $k=1, \dots, K$，其中 $K$ 是当前的聚类数量，我们根据给定 $\mathcal{D}_n$ 中的样本及其聚类分配的情况下，计算 $v_n$ 属于聚类 $k$ 的概率：

$$p(z_{n,k}=1|\mathcal{D}_n, \alpha, \boldsymbol{m}, \boldsymbol{\lambda}, \mathbf{\Psi}, \nu) = p(z_{n,k}=1|\mathcal{D}_n, \alpha)p(v_n|\mathcal{D}_n, z_{n,k}=1, \boldsymbol{m}, \boldsymbol{\lambda}, \mathbf{\Psi}, \nu)$$

遵循乘积法则。现在，根据中国餐厅过程：

$$p(z_{n,k}=1|\mathcal{D}_n, \alpha) = \frac{n_k}{n-1+\alpha}$$

其中 $n_k$ 是分配给聚类 $k$ 的样本数量。另一方面，

$$p(v_n|\mathcal{D}_n, z_{n,k}=1, \boldsymbol{m}, \mathbf{\Psi}, \nu) \approx \frac{1}{\sqrt{|2\pi\Sigma_k|}} \exp (-\frac{1}{2}(v_n-\mu_k)^T\Sigma_k^{-1}(v_n-\mu_k)) \quad (6.14)$$

因此，数据 $\mathcal{D}_n$ 和当前的聚类分配不是直接使用的，而是通过当前的 $\boldsymbol{\mu}_k$ 和 $\boldsymbol{\Sigma}_k$ 间接使用的。

我们还计算了 $v_n$ 属于一个尚未未见的空聚类的概率。它是：

$$p(z_{n,K+1}=1|\mathcal{D}_n, \alpha, \boldsymbol{m}, \boldsymbol{\lambda}, \mathbf{\Psi}, \nu) =$$

第一个因子是：

$$p(z_{n,K+1}=1|\mathcal{D}_n, \alpha) = \frac{\alpha}{n-1+\alpha}$$

![](img/c6c76bf52016db7e78a5e30d4766ef81_214_0.png)

(a) 初始聚类分配。
(b) 10 次迭代后的聚类分配。
(c) 20 次迭代后的聚类分配。
图 6.13: 利克过程方法示例。

根据中国餐厅过程。数据集 $\mathcal{D}_n$ 仅通过其当前大小 $n-1$ 影响这个因子。另一个因子是 $\mathbf{v}_n$ 属于空聚类的概率。由于这个聚类仍然是空的，它的分布完全由先验决定。

$$p(\mathbf{v}_n, \tilde{z}_n, K+1 = 1, \mathbf{m}, \boldsymbol{\lambda}, \boldsymbol{\nu}) = \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{1}{2}(\mathbf{v}_n - \mathbf{m})^T \boldsymbol{\nu}^{-1}(\mathbf{v}_n - \mathbf{m})\right)$$

计算出这些 $K+1$ 个概率后，它们被用于采样 $v_n$ 属于哪个聚类，是现有的聚类还是空聚类。如果是前者，则需要更新该聚类的后验正态逆 Wishart 分布，并从中抽取一个新的协方差矩阵均值。如果是后者，该聚类可能是空的，并且需要计算后验正态逆 Wishart 分布的参数 $\mathbf{m}_{k_n}, \boldsymbol{\lambda}_{k_n}$ 和 $\boldsymbol{\nu}_{k_n}$。两者都根据 $K+1$ 更新。先验通过一个样本 $\mathbf{v}_n$ 更新为后验。从该分布中抽取协方差矩阵 $\boldsymbol{\Sigma}_{K+1}$ 和均值 $\boldsymbol{\mu}_{K+1}$。

一旦考虑了样本，初始化就完成了。虽然图 6.12 和 6.13 显示了不同的结果，但它们都得到了比例约为 0.5 和 0.4 的聚类，这与生成数据时的选择是一致的。

