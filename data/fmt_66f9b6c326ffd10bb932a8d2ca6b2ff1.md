
*   [38] T. Piotrowski, I. Yamada, MV-PURE estimator: minimum-variance pseudo-unbiased reduced-rank estimator for linearly constrained ill-conditioned inverse problems, *IEEE Trans. Signal Process.* 2008;56:3408–3423.
*   [39] I.R. Porteous, *Clifford Algebras and Classical Groups*. Cambridge University Press; 1995.
*   [40] J.E. Potter, New statistical formulas, *Space Guidance Analysis Memo, No 40*. Instrumentation Laboratory, MIT; 1963.
*   [41] J. Proakis, *Digital Communications*. second ed. McGraw Hill; 1989.
*   [42] J.G. Proakis, D.G. Manolakis, *Digital Signal Processing: Principles, Algorithms and Applications*. second ed. MacMillan; 1992.
*   [43] O.-S. Reza, Distributed Kalman filtering for sensor networks, *Proceedings IEEE Conference on Decision and Control*. 2007:5492–5498.
*   [44] A.H. Sayed, *Fundamentals of Adaptive Filtering*. John Wiley; 2003.
*   [45] J. Schur, Über Potenzreihen, die im Innern des Einheitskreises beschränkt sind, *J. Reine Angew. Math.* 1917;147:205–232.
*   [46] K. Slavakis, P. Bouboulis, S. Theodoridis, Adaptive learning in complex reproducing kernel Hilbert spaces employing Wirtinger's subgradients, *IEEE Trans. Neural Netw. Learn. Syst.* 2012;23(3):425–438.
*   [47] G. Strang, *Linear Algebra and Its Applications*. fourth ed. Hartcourt Brace Jovanovich; 2005.
*   [48] M. Viberg, Introduction to array processing, R. Chellappa, S. Theodoridis, eds. *Academic Library in Signal Processing, vol. 3*. Academic Press; 2014:463–499.
*   [49] N. Wiener, E. Hopf, Über eine klasse singulärer integralgleichungen, *S.B. Preuss. Akad. Wiss.* 1931:696–706.
*   [50] N. Wiener, *Extrapolation, Interpolation and Smoothing of Stationary Time Series*. Cambridge, MA: MIT Press; 1949.
*   [51] W. Wirtinger, Zur formalen Theorie der Funktionen von mehr komplexen Veränderlichen, *Math. Ann.* 1927;97:357–375.
*   [52] P. Zhu, B. Chen, J.C. Principe, Learning nonlinear generative models of time series with a Kalman filter in RKHS, *IEEE Trans. Signal Process.* 2014;62(1):141–155.

---

# 第 5 章：在线学习：随机梯度下降算法族

## 章节大纲

*   5.1 引言
*   5.2 最速下降法
*   5.3 均方误差代价函数的应用
    *   时变步长
    *   5.3.1 复值情况
*   5.4 随机逼近
    *   均方误差线性估计的应用
*   5.5 最小均方自适应算法
    *   5.5.1 平稳环境下 LMS 的收敛与稳态性能
        *   参数误差向量的收敛
    *   5.5.2 累积损失界
*   5.6 仿射投影算法
    *   APA 的几何解释
    *   正交投影
    *   5.6.1 归一化 LMS
*   5.7 复值情况
    *   广义线性 LMS
    *   广义线性 APA
*   5.8 LMS 的变体
    *   符号误差 LMS
    *   最小均方四次(LMF)算法
    *   变换域 LMS
*   5.9 仿真示例
*   5.10 自适应判决反馈均衡
*   5.11 线性约束 LMS
*   5.12 非平稳环境下 LMS 的跟踪性能
*   5.13 分布式学习：分布式 LMS
    *   5.13.1 合作策略
        *   中心化网络
        *   去中心化网络
    *   5.13.2 扩散 LMS
    *   5.13.3 收敛与稳态性能：一些要点
    *   5.13.4 基于共识的分布式方案
*   5.14 案例研究：目标定位
*   5.15 总结性评论：共识矩阵
*   习题
    *   计算机练习
*   参考文献

## 5.1 引言

在第 4 章中，我们介绍了均方误差（MSE）最优线性估计的概念，并给出了用于计算最优估计器/滤波器参数/系数的正规方程。正规方程的前提是了解所涉及过程/变量的二阶统计特性，以便获得输入的协方差矩阵和输入-输出互相关向量。然而，在实践中，设计师通常手头只有一组训练样本；因此，协方差矩阵和互相关向量必须以某种方式进行估计。更重要的是，在许多实际应用中，底层统计特性可能是时变的。我们在介绍卡尔曼滤波时讨论过这种情况。当时采取的途径是采用状态空间表示，并假设模型的时间动力学是已知的。然而，尽管卡尔曼滤波是一个优雅的工具，但由于涉及的矩阵运算和求逆，它在高维空间中扩展性不佳。

本章的重点是介绍用于估计未知参数向量的*在线学习*技术。这些是时间迭代方案，每当获取一组测量数据（输入-输出观测对）时，都会更新可用的估计值。因此，与所谓的*批处理*方法形成对比，后者将整个数据块作为单个实体进行处理，在线算法一次仅对单个数据点进行操作；因此，此类方案不要求预先知道并存储训练数据集。在线算法方案以*时间迭代*的方式从数据中学习潜在统计特性。因此，无需提供进一步的统计信息。本章将要开发和研究的算法家族的另一个特征是其计算简洁性。更新未知参数向量估计值所需的复杂度与未知参数的数量呈线性关系。这是此类方案在许多实际应用中广受欢迎的主要原因之一；除了复杂度，我们还将讨论促成其流行的其他原因。关于批处理与在线算法的讨论见第 8.12 节。

此类学习算法以时间迭代模式工作，这赋予了它们敏捷性，能够学习并*跟踪*所涉及过程/变量统计特性的缓慢时变；这也是这些算法被称为*时自适应*或简称为*自适应*的原因，因为它们能适应不断变化的环境需求。自 1960 年代初以来，在线/时自适应算法已在信号处理、控制和通信等广泛应用中被大量使用。最近，此类方案背后的理念在数据驻留于大型数据集（具有海量样本）的应用背景下越来越受欢迎；对于此类任务，将所有数据点存储在内存中可能是不可能的，必须逐个考虑。此外，批处理技术的复杂度可能达到当今技术无法承受的水平。目前的趋势是将此类应用称为*大数据*问题。

在本章中，我们专注于一类非常流行的在线/自适应算法，该类算法源自用于优化的经典梯度下降法。虽然我们的重点将放在平方误差损失函数上，但相同的基本原理也可采用于其他（可微）损失函数。不可微损失函数的情况将在第 8 章中处理。

介绍了梯度下降概念，并引入了随机逼近的概念。除了处理该算法家族的一些经典成员（如 `LMS`、`APA`、`NLMS` 和变换域 `LMS`）外，还考虑了与在线算法在时变环境中的收敛分析和跟踪性能相关的重要问题。最后，介绍了图上在线分布式学习的最新趋势，并展示了一些代表性算法。章节末尾将探讨一个与目标定位任务相关的案例研究。随机梯度家族在深度神经网络背景下的多种算法变体见第 18 章。在线处理的基本原理将贯穿全书。

## 5.2 最速下降法

我们的出发点是*梯度下降*法，它是用于可微代价函数 `J(θ)`（`θ ∈ ℝ^l`）迭代极小化的最广泛使用的方法之一。与任何其他迭代技术一样，该方法从初始估计 `θ⁰` 开始，并生成一个序列 `θ^(i)`（`i = 1, 2, …`），使得

```
θ^(i) = θ^(i−1) + μ[i]Δθ^(i),  i > 0,
```

(5.1)

其中 `μ[i] > 0`。本书将要讨论的所有用于迭代最小化代价函数的方案，都具有公式 (5.1) 的一般形式。它们的区别在于 `μ[i]` 和 `Δθ^(i)` 的选择方式；后一个向量被称为*更新方向*或*搜索方向*。序列 `μ[i]` 被称为第 *i* 次迭代的*步长*；注意 `μ[i]` 的值可以是常数，也可以在每次迭代中改变。在梯度下降法中，`Δθ^(i)` 的选择旨在保证

`J(θ^(i)) < J(θ^(i−1))`

除非在极小值点 `θ[*]` 处。

假设在第 (*i* − 1) 次迭代步骤中已获得值 `θ^(i−1)`。然后，对于足够小的 `μ[i]`，并在 `θ^(i−1)` 处利用一阶泰勒展开，我们可以写成

`J(θ^(i)) = J(θ^(i−1) + μ[i]Δθ^(i)) ≈ J(θ^(i−1)) + μ[i]∇J(θ^(i−1))^(T)Δθ^(i).`

仔细观察上述近似，我们基本上所做的就是针对 `Δθ^(i)` 在局部将代价函数*线性化*。选择搜索方向以使得

∇*J*(**θ**^((*i* − 1)))^(*T*)*Δ***θ**^((*i*)) < 0

这保证了 *J*(**θ**^((*i* − 1))+*μ*[*i*]*Δ***θ**^((*i*))) < *J*(**θ**^((*i* − 1)))。对于这种选择，*Δ***θ**^((*i*)) 和 ∇*J*(**θ**^((*i* − 1))) 必须形成一个*钝*角。图 5.1 展示了二维情况下代价函数的图形，**θ**∈ ℝ²，而图 5.2 展示了二维平面中相应的等值线。请注意，通常等值线可以具有任意形状，并不一定是椭圆；这完全取决于 *J*(**θ**) 的函数形式。然而，由于已假设 *J*(**θ**) 可微，等值线必须是光滑的，并且在任意一点都接受一条（唯一的）切平面，因为这是由相应的梯度定义的。此外，回顾基本微积分知识，梯度向量 ∇*J*(**θ**) 垂直于点 **θ** 处对应等值线的切平面（切线）（问题 5.1）。图 5.3 说明了这种几何关系；为了便于绘图和简化符号，我们去掉了迭代索引 *i*。请注意，选择与梯度形成钝角的搜索方向，会将 **θ**^((*i* − 1)) + *μ*[*i*]*Δ***θ**^((*i*)) 置于一个对应 *J*(**θ**) 较低值的等值线上的点处。现在提出了两个问题：(a) 选择移动的最佳搜索方向，以及 (b) 计算沿该方向可以前进多远。即使不需要太多数学知识，从图 5.3 也可以明显看出，如果 *μ*[*i*]||*Δ***θ**^((*i*))|| 太大，那么新点可能会被置于一个对应值比当前值更大的等值线上；毕竟，一阶泰勒展开对于偏离 **θ**^((*i* − 1)) 很小的情况近似成立。

### 图 5.1 二维参数空间中的代价函数

![Figure 5.1 A cost function in the two-dimensional parameter space.](img/gr001.jpg)

**图 5.1** 二维参数空间中的代价函数。

### 图 5.2 图 5.1 中代价函数的等值线

![Figure 5.2 The corresponding isovalue curves of the cost function in Fig. 5.1, in the two-dimensional plane. All the points θ lying on the same (isovalue) ellipse score the same value for the cost J(θ). Note that as we move away from the optimal value, θ⁎, the values of c increase.](img/gr002.jpg)

**图 5.2** 图 5.1 中代价函数在二维平面上的对应等值线。所有位于同一条（等值）椭圆上的点 `θ` 对代价 `J(θ)` 具有相同的值。请注意，随着我们远离最优值 `θ*`，`c` 的值会增加。

### 图 5.3 梯度向量与切平面

![Figure 5.3 The gradient vector at a point θ is perpendicular to the tangent plane (dotted line) at the isovalue curve crossing θ. The descent direction forms an obtuse angle, ϕ, with the gradient vector.](img/gr003.jpg)

**图 5.3** 点 `θ` 处的梯度向量垂直于穿过 `θ` 的等值曲线处的切平面（虚线）。下降方向与梯度向量形成钝角 `ϕ`。

#### 最速下降方向推导

为了解决这两个问题中的第一个，让我们假设 `μ[i] = 1`，并寻找所有具有单位欧几里得范数且原点位于 `θ^(i-1)` 的向量 `z`。不难发现，在所有可能的方向中，使内积 `∇J(θ^(i-1))^T z` 取得最负值的方向，是负梯度方向：

```
z = - ∇J(θ^(i-1)) / || ∇J(θ^(i-1)) ||
```

这在 **图 5.4** 中有所说明。以 `θ^(i-1)` 为中心作单位欧几里得范数球。然后从所有以 `θ^(i-1)` 为原点的单位范数向量中，选择指向负梯度方向的那个。因此，对于所有单位欧几里得范数向量，最速下降方向与（负）梯度下降方向一致，相应的更新递推公式变为：

![Equation](img/fx001.jpg) (5.3)

请注意，我们仍需解决第二个问题，即 `μ[i]` 的选择。该选择必须能保证极小化序列的收敛性。我们稍后将讨论这个问题。

### 图 5.4 单位欧几里得范数下的下降方向

![Figure 5.4 From all the descent directions of unit Euclidean norm (dotted circle centered at θ(i−1), which for notational simplicity is shown as θ), the negative gradient one leads to the maximum decrease of the cost function.](img/gr004.jpg)

**图 5.4** 在所有单位欧几里得范数的下降方向中（以 `θ^(i-1)` 为中心的虚线圆，为简化符号显示为 `θ`），负梯度方向导致代价函数最大程度的下降。

Eq. (5.3) 中的迭代过程在 Fig. 5.5 中针对一维情况进行了说明。如果在当前迭代中算法“落在”了 `θ₁` 处，则此时 `J(θ)` 的导数为正（锐角 `ϕ₁` 的正切），这将迫使更新向左移动，朝向最小值。如果当前估计值为 `θ₂`，情况则不同。导数为负（钝角 `ϕ₂` 的正切），这将推动更新向右移动，同样朝向最小值。但请注意，向左或向右移动多远非常重要。例如，从 `θ₁` 向左移动过大可能会使更新落在最优值的另一侧。在这种情况下，算法可能会在最小值附近振荡而永不收敛。本章将投入大量精力，提供理论框架以确定步长值的界限，从而保证收敛。

![Figure 5.5 Once the algorithm is at θ1, the gradient descent will move the point to the left, toward the minimum. The opposite is true for point θ2.](img/gr005.jpg)

Figure 5.5 一旦算法位于 `θ₁`，梯度下降法将把该点向左移动，朝向最小值。对于 `θ₂` 点则情况相反。

梯度下降法表现出近似的**线性收敛**；即 `θ⁽ⁱ⁾` 与最小值之间的误差以**几何级数**的形式渐近收敛到零。然而，收敛速度在很大程度上取决于 `J(θ)` 的海森矩阵的特征值分布。第 5.3 节将揭示收敛速度对特征值的依赖关系。对于较大的特征值分布，收敛速度可能变得极低。另一方面，该方法的巨大优势在于其计算量要求低。

最后必须指出，我们通过单位欧几里得范数搜索所有方向，得出了 Eq. (5.3) 中的方案。然而，欧几里得范数并没有什么“神圣”不可替代之处。可以采用其他范数，例如 `ℓ₁` 范数和 `P` 加权范数 `(zᵀPz)¹ᐟ²`，其中 `P` 是正定矩阵。在这些选择下，将得到替代的更新迭代（参见文献 [23]）。在第 6 章中，当我们处理牛顿迭代法和坐标下降最小化方案时，将回到这一点。

## 5.3 均方误差代价函数的应用
