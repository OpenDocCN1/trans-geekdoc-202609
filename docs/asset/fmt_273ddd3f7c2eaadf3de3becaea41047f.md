
- [11] Cai XY, Dai GZ, Yang LB, et al. 谱聚类算法综述. 计算机科学, 2008, 35(7), 14-18.

- [12] Malik J, Belongie S, Leung T, et al. 用于图像分割的轮廓和纹理分析. 国际计算机视觉期刊, 2001, 43(1), 7-27.

- [13] Thierry D, Lambertus H. 使用超流线可视化二阶张量场. IEEE 计算机图形学与应用, 1993, 13(4), 25-33.

- [14] Jebara T, Schogolev V. 用于谱聚类的 B-匹配. 欧洲机器学习会议. 施普林格出版, 2006, 679-686.

- [15] Fischer B, Buhmann JM. 用于光滑曲线分组和纹理分割的路径基聚类. 模式分析与机器学习汇刊, IEEE 汇刊, 2003, 25(4), 513-518.

- [16] Li XL. 基于张量场的数据降维方法研究与应用. 硕士学位论文, 中国苏州, 苏州大学, 2010.

- [17] Zhou D, Bousquet O, Lal TN, et al. Scholkopf: 具有局部和全局一致性的学习. 神经信息处理系统进展, 2004, 16, 321-328.

- [18] Zelnik-Manor L, Perona P. 自调谱聚类. 神经信息处理系统进展, 2004, 1601-1608.

- [19] Fischer I, Poland J. 放大谱聚类的块矩阵结构. Idsia, 2005, 21-28.

- [20] Brand M, Huang K. 谱嵌入与聚类的统一定理 [J]. Ai & Stats, 2003.

- [21] Xiang T, Gong S. 基于特征向量选择的谱聚类. 模式识别, 2008, 41(3), 1012–1029.

- [22] Xu SL, et al. 谱理论与等谱问题，曲率与拓扑不变量：现代微分几何. 中国科学技术大学出版社, 2009.

- [23] Chan PK, Schleg MDF, Zien JY. 谱 K-路比例割划分与聚类, 1994, 13(9), 1088–1096.

- [24] Luxburg U. 谱聚类教程. Kluwer 学术出版社, 2007.

- [25] Rathi Y, Tannenbaum A, Michailovich O. 张量流形上的图像分割. IEEE 计算机视觉与模式识别会议. IEEE, 2007, 1–8.

- [26] He XF, Niyogi P. 局部保持投影. 神经信息处理系统进展, 2004, 16(1), 186–197.

- [27] Zhang L, Qiao L, Chen S. 图优化局部保持投影. 模式识别, 2010, 43(6), 1993–2002.

- [28] Qiao L, Chen S, Tan X. 应用于人脸识别的稀疏保持投影. 模式识别, 2010, 43(1), 331–341.

- [29] Guo YF, Li SJ, Yang JY, et al. 基于广义 Fisher 判别准则的广义 Foley-Sammon 变换及其在人脸识别中的应用. 模式识别快报, 2003, 24(1–3): 147–158.

- [30] Wang H, Yan S, Xu D, et al. 降维中的迹比与比迹. IEEE 计算机视觉与模式识别会议. IEEE 计算机协会, 2007, 1–8.

- [31] Jia Y, Nie F, Zhang C. 重访迹比问题. IEEE 神经网络汇刊, 2009, 20(4), 729–735.

- [32] Fan RKC. 谱图理论. 由美国数学学会数学科学会议委员会出版, 1997.

- [33] Kent JT, Mardia KV, McDonnell P. 复 Bingham 四次分布与形状分析. 皇家统计学会期刊, 2010, 68(5), 747–765.

- [34] Jupp PE, Mardia KV. 矩阵 Von Mises-Fisher 和 Bingham 分布的最大似然估计量. 统计学年鉴, 1979, 7(3), 599–606.

- [35] Mardia KV. 方向统计与形状分析. 应用统计期刊, 1999, 26(8), 949–957.

# 13 芬斯勒几何学习

芬斯勒几何是黎曼几何的超集，其度量具有更一般的形式，不受二次限制。本章主要介绍芬斯勒几何的相关知识和芬斯勒几何学习算法。

## 13.1 基本概念

### 13.1.1 黎曼流形

设 $M$ 是一个 $m$ 维光滑流形，$G$ 是 $M$ 上的对称二阶共变张量场。若 $(U, u^i)$ 是 $M$ 的一个局部坐标系，则 $U$ 上的张量场 $G$ 可以表示为

$$G = g_{ij} du^i \otimes du^j \quad (13.1)$$

其中 $g_{ij} = g_{ji}$ 是 $U$ 上的光滑函数。$G$ 在每一点 $p \in M$ 处给 $T_p(M)$ 赋予一个双线性函数。

假设

$$X = X^i \frac{\partial}{\partial u^i}, \quad Y = Y^i \frac{\partial}{\partial u^i}$$

令

$$G(X, Y) = g_{ij} X^i Y^j \quad (13.2)$$

我们称张量 $G$ 在点 $p$ 处是非退化的。如果存在向量 $X \in T_p(M)$ 使得对所有 $Y \in T_p(M)$ 都有 $G(X, Y) = 0$，则必须有 $\det(g_{ij}(p)) \neq 0$。换句话说，$G$ 在 $p$ 处非退化的充要条件是线性方程组

$$g_{ij}(p) X^i = 0, \quad 1 \leq j \leq m$$

仅有零解，即 $\det(g_{ij}(p)) \neq 0$。

### 13.1.2 芬斯勒几何

从上一节可以看到，黎曼几何是基于正定二阶微分形式的度量几何

$$G = ds^2 = g_{ij}(u)du^i \otimes du^j \ .$$

其中 $u^{i}$ 是局部坐标，$g_{ij} = g_{ji}$ 是流形上的光滑函数。

在本节中，我们考虑一种更一般的情况，即度量形式不受二次限制。假设

$$ds = F\left(u^{1}, \ldots, u^{m}; du^{1}, \ldots, du^{m}\right) \tag{13.4}$$

其中 $F(x;y)$ 是具有 $2m$ 个独立变量的非负光滑函数，当 $y=0$ 时称为芬斯勒函数。$F(x;y)$ 还要求关于独立变量 $y$ 是一阶齐次函数，即

$$F\left(x^{1}, \ldots, x^{m}; \lambda y^{1}, \ldots, \lambda y^{m}\right) = |\lambda| F\left(x^{1}, \ldots, x^{m}; y^{1}, \ldots, y^{m}\right), \forall \lambda \in R \ . \tag{13.5}$$

芬斯勒几何的起点是微积分的第一个概念，即计算曲线的弧长。其各种应用要求式 (13.4) 具有普适性。

**定义 13.2.** 设 $M$ 是一个 $m$ 维流形。如果其上任一曲线

$$t \mapsto \left(u^{1}(t), \ldots, u^{m}(t)\right), a \leq t \leq b$$

的长度 $s$ 由积分给出

$$s = \int_{a}^{b} F\left(u^{1}, \ldots, u^{m}; \frac{du^{1}}{dt}, \ldots, \frac{du^{m}}{dt}\right) dt \tag{13.6}$$

其中 $F$ 是具有性质 (13.4) 的函数，则称 $M$ 为芬斯勒流形 [1]。

## 13.2 基于芬斯勒度量的 KNN 算法

在本节中，我们介绍芬斯勒度量，它比黎曼度量更为一般。我们用基于芬斯勒度量 [2] 的距离度量来替换传统 K 近邻（`KNN`）[3, 4] 算法中样本点之间的距离度量，并提出了一种基于芬斯勒度量的 `KNN` 算法。实验结果表明，引入芬斯勒度量可以提高 `KNN` 算法的分类性能。

### 13.2.1 K 近邻算法

`KNN` 算法是机器学习中最为成熟的算法之一。它最初由 Cover 和 Hart 提出。它具有简单直观的优点

易于思考、实现简单、分类错误率低等。`KNN` 算法的基本思想如下。对于待分类的样本，通过投票决定其类别，依据是与其距离最近的 $K$ 个邻居的分类属性。传统 `KNN` 算法的距离度量方法主要使用待测样本与训练集之间的欧氏距离，或通过特征加权计算得出的距离。

首先，介绍传统 `KNN` 算法的基本思想。`KNN` 算法假设所有样本对应于 $n$ 维空间 $\mathbf{R}^{n}$ 中的点，并根据标准欧氏距离定义样本的最近邻。任意样本 $\mathbf{x}$ 代表特征向量 $\mathbf{x}=(x^{1}, x^{2}, \ldots, x^{m})$，其中 $x^{i}$ 代表样本 $\mathbf{x}$ 的第 $i$ 个特征值。然后，两个样本 $x_{i}$ 和 $x_{j}$ 之间的距离定义为 $d\left(x_{i}, x_{j}\right)$：

$$d\left(x_{i}, x_{j}\right)=\sqrt{\sum_{l=1}^{m}\left(x_{i}^{l}-x_{j}^{l}\right)^{2}} . \tag{13.7}$$

在最近邻学习中，目标函数可以是离散问题（分类问题）或连续问题（回归问题）。本章讨论目标函数为离散的情况，即分类问题可以描述为 $f: R^{n} \rightarrow V$，其中 $V=\left\{v_{1}, v_{2}, \ldots, v_{s}\right\}$ 对应 $s$ 个类别。`KNN` 算法的返回值 $\hat{f}\left(x_{q}\right)$ 是 $f\left(x_{q}\right)$ 的估计，即样本 $x_{q}$ 的 $K$ 个最近训练样本中最常见的 $f$ 值：

$$\hat{f}\left(x_{q}\right) \leftarrow \arg \max _{v \in V} \sum_{i=1}^{K} \delta\left(v, f\left(x_{i}\right)\right) \quad \delta(a, b)=\begin{cases}1, & \text { 若 } a=b \\ 0, & \text { 若 } a \neq b .\end{cases} \tag{13.8}$$

由于 `KNN` 算法是一种惰性学习方法，它存在许多缺点，例如分类速度慢、属性权重等因素对准确率的影响以及对样本库容量的强依赖性。许多研究人员试图改进 `KNN` 算法。主要的改进方法如下：

- 降低计算复杂度：由于每个测试样本都需要其最近的 $K$ 个邻居，每次计算都需要遍历整个训练数据集，并对计算出的距离进行排序。为了降低算法的计算复杂度，一类方法减少了训练集的规模 [5]，而另一类则使用快速算法来快速搜索 $K$ 个最近邻 [6, 7]。
- 优化相似度度量方法：基本 `KNN` 算法使用欧氏度量，该度量对噪声特征敏感。为了克服 `KNN` 算法中特征方面的缺陷，可以在度量相似性的距离公式中为特征分配不同的权重。本章采用优化相似度测度的方法，使用 Finsler 度量代替欧氏距离来改进 `KNN` 算法。
- 优化决策策略：基本 `KNN` 算法的决策规则存在明显的缺陷。当样本分布密度不均匀时，考虑最近 $K$ 个邻居的距离大小而非它们各自的距离，这可能会导致误判。因此，一种改进策略是使用距离的倒数作为样本对决策贡献的权重。

### 13.2.2 基于 Finsler 度量的 KNN 算法

Finsler 度量比 Riemann 度量更为通用。由于其定义的通用性，我们可以构造许多 Finsler 度量。许多学者研究了 Finsler 几何学，并给出了一些具有良好性质或易于计算的 Finsler 度量 [8–15]。

本节采用一类可计算的 Finsler 度量，即 ($\alpha$，$\beta$) 度量 [13, 14]。它们在 Finsler 几何学中起着至关重要的作用。设 $F = \alpha\phi(s)$，$s = \beta/\alpha$，其中 $\alpha = \sqrt{a_{ij}(x)y^{i}y^{j}}$ 是 Riemann 度量，$\beta = b_{i}(x)y^{i}$ 是非零 1 形式，$y$ 是 $x$ 的微分，且 $\phi = \phi(s)$ 定义在开区间 $(-b_{0}, b_{0})$ 上并满足

$$\phi(0) = 1, \phi(s) > 0, \phi(s) - s\phi^{\prime}(s) + (b^{2} - s^{2})\phi^{\prime\prime}(s) > 0, |s| \leq b < b_{0} \quad(13.9)$$

对于任何 $x \in M$，$F$ 是流形 $M$ 上的正定 Finsler 度量。$F$ 被称为 ($\alpha$，$\beta$) 度量。容易验证 ($\alpha$，$\beta$) 度量满足 Finsler 度量的定义如下：

设：$\alpha_{\lambda} = \alpha(x^{1}, \dots, x^{m}; \lambda y^{1}, \dots, \lambda y^{m}), \beta_{\lambda} = \beta(x^{1}, \dots, x^{m}; \lambda y^{1}, \dots, \lambda y^{m})$

$\therefore \alpha_{\lambda} = \alpha(x^{1}, \dots, x^{m}; \lambda y^{1}, \dots, \lambda y^{m}) = \sqrt{a_{ij}(x)\lambda y^{i}\lambda y^{j}} = |\lambda|\sqrt{a_{ij}(x)y^{i}y^{j}}$

$\beta_{\lambda} = \beta(x^{1}, \dots, x^{m}; \lambda y^{1}, \dots, \lambda y^{m}) = b_{i}(x)\lambda y^{i} = \lambda b_{i}(x)y^{i}$

$\therefore F(x^{1}, \dots, x^{m}; \lambda y^{1}, \dots, \lambda y^{m}) = \alpha_{\lambda}\phi(\beta_{\lambda}/\alpha_{\lambda}) = |\lambda|\sqrt{a_{ij}(x)y^{i}y^{j}}\phi\left(\frac{\lambda}{|\lambda|}\frac{\beta}{\alpha}\right)$。

因此，我们只需证明函数 $\phi$ 是偶函数且恒大于 0，即 $\phi(-s) = \phi(s)$ 且 $\phi(s) \geq 0$ 可以保证 ($\alpha$，$\beta$) 度量是 Finsler 度量。

本节使用 Finsler 度量的简洁形式。设 $F = \alpha + |\beta|$，其中 $\alpha$ 是欧氏距离，$\alpha = \sqrt{y^{i}y^{i}}$，$\beta = tw^{T}y$，$t$ 是任意常数，$w$ 是投影向量。注意，$w$ 是线性判别分析 (`LDA`) [16] 算法中的投影向量。假设 $X$ 是一个数据集，其类别设置为 $C = \{C_{1}, C_{2}, \dots, C_{s}\}$。假设 $Z = w^{T}X$。那么，投影后的类内距离 $S_{W}^{\prime}$ 和类间距离 $S_{B}^{\prime}$ 可以表示为

$$S_{W}^{\prime} = \sum_{i=1}^{s} N_{i}\left(w^{T}m_{i} - w^{T}m\right)\left(w^{T}m_{i} - w^{T}m\right)^{T}\quad(13.10)$$

![](img/456a7a56403cbb2b5f1a261793529a51_404_0.png)

其中 $m=1/s\sum_{i=1}^{s}m_{i}$，$N_{i}=\sum_{x^{j}\in C_{i}}1$，$m_{i}=1/N_{i}\sum_{x^{j}\in C_{i}}x^{j}$。投影后的类内距离 $S_{W}$ 和类间距离 $S_{B}$ 可以表示为

![](img/456a7a56403cbb2b5f1a261793529a51_404_1.png)

然后，我们有

![](img/456a7a56403cbb2b5f1a261793529a51_404_2.png)

为了使类内距离更小，类间距离尽可能大，我们可以最大化以下函数：

![](img/456a7a56403cbb2b5f1a261793529a51_404_3.png)

投影向量 $\boldsymbol{w}$ 可以表示为

![](img/456a7a56403cbb2b5f1a261793529a51_404_4.png)

因此，$\boldsymbol{w}$ 可以通过求解以下特征方程得到：

![](img/456a7a56403cbb2b5f1a261793529a51_404_5.png)

该方程最大特征值对应的特征向量即为解。因此，Finsler 度量公式可以写为

![](img/456a7a56403cbb2b5f1a261793529a51_404_6.png)

因此，数据集中两点之间的距离可以定义为

![](img/456a7a56403cbb2b5f1a261793529a51_404_7.png)

Finsler 度量 KNN (`FMKNN`) 算法的基本流程如下：

1. 设置邻居参数 `K`。
2. 根据公式 (13.18) 寻找投影向量 `w`。
3. 根据数据集构建邻域图，其中节点为所有数据样本。点之间的距离可以通过公式 (13.20) 获得。
