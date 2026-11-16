

然后，算子 \(\mathbb{T}_{\mathbb{A}_2}\) 的不动点属于集合 (Reich, 1983, Lemma 1.4)

\(\mathcal{E} = \bigcap_{r=1}^R \mathcal{E}_r^{\mathsf{A}}.\) (A.9)

因此，算子 \(\mathbb{T}_{\mathbb{A}_2}$ 对应于特征值 1 的任何特征向量都必须位于子空间 \(\mathcal{E}_r^{\mathsf{A}}\) 的交集中，我们用 \(\mathcal{E}$ 表示该交集。特别是，如果满足方程 (A.3)，则元素 \(\bar{\boldsymbol{g}}$ 位于 \(\mathcal{E}$ 中，即，

\(\mathbb{T}_{\mathbb{A}_2}[\bar{\boldsymbol{g}}] = \bar{\boldsymbol{g}}, \implies \bar{\boldsymbol{g}} \in \mathcal{E}\) (A.10)

且方程 (A.4) 亦满足。

有了结果 (A.10)，我们观察到，R 阶 CLM 正则性的一个充要条件是空间 \(\mathcal{E}$ 为平凡空间，即，

\(\mathcal{E} = \{ \mathbf{0} \}.\) (A.11)

在以下内容中，我们将方程 (A.11) 称为 *非奇异性条件*。在线性弹性和线性粘性材料的背景下，我们对空间 \(\mathcal{E}_r^{\mathsf{A}}\) 推导了非奇异性条件 (A.11)，使得

\(\mathcal{E}_r^{\mathsf{A}} \subset \text{Sym}(3), \forall r \in \{1, ..., R\} \text{ or } \mathcal{E}_r^{\mathsf{A}} \subset \text{Sym}_0(3), \forall r \in \{1, ..., R\}.\) (A.12)

然而，所提出的证明扩展到其他可以用方程 (A.1) 形式表述的问题，例如热弹性或压电问题 (Milton, 2002, §9)。以 CLM 作为 DMN 架构中的构建块为目标，我们有兴趣了解是否存在特定的层状方向 \(\boldsymbol{n}_r$ 和 CLM 阶数 \(R$ 的选择，使得 CLM 的有效性质始终是非奇异的，即，满足非奇异性条件 (A.11)。对于刚性纤维的不可压缩悬浮液，我们研究了具有刚性核心材料 \(m_1$ 和不可压缩包覆材料 \(m_2$ 的 CLM 的这一问题。

## A.2 具有不可压缩包覆材料和刚性核心材料的包覆层状材料

对于涉及不可压缩介质中刚性包含体的应用，我们考虑具有不可压缩包覆材料 \(m_2$ 和刚性核心材料 \(m_1$ 的 CLM。因此，空间 \(\mathcal{E}_r^A \subset \text{Sym}_0(3)$ 具有形式

\(\mathcal{E}_r^A = \{ B \in \text{Sym}_0(3) \mid B \cdot (n_r \otimes_s a) = 0,\)
\(\forall a \in \mathbb{R}^3 \text{ with } a \cdot n_r = 0 \},\) (A.13)

空间 \(\mathcal{E}_r^A$ 和 \(\text{Sym}_0(3)$ 的尺寸由以下给出

\(\text{dim}(\mathcal{E}_r^A) = 3, \text{ and } \text{dim}(\text{Sym}_0(3)) = 5.\) (A.14)

因为维度 \(\text{dim}(\mathcal{E}_1^A + \mathcal{E}_2^A)$ 被空间 \(\text{Sym}_0(3)$ 的维度所界限，使得

\(\text{dim}(\mathcal{E}_1^A + \mathcal{E}_2^A) \le 5,\) (A.15)

根据两个空间 \(\mathcal{E}_1^A$ 和 \(\mathcal{E}_2^A$ 交集的维度

\(\text{dim}(\mathcal{E}_1^A \cap \mathcal{E}_2^A) = \text{dim}(\mathcal{E}_1^A) + \text{dim}(\mathcal{E}_2^A) - \text{dim}(\mathcal{E}_1^A + \mathcal{E}_2^A),\) (A.16)

可得

\(\text{dim}(\mathcal{E}_1^A \cap \mathcal{E}_2^A) \ge 3 + 3 - 5 = 1.\) (A.17)

换句话说，空间 \(\mathcal{E}_1^A$ 和 \(\mathcal{E}_2^A$ 的交集至少为一维。因此，两个层状方向不足以满足条件 (A.11)。除了所需的层数之外，我们还想知道层状方向之间的角度是否存在限制。假设一个层状方向与另外两个方向正交。我们讨论方向 \(\boldsymbol{n}_3$ 与法向量 \(\boldsymbol{n}_1$ 和 \(\boldsymbol{n}_2$ 正交的情况。其他情况通过变换索引类似处理。此时有

\(\boldsymbol{n}_3 \cdot \boldsymbol{n}_1 = 0, \quad \text{and} \quad \boldsymbol{n}_3 \cdot \boldsymbol{n}_2 = 0,\) (A.18)

且交集 \(\mathcal{E}_1^{\text{A}} \cap \mathcal{E}_2^{\text{A}} \cap \mathcal{E}_3^{\text{A}}$ 不仅包含零元素 \(\mathbf{0}$。因此，条件 (A.11) 被违反。为证明这一点，我们考虑空间 \(\mathcal{E}_r^{\text{A}}$ 的替代描述

\(\mathcal{E}_r^{\text{A}} = \{ \boldsymbol{B} \in \text{Sym}_0(3) \mid \boldsymbol{B}\boldsymbol{n}_r = \alpha \boldsymbol{n}_r \quad \text{for some} \quad \alpha \in \mathbb{R} \}\) (A.19)

这与方程 (A.13) 等价，并通过所有具有层状方向 \(\boldsymbol{n}_r$ 作为特征向量的张量 \(\boldsymbol{B} \in \mathcal{E}_r^{\text{A}}$ 来表征空间 \(\mathcal{E}_r^{\text{A}}\)。那么张量

\(\boldsymbol{B} = \boldsymbol{n}_1 \otimes \boldsymbol{n}_1 + \boldsymbol{m}_2 \otimes \boldsymbol{m}_2 - 2\boldsymbol{n}_3 \otimes \boldsymbol{n}_3,\) (A.20)

其中层状方向 \(\boldsymbol{m}_2$ 通过正交化构造，使得

\(\boldsymbol{m}_2 = \boldsymbol{n}_2 - (\boldsymbol{n}_1 \cdot \boldsymbol{n}_2)\boldsymbol{n}_1,\) (A.21)

是交集 \(\mathcal{E}_1^{\text{A}} \cap \mathcal{E}_2^{\text{A}} \cap \mathcal{E}_3^{\text{A}}$ 的一个元素。这是因为

\(\text{tr}(\boldsymbol{B}) = 0, \boldsymbol{B}\boldsymbol{n}_1 = \boldsymbol{n}_1, \quad \boldsymbol{B}\boldsymbol{n}_2 = \boldsymbol{n}_2, \quad \boldsymbol{B}\boldsymbol{n}_3 = \boldsymbol{n}_3,\) (A.22)

因此条件 (A.11) 被违反。换句话说，具有不可压缩包覆材料和刚性核心材料的三阶 CLM 的有效性质 \(\bar{\mathbb{A}}$，其中一个层状方向 \(\boldsymbol{n}_3$ 与另外两个层状方向 \(\boldsymbol{n}_1$ 和 \(\boldsymbol{n}_2$ 正交，总是奇异的。特别是，如果所有三个层状方向相互正交，则三阶 CLM 的有效性质 \(\bar{\mathbb{A}}$ 是奇异的。

相比之下，设三个层状方向相互非正交且相互非共线，即，

\(0 < |\boldsymbol{n}_1 \cdot \boldsymbol{n}_2| < 1, \quad 0 < |\boldsymbol{n}_1 \cdot \boldsymbol{n}_3| < 1, \quad 0 < |\boldsymbol{n}_2 \cdot \boldsymbol{n}_3| < 1.\) (A.23)

我们考虑交集 \(\mathcal{E}_1^{\text{A}} \cap \mathcal{E}_2^{\text{A}} \cap \mathcal{E}_3^{\text{A}}$ 中的一个元素 \(\boldsymbol{B}$，并希望证明张量 \(\boldsymbol{B}$ 消失，从而满足非奇异性条件 (A.11)。因为张量 \(\boldsymbol{B}$ 是对称的，其对应于不同特征值的特征向量相互正交。因此，如果特征值互异，则层状方向需要相互正交。然而，这与我们的假设 (A.23) 矛盾。因此，张量 \(\boldsymbol{B}$ 具有一个特征值 \(\alpha$ 及其对应的特征空间 \(\mathbb{R}^3$，即，张量 \(\boldsymbol{B}$ 具有形式

\(\boldsymbol{B} = \alpha \boldsymbol{I}, \quad \alpha \in \mathbb{R}.\) (A.24)

此外，因为张量 \(\boldsymbol{B}$ 的迹消失，即 \(\text{tr}(\boldsymbol{B}) = 0$，可得特征值 \(\alpha$ 为零。因此，张量 \(\boldsymbol{B}$ 必须消失，非奇异性条件 (A.11) 得以满足，并且具有不可压缩包覆材料 \(m_2$ 和刚性核心材料 \(m_1$ 的三阶 CLM 的有效性质 \(\bar{\mathbb{A}}$ 是非奇异的，前提是三个层状方向相互非正交且非共线。

## 参考文献

Advani, S. G., Tucker III, C. L., 1987. 使用张量描述和预测短纤维复合材料中的纤维取向. Journal of Rheology 31 (8), 751–784.

Armijo, L., 1966. 具有利普希茨连续一阶偏导数的函数的最小化. Pacific Journal of Mathematics 16 (1), 1–3.

Ashwin, N. R., Cao, Z., Muralidhar, N., Tafti, D., Karpatne, A., 2022. 预测致密颗粒悬浮液中流体力的深度学习方法. Powder Technology 401, 117303.

Ashwin, N. R., Tafti, D., Muralidhar, N., Cao, Z., 2024. 致密椭球颗粒悬浮液中流动和力预测的物理信息深度学习. Powder Technology 439, 119684.

Balboa Usabiaga, F., Kallemov, B., Delmotte, B., Bhalla, A., Griffith, B., Donev, A., 2017. 被动和主动刚性颗粒悬浮液的流体力学：一种刚性多团块方法. Communications in Applied Mathematics and Computational Science 11 (2), 217–296.

Barzilai, J., Borwein, J. M., 1988. 两点步长梯度方法. IMA Journal of Numerical Analysis 8 (1), 141–148.

BASF, 2020. Ultramid®B3K 聚酰胺 6 材料数据. https://www.campusplastics.com/campus/de/datasheet/Ultramid%C2%AE+B3K/BASF/20/3a22f000, 访问日期: 2020-09-26.

Batchelor, G., 1970. 无力颗粒悬浮液中的应力系统. Journal of Fluid Mechanics 41 (3), 545–570.

