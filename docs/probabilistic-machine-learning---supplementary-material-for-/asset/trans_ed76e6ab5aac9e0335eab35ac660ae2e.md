

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_37_0.png)

图 4.4：联想记忆如何重建图像的示例。这些是大小为 150 × 150 像素的二值图像。顶部：训练图像。中间行：部分可见的测试图像。底部行：最终状态估计。改编自 [HKP91] 的图 2.1。由 hopfield__demo.py 生成。

我们想要记忆。（我们将在下面讨论如何做到这一点）。然后，在测试时，我们向网络展示一个部分模式。我们希望估计缺失的变量；这称为 **模式补全**。也就是说，我们想要计算

\(\boldsymbol{x}^* = \underset{\boldsymbol{x}}{\text{argmin}} \mathcal{E}(\boldsymbol{x})\) (4.7)

我们可以使用 **迭代条件众数（ICM）** 来求解这个优化问题，即我们根据邻居将每个隐藏变量设置为其最可能的状态。选择最可能的状态相当于使用规则

\(\boldsymbol{x}^{t+1} = \text{sgn}(\mathbf{W}\boldsymbol{x}^t)\) (4.8)

这可以被视为 Gibbs 采样的确定性版本（见 **??**）。

我们在图 4.4 中说明了此过程。在顶部行，我们展示了一些训练示例。在中间行，我们展示了一个损坏的输入，对应于初始状态 \(\boldsymbol{x}^0\)。在底部行，我们展示了经过 30 次 ICM 迭代后的最终状态。整个过程可以被视为根据示例的一部分从记忆中检索完整示例。

为了学习权重 \(\mathbf{W}\)，我们可以使用 **??** 中描述的最大似然估计方法。（另请参见 [HSDK12]。）但是，[Hop82] 提出了一种更简单的启发式方法，即使用以下 **外积方法**：

\(\mathbf{W} = \left( \frac{1}{N} \sum_{n=1}^N \boldsymbol{x}_n \boldsymbol{x}_n^\top \right) - \mathbf{I}\) (4.9)

这通过 \(N\) 将输出乘积矩阵归一化，然后将对角线设置为 0。这确保了与训练集中任何示例匹配的模式的能量较低。这是我们在图 4.4 中使用的技术。然而，请注意，此方法不仅存储原始模式，还存储它们的逆以及其他线性组合。因此，模型在存储的示例开始在记忆中“碰撞”之前，可存储的示例数量存在上限。Hopfield 证明，对于随机模式，网络容量约为 \(\sim 0.14N\)。

## 4.2.2 受限玻尔兹曼机（RBMs）的更多细节

在本节中，我们将更详细地讨论 RBM。

### 4.2.2.1 二元 RBMs

最常见的 RBM 形式具有二元隐藏节点和二元可见节点。联合分布则具有以下形式：

\(p(\boldsymbol{x}, \boldsymbol{z}|\boldsymbol{\theta}) = \frac{1}{Z(\boldsymbol{\theta})} \exp(-\mathcal{E}(\boldsymbol{x}, \boldsymbol{z}; \boldsymbol{\theta})) \tag{4.10}\)

\(\mathcal{E}(\boldsymbol{x}, \boldsymbol{z}; \boldsymbol{\theta}) \triangleq -\sum_{d=1}^D \sum_{k=1}^K x_d z_k W_{dk} - \sum_{d=1}^D x_d b_d - \sum_{k=1}^K z_k c_k \tag{4.11}\)

\(= -(\boldsymbol{x}^{\text{T}}\mathbf{W}\boldsymbol{z} + \boldsymbol{x}^{\text{T}}\boldsymbol{b} + \boldsymbol{z}^{\text{T}}\boldsymbol{c}) \tag{4.12}\)

\(Z(\boldsymbol{\theta}) = \sum_{\boldsymbol{x}} \sum_{\boldsymbol{z}} \exp(-E(\boldsymbol{x}, \boldsymbol{z}; \boldsymbol{\theta})) \tag{4.13}\)

其中，\(\mathcal{E}\) 是能量函数，\(\mathbf{W}\) 是一个 \(D \times K\) 权重矩阵，\(\boldsymbol{b}\) 是可见偏置项，\(\boldsymbol{c}\) 是隐藏偏置项，\(\boldsymbol{\theta} = (\mathbf{W}, \boldsymbol{b}, \boldsymbol{c})\) 是所有参数。为了记号简洁，我们将通过添加虚拟单元 \(x_0 = 1\) 和 \(z_0 = 1\) 并设置 \(\mathbf{w}_{0,:} = \boldsymbol{c}\) 和 \(\mathbf{w}_{:,0} = \boldsymbol{b}\) 来将偏置项吸收到权重矩阵中。请注意，天真地计算 \(Z(\boldsymbol{\theta})\) 需要 \(O(2^D 2^K)\) 的时间，但我们可以利用图的结构将其减少到 \(O(\min\{D2^K, K2^D\})\) 的时间。

当使用二元 RBM 时，后验可以计算如下：

\(p(\boldsymbol{z}|\boldsymbol{x}, \boldsymbol{\theta}) = \prod_{k=1}^K p(z_k|\boldsymbol{x}, \boldsymbol{\theta}) = \prod_k \text{Ber}(z_k|\boldsymbol{\sigma}(\boldsymbol{w}_{:,k}^{\text{T}}\boldsymbol{x})) \tag{4.14}\)

通过对称性，可以证明，给定隐藏变量时，我们可以按如下方式生成数据：

\(p(\boldsymbol{x}|\boldsymbol{z}, \boldsymbol{\theta}) = \prod_d p(x_d|\boldsymbol{z}, \boldsymbol{\theta}) = \prod_d \text{Ber}(x_d|\boldsymbol{\sigma}(\boldsymbol{w}_{d,:}^{\text{T}}\boldsymbol{z})) \tag{4.15}\)

我们可以用矩阵-向量记法写出这一点：

\(\mathbb{E}[\boldsymbol{z}|\boldsymbol{x}, \boldsymbol{\theta}] = \boldsymbol{\sigma}(\mathbf{W}^{\text{T}}\boldsymbol{x}) \tag{4.16}\)

\(\mathbb{E}[\boldsymbol{x}|\boldsymbol{z}, \boldsymbol{\theta}] = \boldsymbol{\sigma}(\mathbf{W}\boldsymbol{z}) \tag{4.17}\)

\(\mathbf{W}\) 中的权重称为 **生成权重**，因为它们用于生成观察值，而 \(\mathbf{W}^{\text{T}}\) 中的权重称为 **识别权重**，因为它们用于识别输入。

从方程 4.14 可以看出，我们按输入向量 \(\boldsymbol{x}\) 与权重向量 \(\boldsymbol{w}_{:,k}\) 的“相似程度”（不考虑缩放因子）来激活隐藏节点 \(k\)。因此，每个隐藏节点都会捕获输入的某些特征，这些特征编码在其权重向量中，类似于前馈神经网络。

例如，考虑文本模型的 RBM，其中 \(\boldsymbol{x}\) 是词袋（即，词汇表上的位向量）。如果“主题” \(k\) 存在于文档中，则令 \(z_k = 1\)。假设文档具有“体育”和“药物”主题。如果我们将每个主题的预测“相乘”，模型可能会给单词“兴奋剂”赋予非常高的概率，因为它满足两个约束。相比之下，将专家相加只会使分布更广（参见图 ??）。特别是，如果我们将“体育”和“药物”的预测混合在一起，我们可能会生成“板球”和“成瘾”等词，这些词来自两个主题的并集，而不是它们的交集。

### 4.2.2.2 类别 RBMs

我们可以通过使用 1-of-C 编码将二元 RBM 扩展到类别可见变量，其中 C 是每个 \(x_d\) 的状态数量。我们按如下方式定义新的能量函数 [SMH07; SH10]：

\(E(\boldsymbol{x}, \boldsymbol{z}; \boldsymbol{\theta}) \triangleq - \sum_{d=1}^D \sum_{k=1}^K \sum_{c=1}^C x_d^c z_k w_{dk}^c - \sum_{d=1}^D \sum_{c=1}^C x_d^c b_d^c - \sum_{k=1}^K z_k c_k \tag{4.18}\)

完整条件分布由以下给出

\(p(x_d = c^* | \boldsymbol{z}, \boldsymbol{\theta}) = S(\{b_d^c + \sum_k z_k w_{dk}^c\}_{c=1}^C)[c^*] \tag{4.19}\)

\(p(z_k = 1 | \boldsymbol{x}, \boldsymbol{\theta}) = \sigma(c_k + \sum_d \sum_c x_d^c w_{dk}^c) \tag{4.20}\)

### 4.2.2.3 高斯 RBMs

我们可以将模型推广到处理实值数据。特别是，高斯 RBM 具有以下能量函数：

\(E(\boldsymbol{x}, \boldsymbol{z} | \boldsymbol{\theta}) = - \sum_{d=1}^D \sum_{k=1}^K w_{dk} z_k x_d - 1/2 \sum_{d=1}^D (x_d - b_d)^2 - \sum_{k=1}^K a_k z_k \tag{4.21}\)

模型的参数为 \(\boldsymbol{\theta} = (w_{dk}, a_k, b_d)\)。（我们假设数据已标准化，因此将方差固定为 \(\sigma^2 = 1\)。）将其与标准或信息形式的高斯分布进行比较（参见第 ?? 节）：

\(N_c(\boldsymbol{x} | \boldsymbol{\eta}, \boldsymbol{\Lambda}) \propto \exp(\boldsymbol{\eta}^T \boldsymbol{x} - 1/2 \boldsymbol{x}^T \boldsymbol{\Lambda} \boldsymbol{x}) \tag{4.22}\)

其中 \(\boldsymbol{\eta} = \boldsymbol{\Lambda}\boldsymbol{\mu}\)。我们看到，我们已设置 \(\boldsymbol{\Lambda} = \mathbf{I}\)，以及 \(\boldsymbol{\eta} = \sum_k z_k \mathbf{w}_{:,k}\)。因此，均值由 \(\boldsymbol{\mu} = \boldsymbol{\Lambda}^{-1}\boldsymbol{\eta} = \sum_k z_k \mathbf{w}_{:,k}\) 给出，这是原型的加权组合。推断和学习所需的完整条件分布由以下给出

\(p(x_d | \boldsymbol{z}, \boldsymbol{\theta}) = N(x_d | b_d + \sum_k w_{dk} z_k, 1) \tag{4.23}\)

\(p(z_k = 1 | \boldsymbol{x}, \boldsymbol{\theta}) = \sigma ( c_k + \sum_d w_{dk} x_d ) \tag{4.24}\)

还可以开发更强大的模型，使（协）方差取决于隐藏状态 [RH10]。

### 4.2.2.4 具有高斯隐藏单元的 RBMs

如果我们使用高斯潜在变量和高斯可见变量，我们就得到了因子分析的无向版本（??）。有趣的是，这在数学上等同于标准的有向版本 [MM01]。

如果我们使用高斯潜在变量和类别观察变量，我们就得到了类别 PCA 的无向版本（第 ?? 节）。在 [SMH07] 中，这被应用于 Netflix 协作过滤问题，但被发现远不如使用二元潜在变量（后者具有更强的表达能力）。

