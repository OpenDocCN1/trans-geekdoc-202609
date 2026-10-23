
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_311_0.png)

图10.2：\(\sigma(w_1 x_1 + w_2 x_2)\) 的图形。这里 \(w = (w_1, w_2)\) 定义了决策边界的法线。该法线右侧的点满足 \(\sigma(w^\top x) > 0.5\)，左侧的点满足 \(\sigma(w^\top x) < 0.5\)。改编自 [Mac03] 的图39.3。由 sigmoid_2d_plot.py 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_311_1.png)

图10.3：说明如何通过将特征从 \(x = (x_1, x_2)\) 变换为 \(\phi(x) = (x_1^2, x_2^2)\)，将二次决策边界转换为线性决策边界。经 Jean-Philippe Vert 友好许可使用。

函数 f 在参数 w 上仍然是线性的，这对于简化学习问题很重要，我们将在第10.2.3节中看到。然而，除了学习线性权重 w 之外，我们还可以通过学习特征提取器 \(\phi(x)\) 的参数来获得更强的能力；我们将在第三部分讨论如何做到这一点。

在图10.3中，我们使用了特征的二次展开。我们也可以使用更高阶的多项式，如第1.2.2.2节所示。在图1.8中，我们展示了在二维逻辑回归问题上使用最高 K 次多项式展开的效果。如图1.8所示，我们看到随着参数数量的增加，模型变得更加复杂，最终会导致过拟合。我们将在第10.2.7节讨论减少过拟合的方法。

未经 Kevin P. Murphy 和 MIT Press 许可，不得分发。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_312_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_312_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_312_2.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_312_3.png)

图10.4：将多项式特征展开应用于一个二类二维逻辑回归问题。(a) 次数 K = 1。(b) 次数 K = 2。(c) 次数 K = 4。(d) 训练和测试误差随次数的变化。由 logreg_poly_demo.py 生成。

## 10.2.3 最大似然估计

在本节中，我们讨论如何使用最大似然估计来估计逻辑回归模型的参数。

### 10.2.3.1 目标函数

为了记号的简洁，忽略偏置项，负对数似然（NLL）由下式给出：

$$\text{NLL}(\mathbf{w}) = -\log \prod_{n=1}^{N} \text{Ber}(y_n|\mu_n) \tag{10.6}$$
$$= -\sum_{n=1}^{N}\log\big[\mu_n^{y_n}\times(1-\mu_n)^{1-y_n}\big] \tag{10.7}$$
$$= -\sum_{n=1}^{N}\big[y_n\log\mu_n+(1-y_n)\log(1-\mu_n)\big] \tag{10.8}$$
$$= \sum_{n=1}^{N}\mathbb{H}(y_n,\mu_n) \tag{10.9}$$

其中 \(\mu_n = \sigma(a_n)\) 是类别1的概率，\(a_n = \mathbf{w}^\top\mathbf{x}_n\) 是对数几率，\(\mathbb{H}(y_n,\mu_n)\) 是二元交叉熵，定义为

$$\mathbb{H}(p,q) = -\big[p\log q + (1-p)\log(1-q)\big] \tag{10.10}$$

如果我们使用 \(\tilde{y}_n \in \{-1,+1\}\) 而不是 \(y_n \in \{0,1\}\)，那么我们可以将其重写如下：

$$\text{NLL}(\mathbf{w}) = -\sum_{n=1}^{N}\big[\mathbb{I}(\tilde{y}_n=1)\log(\sigma(a_n))+\mathbb{I}(\tilde{y}_n=-1)\log(\sigma(-a_n))\big] \tag{10.11}$$
$$= -\sum_{n=1}^{N}\log\big(\sigma(\tilde{y}_n a_n)\big) \tag{10.12}$$
$$= \sum_{n=1}^{N}\log\big(1+\exp(-\tilde{y}_n a_n)\big) \tag{10.13}$$

然而，在本书中，我们主要使用 \(y_n \in \{0,1\}\) 记号，因为这样更容易推广到多类情况（第10.3节），并且更容易看出与交叉熵的联系。

### 10.2.3.2 优化目标

为了找到最大似然估计（MLE），我们必须求解

$$\nabla_{\mathbf{w}}\text{NLL}(\mathbf{w}) = \mathbf{g}(\mathbf{w}) = \mathbf{0} \tag{10.14}$$

我们可以使用任何基于梯度的优化算法来求解，例如我们在第5章讨论的那些算法。我们在第10.2.4节给出了一个具体例子。但首先我们必须推导出梯度，如下所述。

### 10.2.3.3 推导梯度

虽然我们可以使用自动微分方法（第13.3节）来计算 NLL 的梯度，但如下所示，显式地计算也很容易。幸运的是，得到的方程将具有简单直观的解释，正如我们将看到的，这可以用来推导其他方法。

首先，注意

$$\frac{d\mu_n}{da_n}=\sigma(a_n)(1-\sigma(a_n))\tag{10.15}$$

其中 \(a_n = \mathbf{w}^\top \mathbf{x}_n\) 和 \(\mu_n = \sigma(a_n)\)。因此，根据链式法则（以及附录B.3中讨论的向量微积分规则），我们有

$$\frac{\partial}{\partial w_d}\mu_n = \frac{\partial}{\partial w_d}\sigma(\mathbf{w}^\top \mathbf{x}_n)=\frac{\partial}{\partial a_n}\sigma(a_n)\frac{\partial a_n}{\partial w_d}=\mu_n(1-\mu_n)x_{nd}\tag{10.16}$$

偏置项的梯度可以用类似的方法推导，即在上述等式中使用输入 \(x_{n0}=1\)。然而，为了简单起见，我们将忽略偏置项。因此

$$\nabla_{\mathbf{w}}\log(\mu_n)=\frac{1}{\mu_n}\nabla_{\mathbf{w}}\mu_n=(1-\mu_n)\mathbf{x}_n\tag{10.17}$$

类似地，

$$\nabla_{\mathbf{w}}\log(1-\mu_n)=\frac{-\mu_n(1-\mu_n)\mathbf{x}_n}{1-\mu_n}=-\mu_n\mathbf{x}_n\tag{10.18}$$

因此，NLL 的梯度向量由下式给出

$$\nabla_{\mathbf{w}}\text{NLL}(\mathbf{w})=-\sum_{n=1}^{N}[y_n(1-\mu_n)\mathbf{x}_n-(1-y_n)\mu_n\mathbf{x}_n]\tag{10.19}$$
$$=-\sum_{n=1}^{N}[y_n\mathbf{x}_n-y_n\mathbf{x}_n\mu_n-\mathbf{x}_n\mu_n+y_n\mathbf{x}_n\mu_n]\tag{10.20}$$
$$=\sum_{n=1}^{N}(\mu_n-y_n)\mathbf{x}_n\tag{10.21}$$
$$=\mathbf{1}_N^\top(\text{diag}(\boldsymbol{\mu}-\mathbf{y})\mathbf{X})\tag{10.22}$$

这有一个很好的直观解释：观测标签 \(y_n\) 与预测 \(\mu_n\) 之间的差，按输入 \(\mathbf{x}_n\) 加权求和。

### 10.2.3.4 推导 Hessian 矩阵

基于梯度的优化器会找到驻点，其中 \(\mathbf{g}(\mathbf{w})=\mathbf{0}\)。这可能是全局最优，也可能是局部最优。为了确保驻点是全局最优，我们必须证明目标函数是凸的，原因我们将在第5.1.1.1节中解释。直观地说，这意味着 NLL 具有**碗状**，有唯一的最低点，事实也确实如此，如图10.5b所示。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_315_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_315_1.png)

*图10.5：应用于鸢尾花数据集的二元逻辑回归的 NLL 损失曲面，该数据集有1个特征和1个偏置项。目标是使函数最小化。由 iris_logreg_loss_surface.py 生成。*

更正式地，我们必须证明 Hessian 矩阵是半正定的，我们现在就来证明。（有关线性代数的背景知识，参见附录C。）可以证明 Hessian 矩阵由下式给出

$$\mathbf{H}(\mathbf{w}) = \nabla_{\mathbf{w}}\nabla_{\mathbf{w}}^{\top}\mathrm{NLL}(\mathbf{w}) = \sum_{n=1}^{N}(\mu_n(1-\mu_n)\mathbf{x}_n)\mathbf{x}_n^{\top} = \mathbf{X}^{\top}\mathbf{S}\mathbf{X}\qquad(10.23)$$

其中

$$\mathbf{S}\triangleq\mathrm{diag}(\mu_1(1-\mu_1),\dots,\mu_N(1-\mu_N))\qquad(10.24)$$

我们看到 \(\mathbf{H}\) 是半正定的，因为对于任何非零向量 \(\mathbf{v}\)，我们有

$$\mathbf{v}^{\top}\mathbf{X}^{\top}\mathbf{S}\mathbf{X}\mathbf{v} = (\mathbf{v}^{\top}\mathbf{X}^{\top}\mathbf{S}^{\frac12})(\mathbf{S}^{\frac12}\mathbf{X}\mathbf{v}) = \|\mathbf{v}^{\top}\mathbf{X}^{\top}\mathbf{S}^{\frac12}\|_2^2 \ge 0\qquad(10.25)$$

我们可以通过确保对所有 \(n\) 有 \(\mu_n > 0\) 来保证 NLL 是严格凸的；我们可以使用 \(\ell_2\) 正则化来实现这一点，如第10.2.7节所讨论的。

## 10.2.4 随机梯度下降

我们的目标是求解以下优化问题

$$\hat{\mathbf{w}}\triangleq\arg\min_{\mathbf{w}}\mathcal{L}(\mathbf{w})\qquad(10.26)$$

其中 \(\mathcal{L}(\mathbf{w})\) 是损失函数，在这里是负对数似然：

$$\mathrm{NLL}(\mathbf{w}) = -\sum_{n=1}^{N}[y_n\log\mu_n + (1-y_n)\log(1-\mu_n)]\qquad(10.27)$$

其中 \(\mu_n = \sigma(a_n)\) 是类别1的概率，\(a_n = \mathbf{w}^\top \mathbf{x}_n\) 是对数几率。

如第5章所讨论的，我们有很多算法可以用来计算式(10.26)。最简单的也许是使用随机梯度下降（第5.4节）。如果我们使用大小为1的小批量，则得到以下简单的更新方程：

$$\mathbf{w}_{t+1} = \mathbf{w}_t - \eta_t(\mu_n - y_n)\mathbf{x}_n  \qquad(10.28)$$

其中在第 \(t\) 步，我们采样样本 \(n = n_t\)。

由于我们知道目标函数是凸的（见第10.2.3.4节），那么可以证明，只要我们以适当的速率衰减学习率（见第5.4.3节），这个过程将收敛到全局最优。我们可以使用方差缩减技术（如 SAGA，第5.4.5.2节）来提高收敛速度。

## 10.2.5 感知机算法

感知机首次在 [Ros58] 中提出，是一种确定性的二元分类器，形式如下：

$$f(\mathbf{x}_n; \theta) = \mathbb{I}(\mathbf{w}^\top \mathbf{x}_n + b > 0)  \qquad(10.29)$$

这可以看作二元逻辑回归分类器的一个极限情况，其中 sigmoid 函数 \(\sigma(a)\) 被 Heaviside 阶跃函数 \(H(a) \triangleq \mathbb{I}(a > 0)\) 取代。这两个函数的比较见图3.2。

由于 Heaviside 函数不可微，我们不能使用基于梯度的优化方法来拟合这个模型。然而，Rosenblatt 提出了感知机学习算法来解决这个问题。基本思想是从随机权重开始，然后每当模型做出预测错误时迭代更新它们。更精确地，我们使用以下方式更新权重

$$\mathbf{w}_{t+1} = \mathbf{w}_t - \eta_t(\hat{y}_n - y_n)\mathbf{x}_n  \qquad(10.30)$$

其中 \((\mathbf{x}_n, y_n)\) 是在第 \(t\) 次迭代采样的带标签样本，\(\eta_t\) 是学习率或步长。（我们可以将步长设为1，因为权重的大小不影响决策边界。）有关此算法的简单实现，参见 perceptron_demo_2d.py。

式(10.30)中的感知机更新规则有一个直观的解释：如果预测正确，则不进行任何改变，否则我们将权重向使正确答案更有可能的方向移动。更精确地，如果 \(y_n = 1\) 且 \(\hat{y}_n = 0\)，我们有 \(\mathbf{w}_{t+1} = \mathbf{w}_t + \mathbf{x}_n\)；如果 \(y_n = 0\) 且 \(\hat{y}_n = 1\)，我们有 \(\mathbf{w}_{t+1} = \mathbf{w}_t - \mathbf{x}_n\)。

通过比较式(10.30)和式(10.28)，我们看到感知机更新规则等价于二元逻辑回归的 SGD 更新规则，只是使用了近似：将软概率 \(\mu_n = p(y_n = 1|\mathbf{x}_n)\) 替换为硬标签 \(\hat{y}_n = f(\mathbf{x}_n)\)。感知机方法的优点是我们不需要计算概率，这在标签空间非常大时很有用。缺点是该方法只有在数据线性可分时才会收敛 [Nov62]，而用于最小化逻辑回归 NLL 的 SGD 总是会收敛到全局最优的 MLE，即使数据不是线性可分的。

在第13.2节中，我们将把感知机推广到非线性函数，从而显著增强其实用性。

