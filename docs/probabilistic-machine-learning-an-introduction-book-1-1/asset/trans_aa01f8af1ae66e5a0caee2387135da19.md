
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_92_0.png)

Figure 3.11: 2d 高斯密度作为曲面图的可视化。 (a) 使用完整协方差矩阵的分布可以以任意角度定向。 (b) 使用对角协方差矩阵的分布必须与轴平行。 (c) 使用球形协方差矩阵的分布必须具有对称形状。 由 gauss_plot_2d.py 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_92_1.png)

Figure 3.12: 2d 高斯密度以恒定概率密度水平集形式的可视化。 (a) 完整协方差矩阵具有椭圆形轮廓。 (b) 对角协方差矩阵是轴对齐的椭圆。 (c) 球形协方差矩阵具有圆形形状。 由 gauss_plot_2d.py 生成。

图 3.11 和图 3.12 绘制了三种不同类型协方差矩阵在 2d 中的一些 MVN 密度。 完整协方差矩阵有 \(D(D+1)/2\) 个参数，其中除以 2 是因为 \(\boldsymbol{\Sigma}\) 是对称的。 （椭圆形形状的原因在 Sec. C.4.4 中有解释，其中我们讨论二次型的几何形状。） 对角协方差矩阵有 \(D\) 个参数，且非对角项为 0。 球形协方差矩阵，也称为各向同性协方差矩阵，具有形式 \(\boldsymbol{\Sigma}=\sigma^2 \mathbf{I}_D\)，因此它只有一个自由参数，即 \(\sigma^2\)。

## 3.5.2 马哈拉诺比斯距离

在本节中，我们尝试深入了解多维高斯 pdf 的几何形状。 为此，我们将考虑恒定（对数）概率的水平集的形状。

特定点 \(\mathbf{x}\) 处的对数概率由下式给出

\[
\log p(\mathbf{x}|\boldsymbol{\mu},\boldsymbol{\Sigma})=-\frac{1}{2}(\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})+\mathrm{const} \tag{3.85}
\]

\(\mathbf{x}\) 的依赖关系可以用 \(\mathbf{x}\) 与 \(\boldsymbol{\mu}\) 之间的 **Mahalanobis distance** \(\Delta\) 来表示，其平方定义如下：

\[
\Delta^2 \triangleq (\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu}) \tag{3.86}
\]

因此，恒定（对数）概率的轮廓等价于恒定马哈拉诺比斯距离的轮廓。

为了深入了解恒定马哈拉诺比斯距离的轮廓，我们利用 \(\boldsymbol{\Sigma}\) 和 \(\boldsymbol{\Lambda}=\boldsymbol{\Sigma}^{-1}\) 都是正定矩阵（根据假设）这一事实。 考虑 \(\boldsymbol{\Sigma}\) 的以下特征分解（附录 C.4）：

\[
\boldsymbol{\Sigma}=\sum_{d=1}^{D}\lambda_d\mathbf{u}_d\mathbf{u}_d^\mathsf{T} \tag{3.87}
\]

我们可以类似地写出

\[
\boldsymbol{\Sigma}^{-1}=\sum_{d=1}^{D}\frac{1}{\lambda_d}\mathbf{u}_d\mathbf{u}_d^\mathsf{T} \tag{3.88}
\]

令 \(z_d\triangleq\mathbf{u}_d^\mathsf{T}(\mathbf{x}-\boldsymbol{\mu})\)，则 \(\mathbf{z}=\mathbf{U}(\mathbf{x}-\boldsymbol{\mu})\)。 然后我们可以将马哈拉诺比斯距离重写如下：

\[
(\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})=(\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\left(\sum_{d=1}^{D}\frac{1}{\lambda_d}\mathbf{u}_d\mathbf{u}_d^\mathsf{T}\right)(\mathbf{x}-\boldsymbol{\mu}) \tag{3.89}
\]

\[
=\sum_{d=1}^{D}\frac{1}{\lambda_d}(\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\mathbf{u}_d\mathbf{u}_d^\mathsf{T}(\mathbf{x}-\boldsymbol{\mu})=\sum_{d=1}^{D}\frac{z_d^2}{\lambda_d} \tag{3.90}
\]

正如我们在 Sec. C.4.4 中讨论的那样，这意味着我们可以将马哈拉诺比斯距离解释为在新的坐标系 \(\mathbf{z}\) 中的欧几里得距离，其中我们通过 \(\mathbf{U}\) 旋转 \(\mathbf{x}\) 并通过 \(\boldsymbol{\Lambda}\) 缩放。

例如，在 2d 中，让我们考虑满足以下方程的点 \((z_1,z_2)\) 集合：

\[
\frac{z_1^2}{\lambda_1}+\frac{z_2^2}{\lambda_2}=r \tag{3.91}
\]

由于这些点具有相同的马哈拉诺比斯距离，因此它们对应于等概率点。 因此我们看到 2d 高斯的等概率密度轮廓沿椭圆分布。 这在图 C.6 中有所说明。 特征向量决定了椭圆的方向，特征值决定了其拉伸程度。

我们也可以通过线性映射 \(\mathbf{L}\) 来定义马哈拉诺比斯距离，使得 \(\boldsymbol{\Sigma}^{-1}=\mathbf{L}^\mathsf{T}\mathbf{L}\)，其中 \(\mathbf{L}\) 可以从 \(\mathbb{R}^D\) 映射到 \(\mathbb{R}^d\)，其中 \(d\leq D\)。 然后我们有

\[
(\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})=(\mathbf{x}-\boldsymbol{\mu})^\mathsf{T}\mathbf{L}^\mathsf{T}\mathbf{L}(\mathbf{x}-\boldsymbol{\mu})=(\mathbf{L}\boldsymbol{\delta})^\mathsf{T}(\mathbf{L}\boldsymbol{\delta})=\|\mathbf{L}\boldsymbol{\delta}\|_2^2 \tag{3.92}
\]

其中 \(\boldsymbol{\delta}=\mathbf{x}-\boldsymbol{\mu}\)。 这可以被认为是在低维空间中测量欧几里得距离。

## 3.5.3 MVN 的边缘分布和条件分布

假设我们有两个离散随机变量，\(Y_1\) 和 \(Y_2\)。 我们可以将它们的联合分布表示为一个 2d 表，其所有条目之和为一。 例如，考虑以下两个二元变量的示例：

| \(p(Y_1,Y_2)\) | \(Y_2=0\) | \(Y_2=1\) |
|---|---|---|
| \(Y_1=0\) | 0.2 | 0.3 |
| \(Y_1=1\) | 0.3 | 0.2 |

给定联合分布，我们按如下方式定义边缘分布：

\[
p(Y_2=y_2)=\sum_{y_1} p(Y_1=y_1,Y_2=y_2) \tag{3.93}
\]

我们按如下方式定义条件分布：

\[
p(Y_1=y_1|Y_2=y_2)=\frac{p(Y_1=y_1,Y_2=y_2)}{p(Y_2=y_2)} \tag{3.94}
\]

我们现在讨论如何将这些结果推广到联合高斯随机变量，其中用积分代替求和。 我们将随机变量向量 \(\mathbf{x}\) 分为两部分 \(\mathbf{x}_1\) 和 \(\mathbf{x}_2\)，其中 \(\mathbf{x}_2\) 是我们感兴趣的变量，而 \(\mathbf{x}_1\) 称为干扰变量。 \(\mathbf{x}_2\) 的边缘分布可以通过积分消去 \(\mathbf{x}_1\) 如下计算：

\[
p(\mathbf{x}_2)=\int \mathcal{N}(\mathbf{x}|\boldsymbol{\mu},\boldsymbol{\Sigma})\,d\mathbf{x}_1=\mathcal{N}(\mathbf{x}_2|\boldsymbol{\mu}_2,\boldsymbol{\Sigma}_{22}) \tag{3.95}
\]

其中我们定义了（矩）参数的以下划分：

\[
\boldsymbol{\mu}=\begin{pmatrix}\boldsymbol{\mu}_1\\ \boldsymbol{\mu}_2\end{pmatrix},\quad
\boldsymbol{\Sigma}=\begin{pmatrix}\boldsymbol{\Sigma}_{11} & \boldsymbol{\Sigma}_{12}\\ \boldsymbol{\Sigma}_{21} & \boldsymbol{\Sigma}_{22}\end{pmatrix} \tag{3.96}
\]

现在假设我们观察到 \(\mathbf{x}_2\) 的值，并且我们想根据此观测预测 \(\mathbf{x}_1\) 的值。 也就是说，我们想将先验分布 \(p(\mathbf{x}_1)\)（它代表我们在看到任何观测之前对 \(\mathbf{x}_1\) 值的信念）转换为后验分布 \(p(\mathbf{x}_1|\mathbf{x}_2)\)（它代表我们在看到 \(\mathbf{x}_2\) 之后（后验）对 \(\mathbf{x}_1\) 值的信念）。 练习 3.8 要求你推导出以下重要结果：

\[
p(\mathbf{x}_1|\mathbf{x}_2)=\mathcal{N}\left(\mathbf{x}_1\,\middle|\, \boldsymbol{\mu}_1+\boldsymbol{\Sigma}_{12}\boldsymbol{\Sigma}_{22}^{-1}(\mathbf{x}_2-\boldsymbol{\mu}_2),\; \boldsymbol{\Sigma}_{11}-\boldsymbol{\Sigma}_{12}\boldsymbol{\Sigma}_{22}^{-1}\boldsymbol{\Sigma}_{21}\right) \tag{3.97}
\]

请注意，后验均值是 \(\mathbf{x}_2\) 的线性函数，但后验协方差与 \(\mathbf{x}_2\) 无关。 有关简单示例，请参阅练习 3.5。

## 3.5.4 示例：插补缺失值

作为上述结果的一个示例应用，假设我们观察到 \(\mathbf{x}\) 的某些部分（维度），其余部分缺失或未观测。 我们可以利用维度之间的相关性（由协方差矩阵编码）来推断缺失条目； 这称为缺失值插补。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_95_0.png)

Figure 3.13: 使用 MVN 进行数据插补的说明。 (a) 数据矩阵的可视化。 空白条目缺失（未观测）。 红色为正，绿色为负。 正方形的面积与值成正比。 （这被称为 Hinton 图，以著名 ML 研究员 Geoff Hinton 的名字命名。） (b) 真实数据矩阵（隐藏）。 (c) 基于该行部分观测数据、使用真实模型参数的后验预测分布的均值。 由 gaussImputationDemo.m 生成。

图 3.13 显示了一个简单示例。 我们从 \(D=10\) 维高斯分布中采样 \(N\) 个向量，然后故意在每个样本（行）中“隐藏” 50% 的数据。 然后我们根据观测条目和真实模型参数推断缺失条目。 更精确地说，对于数据矩阵的每一行 \(n\)，我们计算 \(p(\mathbf{x}_{n,h}|\mathbf{x}_{n,v},\boldsymbol{\theta})\)，其中 \(v\) 是该行可见条目的索引，\(h\) 是隐藏条目的剩余索引，且 \(\boldsymbol{\theta}=(\boldsymbol{\mu},\boldsymbol{\Sigma})\)。 由此，我们计算每个缺失变量 \(i\in h\) 的边缘分布 \(p(x_{n,i}|\mathbf{x}_{n,v},\boldsymbol{\theta})\)。 从边缘分布中，我们计算后验均值 \(\bar{x}_{n,i}=\mathbb{E}[x_{n,i}|\mathbf{x}_{n,v},\boldsymbol{\theta}]\)。

后验均值代表我们对该条目真实值的“最佳猜测”，其含义是它最小化了我们的期望平方误差，如第 8 章所述。 我们可以使用 \(\mathrm{Var}[x_{n,i}|\mathbf{x}_{n,v},\boldsymbol{\theta}]\) 作为对该猜测的置信度度量，尽管这里未显示。 或者，我们可以从 \(p(\mathbf{x}_{n,h}|\mathbf{x}_{n,v},\boldsymbol{\theta})\) 中抽取多个后验样本； 这称为多重插补，并为下游消耗“填补”数据的算法提供更稳健的估计。

## 3.6 线性高斯系统

在第 3.5.3 节中，我们对无噪声观测进行条件化以推断高斯随机向量隐藏部分的后验。 在本节中，我们扩展这种方法以处理噪声观测。

设 \(\mathbf{z}\in\mathbb{R}^D\) 为未知值向量，\(\mathbf{y}\in\mathbb{R}^K\) 为 \(\mathbf{z}\) 的某种噪声测量。 我们假设这些变量由以下联合分布相关：

\[
p(\mathbf{z})=\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_z,\boldsymbol{\Sigma}_z) \tag{3.98}
\]

\[
p(\mathbf{y}|\mathbf{z})=\mathcal{N}(\mathbf{y}|\mathbf{W}\mathbf{z}+\mathbf{b},\boldsymbol{\Sigma}_y) \tag{3.99}
\]

其中 \(\mathbf{W}\) 是大小为 \(K\times D\) 的矩阵。 这是线性高斯系统的一个例子。
