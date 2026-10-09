

[5] Hart PE. 凝聚最近邻规则. 信息论汇刊（IEEE Trans on Information Theory）, 1968, 14(3), 515–516.

[6] Hwang WI. 基于局部距离搜索的快速kNN分类算法. 电子学快报（Electronics Letters）, 1998, 34(21), 2062–2063.

[7] Pan JS, Qiao YL, Sun SH. 一种快速K近邻分类算法. 基础汇刊（IEEE Trans. Fundamentals）, 2004, 887–A(4), 961–963.

[8] Solange FR, Portugal R. Finsler. Finsler几何的计算机代数包. 非线性分析：理论、方法与应用（Nonlinear Analysis: Theory, Methods & Applications）, 2001, 47(9), 6121–6134.

[9] Chern SS. Finsler几何只是没有二次限制的黎曼几何. 美国数学学会通知（Notices of the American Mathematical Society）, 1996, 43(9), 959–963.

[10] Nie Z. Finsler空间中的拉普拉斯算子及其性质. 高等数学（College Mathematics）, 2004, 4(20), 52–58.

[11] Nie Z. Finsler流形的距离函数与测地球. 高等数学（College Mathematics）, 2000, 6(16), 8–12.

[12] Huang LB. Finsler流形的导航问题及其应用. 博士论文, 北京大学, 中国北京, 2008.

[13] Li BL. 关于一些重要的Finsler度量. 博士论文, 浙江大学, 中国浙江, 2007.

[14] Park HS, Lee IY. 关于具有 $(\alpha, \beta)$ -度量的射影平坦Finsler空间. 韩国数学会通讯（Communications of the Koreana Mathematical Society）, 1999, 14(2), 373–383.

[15] Yang CH, Mo XH, Shen ZM. 构造一些射影平坦的Finsler度量. 科学（中国A辑）（Science in China(Series A)）, 2006, 36(2), 121–133.

[16] Duda RO, Hart PE, Stork DG. 模式识别（第二版）. 学习Rsity统计力学, 2000.

[17] http://archive.ics.uci.edu/ml/datasets/Wine/.

[18] http://archive.ics.uci.edu/ml/datasets/Waveform+Database+Generator+%28Version+2%29/.

[19] Geng X, Zhan DC, Zhou ZH. 用于可视化和分类的监督非线性降维. 系统、人与网络学汇刊. B部分, 控制论：IEEE系统、人与控制论学会出版物（IEEE transactions on systems, man, and cybernetics. Part B, Cybernetics: a publication of the IEEE Systems, Man, and Cybernetics Society）, 2005, 35(6), 1098.

[20] Zhao L, Zhang Z. 基于概率距离用于分类的监督局部线性嵌入. Pergamon出版社, 2009.

[21] Raducanu B, Dornaika F. 用于流形学习的监督非线性降维方法. 模式识别（Pattern Recognition）, 2012, 45(6), 2432–2444.

[22] Sun HQ. 图论及其应用. 科学出版社, 2004.

[23] Hastie T, Tibshirani R, Friedman J. 统计学习基础. 统计学系列丛书（Springer Series in Statistics）, 2001.

[24] Li HZ. 正交矩阵的逆问题及其最优逼近. 上海海运学院学报（Journal of Shanghai Maritime University）, 1990, 4, 71–76.

# 14 同伦边界学习

## 14.1 边界学习算法

边界划分可以分为数据分区和图像划分。目前主要的边界学习算法包括TVQ算法 [1]、Canny算法 [2] 以及RLMC算法 [3]。

### 14.1.1 切向矢量量化（TVQ）算法

针对该算法，Fabio Aiolli和Alessandro Sperduti提出了一种基于边界理论的方案来解决边界问题。该算法基于样本加权策略。其基本思想是增加训练集的新副本，并且样本在充分边界下不进行归类。

Fabio Aiolli和Alessandro Sperduti将此算法作为一个学习示例提出，即预定的实例。它包括基于1-NN分类器的距离切割。1-NN分类器实现了切割距离原型的量化。以这种方式创建的切割距离模型的泛化能力显然得到了提高。这种泛化能力源自标准的切割模型。此外，所获得的模型在OCR任务中优于其他算法，如SVM算法。

**算法 14.1：**
**输入：** $T$ ：迭代次数；$Q$ ：每类的模式数量；$\theta$：边缘临界值
**输出：** $W$

(1) 初始化：$W(1) \leftarrow N, \gamma_{i} \leftarrow 1/N$；对于任意 $\gamma$，$q$，以随机模式，
$$\boldsymbol{M}_{\gamma}^{(q)} \leftarrow \left(\mathbf{c}_{\gamma}^{(q)}, T_{\gamma}^{(q)}\right)\text{ . }$$

for $t = 1, \dots T$
$\forall \gamma$，$\forall q$，$\Delta \boldsymbol{M}_{\gamma}^{(q)} = 0$ ，$\Delta \boldsymbol{M}_{\gamma_{i}}^{(q_{p})} \leftarrow \Delta \boldsymbol{M}_{\gamma_{i}}^{(q_{p})} + \gamma_{i}(t) \frac{\boldsymbol{\delta \mu}_{i}}{\boldsymbol{\delta M}_{\gamma_{i}}^{(q_{p})}}$ ，$\Delta \boldsymbol{M}_{\gamma_{i}}^{(q_{n})} \leftarrow \gamma_{i}(t) \frac{\boldsymbol{\delta \mu}_{i}}{\boldsymbol{\delta M}_{\gamma_{i}}^{(q_{n})}}$ 。

(2) 正则化 $r_{i}^{*} \boldsymbol{\mathcal{S}}$。

与SVM方法相比，该方法直接作用于非线性模型，而不是取核。当两种方法都基于统计学习理论的概念时，它们从经验风险到理想风险均匀收敛。

这种方法与提升（boosting）算法非常相似。然而，提升算法更强调独立假设。因此，乘法策略更适合开关。

## 14.1.2 正则化大间隔分类器（RLMC）

通过在经典大间隔分类器的边缘临界值中加入规则项（在类散布中），当类散布达到最小值时，映射特征向量可以达到最大值 [3]。

**算法 14.2：**

**输入**：数据集包含两类样本 $\{x_i, y_i\}$，$x_i \in \mathbb{R}^n$，$y_i \in \{+1, -1\}$ 表示类标记

**输出：** $W$

- (1) 根据Fisher准则，修改现有的LMC目标函数。通过添加规则项，由组散布生成新的目标函数。
- (2) 通过添加规则项，$\min J(w) = 1/2\,\|w\|^2 = 1/2w^Tw$
$$\begin{aligned}
& \text{s.t. } \sum_{i=1}^N \alpha_i y_i = 0 \quad \alpha_i \geq 0, \quad i = 1, \ldots, N \\
& \min J(w) = 1/2\left(\|w\|^2 + \eta w^T S_w w\right) \\
& \text{s.t. } y_i\left(w^Tx_i + b \geq 1\right) \quad i = 1, \ldots, N
\end{aligned}$$
- (3) 上方方程将两类训练样本映射到方向 $W^*$ 以获得新模型。通过添加规则项，上方方程可以在类散布最小时达到最大边缘。

$S_w = \sum_{i=1}^{2} \sum_{j=1}^{N_i} (x_i - m_i)(x_j - m_i)^T, \ m_j = \frac{1}{N}\sum_{j=1}^{N_i} x_j, \quad i = 1, 2$

- (4) 计算训练样本类内所有类的散布矩阵和平均向量，特别是当 $\eta \geq 0$ 时，其中 $\eta$ 是控制平衡边缘的权重，并且在组内是离散的。

RLMC方法在时间和光照变化下的面部识别中可以实现良好的结果。通过现有的分类器，训练样本被映射到获取的向量中。

## 14.1.3 基于边界马尔可夫随机场和玻尔兹曼机的边界检测算法

通常，边缘检测基于图像灰度的不连续性，包括曲面拟合和边界跟踪。然而，许多边缘检测算法只关注灰度信息，且对噪声敏感。Tan [4] 将边缘检测问题转化为全局优化问题，不仅考虑灰度变化信息，还考虑局部边缘结构。该算法通过边缘检测算子对边缘检测进行初始化，模型参数通过玻尔兹曼机进行估计。最后，使用边缘弛豫玻尔兹曼机搜索算法。

**算法 14.3：**

**输入**：数据集包含两类样本 $(x_i, y_i, x_i \in R^n, y_i \in \{+1, -1\})$ 表示类标记

**输出**：$W$

- (1) 通过边缘检测算子对边缘检测进行初始化：
$e = \{e_{i,j} | i, j \in L\}$ 表示基于灰度图像 $Z$ 由边缘检测算子获得的响应强度。基于微分算法，边缘检测仅依赖于灰度信息。
$$ S_{i,j} = \begin{cases} 1, & \text{if } p\left(z_{i,j} | x_{i,j} = 1\right) \geq p\left(z_{i,j} | x_{i,j} = 0\right) \\ 0, & \text{if } p\left(z_{i,j} | x_{i,j} = 1\right) < p\left(z_{i,j} | x_{i,j} = 0\right) \end{cases} $$
- (2) 通过玻尔兹曼机估计模型参数：
以初始边缘检测的结果作为学习样本，根据玻尔兹曼机学习规则，估计参数 $\alpha_k$ 使得 $P(s)$ 最大化。参数估计问题转化为全局优化问题。
- (3) 基于玻尔兹曼机的边缘弛豫搜索算法：
由于采用了24-邻域系统，当边缘故障距离大于5*5邻域时，搜索算法难以处理；可以采用更大的邻域系统，但这会增加算法复杂度。

该算法的局限性在于，学习算法的学习样本是初始边缘检测结果。虽然它们具有一定的容错性，但当噪声过大时，很难执行该算法。学习算法可以获得主要的局部边缘特征，但存在一些局限性。只有当边缘具有一些规律性（即某些局部边缘特征更明显）时，图像效果才会更好，它更适合纹理图像的边缘检测。改进方案使用标准学习样本进行参数估计，适用于非学习样本，但学习样本和非学习样本必须是同一类型的图像。

### 14.1.4 基于隶属函数的模糊边缘检测算法

传统图像边缘检测模糊算法的步骤，称为Pal-King算法 [5]，如下所示：(1) 使用隶属函数将图像 $f(x, y)$ 映射为模糊隶属度矩阵 $G(i, j)$。(2) 对隶属度矩阵 $G(i, j)$ 进行多次非线性变换 $T_r$，以增强边缘信息并削弱非边缘信息。(3) 对模糊隶属度矩阵 $G(i, j)$ 执行反向变换以获得增强图像。(4) 使用‘Min’或‘Max’提取边缘。

然而，该算法存在许多缺点。因此，需要进行改进。我们在原始图像的基础上引入隶属函数，并且-
