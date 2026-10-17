
4. 对于测试集中的每个点 $x_{q}$，在训练集中找到 $K$ 个最近邻。

(5) 返回

$$\hat{f}(x_{q}) \leftarrow \arg \max _{c \in C} \sum_{i=1}^{K} \delta\left(c, f\left(x_{i}\right)\right)$$

其中 $\hat{f}\left(x_{q}\right)$ 是样本 $x_{q}$ 的类别 $f\left(x_{q}\right)$ 的估计值。FMKNN 算法的一个改进是赋予 $K$ 个近邻加权贡献，距离最近的近邻被赋予更大的值（样本距离越近，相似度越高，贡献越大）。通常通过每个近邻距离的倒数进行加权：

$$
\begin{gathered}\hat{f}\left(x_{q}\right) \leftarrow \arg \max _{c \in C} \sum_{i=1}^{K} w_{i} \delta\left(c, f\left(x_{i}\right)\right), \\ w_{i}=\frac{1}{d_{F i n s l e r}\left(x_{i}, x_{q}\right)} .\end{gathered} \tag{13.21}
$$

用 (13.21) 替换 FMKNN 算法中的步骤 (5)，可以减少噪声数据对算法性能的影响，从而提高算法的鲁棒性。

### 13.2.3 实验结果与分析

在本实验中，我们比较了 KNN、加权 KNN、FMKNN 和加权 FMKNN 算法的分类性能。我们使用 MATLAB 7.1 来实现这些算法。平台为 Windows 7，并采用 UCI 数据集中的 Wine [17] 和 Waveform [18] 数据集。由于 Waveform 数据集相对较大，实验中从 Waveform 中随机选取了 1000 个样本。实验结果如表 13.1、表 13.2、图 13.1 和图 13.2 所示。

从 Wine 数据集的结果可以看出，FMKNN 算法的分类性能优于 KNN 和加权 KNN 算法。

**表 13.1**：在 Wine 数据集中，当 $K$ 取不同值时各算法的分类性能。

| K | KNN | 加权 KNN | FMKNN | 加权 FMKNN |
| :--- | :---: | :---: | :---: | :---: |
| K=1 | 77.65 | 77.65 | 95.88 | 95.88 |
| K=3 | 72.35 | 77.06 | 95.29 | 94.71 |
| K=5 | 71.18 | 78.24 | 95.88 | 95.29 |
| K=7 | 68.24 | 75.88 | 95.88 | 95.29 |
| K=9 | 73.53 | 76.47 | 95.29 | 94.71 |
| K=11 | 71.18 | 76.47 | 95.29 | 94.71 |
| K=13 | 71.18 | 77.06 | 95.88 | 95.29 |
| K=15 | 69.41 | 76.47 | 95.29 | 95.29 |

**表 13.2**：在 Waveform 数据集中，当 $K$ 取不同值时各算法的分类性能。

| K | KNN | 加权 KNN | FMKNN | 加权 FMKNN |
| :--- | :---: | :---: | :---: | :---: |
| K=1 | 86.6 | 86.6 | 89.9 | 89.9 |
| K=3 | 89.1 | 89.1 | 91.2 | 91.4 |
| K=5 | 89.5 | 89.5 | 91.8 | 91.8 |
| K=7 | 90.1 | 90.1 | 91.3 | 91.4 |
| K=9 | 91.1 | 91.1 | 91.5 | 91.7 |
| K=11 | 91.5 | 91.5 | 92.0 | 91.8 |
| K=13 | 90.8 | 90.8 | 92.2 | 91.6 |
| K=15 | 91.3 | 91.2 | 92.2 | 91.8 |

![](img/456a7a56403cbb2b5f1a261793529a51_406_0.png)

**图 13.1**：各算法在 Wine 数据集上的分类性能。

然而，由于 Finsler 度量中的参数设置，FMKNN 在加权后并未提升分类性能。在本实验中，FMKNN 算法中的常数 $t$ 取较大的值 1000。因此，在加权过程中，加权值会较小，加权效果未必好。从 Waveform 数据集的结果来看，我们仍然可以看出 FMKNN 算法的分类性能优于 KNN 和加权 KNN。然而，FMKNN 和加权 FMKNN 之间没有明显的关联，这与 Wine 数据集中的实验效果相近。

![](img/456a7a56403cbb2b5f1a261793529a51_407_0.png)

**图 13.2**：各算法在 Waveform 数据集上的分类性能。

实验结果表明，引入 Finsler 度量可以提高算法的分类性能。FMKNN 存在一些不足之处。我们在选择 Finsler 度量函数时使用 LDA 的投影向量。因此，在计算 Finsler 度量时，FMKNN 算法仅在 LDA 效果较好的数据集上能取得更好的结果。因此，如何选择更具通用性的 Finsler 度量函数将是我们后续工作的重点。

## 13.3 基于 Finsler 度量的几何学习算法

近年来，许多研究人员改进了经典的流形学习算法。监督流形学习算法通过利用样本的标签信息，旨在减小类内差异并增大类间差异。在本节中，我们介绍 Finsler 度量，并给出一种基于 Finsler 度量的几何学习算法，该算法利用样本的类别标签。该算法是一种监督学习算法，能够处理多流形结构数据。首先，简要介绍监督流形学习算法；然后，给出基于 Finsler 度量的几何学习算法。

### 13.3.1 监督流形学习算法

许多研究人员开发了经典流形学习算法（即 ISOMAP、LLE 和 LE 算法）的改进版本，并给出了相应的监督学习算法，即监督等距特征映射（S-ISOMAP）[19]、监督局部线性嵌入（S-LLE）[20] 以及监督拉普拉斯特征映射（S-LE）[21]。本节简要介绍这些监督流形学习算法。

#### 13.3.1.1 S-ISOMAP

S-ISOMAP 是 ISOMAP 算法的监督学习版本。其主要思想是利用样本的类别信息来改进样本间距离的公式。公式如下：

$$
D \left(x_{i}, x_{j}\right)= \left\{ \begin{aligned} \sqrt{1-e^{\frac{-d^{2}\left(x_{i}, x_{j}\right)}{\beta}}} & \quad y_{i}=y_{j} \\ e^{\frac{d^{2}\left(x_{i}, x_{j}\right)}{\beta}}-\alpha & \quad y_{i} \neq y_{j} \end{aligned} \right. \quad(13.22)
$$

其中 $d\left(x_{i}, x_{j}\right)$ 表示样本 $x_{i}$ 和 $x_{j}$ 之间的欧氏距离，$y_{i}$ 和 $y_{j}$ 分别表示 $x_{i}$ 和 $x_{j}$ 的类别标签，$\alpha$、$\beta$ 为待定参数。$\alpha$ 通常取 $(0,1)$ 范围内的常数值，而 $\beta$ 取数据集中所有样本点欧氏距离的平均值。通过 (13.22) 可以减小同类样本间的距离并增大不同类样本间的距离。这种方法可以减少噪声干扰。根据 ISOMAP 的基本思想降低数据维度。首先，根据 KNN 算法构建邻接图。然后，使用 Floyd 最短路径算法寻找任意样本点之间的最短路径，并由最短路径构建邻接矩阵 $M$。最后，采用 MDS 算法根据 $M$ 矩阵降维。

#### 13.3.1.2 S-LLE

S-LLE 是 LLE 算法的监督学习版本。其主要思想是根据样本的类别信息修改样本间的距离公式，从而改变样本的近邻，进而影响数据集最终的低维表示。样本间距离的改进公式如下：

$$
\begin{aligned} & \Delta^{\prime}=\Delta+\alpha \max \left(\Delta\right) \Delta \\ & \Lambda_{i j}= \begin{cases} 0 & y_{i}=y_{j} \\ 1 & y_{i} \neq y_{j} \end{cases} \quad(13.23) \end{aligned}
$$

其中 $\Delta$ 是样本点间欧氏距离矩阵，$\alpha$ 是 $(0, 1)$ 范围内的常数。经过 (13.23) 变换后，同类样本间的距离不变，但不同类数据间的距离增加，从而在寻找近邻时能获得更多相似的数据。找到 $\Delta'$ 后，可以通过 $\Delta'$ 找到 LLE 的 $K$ 个近邻，并利用算法的基本框架获得数据集的低维表示。

#### 13.3.1.3 S-LE

S-LE 是 LE 算法的监督学习版本。其主要思想是先求解相似数据集合的近邻集和不同类数据集合的邻域集。

$$
AS(x_i) = \frac{1}{N} \sum_{j=1}^{N} \exp \left(-\frac{\|x_i - x_j\|^2}{\beta}\right) \quad (13.24)
$$

$$
N_w(x_i) = \left\{ x_j \middle| y_i = y_j, \exp \left(-\frac{\|x_i - x_j\|^2}{\beta}\right) > AS(x_i) \right\} \quad (13.25)
$$

$$
N_b(x_i) = \left\{ x_j \middle| y_i \neq y_j, \exp \left(-\frac{\|x_i - x_j\|^2}{\beta}\right) > AS(x_i) \right\} \quad . (13.26)
$$

然后，根据这两个邻集得到两个邻接矩阵，并得到两个优化函数如下：

$$
W_{w,ij} = \begin{cases} \exp \left(-\frac{\|x_i-x_j\|^2}{\beta}\right) & \text{if } x_j \in N_w(x_i) \text{ or } x_i \in N_w(x_j) \\ 0 & \text{otherwise} \end{cases} \quad (13.27)
$$

$$
W_{b,ij} = \begin{cases} 1 & \text{if } x_j \in N_b(x_i) \text{ or } x_i \in N_b(x_j) \\ 0 & \text{otherwise} . \end{cases} \quad (13.28)
$$

设 $x_i'$ 为 $x_i$ 的低维表示。那么，对于每个样本点，都有一个目标函数

$$
\min \frac{1}{2} \sum_{i,j} \|x_i' - x_j'\|^2 W_{w,ij} \quad (13.29)
$$

$$
\max \frac{1}{2} \sum_{i,j} \|x_i' - x_j'\|^2 W_{b,ij} \quad . (13.30)
$$

设 $Z = [x_1'$, $\dots$, $x_N']^T$。那么，目标函数 (13.29)、(13.30) 可以重写为

$$
\min \text{ tr } (Z^T L_w Z) \quad (13.31)
$$

$$
\max \text{ tr } (Z^T L_b Z) \quad (13.32)
$$

其中 $L_w = D_w - W_w$，$L_b = D_b - W_b$。通过利用约束条件 $Z^T D_w Z = I$，目标函数 (13.31) 和 (13.32) 可以合并为目标函数

$$\underset{Z}{\operatorname{argmax}} \left\{y \operatorname{tr}\left(Z^T L_b Z\right) + (1-y) \operatorname{tr}\left(Z^T W_w Z\right) \right\} \quad \text{s.t.} \quad Z^T D_w Z = I \quad (13.33)$$

其中 $y \in [0, 1]$ 是一个常数。令 $B = yL_b + (1 - y) W_w$。目标函数 (13.33) 可以写为

$$\underset{Z}{\operatorname{argmax}} \operatorname{tr}\left(Z^T B Z\right) \quad \text{s.t.} \quad Z^T D_w Z = I \ . \quad (13.34)$$

求解 (13.34) 的过程即为求解特征方程的过程：

$$Bz = \lambda D_w z \ . \quad (13.35)$$

特征方程 (13.35) 最大的 $d$ 个特征值对应的特征向量为 $z_1, z_2, \ldots, z_d$，且 $Z = [z_1, z_2, \ldots, z_d]$ 即为数据集的低维嵌入。

## 13.3.2 Finsler 几何学习算法

假设数据集是有类别的，且已知训练数据的类别信息。首先，根据训练数据的分类信息对数据集进行划分。设数据集为 $S$。数据集的一个划分为 $S_1, S_2, \ldots S_n$。假设每个划分 $S_i, 1 \le i \le n$ 具有单一的流形结构，则可以使用现有的经典流形学习算法进行降维。在找到划分集的低维表示后，我们需要给出划分集合并的方法。$S_i$ 的中心点为 $p_i$，计算任意两个中心点之间的 Finsler 距离以形成距离矩阵 $M$，$M_{ij} = d_{\text{Finsler}}(p_i, p_j)$。然后，通过对距离矩阵应用 MDS 算法获得中心点的低维表示。最后，对每个划分集 $S_i$ 的低维表示以及中心点的低维表示进行旋转和平移，并保持划分数据集之间的几何结构关系，从而得到整个数据集的低维表示。

由于训练数据集具有自身的类别信息，因此很容易对训练数据集进行划分。只要将同一类数据归类到同一组数据中，就能实现划分的目的。然而，对于测试数据集，我们并没有类别信息，测试数据的划分需要一定的操作。本文采用基于中心点的数据集划分方法来分类测试数据，该方法是先计算数据的训练数据中心，然后将测试样本划分到与其类别对应的最近中心点。

对于测试数据点 $p$，它属于集合 $C_p$。然后，$C_p = S_i$，$i = \arg \min d(p, p_i)$。这里，$d$ 是欧氏距离。

下面给出一种基于中心点的数据集划分方法。参见算法 13.1。

### 算法 13.1：基于中心点的数据集划分

**输入：** 训练数据集 $X_{\text{tr}} = \{\mathbf{x}_{\text{tr}1}, \mathbf{x}_{\text{tr}2}, \ldots, \mathbf{x}_{\text{tr}N} \in R^D\}$，训练数据集标签 $Y_{\text{tr}} = \{y_{\text{tr}1}, y_{\text{tr}2}, \ldots, y_{\text{tr}N} \in \mathbb{R}\}$，测试数据集 $X_{\text{tst}} = \{\mathbf{x}_{\text{tst}1}, \mathbf{x}_{\text{tst}2}, \ldots, \mathbf{x}_{\text{tst}M} \in R^D\}$

**输出：** 整个数据集的划分 $S_1, S_2, \ldots, S_n$，其中 $n$ 为数据类别的数量

1. 查找数据集的类别总数

$$T = \text{distinct}\{Y_{\text{tr}}\}$$

$$n = |T|$$

2. 初始化 $S_i = \varnothing, 1 \le i \le n$。设 $T = \{T_1, T_2, \ldots, T_n\}$。

3. 划分训练数据集

$$S_i \leftarrow S_i \cup \mathbf{x}_{\text{tr}j}, y_{\text{tr}j} = T_i, 1 \le j \le N$$

4. 查找训练数据集中每个类别的数据中心点

$$m_i = \frac{\sum_{S_{ij} \in S_i} S_{ij}}{|S_i|}$$

5. 划分测试数据集

$$S_i \leftarrow S_i \cup \mathbf{x}_{\text{tst}j}, i = \underset{1 \le i \le n}{\operatorname{arg} \min} d(\boldsymbol{\rho}_i, \mathbf{x}_{\text{tst}j}), 1 \le j \le M$$

6. 输出划分集 $S_1, S_2, \ldots, S_n$

从算法 13.1 中可以看出，该算法主要关注训练数据集，然后将测试数据集划分到最近的集合中。

算法 13.1 可以视为一个简单的分类过程，它划分整个数据集并为后续的数据处理做准备。

对于已经划分好的数据集，我们假设单个集合 $S_i, 1 \le i \le n$ 具有单一的流形结构。基于上述假设，我们可以使用经典算法来降维。在本文中，我们采用 LLE 算法进行降维。对于整个数据集，我们将使用 LLE 算法对由算法 13.1 划分出的集合 $S_1, S_2, \ldots, S_n$ 进行降维。然后，根据数据集构建邻接图，并使用 Finsler 度量来测量距离。

### 算法 13.2：数据中心点降维算法
