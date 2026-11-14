

![](img/ca72c1626f4850f058a9edc138c1ac73_714_0.png)

图 18.5：通过相乘基本核得到的一维结构示例。第一行显示 K(x, x' = 1)。第二行显示从 GP(f|0, K) 中采样的一些函数。改编自 [Duw14] 中的图 2.2。由 combining_kernels_by_multiplication.ipynb 生成。

![](img/ca72c1626f4850f058a9edc138c1ac73_714_1.png)

图 18.6：通过相加基本核得到的一维结构示例。第一行显示 K(x, x' = 1)。第二行显示从 GP(f|0, K) 中采样的一些函数。改编自 [Duw14] 中的图 2.2。由 combining_kernels_by_summation.ipynb 生成。

## 18.2.5 Mercer 定理

回顾，任何正定矩阵 K 都可以使用形式为 K = U^T \Lambda U 的特征分解来表示，其中 \Lambda 是特征值 \lambda_i > 0 的对角矩阵，U 是包含特征向量的矩阵。现在考虑 K 的元素 (i, j)：

$$k_{ij} = (\mathbf{\Lambda}^{\frac{1}{2}} \mathbf{U}_{i:})^T (\mathbf{\Lambda}^{\frac{1}{2}} \mathbf{U}_{j:})$$

其中 $\mathbf{U}_{:i}$ 是 $\mathbf{U}$ 的第 $i$ 列。如果我们定义 $\boldsymbol{\phi}(\mathbf{x}_i) = \mathbf{U}_{:i}$，则可以写成
$$k_{ij} = \sum_{m=1}^M \lambda_m \phi_m(\mathbf{x}_i) \phi_m(\mathbf{x}_j)$$
其中 $M$ 是核矩阵的秩。因此，我们可以看到，核矩阵的条目可以通过计算某些特征向量的内积来得到，这些特征向量由核矩阵的特征向量隐式定义。

这一思想可以推广到核函数，而不仅仅是核矩阵，如下所示。首先，我们定义核 $\mathcal{K}$（相对于度量 $\mu$）的 **特征函数** $\phi()$，其特征值为 $\lambda$，即满足以下条件的函数：

$$\int \mathcal{K}(\mathbf{x}, \mathbf{x}') \boldsymbol{\phi}(\mathbf{x}) d\mu(\mathbf{x}) = \lambda \boldsymbol{\phi}(\mathbf{x}')$$

我们通常按特征值递减顺序对特征函数进行排序，$\lambda_1 \ge \lambda_2 \ge \cdots$。特征函数相对于 $\mu$ 正交：

$$\int \phi_i(\mathbf{x}) \phi_j(\mathbf{x}) d\mu(\mathbf{x}) = \delta_{ij}$$

其中 $\delta_{ij}$ 是克罗内克 delta。有了这个定义，我们可以陈述 **Mercer 定理**。非正式地说，它表示任何正定核函数都可以表示为以下无穷级数：

$$\mathcal{K}(\mathbf{x}, \mathbf{x}') = \sum_{m=1}^\infty \lambda_m \phi_m(\mathbf{x}) \phi_m(\mathbf{x}')$$

其中 $\phi_m$ 是核的特征函数，$\lambda_m$ 是相应的特征值。这是公式 (18.38) 的功能类比。

**退化核**仅具有有限个非零特征值。在这种情况下，我们可以将核函数重写为两个有限长度向量之间的内积。例如，考虑来自公式 (18.24) 的二次核 $\mathcal{K}(\mathbf{x}, \mathbf{x}') = \langle \mathbf{x}, \mathbf{x}' \rangle^2$。如果我们定义 $\boldsymbol{\phi}(x_1, x_2) = [x_1^2, \sqrt{2}x_1x_2, x_2^2] \in \mathbb{R}^3$，则可以将其写为 $\mathcal{K}(\mathbf{x}, \mathbf{x}') = \boldsymbol{\phi}(\mathbf{x})^\mathsf{T} \boldsymbol{\phi}(\mathbf{x})$。因此，我们可以看到这个核是退化的。

现在考虑 RBF 核。在这种情况下，相应的特征表示是无限维的（详情见第 18.2.6 节）。然而，通过使用核函数，我们可以避免处理无限维向量。

从上面可以看出，我们可以用对核函数的调用来替换显式（可能是无限维）特征空间中的内积运算，即用 $\mathcal{K}(\mathbf{x}, \mathbf{x}')$ 替换 $\boldsymbol{\phi}(\mathbf{x})^\mathsf{T} \boldsymbol{\phi}(\mathbf{x})$。这被称为 **核技巧**。

## 18.2.6 使用随机特征近似核

尽管核的威力在于能够避免处理输入的特征化表示，但这种核化方法需要 $O(N^3)$ 时间来逆转格拉姆矩阵 $\mathbf{K}$，正如我们将在第 18.3 节中看到的那样。这可能使得在大规模数据上使用此类方法变得困难。

幸运的是，我们可以使用随机选择的有限个 $M$ 个基函数来近似许多核的特征映射，从而将成本降低到 $O(NM + M^3)$。我们将展示如何通过回到公式 (18.22) 中的 Bochner 定理来对平移不变核进行此操作。对于高斯 RBF 核，我们已看到谱密度是高斯分布。因此，我们可以通过采样随机高斯向量来轻松计算该积分的蒙特卡洛近似。这得到以下近似：$\mathcal{K}(\boldsymbol{x}, \boldsymbol{x}') \approx \boldsymbol{\phi}(\boldsymbol{x})^\mathsf{T}\boldsymbol{\phi}(\boldsymbol{x})$，其中（实值）特征向量由以下给出：

$$\boldsymbol{\phi}(\boldsymbol{x}) = \sqrt{\frac{1}{D}} [\sin(\boldsymbol{z}_1^\mathsf{T}\boldsymbol{x}), \cdots, \sin(\boldsymbol{z}_D^\mathsf{T}\boldsymbol{x}), \cos(\boldsymbol{z}_1^\mathsf{T}\boldsymbol{x}), \cdots, \cos(\boldsymbol{z}_D^\mathsf{T}\boldsymbol{x})]$$ (18.42)

$$= \sqrt{\frac{1}{D}} [\sin(\boldsymbol{Z}^\mathsf{T}\boldsymbol{x}), \cos(\boldsymbol{Z}^\mathsf{T}\boldsymbol{x})]$$ (18.43)

这里 \(\mathbf{Z} = (1/\sigma)\mathbf{G}\)，其中 \(\mathbf{G} \in \mathbb{R}^{d \times D}\) 是一个随机高斯矩阵，其条目独立同分布地从 \(\mathcal{N}(0, 1)\) 中采样。公式 (18.43) 中的表示称为 **随机傅里叶特征** (**RFF**) [SS15; RR08] 或“随机厨房水槽的加权和” [RR09]。（通过确保 \(\mathbf{Z}\) 的行是随机但正交的，可以获得更好的近似；这称为 **正交随机特征** [Yu+16]。）

可以为其他类型的核创建类似的随机特征表示。然后我们可以通过定义 \(f(\boldsymbol{x}; \boldsymbol{\theta}) = \mathbf{W}\boldsymbol{\varphi}(\mathbf{Zx}) + \boldsymbol{b}\) 来使用此类特征进行监督学习，其中 \(\mathbf{Z}\) 是随机高斯矩阵，\(\boldsymbol{\varphi}\) 的形式取决于所选核。这相当于一个具有一个隐藏层的 MLP，具有随机的输入到隐藏权重；由于我们只优化隐藏到输出权重 \(\boldsymbol{\theta} = (\mathbf{W}, \boldsymbol{b})\)，该模型相当于具有固定随机特征的线性模型。如果我们使用足够多的随机特征，我们可以近似核化预测模型的性能，但计算成本现在是 \(O(N)\) 而不是 \(O(N^2)\)。

不幸的是，随机特征可能导致比使用非退化核更差的性能，因为它们没有足够的表达能力。我们将在 18.5 节中讨论将 GP 扩展到大型数据集的其他方法。

## 18.3 带高斯似然的 GP

在本节中，我们将使用高斯似然讨论回归问题的 GP。在这种情况下，所有计算都可以使用标准线性代数方法以封闭形式进行。我们将在本章后面将此框架扩展到非高斯似然。

### 18.3.1 使用无噪声观测值进行预测

假设我们观察到一个训练集 \(\mathcal{D} = \{(\boldsymbol{x}_n, y_n) : n = 1 : N\}\)，其中 \(y_n = f(\boldsymbol{x}_n)\) 是在 \(\boldsymbol{x}_n\) 处计算的函数的无噪声观测值。如果我们要求 GP 对它已经见过的 \(\boldsymbol{x}\) 值预测 \(f(\boldsymbol{x})\)，我们希望 GP 返回没有不确定性的答案 \(f(\boldsymbol{x})\)。换句话说，它应该充当训练数据的 **插值器**。这里我们假设观测到的函数值是无噪声的。我们将稍后考虑有噪声观测的情况。

现在我们考虑对可能不在 \(\mathcal{D}\) 中的新输入进行输出预测的情况。具体来说，给定大小为 \(N_* \times D\) 的测试集 \(\mathbf{X}_*\)，我们想要预测函数输出 \(\boldsymbol{f}_* = [f(\boldsymbol{x}_1), \dots, f(\boldsymbol{x}_{N_*})]\)。

