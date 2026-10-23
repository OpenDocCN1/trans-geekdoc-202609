

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_689_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_689_1.png)

*图20.31：将度量型MDS应用于(a) Swiss roll。由manifold_swiss_sklearn.py生成 (b) UCI数字。由manifold_digits_sklearn.py生成。*

其中 $\hat{d}_{ij} = \|\mathbf{z}_i - \mathbf{z}_j\|$。这被称为**度量型MDS**。请注意，这与经典MDS所使用的目标不同，因此即使 $d_{ij}$ 是欧氏距离，结果也会有所不同。

我们可以使用梯度下降来求解这个优化问题。然而，更好的做法是使用一种称为**SMACOF** [Lee77] 的边界优化算法（第5.7节），其全称是“Scaling by MAjorizing a COmplicated Function”。（这也是scikit-learn中实现的方法。）将其应用于我们运行示例的结果见图20.31。

## 20.4.4.3 非度量型MDS

与试图匹配点之间的距离不同，我们可以只尝试匹配点之间相似度的排序。为此，令 $f(d)$ 为从距离到排序的单调变换。现在定义损失

\[
\mathcal{L}_{\text{NM}}(\mathbf{Z}) = \sqrt{\frac{\sum_{i<j}(f(d_{ij}) - \hat{d}_{ij})^2}{\sum_{i<j} \hat{d}_{ij}^2}} \tag{20.110}
\]

其中 $\hat{d}_{ij} = \|\mathbf{z}_i - \mathbf{z}_j\|$。最小化该目标被称为**非度量型MDS**。

该目标可以通过迭代方式进行优化。首先，在给定 $\mathbf{Z}$ 的情况下，使用保序回归优化函数 $f$；这会找到输入距离的最优单调变换，以匹配当前的嵌入距离。然后，在给定 $f$ 的情况下，使用梯度下降优化嵌入 $\mathbf{Z}$，并重复此过程。

## 20.4.4.4 Sammon映射

度量型MDS试图最小化距离平方和，因此它最重视大距离。然而，对于许多嵌入方法而言，小距离更为重要，因为它们捕捉了局部结构。一种捕捉这一点的方法是将损失函数的每一项除以 $d_{ij}$，从而使小距离获得更大的权重：

\[
\mathcal{L}_{\text{sammon}}(\mathbf{Z}) = \left(\frac{1}{\sum_{i<j} d_{ij}}\right) \sum_{i<j} \frac{(\hat{d}_{ij} - d_{ij})^2}{d_{ij}} \tag{20.111}
\]

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_690_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_690_1.png)

*图20.32：(a) 如果我们沿流形测量距离，会发现d(1,6) > d(1,4)，而如果在环境空间中测量，会发现d(1,6) < d(1,4)。底部的图显示了底层的一维流形。(b) 某些数据点的K近邻图；红色路径是该图上A和B之间的最短距离。引自[Hin13]。经Geoff Hinton善意许可使用。*

最小化该目标将得到Sammon映射。（求和项前面的系数只是为了简化损失的梯度。）不幸的是，这是一个非凸目标，而且可以说它过于强调将非常小的距离精确匹配。我们稍后将讨论更好的捕捉局部结构的方法。

## 20.4.5 Isomap

如果高维数据位于弯曲流形上或附近，例如Swiss roll示例，那么即使两个点沿流形的距离很大，MDS也可能认为它们很近。如图20.32a所示。

一种捕捉这一点的方法是创建数据点之间的K近邻图⁶，然后通过该图上的最短距离来近似一对点之间的流形距离；这可以使用Dijkstra最短路径算法高效计算。参见图20.32b的图示。一旦我们计算出了这个新的距离度量，就可以应用经典MDS（即PCA）。这是一种在避免局部最优的同时捕捉局部结构的方法。整个方法称为Isomap [TSL00]。

6. 在scikit-learn中，可以使用函数 `sklearn.neighbors.kneighbors_graph`。

该方法在我们运行示例上的结果见图20.33。我们可以看到这些结果相当合理。然而，如果数据有噪声，近邻图中可能会出现“虚假”边，从而导致“短路”，显著扭曲嵌入结果，如图20.34所示。这个问题被称为“拓扑不稳定性” [BS02]。选择非常小的邻域并不能解决这个问题，因为这会将流形分割成大量不连通的区域。人们还提出了其他各种解决方案，例如 [CC07]。

## 20.4.6 核PCA

PCA（以及经典MDS）寻找数据的最佳线性投影，以保留所有点之间的两两相似性。在本节中，我们考虑非线性投影。关键思想

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_693_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_693_1.png)

*图20.36：将核PCA应用于(a) Swiss roll。由manifold_swiss_sklearn.py生成。(b) UCI数字。由manifold_digits_sklearn.py生成。*

## 20.4.7 最大方差展开

该算法 [WSS04] 也被称为**最大方差展开**，它试图学习一个嵌入 $\{\mathbf{z}_i\}$，使得

\[
\max_{\mathbf{Z}} \sum_{ij} \|\mathbf{z}_i - \mathbf{z}_j\|_2^2 \quad \text{s.t.} \quad \|\mathbf{z}_i - \mathbf{z}_j\|_2^2 = \|\mathbf{x}_i - \mathbf{x}_j\|_2^2 \quad \text{for all } (i,j) \in G \tag{20.113}
\]

其中 $G$ 是近邻图（与Isomap中相同）。这种方法显式地尝试在满足近邻约束的同时“展开”数据流形。

通过定义核矩阵 $\mathbf{K} = \mathbf{Z}\mathbf{Z}^\top$ 并进行优化，这可以被重新表述为一个**半定规划**（SDP）问题

\[
\max_{\mathbf{K}} \mathrm{tr}(\mathbf{K}) \quad \text{s.t.} \quad \|\mathbf{z}_i - \mathbf{z}_j\|_2^2 = \|\mathbf{x}_i - \mathbf{x}_j\|_2^2 \;\; \forall (i,j) \in G,\quad \sum_{ij} K_{ij} = 0,\quad \mathbf{K} \succeq 0 \tag{20.114}
\]

然后将得到的核传递给kPCA，得到的特征向量即为低维嵌入。

## 20.4.8 局部线性嵌入（LLE）

到目前为止我们讨论的技术都依赖于两两相似性全矩阵的特征分解，无论是在原始空间（PCA）、特征空间（kPCA）还是沿KNN图（Isomap）。在本节中，我们讨论**局部线性嵌入**（LLE）[RS00]，这是一种求解稀疏特征问题的技术，因此更关注数据中的局部结构。

LLE假设每个点 $\mathbf{x}_i$ 周围的数据流形是局部线性的。最佳线性近似可以通过使用重构权重 $w_i$ 将 $\mathbf{x}_i$ 预测为其 $K$ 个最近邻的线性组合来获得。这可以通过求解以下问题得到

\[
\hat{\mathbf{W}} = \arg\min_{\mathbf{W}} \sum_{i=1}^{N} \left( \mathbf{x}_i - \sum_{j=1}^{N} w_{ij} \mathbf{x}_j \right)^2 \tag{20.115}
\]

约束条件为

\[
w_{ij} = 0 \quad \text{if } \mathbf{x}_j \notin \operatorname{nbr}(\mathbf{x}_i, K); \qquad \sum_{j=1}^{N} w_{ij} = 1 \quad \text{for } i = 1,\ldots,N \tag{20.116}
\]

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_694_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_694_1.png)

*图20.37：将LLE应用于(a) Swiss roll。由manifold_swiss_sklearn.py生成。(b) UCI数字。由manifold_digits_sklearn.py生成。*

注意，我们需要对权重施加和为1的约束，以防止平凡解 $\mathbf{W} = \mathbf{0}$。得到的权重向量 $\mathbf{w}_{i,:}$ 构成了 $\mathbf{x}_i$ 的**重心坐标**。

该超平面到低维空间的任何线性映射都会保持重构权重，从而保持局部几何结构。因此，我们可以通过求解以下问题来得到每个点的低维嵌入

\[
\hat{\mathbf{Z}} = \arg\min_{\mathbf{Z}} \sum_i \left\| \mathbf{z}_i - \sum_{j=1}^{N} \hat{w}_{ij} \mathbf{z}_j \right\|_2^2 \tag{20.117}
\]

其中，如果 $j$ 不是 $i$ 的 $K$ 个最近邻之一，则 $\hat{w}_{ij}=0$。我们可以将此损失重写为

\[
\mathcal{L}(\mathbf{Z}) = \| \mathbf{Z} - \mathbf{W}\mathbf{Z} \|^2 = \mathbf{Z}^\top (\mathbf{I} - \mathbf{W})^\top (\mathbf{I} - \mathbf{W})\mathbf{Z} \tag{20.118}
\]

因此，解由 $(\mathbf{I} - \mathbf{W})^\top (\mathbf{I} - \mathbf{W})$ 对应于最小非零特征值的特征向量给出，如第C.4.8节所示。

LLE在我们运行示例上的一些结果见图20.37。在这种情况下，结果似乎不如Isomap产生的结果好。然而，该方法对短路（噪声）的敏感度往往稍低一些。

## 20.4.9 拉普拉斯特征映射

在本节中，我们描述**拉普拉斯特征映射**或**谱嵌入** [BN01]。其思想是计算数据的低维表示，使得数据点与其 $K$ 个最近邻之间的加权距离最小化。我们对第一个最近邻赋予比第二个更大的权重，依此类推。下面给出详细说明。

### 20.4.9.1 使用图拉普拉斯算子的特征向量计算嵌入

我们希望找到使以下损失最小化的嵌入

\[
\mathcal{L}(\mathbf{Z}) = \sum_{(i,j)\in E} W_{i,j} \|\mathbf{z}_i - \mathbf{z}_j\|_2^2 \tag{20.119}
\]

