

![](img/ca72c1626f4850f058a9edc138c1ac73_636_0.png)

![](img/ca72c1626f4850f058a9edc138c1ac73_636_1.png)

图 15.5：(a) 当对截距项使用 $\mathcal{N}(0, \omega)$ 前验时，逻辑回归输出的前验，其中 $\omega = 10$ 或 $\omega = 1.5$。改编自 [McE20] 中的图 11.3。由 `logreg_prior_offset.ipynb` 生成。(b) 当对随机二元特征向量（维数不断增加）使用二元逻辑回归时，我们预期看到的 1 的比例分布。我们对回归系数使用 $\mathcal{N}(0, 1.5)$ 前验。改编自 [Gel+20] 中的图 3。由 `logreg_prior.ipynb` 生成。

根据输入，概率会增加或减少。但是，我们如何设置前验方差呢？使用较大的值来近似均匀分布很诱人，但这是个坏主意。

为了了解原因，请考虑一个仅具有截距项且没有特征的二元逻辑回归模型：

$p(y|\theta) = \text{Ber}(y|\sigma(\alpha))$ (15.143)
$p(\alpha) = \mathcal{N}(\alpha|0, \omega)$ (15.144)

如果我们将前验设置为较大的 $\omega = 10$，则 $y$ 的隐含前验是一种极端分布，其大部分密度集中在 0 或 1 附近，如图 15.5a 所示。相比之下，如果我们使用较小的 $\omega = 1.5$，则得到一个较平坦的分布，如图所示。

如果我们有输入特征，问题会变得棘手一些，因为 logits 的大小现在将取决于输入变量的数量和分布。例如，假设我们生成 $N$ 个随机二元向量 $x_n$，每个维度为 $D$，其中 $x_{nd} \sim \text{Ber}(p)$，且 $p = 0.8$。然后我们计算 $p(y_n = 1 | x_n) = \sigma(\beta^T x_n)$，其中 $\beta \sim \mathcal{N}(0, 1.5 \mathbf{I})$。我们对 $\beta$ 采样 $S$ 个值，并且对于每个值，我们从上述分布中采样一个标签向量 $y_{1:N:S}$。然后我们计算正标签的比例 $f_s = \frac{1}{N} \sum_{n=1}^N \mathbb{I}(y_{n,s} = 1)$。我们在图 15.5b 中将 $\{f_s\}$ 的分布作为 $D$ 的函数进行绘制。我们可以看到，诱导的前验起初是平坦的，但最终会向 0 和 1 的极端值倾斜。为了避免这种情况，我们应该对输入进行标准化，并将前验的方差按 $1/\sqrt{D}$ 进行缩放。我们也可以使用重尾分布，例如柯西分布或 Student 分布 [Gel+08; GLM15]，而不是高斯前验。

## 15.3.5 后验的拉普拉斯近似

不幸的是，与线性回归不同，我们无法解析地计算后验，因为没有相应的共轭前验。（这与 MLE 的情况类似，线性回归有封闭式解，但逻辑回归没有。）幸运的是，我们可以使用一系列近似推断方法。

在本节中，我们使用拉普拉斯近似。如在第 7.4.3 节中所述，这使用高斯分布来近似后验。高斯分布的均值等于 MAP 估计 $\hat{\mathbf{w}}$，协方差等于在 MAP 估计处计算的逆海森矩阵 $\mathbf{H}$，即，

\(p(\mathbf{w}|\mathcal{D}) \approx \mathcal{N}(\mathbf{w}|\hat{\mathbf{w}},\mathbf{H}^{-1}), \hat{\mathbf{w}} = \arg \min - \log p(\mathbf{w}, \mathcal{D}), \mathbf{H} = -\nabla^2_{\mathbf{w}} \log p(\mathbf{w}, \mathcal{D})|_{\hat{\mathbf{w}}}\) (15.145)

我们可以使用标准优化方法找到众数，然后可以在众数处解析地或使用自动微分来计算海森矩阵。

举例来说，请考虑图 15.6(a) 中所示的二元数据。有许多参数设置对应于能够完美分离训练数据的直线；我们展示了 4 条示例直线。对于图 15.6(a) 中的每个决策边界，我们将相应的参数向量作为图 15.6(b) 中对数似然曲面上的点进行绘制。这些参数值为 $\mathbf{w}_1 = (3, 1), \mathbf{w}_2 = (4, 2), \mathbf{w}_3 = (5, 3)$，和 $\mathbf{w}_4 = (7, 3)$。这些点都近似满足 $\mathbf{w}_i(1)/\mathbf{w}_i(2) \approx \hat{\mathbf{w}}_{\text{mle}}(1)/\hat{\mathbf{w}}_{\text{mle}}(2)$，因此接近最大似然决策边界的方向。这些点按权重范数递增排序（3.16、4.47、5.83 和 7.62）。无约束的 MLE 具有 $||\boldsymbol{w}||=\infty$，因此在右上角无限远处。

为了确保唯一解，我们使用以原点为中心的（球形）高斯前验，$\mathcal{N}(\boldsymbol{w}|\boldsymbol{0},\sigma^2\boldsymbol{I})$。
$\sigma^2$ 的值控制前验的强度。如果我们设置 $\sigma^2=\infty$，则强制 MAP 估计为 $\boldsymbol{w}=\boldsymbol{0}$；这将导致最不确定的预测，因为所有点 $\boldsymbol{x}$ 都会产生形式为 $p(y=1|\boldsymbol{x})=0.5$ 的预测分布。如果我们设置 $\sigma^2=0$，MAP 估计将变为 MLE，从而导致最不确定的预测。（具体来说，所有正标记点都将具有 $p(y=1|\boldsymbol{x})=1.0$，所有负标记点都将具有 $p(y=1|\boldsymbol{x})=0.0$，因为数据是可分的。）作为一种折中（为了制作良好的示例），我们选择 $\sigma^2=100$ 的值。
将此前验与似然相乘，得到图 15.6(c) 中所示的未归一化后验。蓝点表示 MAP 估计。该后验的拉普拉斯近似在图 15.6(d) 中显示。我们可以看到，它正确地得到了众数（由构造决定），但后验的形状有些扭曲。（西南-东北方向捕捉了关于 $\boldsymbol{w}$ 大小的不确定性，而东南-西北方向捕捉了关于决策边界方向的不确定性。）

## 15.3.6 近似后验预测分布

接下来，我们需要将参数的后验转换为预测的后验，如下所示：

\(p(y|\boldsymbol{x},\mathcal{D})=\int p(y|\boldsymbol{x},\boldsymbol{w})p(\boldsymbol{w}|\mathcal{D})d\boldsymbol{w}\) (15.146)

计算该积分的最简单方法是使用蒙特卡洛近似。例如，在二元逻辑回归的情况下，我们有

\(p(y=1|\boldsymbol{x},\mathcal{D})\approx\frac{1}{S}\sum_{s=1}^S \sigma(\boldsymbol{w}_s^\top\boldsymbol{x})\) (15.147)

其中 $\boldsymbol{w}_s\sim p(\boldsymbol{w}|\mathcal{D})$ 是后验样本。

然而，我们也可以对积分使用确定性近似，这通常更快。给定测试点 $\boldsymbol{x}_*$，令 $\boldsymbol{f}_*=f(\boldsymbol{x}_*,\boldsymbol{w})$ 为 sigmoid/softmax 层之前的预测 logits。如果参数的后验是高斯分布，$p(\boldsymbol{w}|\mathcal{D})=\mathcal{N}(\boldsymbol{\mu},\boldsymbol{\Sigma})$，那么 logits 上的预测分布也是高斯分布：

\(p(\boldsymbol{f}_*|\boldsymbol{x}_*,\mathcal{D})=\int\delta(\boldsymbol{f}_*-f(\boldsymbol{x}_*,\boldsymbol{w}))\mathcal{N}(\boldsymbol{w}|\boldsymbol{\mu},\boldsymbol{\Sigma})d\boldsymbol{w}=\mathcal{N}(\boldsymbol{f}_*|\boldsymbol{\mu}^\top\boldsymbol{x}_*,\boldsymbol{x}_*^\top\boldsymbol{\Sigma}\boldsymbol{x}_*)\stackrel{\text{def}}{=}\mathcal{N}(\boldsymbol{f}_*|\boldsymbol{\mu}_*,\boldsymbol{\Sigma}_*)\) (15.148)

在二元逻辑回归的情况下，我们可以用 probit 函数 $\Phi$ 近似 sigmoid（参见第 15.4 节），这使我们能够解析地求解积分：

\(p(y_*|\boldsymbol{x}_*)\approx\int\Phi(f_*)\mathcal{N}(f_*|\mu_*,\sigma_*^2)df_*=\sigma\left(\frac{\mu_*}{\sqrt{1+\frac{\pi}{8}\sigma_*^2}}\right)\) (15.149)

