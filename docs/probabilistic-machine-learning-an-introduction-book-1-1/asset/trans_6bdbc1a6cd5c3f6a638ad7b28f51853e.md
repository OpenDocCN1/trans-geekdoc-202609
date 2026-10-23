
将标签集合 **Y** 映射为一个标量。显然，$f(\emptyset)=0$，并且 $f$ 是非递减的，即 $f(Y^{\text{large}}) \ge f(Y^{\text{small}})$，这源于“更多信息总是有益”的原则。此外，[KG05] 证明了 $f$ 具有**次模性**。因此，顺序贪心方法在常数因子内达到最优。如果我们将这种贪心技术与 BALD 目标函数相结合，就得到了名为 **BatchBALD** [KAG19] 的方法。

## 19.8 练习

### 练习 19.1 [信息增益方程]

考虑在主动学习环境中评估查询数据点 **x** 效用的以下两个目标函数：

$U(\mathbf{x}) \triangleq \mathbb{H}\left(p(\boldsymbol{\theta}|\mathcal{D})\right) - \mathbb{E}_{p(y|\mathbf{x},\mathcal{D})}\left[\mathbb{H}\left(p(\boldsymbol{\theta}|\mathcal{D},\mathbf{x},y)\right)\right]$  (19.69)

$U'(\mathbf{x}) \triangleq \mathbb{E}_{p(y|\mathbf{x},\mathcal{D})}\left[\mathbb{K}\mathbb{L}\left(p(\boldsymbol{\theta}|\mathcal{D},\mathbf{x},y) \| p(\boldsymbol{\theta}|\mathcal{D})\right)\right]$  (19.70)

证明这两个目标函数是相等的。

## 20 降维

无监督学习的一种常见形式是**降维**，我们学习从高维可见空间 $\mathbf{x} \in \mathbb{R}^D$ 到低维潜在空间 $\mathbf{z} \in \mathbb{R}^L$ 的映射。该映射可以是参数模型 $\mathbf{z}=f(\mathbf{x};\boldsymbol{\theta})$，可应用于任何输入；也可以是非参数映射，我们为数据集中的每个输入 $\mathbf{x}_n$ 计算一个**嵌入** $\mathbf{z}_n$，但不适用于其他点。后一种方法主要用于数据可视化，而前一种方法也可用作其他类型学习算法的预处理步骤。例如，我们可以先通过从 $\mathbf{x}$ 到 $\mathbf{z}$ 的学习映射来降低维度，然后在该嵌入上学习一个简单的线性分类器，通过映射 $\mathbf{z}$ 到 $y$ 来实现。

### 20.1 主成分分析 (PCA)

最简单且最广泛使用的降维形式是**主成分分析**或 **PCA**。基本思想是找到高维数据 $\mathbf{x} \in \mathbb{R}^D$ 到低维子空间 $\mathbf{z} \in \mathbb{R}^L$ 的线性正交投影，使得低维表示是原始数据的“良好近似”，其意义如下：如果我们投影或编码 $\mathbf{x}$ 得到 $\mathbf{z}=\mathbf{W}^{\mathsf{T}}\mathbf{x}$，然后解投影或解码 $\mathbf{z}$ 得到 $\hat{\mathbf{x}}=\mathbf{W}\mathbf{z}$，我们希望 $\hat{\mathbf{x}}$ 在 $\ell_2$ 距离下接近 $\mathbf{x}$。特别是，我们可以定义如下的**重建误差**或**失真**：

$$\mathcal{L}(\mathbf{W}) \triangleq \frac{1}{N}\sum_{n=1}^{N}\left\|\mathbf{x}_n-\operatorname{decode}(\operatorname{encode}(\mathbf{x}_n;\mathbf{W});\mathbf{W})\right\|_2^2 \tag{20.1}$$

其中编码和解码阶段都是线性映射，如下文所述。在第 20.1.2 节中，我们证明通过设置 $\hat{\mathbf{W}}=\mathbf{U}_L$ 可以最小化该目标函数，其中 $\mathbf{U}_L$ 包含经验协方差矩阵中特征值最大的 $L$ 个特征向量

$$\hat{\boldsymbol{\Sigma}}=\frac{1}{N}\sum_{n=1}^{N}(\mathbf{x}_n-\bar{\mathbf{x}})(\mathbf{x}_n-\bar{\mathbf{x}})^{\mathsf{T}}=\frac{1}{N}\mathbf{X}_c^{\mathsf{T}}\mathbf{X}_c \tag{20.2}$$

其中 $\mathbf{X}_c$ 是 $N \times D$ 设计矩阵的中心化版本。在第 20.2.2 节中，我们证明这等价于最大化已知为概率 PCA 的潜在线性高斯模型的对数似然。

#### 20.1.1 示例

在给出详细推导之前，我们先展示一些示例。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_654_0.png)

图 20.1：PCA 的示意图，我们从 2d 投影到 1d。圆圈是原始数据点，十字是重建结果。红色星号是数据均值。由 pcaDemo2d.py 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_654_1.png)

图 20.2：对 MNIST 数字类 9 应用 PCA 的示意图。网格点位于数据分布沿每个维度的 5、25、50、75、95% 分位数处。带圆圈的点是网格顶点最近的投影图像。改编自 [HTF09] 中的图 14.23。由 pca_digits.py 生成。

图 20.1 展示了一个非常简单的例子，我们将 2d 数据投影到 1d 线上。投影点（由绿色十字标记）捕获了原始数据的大部分变化，这些变化发生在对角线上（而不是垂直于该线的方向上）。

在图 20.2 中，我们展示了将数字 9 的一些 MNIST 图像投影到 2d 时会发生什么。尽管输入是高维的（具体为 28 × 28 = 784 维），但“有效自由度”的数量要少得多，因为像素是相关的，并且许多数字看起来相似。因此，我们可以将每个图像表示为低维线性空间中的一个点。我们可以看到，第一主成分（水平方向）似乎捕获了数字的方向，而第二成分（垂直方向）似乎捕获了线条粗细。

在图 20.3 中，我们展示了应用于另一个数据集的 PCA，称为 Olivetti 人脸数据集，它是一组 64 × 64 灰度图像。我们将这些图像投影到 3d 子空间。所得的基向量（投影矩阵 W 的列）作为图像显示在图 20.3b 中；这些被称为特征脸 [Tur13]，原因将在第 20.1.2 节中解释。我们看到，数据中的主要变化模式与整体光照以及面部眉毛区域的差异有关。如果我们使用足够的维度（但少于我们最初使用的 4096 维），我们可以使用表示 z = W^T x 作为最近邻分类器的输入来执行人脸识别；这比在像素空间中工作更快且更可靠 [MWP98]。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_655_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_655_1.png)

#### 20.1.2 算法推导

假设我们有一个（未标记的）数据集 $\mathcal{D} = \{\mathbf{x}_n : n = 1 : N\}$，其中 $\mathbf{x}_n \in \mathbb{R}^D$。我们可以将其表示为 $N \times D$ 数据矩阵 $\mathbf{X}$。我们将假设 $\bar{\mathbf{x}} = \frac{1}{N}\sum_{n=1}^N \mathbf{x}_n = \mathbf{0}$，这可以通过中心化数据来保证。

我们希望通过低维表示 $\mathbf{z}_n \in \mathbb{R}^L$ 来近似每个 $\mathbf{x}_n$。我们假设每个 $\mathbf{x}_n$ 都可以用基函数 $\mathbf{w}_1, \ldots, \mathbf{w}_L$ 的加权组合来“解释”，其中每个 $\mathbf{w}_k \in \mathbb{R}^D$，权重由 $\mathbf{z}_n \in \mathbb{R}^L$ 给出，即我们假设 $\mathbf{x}_n \approx \sum_{k=1}^L z_{nk} \mathbf{w}_k$。向量 $\mathbf{z}_n$ 是 $\mathbf{x}_n$ 的低维表示，被称为潜在向量，因为它由数据中未观察到的潜在或“隐藏”值组成。这些潜在变量的集合称为潜在因子。

我们可以如下测量由该近似产生的误差：

$$\mathcal{L}(\mathbf{W}, \mathbf{Z}) = \frac{1}{N} \left\|\mathbf{X} - \mathbf{Z} \mathbf{W}^{\mathsf{T}}\right\|_F^2 = \frac{1}{N} \left\|\mathbf{X}^{\mathsf{T}} - \mathbf{W} \mathbf{Z}^{\mathsf{T}}\right\|_F^2 = \frac{1}{N} \sum_{n=1}^{N} \left\|\mathbf{x}_n - \mathbf{W} \mathbf{z}_n\right\|^2 \tag{20.3}$$

其中 $\mathbf{Z}$ 的行包含 $\mathbf{X}$ 的行低维版本。这被称为（平均）重建误差，因为我们用 $\hat{\mathbf{x}}_n = \mathbf{W} \mathbf{z}_n$ 来近似每个 $\mathbf{x}_n$。

我们希望最小化这个目标函数，并受限于 $\mathbf{W}$ 是正交矩阵。下面我们证明最优解是通过设置 $\hat{\mathbf{W}} = \mathbf{U}_L$ 获得的，其中 $\mathbf{U}_L$ 包含经验协方差矩阵中特征值最大的 $L$ 个特征向量。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_657_0.png)

**图 20.4：** 投影到不同 1d 向量上的点方差的示意图。$v_1$ 是第一主成分，它最大化投影的方差。$v_2$ 是第二主成分，它是垂直于 $v_1$ 的方向。最后，$v'$ 是介于 $v_1$ 和 $v_2$ 之间的某个其他向量。改编自 [Gér19] 中的图 8.7。由 `pca_projected_variance.py` 生成

#### 20.1.2.2 最优权重向量最大化投影数据的方差

在继续之前，我们做一个有趣的观察。由于数据已经中心化，我们有

$$\mathbb{E}[z_{n1}] = \mathbb{E}[\mathbf{x}_n^\top \mathbf{w}_1] = \mathbb{E}[\mathbf{x}_n]^\top \mathbf{w}_1 = 0 \tag{20.14}$$

因此，投影数据的方差由下式给出

$$\mathbb{V}[\tilde{z}_1] = \mathbb{E}[\tilde{z}_1^2] - \bigl(\mathbb{E}[\tilde{z}_1]\bigr)^2 = \frac{1}{N}\sum_{n=1}^{N} z_{n1}^2 - 0 = -\mathcal{L}(\mathbf{w}_1) + \mathrm{const} \tag{20.15}$$

由此可见，*最小化*重建误差等价于*最大化*投影数据的方差：

$$\arg\min_{\mathbf{w}_1}\mathcal{L}(\mathbf{w}_1) = \arg\max_{\mathbf{w}_1}\mathbb{V}[\tilde{z}_1(\mathbf{w}_1)] \tag{20.16}$$

这就是为什么常说 PCA 找到最大方差的方向。（见图 20.4 的示意图。）然而，最小误差表述更容易理解且更具通用性。

#### 20.1.2.3 归纳步骤

现在让我们找到另一个方向 $\mathbf{w}_2$，以进一步最小化重建误差，约束条件为 $\mathbf{w}_1^\top \mathbf{w}_2 = 0$ 和 $\mathbf{w}_2^\top \mathbf{w}_2 = 1$。误差为

$$\mathcal{L}(\mathbf{w}_1, \tilde{z}_1, \mathbf{w}_2, \tilde{z}_2) = \frac{1}{N}\sum_{n=1}^{N}\left\|\mathbf{x}_n - z_{n1}\mathbf{w}_1 - z_{n2}\mathbf{w}_2\right\|^2 \tag{20.17}$$

