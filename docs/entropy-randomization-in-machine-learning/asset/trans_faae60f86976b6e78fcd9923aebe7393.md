

$$\begin{array}{r} \left. \mathcal{H}\lbrack P(\mathbf{a}),L(\overline{\xi})\rbrack = - {\int_{\mathcal{A}}P}(\mathbf{a})\,\ln P(\mathbf{a})d\mathbf{a} - {\int_{\mathcal{K}}L}(\overline{\xi})\ln L(\overline{\xi})d\overline{\xi}\Rightarrow\max, \right. \\ \end{array}$$

(3.87)

受约束条件

$$\begin{array}{r} {{\int_{\mathcal{A}}P}(\mathbf{a})d\mathbf{a} = 1,\text{\quad\quad}{\int_{\mathcal{K}}L}(\overline{\xi})d\overline{\xi} = 1,} \\ \end{array}$$

(3.88)

以及

$$\begin{array}{r} {\mathcal{M}\left\{ \mathbf{z} \right\} = {\int_{\mathcal{A}}U}P(\mathbf{a})d\mathbf{a} + {\int_{\mathcal{K}}\overline{\xi}}L(\overline{\xi})d\overline{\xi} = \mathbf{y}.} \\ \end{array}$$

(3.89)

这是一个熵-线性函数规划问题 \[138\]。其解的形式为

$$\begin{aligned} & {P^{\*}(\mathbf{a}) = \pi^{- 1}(\overline{\theta})\exp\left\langle - \overline{\theta},U\,\mathbf{a} \right\rangle,} \\ & {L^{\*}(\overline{\xi}) = \varpi^{- 1}(\overline{\theta})\exp\left\langle - \overline{\theta},\overline{\xi} \right\rangle,} \\ \end{aligned}$$

(3.90)

其中

$$\begin{aligned} {\pi(\overline{\theta})} & {= {\int_{\mathcal{A}}\exp}\left\langle - \overline{\theta},U\,\mathbf{a} \right\rangle d\mathbf{a},} \\ {\varpi(\overline{\theta})} & {= {\int_{\mathcal{K}}\exp}\left\langle - \overline{\theta},\overline{\xi} \right\rangle d\overline{\xi}.} \\ \end{aligned}$$

(3.91)

拉格朗日乘子 $\overline{\theta}$ 由平衡方程 (3.89) 求得：

$$\begin{array}{r} {{\int_{\mathcal{A}}U}P^{\*}(\mathbf{a})d\mathbf{a} + {\int_{\mathcal{K}}\overline{\xi}}L^{\*}(\overline{\xi})d\overline{\xi} = \mathbf{y}.} \\ \end{array}$$

(3.92)

因此，RML 的 *s*\-问题的解给出了两个熵最优的 PDF *P*^(\*)(**a**)（模型参数）和 $L^{\*}(\overline{\xi})$（测量噪声）。

在 *第二阶段*，使用线性模型 (3.80)，其参数和测量噪声相互独立。观测向量 **v** 的概率密度函数 *F*(**v**) 的形式为

$$\begin{array}{r} {F(\mathbf{v}) = {\int_{\mathcal{K}}G}(\mathbf{v} - \overline{\xi})L^{\*}(\overline{\xi})d\overline{\xi},} \\ \end{array}$$

(3.93)

其中 *G*( • ) 是向量 **z** (3.80) 的密度。根据该等式，

$$\begin{array}{r} {\mathbf{a} = {(U^{\intercal}U)}^{- 1}\, U^{\intercal}\mathbf{z}.} \\ \end{array}$$

(3.94)

因此，

$$\begin{array}{r} {P^{\*}({(U^{\intercal}U)}^{- 1}\, U^{\intercal}\mathbf{z}) = \eta(\mathbf{z}),} \\ \end{array}$$

(3.95)

其中向量 **z** 定义在集合 𝒵 (3.78) 上。对该函数进行归一化，得到向量 **z** 的 PDF

$$\begin{array}{r} {G(\mathbf{z}) = \frac{\eta(\mathbf{z})}{{\int_{\mathcal{Z}}\eta}(\mathbf{z})}d\mathbf{z}} \\ \end{array}$$

(3.96)

该 PDF 在集合 𝒵 (3.78) 上归一化。

好，等式 (3.93) 给出了 *s*\-问题随机化模型的 PDF *F*(**v**)， **v** ∈ 𝒱 (3.81)。记其为 *F*[*s*](**v**)。

使用类似的程序对 *r*\-问题 (3.82–3.84) 进行处理，数据矩阵使用缩减后的 *W* (3.75)，求得在集合 𝒯 (3.86) 上归一化的 PDF *F*[*r*](**t**)。

为比较 PDF *F*[*s*](**v**) 和 *F*[*r*](**t**)，引入集合

$$\begin{array}{r} {\mathcal{C} = \mathcal{V}{\cap \mathcal{T}},} \\ \end{array}$$

(3.97)

并在该集合上对这些函数进行归一化。归一化后的 PDF 的形式为

$$\begin{array}{r} {{\widetilde{F}}_{s}(\mathbf{c}) = \frac{F_{s}(\mathbf{c})}{{\int_{\mathcal{C}}F_{s}}(\mathbf{c})d\mathbf{c}},} \\ {{\widetilde{F}}_{r}(\mathbf{c}) = \frac{F_{r}(\mathbf{c})}{{\int_{\mathcal{C}}F_{r}}(\mathbf{c})d\mathbf{c}}.} \\ \end{array}$$

在 *第三阶段*，将使用 Kullback–Leibler 散度作为 PDF *F̃*[*r*](**c**) 与 *F̃*[*s*](**c**) 之间 *绝对信息误差 Δ* 的度量：

$$\begin{array}{r} {KL({\widetilde{F}}_{s},{\widetilde{F}}_{r}) = {\int_{\mathcal{C}}{\widetilde{F}}_{r}}(\mathbf{c})\ln\frac{{\widetilde{F}}_{r}(\mathbf{c})}{{\widetilde{F}}_{s}(\mathbf{c})} = \Delta \geq 0.} \\ \end{array}$$

(3.98)

注意，最小值 *Δ* = 0 在 *F̃*[*r*](**c**) = *F̃*[*s*](**c**) 时取得。

此外，引入 *相对信息误差 δ* 的形式为

$$\begin{array}{r} {\delta = \frac{\Delta}{H_{s} + H_{r}},} \\ \end{array}$$

(3.99)

其中

$$\begin{aligned} H_{s} & {= {\int_{\mathcal{C}}{\widetilde{F}}_{s}}(\mathbf{c})\ln{\widetilde{F}}_{s}(\mathbf{c})d\mathbf{c},} \\ H_{r} & {= {\int_{\mathcal{C}}{\widetilde{F}}_{r}}(\mathbf{c})\ln{\widetilde{F}}_{r}(\mathbf{c})d\mathbf{c}.} \\ \end{aligned}$$

(3.100)

这些等式是定义在支撑集 𝒞 (3.97) 上的 PDF *F̃*[*s*] 和 *F̃*[*r*] 的信息熵。

## 3.6 EDR 在二分类问题中效率的估计

EDR 方法将通过计算实验在真实数据上与主成分分析 (PCA) 和随机投影 (RP) 方法进行表征和比较效率，该实验针对具有线性分类器的二分类问题。

### 3.6.1 线性分类器

### 3.6.2 计算实验方案

遵循 \[[162](#refbib.xhtml#r162), [190](#refbib.xhtml#r190)\]，EDR 方法通过求解原始属性空间和缩减属性空间中的二分类问题，并在分类准确率 (3.107) 方面与 PCA 和 RP 方法进行比较，从而进行了实验研究。为了使结果稳定，使用了蒙特卡洛模拟和交叉验证。

实验包含若干阶段：

1. 在原始空间中求解分类问题；
2. 在 PCA 缩减空间中求解分类问题；
3. 在 RP 缩减空间中求解分类问题；
4. 在 EDR 缩减空间中求解分类问题。

阶段 2–4 依次针对维度每次减少 1 实现，即 *r* = *s* − 1, …, 1，其中 *r* 表示缩减空间的维度。阶段 4 对 *δ* 的不同取值实现，即信息容量的允许下降量。

实验研究用的 Python 程序在 OS Linux 上开发，使用了 `numpy 1.14.3`、`scipy 1.1.0`、`sklearn 0.19.1` 库。通过 scikit-learn 库 \[[128](#refbib.xhtml#r128)\] 的相应类 `PCA` 和 `GaussianRandomProjection` 进行主成分分析和随机投影方法降维。分类问题使用支持向量机 \[[70](#refbib.xhtml#r70)\] 求解，即使用线性核的 `SVC` 类。

实验研究基于两组数据集如下。第一组 (*simulation*) 是一个包含 100 个对象、10 个属性的合成数据集。数据由 `make_classification` 函数 \[[26](#refbib.xhtml#r26)\] 生成，参数为 `n_classes=2`、`n_clusters_per_class=2`、`n_informative=10`、`n_redundant=0` 和 `class_sep=1.0`。该函数在维度为 `n_informative` 的空间中生成点，围绕超立方体的边缘呈正态分布（零均值、单位方差），并加入少量噪声。

第二组数据集 (*heart*) 由心脏病研究中收集的真实数据组成 \[[2](#refbib.xhtml#r2)\]。该数据集包含 270 个对象、13 个属性。

所有实验中，数据均归一化到区间 \[0,1\]。

### 3.6.3 实验结果

