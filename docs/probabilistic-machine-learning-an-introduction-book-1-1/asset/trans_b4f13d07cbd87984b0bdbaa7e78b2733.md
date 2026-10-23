
## 10.6 贝叶斯逻辑回归

到目前为止，我们主要关注参数的点估计，即最大似然估计（MLE）或最大后验估计（MAP）。然而，在某些情况下，我们需要计算后验分布 $p(\mathbf{w}|\mathcal{D})$，以捕捉我们的不确定性。这在数据量较少的场景中特别有用，而错误决策可能带来高昂代价；例如，这在在线广告领域就会出现（参见第 8.3 节）。

与线性回归不同，逻辑回归模型的后验分布无法精确计算。我们可以使用一系列近似算法，如我们在第 7.7 节中简要讨论的那样。在本节中，我们给出几种不同方法的示例。但在讨论如何近似后验分布之前，我们先讨论如何使用后验分布进行预测。

### 10.6.1 近似后验预测分布

后验分布 $p(\mathbf{w}|\mathcal{D})$ 告诉我们在给定数据的情况下，关于模型参数我们所知道的一切。然而，在机器学习应用中，主要任务通常是预测给定输入 $\mathbf{x}$ 的输出 $y$，而不是试图理解我们模型的参数。因此，我们需要计算后验预测分布：

$$
p(y|\mathbf{x}, \mathcal{D}) = \int p(y|\mathbf{x}, \mathbf{w}) p(\mathbf{w}|\mathcal{D}) \, d\mathbf{w} \tag{10.112}
$$

如我们在第 2.4.2 节中讨论的那样，一种简单的方法是首先计算参数的点估计 $\hat{\mathbf{w}}$，例如 MLE 或 MAP 估计，然后假设 $p(\mathbf{w}|\mathcal{D}) = \delta(\mathbf{w} - \hat{\mathbf{w}})$，从而忽略所有后验不确定性。在这种情况下，上述积分简化为以下代入近似：

$$
p(y|\mathbf{x}, \mathcal{D}) \approx \int p(y|\mathbf{x}, \mathbf{w}) \delta(\mathbf{w} - \hat{\mathbf{w}}) \, d\mathbf{w} = p(y|\mathbf{x}, \hat{\mathbf{w}}) \tag{10.113}
$$

然而，如果我们想要计算预测中的不确定性，我们应该使用非退化的后验分布。正如我们将看到的，使用高斯后验分布很常见。但我们仍然需要近似方程 (10.112) 中的积分。我们将在下面讨论一些方法。

#### 10.6.1.1 蒙特卡洛近似

最简单的方法是使用积分的蒙特卡洛近似。这意味着我们从后验分布中抽取 $S$ 个样本，$\mathbf{w}_s \sim p(\mathbf{w}|\mathcal{D})$，然后计算：

$$
p(y=1|\mathbf{x}, \mathcal{D}) \approx \frac{1}{S} \sum_{s=1}^{S} \sigma(\mathbf{w}_s^\top \mathbf{x}) \tag{10.114}
$$

#### 10.6.1.2 Probit 近似

虽然蒙特卡洛近似很简单，但它可能很慢，因为我们需要在测试时为每个输入 $\mathbf{x}$ 抽取 $S$ 个样本。幸运的是，如果 $p(\mathbf{w}|\mathcal{D}) = \mathcal{N}(\mathbf{w}|\boldsymbol{\mu}, \boldsymbol{\Sigma})$，存在一种简单且准确的确定性近似方法，最早由 [SL90] 提出。为了解释这种近似，我们遵循 [Bis06, p219] 的表述。关键观察点是，Sigmoid 函数 $\sigma(a)$ 在形状上与高斯累积分布函数（cdf，参见第 3.3.1 节）$\Phi(a)$ 相似。特别是，我们有 $\sigma(a) \approx \Phi(\lambda a)$，其中 $\lambda^2 = \pi/8$ 确保这两个函数在原点具有相同的斜率。这很有用，因为我们可以精确积分高斯累积分布函数相对于高斯概率密度函数：

$$
\int \Phi(\lambda a) \mathcal{N}(a|m, v) \, da = \Phi\left(\frac{m}{(\lambda^{-2}+v)^{1/2}}\right) = \Phi\left(\frac{\lambda m}{(1+\lambda^2v)^{1/2}}\right) \approx \sigma(\kappa(v)m) \tag{10.115}
$$

其中我们定义了：

$$
\kappa(v) \triangleq (1+\pi v/8)^{-1/2} \tag{10.116}
$$

因此，如果我们定义 $a = \mathbf{x}^{\mathsf T}\mathbf{w}$，我们有：

$$
p(y=1|\mathbf{x}, \mathcal{D}) \approx \sigma(\kappa(v)m) \tag{10.117}
$$

$$
m = \mathbb{E}[a] = \mathbf{x}^{\mathsf T}\boldsymbol{\mu} \tag{10.118}
$$

$$
v = \mathbb{V}[a] = \mathbb{V}[\mathbf{x}^{\mathsf T}\mathbf{w}] = \mathbf{x}^{\mathsf T}\boldsymbol{\Sigma}\mathbf{x} \tag{10.119}
$$

其中我们在最后一行使用了方程 (D.68)。由于 $\Phi^{-1}$ 被称为 Probit 函数，我们将这种近似方法称为 **Probit 近似**。

使用方程 (10.117) 得到的预测结果在置信度方面比代入估计更温和（不那么极端）。为了看出这一点，请注意 $0 < \kappa(v) < 1$，因此 $\kappa(v)m < m$，所以 $\sigma(\kappa(v)m)$ 比 $\sigma(m)$ 更接近 0.5。然而，决策边界本身不会受到影响。为了看出这一点，请注意决策边界是满足 $p(y=1|\mathbf{x}, \mathcal{D}) = 0.5$ 的点 $\mathbf{x}$ 的集合。这意味着 $\kappa(v)m = 0$，进而意味着 $m = \bar{\mathbf{w}}^{\mathsf T}\mathbf{x} = 0$；但这与来自代入估计的决策边界相同。因此，“采用贝叶斯方法”并不会改变误分类率（在这种情况下），但它确实改变了模型的置信度估计，这可能很重要，正如我们在第 10.6.2 节中展示的。

在多类情况下，[Nab01, p353] 建议将第 10.6.1.2 节中的 Spiegelhalter 方法扩展为如下形式：

$$
p(y=c|\mathbf{x}, \mathcal{D}) \approx \frac{\exp(\kappa(v_c)m_c)}{\sum_{c'}\exp(\kappa(v_{c'})m_{c'})} \tag{10.120}
$$

$$
m_c = \mathbf{m}_c^{\mathsf T}\mathbf{x} \tag{10.121}
$$

$$
v_c = \mathbf{x}^{\mathsf T}\mathbf{V}_{c,c}\mathbf{x} \tag{10.122}
$$

其中 $\kappa$ 定义在方程 (10.116) 中。与二元情况不同，考虑后验协方差会产生不同于代入方法的预测结果（参见 [RW06] 中的练习 3.10.3）。

### 10.6.2 拉普拉斯近似

如我们在第 7.7.2 节中讨论的，拉普拉斯近似使用高斯分布来近似后验分布。该高斯分布的均值等于 MAP 估计 $\hat{\mathbf{w}}$，协方差等于在 MAP 估计处计算的逆 Hessian 矩阵 $\mathbf{H}$，即 $p(\mathbf{w}|\mathcal{D}) \approx \mathcal{N}(\mathbf{w}|\hat{\mathbf{w}},\mathbf{H}^{-1})$。我们可以使用标准的优化方法找到模式（参见第 10.2.7 节），并可以使用第 10.2.3.4 节的结果来计算模式处的 Hessian 矩阵。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_0.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_1.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_2.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_338_3.png)

图 10.14：(a) 数据的图示。(b) 逻辑回归模型的对数似然。直线从原点沿 MLE 的方向绘制（MLE 位于无穷远处）。数字对应于参数空间中的 4 个点，对应于 (a) 中的线条。(c) 未归一化的对数后验（假设模糊球形先验）。(d) 后验分布的拉普拉斯近似。改编自 Mark Girolami 的图表。由 logregLaplaceGirolamiDemo.m 生成。

作为一个例子，考虑图 10.14(a) 中示意的数据。有许多参数设置对应于能够完美分离训练数据的直线；我们展示了 4 条示例线。似然曲面如图 10.14(b) 所示。对角线连接原点和网格中似然最大的点，$\hat{\mathbf{w}}_{mle} = (8.0, 3.4)$。（无约束 MLE 满足 $\|\mathbf{w}\| = \infty$，如我们在第 10.2.7 节中讨论的；可以通过沿对角线无限向右延伸来获得该点。）

对于图 10.14(a) 中的每个决策边界，我们在图 10.14(b) 中绘制了对应的参数向量。这些参数值为 $\mathbf{w}_1 = (3, 1)$，$\mathbf{w}_2 = (4, 2)$，$\mathbf{w}_3 = (5, 3)$，以及 $\mathbf{w}_4 = (7, 3)$。这些点都近似满足 $\mathbf{w}_i(1)/\mathbf{w}_i(2) \approx \hat{\mathbf{w}}_{mle}(1)/\hat{\mathbf{w}}_{mle}(2)$，因此它们接近最大似然决策边界的取向。这些点按权重范数递增的顺序排列（3.16, 4.47, 5.83 和 7.62）。

为了确保唯一解，我们使用以原点为中心的（球形）高斯先验，$\mathcal{N}(\mathbf{w}|0, \sigma^2 \mathbf{I})$。$\sigma^2$ 的值控制先验的强度。如果我们设置 $\sigma^2 = \infty$，我们强制 MAP 估计为 $\mathbf{w} = 0$；这将导致最大不确定性的预测，因为所有点 $\mathbf{x}$ 都会产生形式为 $p(y=1|\mathbf{x}) = 0.5$ 的预测分布。如果我们设置 $\sigma^2 = 0$，MAP 估计将变为 MLE，导致最小不确定性的预测。（特别地，所有正标签点将具有 $p(y = 1|\mathbf{x}) = 1.0$，所有负标签点将具有 $p(y = 1|\mathbf{x}) = 0.0$，因为数据是可分离的。）作为一种折衷（为了使图示更好看），我们选择 $\sigma^2 = 100$ 的值。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_0.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_1.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_2.png)
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_339_3.png)

图 10.15：二维逻辑回归模型的后验预测分布。左上：$p(y = 1|\mathbf{x}, \mathbf{w}_{map})$ 的等高线。右上：来自后验预测分布的样本。左下：对这些样本进行平均。右下：缓和的输出（Probit 近似）。改编自 Mark Girolami 的图表。由 logregLaplaceGirolamiDemo.m 生成。

将此先验与似然相乘，得到图 10.14(c) 中显示的未归一化后验分布。MAP 估计由蓝点表示。此分布的拉普拉斯近似显示在图 10.14(d) 中。我们可以看到，它正确地得到了模式（由构造决定），但后验分布的形状有些失真。（西南-东北方向的取向捕捉了关于 $\mathbf{w}$ 幅值的不确定性，而东南-西北方向的取向捕捉了关于决策边界取向的不确定性。）

在图 10.15 中，我们展示了后验预测分布的等高线。图 10.15(a) 显示了使用 MAP 估计的代入近似。我们可以看到，关于决策边界没有不确定性，即使我们正在生成标签的概率预测。图 10.15(b) 显示了当我们代入来自高斯后验的样本时会发生什么。现在我们看到关于“最佳”决策边界的取向存在相当大的不确定性。图 10.15(c) 显示了这些样本的平均值。通过对多个预测进行平均，我们看到决策边界的不确定性随着我们远离训练数据而“扩散”。图 10.15(d) 显示 Probit 近似给出了与蒙特卡洛近似非常相似的结果。

