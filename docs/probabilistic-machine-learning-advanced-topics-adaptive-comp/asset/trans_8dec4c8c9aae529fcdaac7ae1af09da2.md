

![](img/ca72c1626f4850f058a9edc138c1ac73_52_0.png)

图 2.6: (a) 当 K = 3 时，狄利克雷分布定义在单纯形上的分布，可以由三角形曲面表示。曲面上的点满足 0 <= theta_c <= 1 且 sum_{c=1}^3 theta_c = 1。由 dirichlet_3d_triangle_plot.ipynb 生成。(b) alpha = (20,20,20) 的狄利克雷密度图。(c) alpha = (3, 3, 20) 的狄利克雷密度图。(d) alpha = (0.1, 0.1, 0.1) 的狄利克雷密度图。由 dirichlet_3d_spiky_plot.ipynb 生成。

狄利克雷分布可用于区分 aleatoric（数据）不确定性与 epistemic 不确定性。为说明这一点，请考虑一个 3 面骰子。如果我们知道每个结果的可能性相同，可以使用“陡峭”的对称狄利克雷分布，例如 Dir(20, 20, 20)，如图 2.6(b) 所示；这反映了我们确定结果将是不可预测的这一事实。相比之下，如果我们不确定结果会是什么样子（例如，可能是一个有偏的骰子），则可以使用“平坦”的对称狄利克雷分布，例如 Dir(1, 1, 1)，它可以生成各种可能的结果分布。我们可以使狄利克雷分布条件化于输入，从而得到所谓的 **先验网络** [MG18]，因为它编码的是 p(pi|x)（输出是分布），而不是 p(y|x)（输出是标签）。

![](img/ca72c1626f4850f058a9edc138c1ac73_53_0.png)

图 2.7: 不同参数值下 5 维对称狄利克雷分布的样本。(a) \(\boldsymbol{\alpha} = (0.1, \dots, 0.1)\)。这会产生非常稀疏的分布，包含许多 0。(b) \(\boldsymbol{\alpha} = (1, \dots, 1)\)。这会产生更均匀（且密集）的分布。由 `dirichlet_samples_plot.ipynb` 生成。

## 2.3 高斯联合分布

对于连续随机变量，最广泛使用的联合概率分布是 **多元高斯分布** 或 **多元正态分布** (**MVN**)。其流行部分是因为该分布在数学上很方便，也因为在许多情况下高斯假设相当合理。确实，高斯分布是在给定一阶和二阶矩的条件下熵最大的分布（第 2.4.7 节）。鉴于其重要性，本节将详细讨论高斯分布。

### 2.3.1 多元正态分布

在本节中，我们将详细讨论多元高斯分布或多元正态分布。

#### 2.3.1.1 定义

MVN 密度由以下定义：

```
\(\mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma}) \triangleq \frac{1}{(2\pi)^{D/2}|\boldsymbol{\Sigma}|^{1/2}} \exp \left[-\frac{1}{2}(\boldsymbol{x}-\boldsymbol{\mu})^{\mathsf{T}} \boldsymbol{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})\right]\)
```

其中 \(\boldsymbol{\mu} = \mathbb{E}[\boldsymbol{x}] \in \mathbb{R}^D\) 是均值向量，\(\boldsymbol{\Sigma} = \text{Cov}[\boldsymbol{x}]\) 是 \(D \times D\) 协方差矩阵。归一化常数 \(Z = (2\pi)^{D/2}|\boldsymbol{\Sigma}|^{1/2}\) 仅用于确保 pdf 积分为 1。指数内部的表达式（忽略 \(-0.5\) 的系数）是数据向量 \(\boldsymbol{x}\) 与均值向量 \(\boldsymbol{\mu}\) 之间的平方 **马氏距离**，由以下给出：

```
\(d_{\boldsymbol{\Sigma}}(\boldsymbol{x}, \boldsymbol{\mu})^2 = (\boldsymbol{x}-\boldsymbol{\mu})^{\mathsf{T}} \boldsymbol{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})\)
```

在 2d 中，MVN 称为 **双变量高斯分布**。其 pdf 可表示为 \(\boldsymbol{x} \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})\)，其中 \(\boldsymbol{x} \in \mathbb{R}^2\)，\(\boldsymbol{\mu} \in \mathbb{R}^2\)，且

```
\(\boldsymbol{\Sigma} = \begin{pmatrix} \sigma_1^2 & \sigma_{12}^2 \\ \sigma_{21}^2 & \sigma_2^2 \end{pmatrix} = \begin{pmatrix} \sigma_1^2 & \rho \sigma_1 \sigma_2 \\ \rho \sigma_1 \sigma_2 & \sigma_2^2 \end{pmatrix}\)
```

![](img/ca72c1626f4850f058a9edc138c1ac73_54_0.png)

图 2.8: 基于等概率密度水平集的 2d 高斯密度可视化。(a) 完整协方差矩阵具有椭圆形等高线。(b) 对角协方差矩阵是轴对齐椭圆。(c) 球形协方差矩阵具有圆形。由 gauss_plot_2d.ipynb 生成。

其中相关系数由 $\rho \triangleq \frac{\sigma_{12}^2}{\sigma_1 \sigma_2}$ 给出。

图 2.8 绘制了三种不同类型协方差矩阵下 2d 中的部分 MVN 密度。**完整协方差矩阵**具有 \(D(D + 1)/2\) 个参数，由于 \(\mathbf{\Sigma}\) 是对称的，我们除以 2。**对角协方差矩阵**具有 \(D\) 个参数，且非对角线项为 \(0\)。**球形协方差矩阵**（也称为各向同性协方差矩阵）形式为 \(\mathbf{\Sigma} = \sigma^2 \mathbf{I}_D\)，因此它只有一个自由参数，即 \(\sigma^2\)。

#### 2.3.1.2 高斯球壳

多元高斯分布在高维中可能表现得相当反直觉。特别是，我们可以问：如果我们绘制样本 $\mathbf{x} \sim \mathcal{N}(\mathbf{0}, \mathbf{I}_D)$，其中 $D$ 是维度的数量，我们预期大多数 $\mathbf{x}$ 位于哪里？由于 pdf 的峰值（众数）位于原点，自然预期大多数样本靠近原点。然而，在高维中，高斯分布的典型集是一个薄球壳或环形，距离原点的距离为 $r = \sigma \sqrt{D}$，厚度为 $O(\sigma D^{\frac{1}{4}})$。其直观原因如下：尽管密度按 $e^{-r^2/2}$ 衰减，意味着从原点开始密度降低，但球体的体积按 $r^D$ 增长，意味着从原点开始体积增加，由于质量等于密度乘以体积，大多数点最终落在这两个术语“平衡”的这个环形中。这称为“高斯肥皂泡”现象，如图 2.9 所示。^6

要了解为什么高斯分布的典型集集中在半径 $\sqrt{D}$ 的薄环形中，请考虑点 $\mathbf{x}$ 到原点的平方距离，$d(\mathbf{x}) = \sqrt{\sum_{i=1}^D x_i^2}$，其中 $x_i \sim \mathcal{N}(0, 1)$。预期平方距离由 $\mathbb{E} [d^2] = \sum_{i=1}^D \mathbb{E} [x_i^2] = D$ 给出，平方距离的方差由 $\mathbb{V} [d^2] = \sum_{i=1}^D \mathbb{V} [x_i^2] = D$ 给出。随着 $D$ 增大，变异系数（即相对于均值的标准差）趋于零：

```
\lim_{D \to \infty} \frac{\text{std } [d^2]}{\mathbb{E} [d^2]} = \lim_{D \to \infty} \frac{\sqrt{D}}{D} = 0 \tag{2.74}
```

6. 有关更详细的解释，请参阅 Ferenc Huszar 的这篇博客文章：https://www.inference.vc/high-dimensional-gaussian-distributions-are-soap-bubble/。

![](img/ca72c1626f4850f058a9edc138c1ac73_55_0.png)

图 2.9: (a) 说明高斯分布的典型集为何不集中在分布众数处的卡通图。(b) 高斯分布典型集的图示，其集中在距离原点厚度为 \(\sigma D^{1/4}\)、距离为 \(\sigma D^{1/2}\) 的薄环形中。我们还展示了密度最高的图像（左侧全灰图像）以及一些高概率样本（右侧斑点噪声图像）。摘自 [Nal+19a] 的图 1。经 Eric Nalisnick 友好许可使用。

因此，预期平方距离集中在 \(D\) 附近，所以预期距离集中在 \(\mathbb{E}[d(\boldsymbol{x})] = \sqrt{D}\) 附近。更严格的证明见 [Ver18]，典型集的讨论见第 5.2.3 节。

为了了解这在图像背景下的含义，在图 2.9b 中，我们展示了一些从形式为 \(\mathcal{N}(\boldsymbol{\mu}, \sigma^2 \mathbf{I})\) 的高斯分布中采样的灰度图像，其中 \(\boldsymbol{\mu}\) 对应全灰图像。然而，随机采样的图像极不可能接近全灰，如图所示。

#### 2.3.1.3 MVN 的边缘分布和条件分布

让我们将随机变量向量 \(\boldsymbol{x}\) 划分为两部分，\(\boldsymbol{x}_1\) 和 \(\boldsymbol{x}_2$，因此

```
\(\boldsymbol{\mu} = \begin{pmatrix} \boldsymbol{\mu}_1 \\ \boldsymbol{\mu}_2 \end{pmatrix}, \quad \boldsymbol{\Sigma} = \begin{pmatrix} \boldsymbol{\Sigma}_{11} & \boldsymbol{\Sigma}_{12} \\ \boldsymbol{\Sigma}_{21} & \boldsymbol{\Sigma}_{22} \end{pmatrix}\)
```

该分布的边缘分布由以下给出（证明见第 2.3.1.5 节）：

```
\(p(\boldsymbol{x}_1) = \int \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})d\boldsymbol{x}_2 \triangleq \mathcal{N}(\boldsymbol{x}_1|\boldsymbol{\mu}_1^m, \boldsymbol{\Sigma}_1^m) = \mathcal{N}(\boldsymbol{x}_1|\boldsymbol{\mu}_1, \boldsymbol{\Sigma}_{11})\)
```

```
\(p(\boldsymbol{x}_2) = \int \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})d\boldsymbol{x}_1 \triangleq \mathcal{N}(\boldsymbol{x}_2|\boldsymbol{\mu}_2^m, \boldsymbol{\Sigma}_2^m) = \mathcal{N}(\boldsymbol{x}_2|\boldsymbol{\mu}_2, \boldsymbol{\Sigma}_{22})\)
```

条件分布可证明具有以下形式（证明见第 2.3.1.5 节）：

```
\(p(\boldsymbol{x}_1|\boldsymbol{x}_2) = \mathcal{N}(\boldsymbol{x}_1|\boldsymbol{\mu}_{1|2}^c, \boldsymbol{\Sigma}_{1|2}^c) = \mathcal{N}(\boldsymbol{x}_1|\boldsymbol{\mu}_1 + \boldsymbol{\Sigma}_{12} \boldsymbol{\Sigma}_{22}^{-1}(\boldsymbol{x}_2 - \boldsymbol{\mu}_2), \boldsymbol{\Sigma}_{11} - \boldsymbol{\Sigma}_{12} \boldsymbol{\Sigma}_{22}^{-1} \boldsymbol{\Sigma}_{21})\)
\(p(\boldsymbol{x}_2|\boldsymbol{x}_1) = \mathcal{N}(\boldsymbol{x}_2|\boldsymbol{\mu}_{2|1}^c, \boldsymbol{\Sigma}_{2|1}^c) = \mathcal{N}(\boldsymbol{x}_2|\boldsymbol{\mu}_2 + \boldsymbol{\Sigma}_{21} \boldsymbol{\Sigma}_{11}^{-1}(\boldsymbol{x}_1 - \boldsymbol{\mu}_1), \boldsymbol{\Sigma}_{22} - \boldsymbol{\Sigma}_{21} \boldsymbol{\Sigma}_{11}^{-1} \boldsymbol{\Sigma}_{12})\)
```

请注意，\(p(\boldsymbol{x}_1|\boldsymbol{x}_2)\) 的后验均值是 \(\boldsymbol{x}_2\) 的线性函数，但后验协方差与 \(\boldsymbol{x}_2\) 无关；这是高斯分布的一个特殊性质。

