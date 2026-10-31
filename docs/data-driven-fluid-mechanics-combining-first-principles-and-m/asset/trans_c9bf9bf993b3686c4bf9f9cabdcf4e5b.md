

![](img/ddadb1d3eaa6f9576eea68f95d453bca_29_0.png)

Figure 1.3 尾迹动力学原理示意图。左侧显示平均流场（上）、位移模态（中）和定常解（下）。右侧展示了在平均场抛物面（中间列）上插值的涡街。短期平均流场也以流线图的形式呈现。改编自 Morzyński et al. (2007)。

scaling (CMDS) can be employed for any data. Second (Section 1.3.2), manifold extraction with local linear embedding (LLE) is particularly powerful for low-dimensional dynamics.

### 1.3.1 Proximity Maps with Multidimensional Scaling

邻近映射的目标是将高维快照在视觉上可访问的、通常是二维的特征空间中作图，使得邻域关系尽可能得以保留。设 γ^m = [γ₁^m, γ₂^m]^T ∈ ℝ²（上标“T”表示转置），其中 m = 1, …, M 为与快照 u^m, m = 1, …, M 对应的二维特征向量。在 CMDS (Cox & Cox 2000) 中，这些特征最小化快照之间距离的累积误差

E = Σ_{m=1}^M Σ_{n=1}^M [‖u^m - u^n‖ - ‖γ^m - γ^n‖]². (1.9)

平移自由度通过要求特征中心化来消除，Σ_{m=1}^M γ^m = 0。旋转自由度通过要求第一个特征坐标具有最大变化来固定。一般而言，对于 N 维特征空间，全部 I ∈ {1,…,N} 的前 I 个方差之和最大化。然而，对于镜像下的误差不变性，却无解，就像 POD 模态和幅值的符号不确定性一样。事实上，得到的邻近映射产生前两个 POD 幅值 a₁, a₂。所得度量可针对特定应用进行定制，例如识别具有相似代价函数的区域（Kaiser et al. 2017b）。由于邻近映射基于保留邻域信息，它与 LLE 密切相关。

在此表述中，特征 γ₁ 和 γ₂ 与第 1.4.1 节中讨论的 POD 模态幅值 a₁ 和 a₂ 完全一致。因此，邻近映射与这些 POD 模态系数的相位图相同。提出了众多邻近映射的推广。在控制情况下，误差还可包括代价函数以使性能相似的状态更接近（Kaiser et al. 2017）。

![](img/ddadb1d3eaa6f9576eea68f95d453bca_30_0.png)

Figure 1.4 16 个圆柱尾迹瞬态的 LLE。图显示了由 K = 15 个最近邻得到的嵌入坐标 γ = [γ1, γ2]ᵀ 的前两个分量。详见 Ehlert et al. (2020)。

### 1.3.2 Identifying the Manifold with Local Linear Embedding

LLE (Roweis & Lawrence 2000) 旨在用低维流形近似通常高维空间中的 M 个数据点。特别是，原数据空间中的邻近点在低维嵌入空间中仍保持邻近。

结果是从快照 u^m 到 N 维特征 γ^m ∈ R^N 的最优映射。邻域关系保留如下。设 i1^m,...,iK^m 为第 m 个快照的 K 个最近快照的索引。设

$$\boldsymbol{u}^m \approx \sum_{k=1}^{K} w_{mk} \boldsymbol{u}^{i^m_k}$$

为其邻居以优化的非负权重 w_mk 最佳近似第 m 个快照，且权重之和为 1。这些权重约束强制局部插值。然后，特征向量也可以用相同的展开式近似，γ^m ≈ Σ_{k=1}^K w_mk γ^{i^m_k}。这里，K 是一个设计参数。它必须大于流形的维度，但又足够小以满足流形局部线性行为的假设。N 增加直到误差收敛。然后，N 表示流形的维度。详情请参阅原始文献（Roweis & Lawrence 2000）。

图 1.4 显示了尾迹快照数据的 LLE 特征坐标。原点对应定常解 u_s，而外圆代表
瞬态后涡脱落状态。对极坐标表示 γ₁+jγ₂ = r exp(jθ) 的分析表明，距离 r 与波动能量相关性良好，而 θ 可视为涡脱落相位（Ehlert et al. 2020）。

### 1.3.3 Other Features

显然，可以构造许多其他特征。CMDS 和 LLE 的一个明显设计参数是两个快照之间选择的距离，例如域和所考虑的状态变量。

这里，我们提及一个对实验具有重要意义的特征向量：来自传感器信号的时间延迟坐标（Takens 1981）。虽然流体流动的降阶表示降低了状态的维度，但时间延迟坐标将测量信号的维度提高到轨迹不再相交（无假邻居）且可识别动力系统的水平。Loiseau et al. (2018) 讨论了从升力系数构建瞬态圆柱尾迹速度场流形。

## 1.4 Low-Dimensional Representations

低维状态表示是理解、状态估计、动态建模和控制的关键使能因素。本节的起点是 M 个流场快照 u^m(x), m = 1, …, M 的集合（第 1.2 节）。低维数据驱动表示与机器学习中的自编码器同义。自编码器旨在对快照数据进行低维参数化，例如在 ℝ^N 中。更精确地说，自编码器包含一个从高维或无限维状态空间到低维特征空间的编码器 G，例如，

*u^m ↦ a^m := G(u^m) ∈ ℝ^N,  m = 1, …, M*  (1.10)

和一个解码器或状态估计器 H，例如，

*a^m ↦ û^m := H(a^m),  m = 1, …, M*  (1.11)

用于状态重构。理想情况下，自编码器识别最佳的编码器 G 和解码器 H 的配对，使估计器/解码器的样本内误差最小化

*E_in := (1/M) Σ_{m=1}^M ||û^m - u^m||_Ω^2.*  (1.12)

### 1.4.1 Optimal Subspaces with Proper Orthogonal Decomposition

POD 可被视为到 N 维仿射子空间的最优线性自编码器。设 u_0 为快照集合的平均值，u_i, i = 1, …, N 为 N 个
POD 模态，且 $a_i$ 为相应的模态系数。则速度场 $\boldsymbol{u}$ 到模态幅值 $\boldsymbol{a} = [a_1, \ldots, a_N]^\mathsf{T}$ 的编码器 $\boldsymbol{G}$ 定义为

$a_i := (\boldsymbol{u} - \boldsymbol{u}_0, \boldsymbol{u}_i)_\Omega, \quad i = 1, \ldots, N, \tag{1.13}$

而解码器 $\boldsymbol{H}$ 为

$\hat{\boldsymbol{u}}(\boldsymbol{x}) = \boldsymbol{u}_0(\boldsymbol{x}) + \sum_{i=1}^{N} a_i \boldsymbol{u}_i(\boldsymbol{x}). \tag{1.14}$

POD 模态是正交归一集合，按能量含量排序。最优性条件（例如 Holmes et al. 2012）意味着来自 (1.12) 的最小样本内表示误差。我们找不到另一个 $N$ 阶 Galerkin 展开（更精确地说，不同的 N 维子空间）产生更小的误差。

对于瞬态尾迹数据，最具能量的 POD 模态 $\boldsymbol{u}_i$ 和幅值演化 $a_i$ 显示在 Noack et al. (2016) 的图 3 和 4 中。前两个模态对应于 von Kármán 涡脱落。第三个模态解析了平均场的改变。后续模态混合了不同的频率和波长。

### 1.4.2 Coarse-Graining the Data into Bins with Clustering

聚类的关键思想是用少量，例如 $K$，个质心 $\boldsymbol{c}_k$，k = 1, …, K 来表示快照。每个快照 $\boldsymbol{u}^m$ 可与其最近的质心 $\boldsymbol{c}_k$ 相关联。因此，编码器 $\boldsymbol{G}$ 将速度场 $\boldsymbol{u}$ 映射到 k ∈ {1, …, K}，即最近质心的索引。换句话说，编码器创建了相似快照的“箱”。解码器 $\boldsymbol{H}$ 用最近的质心 $\hat{\boldsymbol{u}} = \boldsymbol{c}_k$ 近似速度场。k-means 算法旨在最小化样本内表示误差（Arthur & Vassilvitskii 2007）。对于通用数据，质心可预期在索引编号意义下唯一。用 $K$ 个箱进行聚类不能产生比用 $K$ 个模态 $\boldsymbol{u}_i$，i = 0, …, K - 1 的 POD 表示更低的样本内误差。聚类和 POD 都跨越 K - 1 维子空间，但 POD 展开可以插值状态，而质心是对应快照箱的固定表示。

图 1.5 显示了用 LLE 特征可视化的 10 个质心的结果。质心试图填充圆形区域。一个质心是定常解；七个质心解析极限环；一对相位相反的质心代表低幅振荡。

### 1.4.3 Comparison and Discussion

POD 和聚类是相当不同的自编码器。虽然 POD 基于模态的叠加，但质心是不可叠加的代表性状态。LLE 可以推广为自编码器。特征向量 $\boldsymbol{\gamma}$ 在编码步骤中获得。解码器可以很容易地构造，例如用 K-最近邻插值（Ehlert et al. 2020）。

图 1.6 显示了模拟数据三种方法的重构误差。三种方法在瞬态阶段的重构误差最大

