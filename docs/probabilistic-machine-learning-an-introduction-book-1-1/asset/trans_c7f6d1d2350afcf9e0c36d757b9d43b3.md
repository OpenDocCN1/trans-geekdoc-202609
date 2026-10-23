

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_695_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_695_1.png)

图20.38：拉普拉斯特征映射应用于(a)瑞士卷。由manifold_swiss_sklearn.py生成。(b) UCI数字数据集。由manifold_digits_sklearn.py生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_695_2.png)

图20.39：由无向图导出的拉普拉斯矩阵的图示。来自 https://en.wikipedia.org/wiki/Laplacian_matrix。经维基百科作者AzaToth善意许可使用。

其中，如果$i$和$j$是KNN图中的邻居，则 $W_{ij} = \exp\left(-\frac{1}{2\sigma^2}||\mathbf{x}_i - \mathbf{x}_j||^2_2\right)$，否则为0。我们添加约束 $\mathbf{Z}^\top \mathbf{D} \mathbf{Z} = \mathbf{I}$ 以避免 $\mathbf{Z} = \mathbf{0}$ 的退化解，其中 $\mathbf{D}$ 是存储每个节点度的对角权重矩阵，$D_{ii} = \sum_j W_{i,j}$。

我们可以将上述目标重写如下：

$\mathcal{L}(\mathbf{Z}) = \sum_{ij} W_{ij}(||\mathbf{z}_i||^2 + ||\mathbf{z}_j||^2 - 2\mathbf{z}_i\mathbf{z}_j^\top)$  (20.120)
$= \sum_i D_{ii}||\mathbf{z}_i||^2 + \sum_j D_{jj}||\mathbf{z}_j||^2 - 2 \sum_{ij} W_{ij}\mathbf{z}_i\mathbf{z}_j^\top$  (20.121)
$= 2\mathbf{Z}^\top \mathbf{D} \mathbf{Z} - 2\mathbf{Z}^\top \mathbf{W} \mathbf{Z} = 2\mathbf{Z}^\top \mathbf{L} \mathbf{Z}$  (20.122)

其中 $\mathbf{L} = \mathbf{D} - \mathbf{W}$ 是图拉普拉斯（见第20.4.9.2节）。可以证明，最小化该目标等价于求解特征值问题 $\mathbf{L}\mathbf{z}_i = \lambda \mathbf{D}\mathbf{z}_i$，以获得 $L$ 个最小的非零特征值。

将该方法（使用RBF核）应用于我们的运行示例的结果见图20.38。

## 20.4.9.2 什么是图拉普拉斯？

上文我们看到，为了学习高维点的良好嵌入，可以计算图拉普拉斯的特征向量。在本节中，我们给出一些关于其为何有效的直观认识。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_696_0.png)

图20.40：定义在图上的（正）函数的图示。来自[Shv+19]的图1。经Pascal Frossard善意许可使用。

设 $W$ 为图的对称权重矩阵，其中 $W_{ij}=W_{ji}\geq 0$。设 $\mathbf{D}=\operatorname{diag}(d_i)$ 为包含每个节点加权度的对角矩阵，$d_i=\sum_j w_{ij}$。我们将图**拉普拉斯**定义如下：

$$\mathbf{L}\triangleq \mathbf{D}-\mathbf{W} \tag{20.123}$$

因此 $\mathbf{L}$ 的元素由下式给出：

$$L_{ij}=\begin{cases} d_i & \text{if } i=j\\ -w_{ij} & \text{if } i\ne j\text{ and }w_{ij}\ne 0\\ 0 & \text{otherwise}\end{cases} \tag{20.124}$$

计算示例见图**20.39**。

假设我们为图中的每个节点 $i$ 关联一个值 $f_i\in\mathbb{R}$（例如见图20.40）。然后，我们可以将图拉普拉斯用作差分算子，计算函数在某一点的离散导数：

$$(\mathbf{L}f)(i)=\sum_{j\in\operatorname{nbr}_i}W_{ij}[f(i)-f(j)] \tag{20.125}$$

其中 $\operatorname{nbr}_i$ 是节点 $i$ 的邻居集合。我们还可以通过计算函数 $f$ 的**狄利克雷能量**来获得其“平滑度”的整体度量，如下所示：

$$f^T\mathbf{L}f=f^T\mathbf{D}f-f^T\mathbf{W}f=\sum_i d_i f_i^2-\sum_{i,j}f_i f_j w_{ij} \tag{20.126}$$

$$=\frac{1}{2}\left(\sum_i d_i f_i^2-2\sum_{i,j}f_i f_jw_{ij}+\sum_j d_jf_j^2\right)=\frac{1}{2}\sum_{i,j}w_{ij}(f_i-f_j)^2 \tag{20.127}$$

通过研究拉普拉斯矩阵的特征值和特征向量，我们可以确定该函数的各种有用性质。（应用线性代数研究图的邻接矩阵或相关矩阵，被称为**谱图理论**[Chu97]。）例如，我们看到**L**是对称且半正定的，因为对于所有 **f** ∈ ℝ^N，均有 **f**^T **L** **f** ≥ 0，这是由式(20.127)以及 $w_{ij} \geq 0$ 的假设得出的。因此**L**有N个非负实值特征值，0 ≤ λ₁ ≤ λ₂ ≤ … ≤ λ_N。相应的特征向量按平滑度递减的顺序构成定义在图上的函数 f 的一组正交基。

在第20.4.9.1节中，我们讨论了拉普拉斯特征映射，这是一种为高维数据向量学习低维嵌入的方法。其做法是令 $z_{id}=f_i^d$ 为输入 $i$ 的第 $d$ 个嵌入维度，然后为这些函数（即点的嵌入）寻找一组在图上平滑变化的基，从而使嵌入保持点在高维空间中的距离关系。

图拉普拉斯在机器学习中还有许多其他应用。例如，在第21.5.1节中，我们讨论了归一化切割（normalized cuts），这是一种基于成对相似性学习高维数据向量聚类的方法；[WTN19]讨论了如何使用状态转移矩阵的特征向量来学习强化学习（RL）的表示。

## 20.4.10 t-SNE

在本节中，我们介绍一种非常流行的学习低维嵌入的非凸技术，称为**t-SNE** [MH08]。它扩展了[HR03]早期的**随机近邻嵌入**方法，因此我们先描述SNE，然后再描述t-SNE扩展。

### 20.4.10.1 随机近邻嵌入（SNE）

SNE的基本思想是将高维欧氏距离转换为表示相似性的条件概率。更精确地说，我们定义 $p_{j|i}$ 为：如果邻居是按照以 $\mathbf{x}_i$ 为中心的高斯分布下各点的概率成比例被选取的，那么点 $j$ 选择点 $i$ 作为其邻居的概率：

$$p_{j|i} = \frac{\exp\left(-\frac{1}{2\sigma_i^2}||\mathbf{x}_i - \mathbf{x}_j||^2\right)}{\sum_{k\neq i} \exp\left(-\frac{1}{2\sigma_i^2}||\mathbf{x}_i - \mathbf{x}_k||^2\right)} \tag{20.128}$$

这里 $\sigma_i^2$ 是数据点 $i$ 的方差，可用于“放大”输入空间密集区域中点的尺度，并缩小较稀疏区域的尺度。（我们稍后将讨论如何估计长度尺度 $\sigma_i^2$）。

设 $\mathbf{z}_i$ 为表示 $\mathbf{x}_i$ 的低维嵌入。我们以类似的方式定义低维空间中的相似性：

$$q_{j|i} = \frac{\exp\left(-||\mathbf{z}_i - \mathbf{z}_j||^2\right)}{\sum_{k\neq i} \exp\left(-||\mathbf{z}_i - \mathbf{z}_k||^2\right)} \tag{20.129}$$

在这种情况下，方差被固定为一个常数；改变它只会重新缩放学习到的映射，而不会改变其拓扑结构。

如果嵌入是好的，那么 $q_{j|i}$ 应该与 $p_{j|i}$ 匹配。因此，SNE将目标定义为

$$\mathcal{L} = \sum_i \mathbb{KL}(P_i||Q_i) = \sum_i \sum_j p_{j|i} \log \frac{p_{j|i}}{q_{j|i}} \tag{20.130}$$

其中 $P_i$ 是在给定 $x_i$ 的条件下对所有其他数据点的条件分布，$Q_i$ 是在给定 $z_i$ 的条件下对所有其他潜在点的条件分布，$KL(P_i||Q_i)$ 是两个分布之间的KL散度（见第6.2节）。

注意，这是一个不对称的目标。特别是，如果用较小的 $q_{j|i}$ 来建模较大的 $p_{j|i}$，代价会很大。因此，该目标倾向于将较远的点拉近，而不是将邻近的点推开。通过观察每个嵌入向量的梯度，我们可以更好地理解其几何结构，梯度由下式给出：

$$\nabla_{z_i} L(Z) = 2 \sum_j (z_j - z_i)(p_{j|i} - q_{j|i} + p_{i|j} - q_{i|j}) \tag{20.131}$$

因此，如果p大于q，则点会相互拉近；如果q大于p，则点会相互排斥。

虽然这是一个直观上合理的目标，但它不是凸的。不过，它仍然可以通过SGD最小化。在实践中，向嵌入点添加高斯噪声并逐渐退火噪声量是有帮助的。[Hin13]建议，在降低噪声水平之前，应“在全局结构开始从映射点的热等离子体中形成的噪声水平上花费很长时间”。

### 20.4.10.2 对称SNE

有一种稍微简单的SNE版本，它最小化高维空间中的联合分布P与低维空间中的联合分布Q之间的单一KL散度：

$$L = KL(P||Q) = \sum_{i<j} p_{ij} \log \frac{p_{ij}}{q_{ij}} \tag{20.132}$$

这被称为对称SNE。

定义 $p_{ij}$ 的显而易见方式是使用

$$p_{ij} = \frac{\exp\left(-\frac{1}{2\sigma^2}||\mathbf{x}_i - \mathbf{x}_j||^2\right)}{\sum_{k<l} \exp\left(-\frac{1}{2\sigma^2}||\mathbf{x}_k - \mathbf{x}_l||^2\right)} \tag{20.133}$$

我们可以类似地定义 $q_{ij}$。相应的梯度变为

$$\nabla_{z_i} L(Z) = 2 \sum_j (z_j - z_i)(p_{ij} - q_{ij}) \tag{20.134}$$

如前所述，如果p大于q，则点会相互拉近；如果q大于p，则点会相互排斥。

虽然对称SNE实现起来稍微容易一些，但它失去了常规SNE的一个优良性质：如果嵌入维度L设置为等于环境维度D，则数据本身就是其最优嵌入。尽管如此，在L << D的真实数据集上，这些方法在实践中似乎给出相似的结果。

7. 关于无监督学习中的退火与相变的讨论，参见[Ros98; WF20]。另见[CP10]关于弹性嵌入算法的讨论，该算法使用同伦方法，以更有效地优化一个与SNE和拉普拉斯特征映射都相关的模型。

