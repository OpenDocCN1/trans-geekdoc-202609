
概率被初始化为其真实值 `P[1]^(0) = P[2]^(0) = P[3]^(0) = 1/3`。[图 12.6](#Chp012_583-634_B9780443292385000184.xhtml#f0050)中的红色曲线对应于 EM 算法在 (A) 初始估计、(B) 五次迭代后以及 (C) 收敛后恢复的混合分布。[图 12.6](#Chp012_583-634_B9780443292385000184.xhtml#f0050)D 显示了对数似然作为迭代次数的函数。

![Figure 12.6 The curves (ellipses) indicate the 80% probability regions. The gray curves correspond to the true Gaussian clusters of Example 12.3. The red curves correspond to (A) the initial values for the mean and the covariance matrices, (B) the mixtures recovered by the EM algorithm after five iterations, and (C) after 30 iterations. (D) The log-likelihood as a function of the number of iterations.](images/B9780443292385000184/gr006.jpg)

图 12.6 曲线（椭圆）指示 80% 概率区域。灰色曲线对应于[示例 12.3](#Chp012_583-634_B9780443292385000184.xhtml#enun0040)的真实高斯簇。红色曲线对应于 (A) 均值和协方差矩阵的初始值、(B) EM 算法五次迭代后恢复的混合分布，以及 (C) 30 次迭代后的结果。(D) 对数似然作为迭代次数的函数。

[图 12.7](#Chp012_583-634_B9780443292385000184.xhtml#f0055) 对应于另一种设置。这一次，均值被初始化在离真实值很远的点上，即：

`μ[1]^(0) = [10, 13]^T,  μ[2]^(0) = [11, 12]^T,  μ[3]^(0) = [13, 11]^T`

![Equation](images/B9780443292385000184/si246.png)

而协方差和概率的初始化方式与之前相同。观察可知，在这种情况下，EM 算法未能捕捉问题的真实性质，陷入了局部最大值。

![Figure 12.7 This is the counterpart of Fig. 12.6, where now the initial values for the means are very far from the true ones. In this case, the EM fails to recover the true nature of the mixtures and has been trapped in a local maximum.](images/B9780443292385000184/gr007.jpg)

[图 12.7](#Chp012_583-634_B9780443292385000184.xhtml#cf0795) 是[图 12.6](#Chp012_583-634_B9780443292385000184.xhtml#f0050)的对应图，此时均值的初始值离真实值很远。在这种情况下，EM 无法恢复混合分布的真实性质，并陷入了局部最大值。

## 12.6.1 高斯混合建模与聚类

聚类属于无监督学习家族，是机器学习的重要组成部分，本书不予涵盖。关于聚类的广泛覆盖见文献 [41] 等。然而，通过 EM 算法进行混合建模的任务给了我们一个机会简要论述几句。在不涉及正式定义的情况下，聚类的任务是将若干点 `x[1], …, x[N]` 分配到 `K` 个组或簇中。分配到同一簇的点必须比分配到不同簇的点更“相似”。一些聚类算法需要用户将簇的数量 `K` 作为输入变量提供。其他方案则将其视为一个由算法从数据中恢复的自由参数。聚类中的另一个主要问题是量化“相似性”。不同的定义会导致不同的聚类结果。聚类是点到簇的一种特定分配。通常，根据最优性准则将点分配到簇是一个 NP-hard 任务（见文献 [41] 等）。因此，通常任何聚类算法都只能提供次优解。
