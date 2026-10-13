

$$
\overline{\mathbf{x}} = \frac{1}{N}\sum\limits_{n = 1}^{N}\mathbf{x}_{n}
$$

![Equation](images/B9780443292385000263/si94.png)

*   `x` 表示原始（未中心化）向量。

*   PCA 基于分布在集合 $\mathcal{X}$ 中*所有*数据观测值上的*全局*信息。实际上，主要的信息来源是样本协方差矩阵 `XX^T`。因此，如果协方差矩阵能为手头的数据提供足够丰富的描述，PCA 就是有效的。例如，对于类高斯分布就是这种情况。文献 [41] 建议对标准方法进行修改，以处理具有聚类性质的数据。稍后，我们将讨论替代 PCA 的技术，以克服这一缺点。

*   计算大矩阵的 SVD 可能计算代价高昂，已经提出了许多高效技术（参见例如 [1,83,194]）。在许多实际情况下，会出现 `l > N` 的情况。当然，在这种情况下，样本协方差不可逆，且某些特征值为零。在这类场景下，最好使用 `X^T X` (`N × N`) 矩阵，而不是 `XX^T` (`l × l`) 矩阵。为此，可以利用第 [6.4](#Chp006_249-291_B9780443292385000123.xhtml) 节中给出的关系，从 `v[i]` 求得 `u[i]`。

*   PCA 的处理方式与 Fisher 线性判别 (FLD) 方法（第 [7](#Chp007_293-342_B9780443292385000135.xhtml) 章）有相似之处。它们都依赖于矩阵的特征结构，这些矩阵以某种方式编码了（协）方差信息。然而，请注意 PCA 是一种*无监督*方法，这与作为*有监督*方法的 FLD 形成对比。因此，PCA 执行降维以保留数据变异性（方差），而 FLD 则保留类别可分性。[图 20.3](#Chp020_1103-1179_B9780443292385000263.xhtml#f0025) 演示了所得（超）平面的差异。

![Figure 20.3 The case of a two-class task in the two-dimensional space. PCA computes the direction along which the variance is maximally retained after the projections of the data on it. In contrast, FLD computes the line so that the class separability is maximized.](images/B9780443292385000263/gr003.jpg)

[图 20.3](#Chp020_1103-1179_B9780443292385000263.xhtml#cf0365) 二维空间中两类任务的情况。PCA 计算数据投影到其上后方差最大保留的方向。相反，FLD 计算使类别可分性最大化的直线。

*   *多维缩放* (MDS) 是另一种线性技术，用于投影到低维空间，同时满足某些约束。给定集合 $\mathcal{X} \subset \mathbb{R}^{(l)}$，目标是投影到低维空间，使得内积得到最优保留；即代价

$$
E = \sum\limits_{i}\sum\limits_{j}\left( \mathbf{x}_{i}^{T}\mathbf{x}_{j} - \mathbf{z}_{i}^{T}\mathbf{z}_{j} \right)^{2}
$$

![Equation](images/B9780443292385000263/si100.png)

*   最小化，其中 `z_i` 是 `x_i` 的像，求和遍历 $\mathcal{X}$ 中所有训练点。该问题类似于 PCA，可以证明解由 Gram 矩阵的特征分解给出，^([^(156)](#fn156))

*   关于这些问题的更多内容可参见 [29,60]。正如我们将在第 [20.9](#Chp020_1103-1179_B9780443292385000263.xhtml#s0145) 节中很快看到的，MDS 保持距离的主要思想以某种方式被用于许多最近开发的非线性降维技术中。

