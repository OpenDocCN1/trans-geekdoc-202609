

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_100_0.png)

**图 3.17：** (a) 二维中的一些数据。(b) 使用 GMM 计算出的、以 $K = 3$ 个聚类划分的一种可能的聚类结果。由 `gmm_2d.py` 生成。

未知，但我们可以使用贝叶斯规则计算它们的后验：

$$r_{nk} \triangleq p(z_n = k \mid \mathbf{x}_n, \boldsymbol{\theta}) = \frac{p(z_n = k \mid \boldsymbol{\theta})p(\mathbf{x}_n \mid z_n = k, \boldsymbol{\theta})}{\sum_{k'=1}^{K} p(z_n = k' \mid \boldsymbol{\theta})p(\mathbf{x}_n \mid z_n = k', \boldsymbol{\theta})} \tag{3.117}$$

量 $r_{nk}$ 被称为簇 $k$ 对数据点 $n$ 的**责任**。在给定这些责任的情况下，我们可以按如下方式计算最可能的簇分配：

$$\hat{z}_n = \underset{k}{\arg\max}\ r_{nk} = \underset{k}{\arg\max}\left[\log p(\mathbf{x}_n \mid z_n = k, \boldsymbol{\theta}) + \log p(z_n = k \mid \boldsymbol{\theta})\right] \tag{3.118}$$

这被称为**硬聚类**。（如果我们使用这些责任将每个数据点按比例分配到不同的簇，则称为**软聚类**。）参见图 3.17 中的示例。

如果我们对 $z_n$ 采用均匀先验，并使用 $\boldsymbol{\Sigma}_k = \mathbf{I}$ 的球形高斯分布，则硬聚类问题简化为

$$z_n = \underset{k}{\arg\min}\ \lVert \mathbf{y}_n - \hat{\boldsymbol{\mu}}_k \rVert_2^2 \tag{3.119}$$

换句话说，我们将每个数据点分配给距离其最近的质心，这里的距离由欧几里得距离度量。这就是 **K 均值聚类**算法的基础，我们将在第 2.1.3 节中讨论该算法。

## 3.7.1.2 使用 GMM 作为先验来正则化逆问题

在本节中，我们考虑使用 GMM 作为黑盒密度模型来正则化多对一映射的逆问题。具体而言，我们考虑从退化版本 $\mathbf{y}$ 中推断“干净”图像 $\mathbf{z}$ 的问题。我们使用如下形式的线性-高斯前向模型：

$$p(\mathbf{y} \mid \mathbf{z}) = \mathcal{N}(\mathbf{y} \mid \mathbf{W}\mathbf{z}, \sigma^2\mathbf{I}) \tag{3.120}$$

其中 $\sigma^2$ 是测量噪声的方差。矩阵 $\mathbf{W}$ 的形式取决于退化的性质，为简单起见，我们假设该性质是已知的。以下是我们方法中可以建模的几种常见退化类型示例：

- 如果退化是由加性噪声引起的（如图 3.18a 所示），我们可以设置 $\mathbf{W} = \mathbf{I}$。由此得到的 MAP 估计可用于**图像去噪**，如图 3.18b 所示。
- 如果退化是由模糊引起的（如图 3.18c 所示），我们可以将 $\mathbf{W}$ 设置为固定的卷积核 [KF09b]。由此得到的 MAP 估计可用于**图像去模糊**，如图 3.18d 所示。
- 如果退化是由遮挡引起的（如图 3.18e 所示），我们可以将 $\mathbf{W}$ 设置为对角矩阵，在对应于遮挡物的位置处为 0。由此得到的 MAP 估计可用于**图像修复**，如图 3.18f 所示。

因此我们看到，线性-高斯似然模型具有令人惊讶的灵活性。给定模型后，我们的目标是通过计算 MAP 估计 $\hat{\mathbf{z}} = \arg\max_{\mathbf{z}} p(\mathbf{z}|\mathbf{y})$ 来对其求逆。然而，对该模型求逆的问题是病态的，因为存在许多可能的潜在图像 $\mathbf{z}$ 映射到相同的观测图像 $\mathbf{y}$。因此，我们需要使用先验来正则化求逆过程。

在 [ZWW11] 中，他们提出使用形式为 $p(\mathbf{z}) = \sum_k p(c = k)\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$ 的 GMM 先验，其中使用 $K = 200$ 个混合分量，并在包含 200 万张干净图像块的数据集上拟合该先验。因此，完整的联合模型具有如下形式：

$$p(c = k, \mathbf{z}, \mathbf{y}|\boldsymbol{\theta}) = p(c = k)\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)\mathcal{N}(\mathbf{y}|\mathbf{Wz}, \sigma^2\mathbf{I}) \tag{3.121}$$

为了计算边际 MAP 估计 $\arg\max_{\mathbf{z}} p(\mathbf{z}|\mathbf{y})$，我们可以使用近似

$$p(\mathbf{z}|\mathbf{y}) \approx p(\mathbf{z}|\mathbf{y}, c^*) \propto \mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_{c^*}, \boldsymbol{\Sigma}_{c^*})\mathcal{N}(\mathbf{y}|\mathbf{Wz}, \sigma^2\mathbf{I}) \tag{3.122}$$

如果我们知道 $c^*$，就可以使用式 (3.102) 中针对高斯分布的贝叶斯规则来计算上述表达式。为了计算 MAP 混合分量 $c^*$，我们可以使用式 (3.105) 得到

$$c^* = \arg\max_c p(c) p(\mathbf{y}|c) = \arg\max_c p(c)\mathcal{N}(\mathbf{y}|\mathbf{W}\boldsymbol{\mu}_c, \sigma^2\mathbf{I} + \mathbf{W}\boldsymbol{\Sigma}_c\mathbf{W}^{\mathsf{T}}) \tag{3.123}$$

图 3.18 展示了该过程实际运行的一些示例。

如果退化是未知的，则称为“盲逆问题”，其难度明显更大。参见例如 [Ani+18; XC19; Wan+20c] 中的相关工作。

## 3.7.2 伯努利混合

如果数据是二值的，我们可以使用**伯努利混合**，其中每个混合分量具有以下形式：

$$p(\mathbf{y}|\mathbf{z}=k,\boldsymbol{\theta}) = \prod_{d=1}^{D} \operatorname{Ber}(y_d|\mu_{dk}) = \prod_{d=1}^{D} \mu_{dk}^{y_d}(1-\mu_{dk})^{1-y_d} \tag{3.124}$$

这里 $\mu_{dk}$ 是位 $d$ 在簇 $k$ 中被激活的概率。

例如，考虑为著名的 **MNIST** 数据集 [LeC+98; YB19] 构建一个无监督密度模型。该数据集包含 6 万张大小为 $28 \times 28 \times 1$ 的训练图像（最后一维大小为 1 表示图像是灰度图），展示了来自 10 个类别的手写数字；图 3.19a 是该数据的一个示例。训练样本有 6 万个，测试样本有 1 万个。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_102_0.png)

图 3.18：使用 GMM 块先验和高斯似然通过 MAP 估计从退化版本（左）恢复干净图像（右）的示例。第一行：图像去噪。第二行：图像去模糊。第三行：图像修复。来自 [RW15] 和 [ZW11]。经 Dan Rosenbaum 和 Daniel Zoran 友好许可使用。

我们使用 $K = 20$ 个分量在训练集数据上拟合了一个伯努利混合模型。（我们使用 EM 算法进行拟合——详见第 5.7.3 节。）每个混合分量得到的参数（即 $\mu_k$ 和 $\pi_k$）如图 3.19b 所示。我们可以看到，该模型“发现”了每种数字的一种表示。（有些数字被表示多次，因为模型不知道“真实”的类别数。关于如何选择混合分量数量 $K$ 的更多信息，请参见第 21.3.7 节。）

## 3.7.3 高斯尺度混合

高斯尺度混合 (GSM) [AM74; Wes87] 类似于一种“无限”的高斯混合，其中每个分量具有不同的尺度（方差）。更准确地说，令 $x = \epsilon z$，其中 $z \sim \mathcal{N}(0, \sigma_0^2)$，$\epsilon \sim p(\epsilon)$。我们可以

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_103_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_103_1.png)

*图 3.19：(a) MNIST 数据集 [LeC+98; YB19] 中前 25 个数字的可视化。由 mnist_viz_tf.py 生成。(b) 我们对二值化的 MNIST 数字数据拟合了 20 个伯努利混合分量。我们可视化了估计的簇均值 $\hat{\mu}_k$。每幅图像上方的数字表示估计的混合权重 $\hat{\pi}_k$。训练该模型时未使用任何标签。由 mixBerMnistEM.m 生成。*

我们可以将其视为对高斯随机变量 $z$ 施加**乘性噪声**。我们有 $x|\epsilon \sim \mathcal{N}(0, \epsilon^2 \sigma_0^2)$。对尺度 $\epsilon$ 求边际积分可得

$$p(x)=\int \mathcal{N}(x|0,\sigma_0^2\epsilon^2)p(\epsilon)d\epsilon\tag{3.125}$$

通过改变先验 $p(\epsilon)$，我们可以生成各种有趣的分布。下面我们给出一些示例。

这种方法的主要优势在于，使用**扩展参数化**通常在计算上更方便，即在模型中显式包含尺度项 $\epsilon$，因为在该条件给定后，分布是高斯分布。我们在第 11.6.4.2 节中使用了该公式，其中我们讨论了使用 lasso 的稀疏回归，并在第 11.4.1.1 节中讨论了稳健回归。

### 3.7.3.1 示例：学生 t 分布作为 GSM

我们可以将学生分布表示为如下 GSM：

$$\mathcal{T}(y|0,\sigma^2,\nu)=\int_0^\infty dz\,\mathcal{N}(y|0,z\sigma^2)\mathrm{IG}\left(z\Big|\frac{\nu}{2},\frac{\nu}{2}\right)=\int_0^\infty dz\,\mathcal{N}(y|0,z\sigma^2)\chi^{-2}(z|\nu,1)dz\tag{3.126}$$

其中 IG 是逆伽马分布（第 3.4.5 节）。（推导见练习 3.7。）因此，我们可以将学生分布视为不同宽度高斯分布的无限叠加；将其积分后，所得到的分布比具有相同方差的高斯分布具有更宽的尾部。这个结果也解释了为什么当自由度变大时学生分布趋近于高斯分布，因为当 $\nu = \infty$ 时，逆伽马分布变成了一个 delta 函数。

