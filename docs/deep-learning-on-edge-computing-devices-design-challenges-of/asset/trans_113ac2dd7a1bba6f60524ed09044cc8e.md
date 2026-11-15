

![](img/5fa4874adaccc5ede04575a2e9e5662a_86_0.png)

**图 5.1** 脑启发的细胞二进制神经网络（CBN-Net）示意图，该网络由多个二进制子网络单元组成。不同子网络单元之间通过可学习的稀疏全球侧向连接相连。

关于 BNNs 的研究。为降低量化误差，XNOR-Net [10] 提出引入通道缩放因子，而 DoReFa-Net [14] 则使用层缩放因子。Bireal-Net [15] 提出在 BNNs 中插入固定快捷连接。环形 BNN [16] 提出了一种卷积核多样性更高的循环卷积，增强了 BNNs 的表征能力。此外，ABC-Net [11]、BENN [13] 和 Group-Net [12] 均利用多个二进制基础模块或模型，以牺牲计算效率为代价提高分类精度。综上所述，二进制神经网络的性能逐渐提升；然而，由于模型容量降低，BNNs 与高精度深度神经网络 [17] 之间仍存在显著的性能差距。

在本章中，我们提出了一种旨在探索 BNN 最优网络结构以提高分类精度的另一种策略。如图 5.1 所示，所提出的细胞二进制神经网络（CBN-Net）具有三个受人脑启发的特性。首先，与由多个子网络 [18] 组成的人类视觉神经网络类似，CBN-Net 也是一种由多个子网络单元组成的层次网络。其次，研究表明，大脑皮层中不同的神经子网络由稀疏的全球侧向树突连接 [19]。同样，CBN-Net 的不同子网络通过按源神经元不同层分组的稀疏全球侧向连接相连。第三，与现有的具有固定网络结构的 BNNs 不同，CBN-Net 中侧向连接的结构如同人脑一样是可学习的 [20]。（参见图 5.2。）

![](img/5fa4874adaccc5ede04575a2e9e5662a_87_0.png)

**图 5.2** 所提 CBN-Net 的一个玩具示例，由两个具有二进制权重和激活值的前馈子网络单元组成。假设不同子网络间水平层之间的通道全局连接为组稀疏，因此只有小比例的层和神经元通道在侧向连接。虚线表示已移除的稀疏连接。

## 5.2 二进制神经网络基础

对于大多数二进制神经网络，卷积层中的权重和输入使用 sign 函数进行二值化。我们将卷积滤波器表示为 \(\mathbf{W} \in \mathbb{R}^{c_{out} \times c_{in} \times r \times r}\)，其中 \(c_{out}\) 是滤波器数量，\(c_{in}\) 是输入通道数，\(r\) 是滤波器大小。权重二值化过程为 \(\mathbf{B}_w = \text{sign}(\mathbf{W})\)，其中 \(\mathbf{B}_w \in \{+1, -1\}^{c_{out} \times c_{in} \times r \times r}\) 表示二进制权重，\(\text{sign}(\cdot)\) 对正输入生成 \(+1\)，对负输入生成 \(-1\)。为了将卷积神经网络约束为具有二进制权重，我们使用二值滤波器 \(\mathbf{B}_w\) 和缩放因子 \(\alpha \in \mathbb{R}\) 来估计实值权重滤波器 \(\mathbf{W}\)，使得 \(\mathbf{W} \approx \alpha \mathbf{B}_w\)。\(\mathbf{X}\) 和 \(\mathbf{W}\) 的卷积操作 (*) 可近似为

\(\mathbf{X} * \mathbf{W} \approx (\mathbf{X} \oplus \mathbf{B}_w)\alpha, \tag{5.1}\)

其中 \(\oplus\) 表示不含任何乘法的卷积。由于权重值为二进制，我们可以通过加法和减法实现卷积。与单精度滤波器相比，二进制权重滤波器将内存使用量降低了 \(32\times\)。为估计二进制权重 \(\mathbf{B}_w\)，我们假设 \(\mathbf{W}\) 和 \(\mathbf{B}_w\) 是 \(\mathbb{R}^n\) 中的向量，其中 \(n = c \times r \times r\)。为寻找 \(\mathbf{W} \approx \alpha \mathbf{B}_w\) 的最优估计，我们求解以下优化问题：

$$\mathcal{L}(\mathbf{B}_w, \alpha) = ||\mathbf{W} - \alpha \mathbf{B}_w||^2,\quad \alpha^*, \mathbf{B}_w^* = \arg \min_{\alpha, \mathbf{B}_w} \mathcal{L}(\mathbf{B}_w, \alpha).$$ (5.2)

展开 Eq. (5.2)，得到以下方程：

$$\mathcal{L}(\mathbf{B}_w, \alpha) = \alpha^2 \mathbf{B}_w^T \mathbf{B}_w - 2\alpha \mathbf{W}^T \mathbf{B}_w + \mathbf{W}^T \mathbf{W}.$$ (5.3)

由于 \(\mathbf{B}_w \in \{+1, -1\}^n\)，\(\mathbf{B}_w^T \mathbf{B}_w = n\) 是常数，而 \(\mathbf{W}^T \mathbf{W}\) 也是常数，因为 \(\mathbf{W}\) 是已知变量。令 \(c = \mathbf{W}^T \mathbf{W}\)。现在我们可以将 Eq. (5.3) 改写为 \(\mathcal{L}(\mathbf{B}_w, \alpha) = \alpha^2 n - 2\alpha \mathbf{W}^T \mathbf{B}_w + c\)。\(\mathbf{B}_w\) 的最优解可通过最大化以下受约束优化问题得到（注意，Eq. (5.2) 中 \(\alpha\) 为正值，因此在最大化时可忽略）：

$$\mathbf{B}_w^* = \arg \max_{\mathbf{B}_w} \{ \mathbf{W}^T \mathbf{B}_w \} \quad \text{s.t. } \mathbf{B}_w \in \{+1, -1\}^n.$$ (5.4)

该优化问题可通过令 \(W_i \ge 0\) 时 \(\mathbf{B}_i = +1\)、\(W_i < 0\) 时 \(\mathbf{B}_i = -1\) 来求解，因此最优解为 \(\mathbf{B}_w^* = \text{sign}(\mathbf{W})\)。为求缩放因子 \(\alpha^*\) 的最优值，我们对 \(\mathcal{L}\) 关于 \(\alpha\) 求导并令其为零：

$$\alpha^* = \frac{\mathbf{W}^T \mathbf{B}_w^*}{n}.$$ (5.5)

将 \(\mathbf{B}_w^*\) 替换为 \(\text{sign}(\mathbf{W})\)，得到

$$\alpha^* = \frac{\mathbf{W}^T \text{sign}(\mathbf{W})}{n} = \frac{\sum |\mathbf{W}_i|}{n} = \frac{1}{n} ||\mathbf{W}||_1,$$ (5.6)

因此，二进制权重滤波器的最优估计可通过对权重值取符号简单实现。最优缩放因子为权重绝对值的平均值。

同一卷积层的输入特征图由 \(\mathbf{X} \in \mathbb{R}^{c_{in} \times h \times m}\) 表示，其中 \(c_{in}\) 是输入通道数，\(h\) 和 \(m\) 分别为特征图的高度和宽度。我们可以以类似方式对输入 \(\mathbf{X}\) 进行二值化，得到由 \(\mathbf{B}_x = \text{sign}(\mathbf{X})\) 表示的二值特征图。现在，我们拥有二进制权重和激活值，因此浮点运算可被高效的逻辑运算取代，即 XNOR-POPCOUNT 操作 $\otimes$ [10]:

$\mathbf{Y} = \alpha(\mathbf{B}_w \otimes \mathbf{B}_x),$

其中 $\mathbf{Y} \in \mathbb{R}^{c_{out} \times h \times m}$ 为二进制卷积层的输出，$\alpha$ 为缩放因子。在训练过程中，我们可以采用一种称为直通估计器（Straight Through Estimator, STE）的广泛使用的方法，通过 sign 函数反向传播梯度，如下所示：

$\frac{\partial \mathcal{L}}{\partial \mathbf{W}} \approx \text{clip}\left( \frac{\partial \mathcal{L}}{\partial \mathbf{B}_w}, -1, +1 \right),$

其中 clip 是分段线性函数 [21]，\(\mathcal{L}\) 是二进制神经网络的总损失函数，\(\mathbf{W}\) 在训练中作为待优化的隐式权重使用。

## 5.3 带侧向连接的细胞二进制神经网络

在本节中，我们详细介绍带侧向连接的细胞二进制神经网络，包括细胞二进制神经网络、组稀疏正则化、损失函数及训练过程。

### 5.3.1 细胞二进制神经网络

如图 5.3 所示，二进制神经网络的结构从使用单一流水线 [7] 演变为采用并行集成流水线 [13] 以实现更准确的分类。作为演化的第三步，所提 CBN-Net 试图探索连接不同子网络单元的最优侧向结构，以进一步提高二进制神经网络的分类精度。

形式上，CBN-Net 由多个二进制子网络组成，上标 $i$ 表示第 $i$ 个二进制子网络，上标 $j$ 表示第 $j$ 个二进制子网络，上标 $k$ 表示第 $k$ 个二进制层。对于第 $i$ 个子网络，我们用 $\mathbf{X}^{(i,k)}$ 表示第 $k$ 层的输入，用 $\mathbf{Y}^{(i,k)}$ 表示输出。第 $i$ 个子网络到第 $j$ 个子网络在第 $k$ 层的侧向连接包含通道权重 $\overline{W}^{(i,j,k)} = [\overline{W}_1^{(i,j,k)}, \overline{W}_2^{(i,j,k)}, \dots, \overline{W}_{c_{out}}^{(i,j,k)}]$，其中 $c_{out}$ 是通道数。

CBN-Net 利用受大脑启发的全球侧向连接，将特征水平传输到不同子网络。第 $i$ 个

