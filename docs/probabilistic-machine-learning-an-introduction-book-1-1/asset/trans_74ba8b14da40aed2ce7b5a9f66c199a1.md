

其中 $\hat{e}_i = \hat{e}_\theta(x_i)$，等等。利用三角不等式，我们有

$$\|\hat{e}_i - \hat{e}_j\| \leq \|\hat{e}_i - c_{y_i}\| + \|\hat{e}_j - c_{y_i}\| \tag{16.18}$$

$$\|\hat{e}_i - \hat{e}_k\| \geq \|\hat{e}_i - c_{y_k}\| - \|\hat{e}_k - c_{y_k}\| \tag{16.19}$$

因此

$$\ell_t(x_i,x_j,x_k) \leq \ell_u(x_i,x_j,x_k) \triangleq \|\hat{e}_i-c_{y_i}\| - \|\hat{e}_k-c_{y_k}\| + \|\hat{e}_j-c_{y_i}\| + \|\hat{e}_k-c_{y_k}\| \tag{16.20}$$

我们可以利用此式推导出三元组损失的可处理上界，如下所示：

$$\mathcal{L}_t(\mathcal{D},\mathcal{S}) = \sum_{(i,j)\in\mathcal{S},(i,k)\notin\mathcal{S},i,j,k\in\{1,\ldots,N\}} \ell_t(x_i,x_j,x_k) \leq \sum_{(i,j)\in\mathcal{S},(i,k)\notin\mathcal{S},i,j,k\in\{1,\ldots,N\}} \ell_u(x_i,x_j,x_k) \tag{16.21}$$

$$= C'\sum_{i=1}^{N}\left(\|x_i-c_{y_i}\| - \frac{1}{3(C-1)}\sum_{m=1,m\neq y_i}^{C}\|x_i-c_m\|\right) \triangleq \mathcal{L}_u(\mathcal{D},\mathcal{S}) \tag{16.22}$$

其中 $C' = 3(C-1)\left(\frac{N}{C}-1\right)\frac{N}{C}$ 是一个常数。显然，$\mathcal{L}_u$ 可以在 $O(NC)$ 时间内计算得出。请参阅 [16.6b 图](#) 获取示意图。

在 [Do+19] 中，他们证明 $0 \leq \mathcal{L}_t - \mathcal{L}_u \leq \frac{N^3}{C^2}K$，其中 $K$ 是依赖于质心分布广度的某个常数。为了确保该界限紧密，质心之间应尽可能远，且它们之间的距离应尽可能相似。确保这一点的一个简单方法是定义 $c_m$ 向量为一热向量（one-hot vectors），每个类别对应一个。这些向量已经具有单位范数，且彼此正交。每对质心之间的距离为 $\sqrt{2}$，这确保了上界相当紧密。

这种方法的缺点在于它假设嵌入层的维度为 $L=C$。对此有两个解决方案。首先，训练后，我们可以添加一个线性投影层，将维度从 $C$ 映射到 $L \neq C$；或者，我们可以取嵌入网络的倒数第二层。第二种方法是从 $L$ 维单位超球面上采样大量点（我们可以通过从标准正态分布中采样然后进行归一化来实现 [Mar+72]），然后运行 K 均值聚类（[2.13 节](#)），其中 $K=C$。在 [Do+19] 中报道的实验中，这两种方法给出了相似的结果。

有趣的是，在 [Rot+20] 中，他们表明增加 $\pi_{\mathrm{intra}}/\pi_{\mathrm{inter}}$ 的比例会在各种检索任务上改善下游性能，其中

$$\pi_{\mathrm{intra}} = \frac{1}{Z_{\mathrm{intra}}}\sum_{c=1}^{C}\sum_{i\neq j:y_i=y_j=c} d(x_i,x_j) \tag{16.23}$$

是类内平均距离，而

$$\pi_{\mathrm{inter}} = \frac{1}{Z_{\mathrm{inter}}}\sum_{c=1}^{C}\sum_{c'=1}^{C} d(\mu_c,\mu_{c'}) \tag{16.24}$$

是类间平均距离，其中 $\mu_c = \frac{1}{Z_c}\sum_{i:y_i=c}\hat{e}_i$ 是来自类别 $c$ 样本的平均嵌入。这表明我们不仅应保持质心远离（以最大化分子），还应防止样本过于接近其质心（以最小化分母）；后者在 [Do+19] 的方法中未被捕捉到。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_539_0.png)

*图 16.7：在深度度量学习方法中添加球形嵌入约束。经 Dingyi Zhang 善意许可使用。*

## 16.2.6 DML 的其他训练技巧

除了 16.2.5 节中的加速技巧外，还有许多其他细节对于确保良好的 DML 性能至关重要。其中许多细节都在 [MBL20; Rot+20] 中进行了讨论。这里我们仅简要提及其中几项。

一个重要问题是迷你批次（minibatch）是如何创建的。在分类问题中（至少是类别平衡的情况下），从训练集中随机选择样本通常就足够了。然而，对于 DML，我们需要确保每个样本在迷你批次中都有与其相似的样本，也有与其不相似的样本。一种方法是使用硬挖掘技术（16.2.5.1 节）。另一个想法是使用应用于先前学习到的嵌入的核心集方法，以在每个步骤中选择多样化的迷你批次 [Sin+20]。然而，[Rot+20] 表明，以下简单策略在创建每个批次时也表现良好：选择 $B/n$ 个类别，然后从每个类别中随机选择 $N_c$ 个样本，其中 $B$ 是批次大小，$N_c = 2$ 是一个调优参数。

另一个重要问题是避免过拟合。由于 DML 文献中使用的大多数数据集都很小，标准做法是使用在 ImageNet 上预训练的图像分类器，如 GoogLeNet（14.3.2.3 节）或 ResNet（14.3.2.4 节），然后使用 DML 损失对模型进行微调。（有关这种迁移学习的更多细节，请参见 19.2 节。）此外，标准做法是使用数据增强（参见 19.1 节）。（实际上，对于某些自监督学习方法，数据增强是创建相似对的唯一方法。）

在 [ZLZ20] 中，他们提出了添加球形嵌入约束（SEC），这是一种额外的逐批次正则化项，鼓励所有样本具有相同的范数。也就是说，正则化器仅仅是该批次中（未归一化的）嵌入范数的经验方差。请参阅图 16.7 获取示意图。类似于使用批归一化（13.4.5 节）的方式，可以将此正则化器添加到任何现有的 DML 损失中，以适度改善训练速度、稳定性以及最终性能。

## 16.3 核密度估计 (KDE)

在本节中，我们考虑一种称为核密度估计或 KDE 的非参数密度估计形式。这是一种生成模型，因为它定义了一个概率分布 $p(x)$，该分布可以逐点评估，并可以从其中采样以生成新数据。

### 16.3.1 密度核

在解释 KDE 之前，我们必须定义“核”的含义。这个术语在机器学习和统计学中有几种不同的含义。¹ 在本节中，我们使用一种特定的核，我们称之为**密度核**。这是一个函数 $\mathcal{K} : \mathbb{R} \to \mathbb{R}_+$，使得 $\int \mathcal{K}(x)dx = 1$ 且 $\mathcal{K}(-x) = \mathcal{K}(x)$。这种对称性意味着 $\int x\mathcal{K}(x)dx = 0$，因此

$\displaystyle \int x\mathcal{K}(x - x_n)dx = x_n$  (16.25)

这种核的一个简单例子是**方波核（boxcar kernel）**，即原点周围单位区间上的均匀分布：

$\displaystyle \mathcal{K}(x) \triangleq 0.5\,\mathbb{I}(|x| \le 1)$  (16.26)

另一个例子是**高斯核**：

$\displaystyle \mathcal{K}(x) = \frac{1}{(2\pi)^{1/2}} e^{-x^2/2}$  (16.27)

我们可以通过引入**带宽**参数 $h$ 来控制核的宽度：

$\displaystyle \mathcal{K}_h(x) \triangleq \frac{1}{h}\mathcal{K}\left(\frac{x}{h}\right)$  (16.28)

我们可以通过定义**径向基函数**或 **RBF** 核来推广到向量值输入：

$\displaystyle \mathcal{K}_h(\mathbf{x}) \propto \mathcal{K}_h(\|\mathbf{x}\|)$  (16.29)

对于高斯核的情况，这变为

$\displaystyle \mathcal{K}_h(\mathbf{x}) = \frac{1}{h^D (2\pi)^{D/2}} \prod_{d=1}^{D} \exp\left(-\frac{1}{2h^2} x_d^2\right)$  (16.30)

虽然高斯核很受欢迎，但它们具有无界支撑。表 16.1 中列出了某些替代核，它们具有紧支撑（计算上可能更快）。请参阅图 16.8 以查看这些核函数的绘图。

### 16.3.2 帕赞窗口密度估计器

为了解释如何使用核来定义非参数密度估计，回想 3.7.1 节中高斯混合模型的形式。如果我们假设固定的球形高斯协方差和均匀的混合权重，我们会得到

$\displaystyle p(\mathbf{x}|\boldsymbol{\theta}) = \frac{1}{K} \sum_{k=1}^{K} \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}_k, \sigma^2\mathbf{I})$  (16.31)

