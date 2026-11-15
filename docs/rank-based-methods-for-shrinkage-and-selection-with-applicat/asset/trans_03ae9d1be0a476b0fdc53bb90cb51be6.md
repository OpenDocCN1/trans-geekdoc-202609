
边界，无论是线性还是非线性，其作用是将一个组的成员与另一个组分开。例如，假设一家银行正在发放贷款，并希望根据与现有客户相关的一组数据，将每个潜在客户分类为值得获得贷款或不值得。我们的目标群体是那些获得贷款并偿还的客户，而备选群体则由那些获得贷款但未偿还的客户组成。这是一个经典的二元分类问题，因为我们希望确定倾向于偿还贷款的客户的特征，作为未来发放贷款的标准。

为解决此问题，已开发出感知机算法、k近邻（kNN）分类、随机森林、逻辑回归和支持向量机等方法（举凡最突出的方法）。通常，一个组被标记为 1 作为目标组，而另一个组被标记为 0。对于某些方法，+1 和 -1 可能是更合适的标签。无论如何，目标都是找到分离边界，以便准确预测任何新数据所属的组。

至今，基于排序的方法尚未用于解决二元分类问题，且这种方法在这项机器学习任务中的表现尚不明确。本章将考察对数似然逻辑回归和一种新的基于排序的逻辑回归。将确立二元分类语境下的异常值概念，并使用基于排序的方法描述检测此类异常值的方法。此外，还有迹象表明，它可以确立逻辑回归在训练集上的最大精度。因此，它是迈向稳健数据科学和机器学习的又一步。

## 11.3.1 对数似然设置

逻辑回归非常适合二元分类问题和概率预测（Hosmer and Lemeshow, 1989）。我们先对基本逻辑回归做简要介绍。首先，我们定义 \(Y_i \in \{0, 1\}\) 为二元因变量，\(\boldsymbol{x}_i = (1, x_{i1}, x_{i2}, \dots, x_{ip})^\top\) 为样本集中第 \(i^{th}\) 观测值的 \((p + 1)\) 维解释变量向量，其中 \(i \in \{1, ..., n\}\)。然后，给定 \(\boldsymbol{x}_i\) 时 \(Y_i = 1\) 的条件概率为

\(P(Y_i = 1|\boldsymbol{x}_i) = p(\boldsymbol{x}_i) = \left[ \frac{1}{1 + \exp(-\boldsymbol{x}_i^\top \boldsymbol{\beta})} \right], \quad (11.3.1)\)

其中 \(\boldsymbol{\beta} = (\beta_0, \beta_1, \dots, \beta_p)^\top\) 是长度为 \(p\) 的感兴趣回归参数向量，其中 \(\beta_0\) 为截距。对上式变换，逻辑回归问题表示为

图 11.1 Sigmoid 函数。

![](img/f3b106d7e76ae3afcec8895afa28732c_367_0.png)

$$ \log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)} = \beta_0 + x_{i1}\beta_1 + \dots + x_{ip}\beta_p. $$ (11.3.2)

左侧称为 logit 链接函数，即 z，也称为对数几率，

$$ z = \log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)}. $$ (11.3.3)

假设我们使用合适的估计量找到估计值 $\hat{\boldsymbol{\beta}}$，并希望预测某个新 $\boldsymbol{x}$ 的响应为 $Y = 1$ 的概率 $\hat{p}(\boldsymbol{x})$。这可以分两步完成。首先，我们使用以下公式计算 $z$：

$$ \hat{z} = \boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}} = \hat{\beta}_0 + \hat{\beta}_1 x_1 + \dots + \hat{\beta}_p x_p. $$ (11.3.4)

其次，我们通过 Sigmoid 函数预测概率：

$$ \hat{p}(\boldsymbol{x}) = \frac{1}{1 + \exp(-\boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}})} = \frac{1}{1 + \exp(-\hat{z})} = p(\hat{z}). $$ (11.3.5)

详细考察 Sigmoid 函数颇具启发性。函数 $p(z)$ 的图形如图 11.1 所示。请注意，当 z 为较大的正值时，概率渐近地趋近于 1，而当 z 为较大的负值时，它渐近地趋近于 0。对于任何给定的 $\boldsymbol{x}$，因变量 $y$ 的基准真值（即真实值）要么是 0，要么是 1。然而，预测值 $\hat{p}(\boldsymbol{x})$ 介于 0 和 1 之间，但不会达到任一端值，原因从 Eq. (11.3.5) 中应能清楚看出。对于二元分类，将预测值 $\hat{p}(\boldsymbol{x})$ 与 0.5 进行比较。如果 $\hat{p}(\boldsymbol{x}) > 0.5$，则预测为 1；如果 $\hat{p}(\boldsymbol{x}) < 0.5$，则预测为 0。

或者，我们也可以基于使用 $\hat{z} = \boldsymbol{x}^{\top}\hat{\boldsymbol{\beta}}$ 的符号检验来做出 1 或 0 的决定。从概念上讲，z 代表一条线或超平面，用于将 0 与 1 分开。请注意，$\hat{\beta}_0$ 在这个表达式中充当偏置项。换句话说，如果 $\boldsymbol{x} = 0$，则 $\hat{\beta}_0 > 0$ 或 $\hat{\beta}_0 < 0$，因此存在由 $\hat{\beta}_0$ 引起的内置偏差。它实际上将 p 维超平面向一个方向或另一个方向偏移，偏移量等于偏置项。其余的系数，$\hat{\beta}_1, \dots, \hat{\beta}_p$，确定实际超平面。p 维中的线性边界（即超平面边界）的位置满足

\hat{\beta}_0 + \hat{\beta}_1 x_1 + \cdots + \hat{\beta}_p x_p = 0.

因此，如果

\hat{\beta}_0 + \hat{\beta}_1 x_1 + \cdots + \hat{\beta}_p x_p > 0，

我们说预测响应为 1；如果

\hat{\beta}_0 + \hat{\beta}_1 x_1 + \cdots + \hat{\beta}_p x_p \le 0，

则预测响应为 0。

这也可以通过检查图 11.1 中 z 的值来理解。如果 z 为正，我们可以将其声明为 1；如果 z 为负，则声明为 0。总结来说，我们可以使用 \hat{z} 或 p(\hat{z}) 来决定给定 \mathbf{x} 的二元响应。

为了确定估计值，我们使用最大似然估计，它可以有多种表述方式。我们将使用以下形式，觉得比较方便：

\mathcal{L}(\mathbf{y}, \mathbf{p}) = \prod_{i=1}^n (p_i)^{y_i} (1 - p_i)^{(1-y_i)},

其中 p_i = p(\mathbf{x}_i) 是 \mathbf{p} = (p(\mathbf{x}_1), \dots, p(\mathbf{x}_n))^T 的第 i\text{th} 元素，y_i 是 \mathbf{Y} = (y_1, \dots, y_n)^T 的第 i\text{th} 元素。更常见的是最小化损失函数的负对数似然（LL）形式，以获得估计值 \hat{\beta}，如下所示

J(\boldsymbol{\beta}) = J(\mathbf{y}, \mathbf{p}) = - \sum_{i=1}^n [y_i \log p_i + (1 - y_i) \log(1 - p_i)].

对于单个观测值 \mathbf{x}，损失函数简化为

J(y, p(\mathbf{x})) = -y \log p(\mathbf{x}) - (1 - y) \log(1 - p(\mathbf{x})).

该函数可以直观地理解：y 只能是 0 或 1。如果 y = 0，则可以忽略第一项，损失由第二项给出，这简化为最小化 \log(1 - p(\mathbf{x}))。如果 y = 1，则可以忽略第二项，这简化为最小化 \log(p(\mathbf{x}))。因此，Eq. (11.3.10) 中的函数具有逻辑回归所需的特性。更重要的是，J(\boldsymbol{\beta}) 关于 \boldsymbol{\beta} 是凸函数，这有助于收敛到全局最小值。因此，对数似然逻辑回归（LLR）估计量为

\hat{\boldsymbol{\beta}}_n^{\text{LLR}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ - \sum_{i=1}^n [y_i \log p_i + (1 - y_i) \log(1 - p_i)] \right}.

然而，正如我们很快将看到的，使用此损失函数存在某些局限性，可能会影响估计值的预测准确性。

逻辑回归中使用的数值优化技术通常是某种形式的梯度下降。这里我们仅为本目的描述最简单的形式。基本上，我们使用初始猜测 \(\boldsymbol{\beta}^{(0)}\) 计算损失函数，然后沿梯度方向走一步以减小 \(J(\boldsymbol{\beta})\) 的值。重复此过程，直到找到最小值。这种迭代方法需要对 Eq. (11.3.10) 中的 \(J(\boldsymbol{\beta})\) 关于 \(\boldsymbol{\beta}\) 计算偏导数。

再考虑只有一个观测值 \(\boldsymbol{x}\) 和一个已知二元响应 y 的情况。从损失函数 \(J(\boldsymbol{\beta})\) 出发，我们可以使用链式法则得到所需的梯度。对于某个参数 \(\beta_j$，有

\(\frac{\partial J(\boldsymbol{\beta})}{\partial \beta_j} = \frac{\partial J(y, p(\boldsymbol{x}))}{\partial p(\boldsymbol{x})} \frac{\partial p(\boldsymbol{x})}{\partial \beta_j} = (p(\boldsymbol{x}) - y)x_j.\)

这源自第一项中的偏导数，

\(\frac{\partial J(y, p(\boldsymbol{x}))}{\partial p(\boldsymbol{x})} = -\frac{y}{p(\boldsymbol{x})} + \frac{1-y}{1-p(\boldsymbol{x})},\)

以及第二项，涉及 Sigmoid 函数的偏导数，

\(\frac{\partial p(\boldsymbol{x})}{\partial \beta_j} = \frac{\exp(-\boldsymbol{x}^{\text{T}}\boldsymbol{\beta})}{(1+\exp(-\boldsymbol{x}^{\text{T}}\boldsymbol{\beta}))^2} x_j = p(\boldsymbol{x})(1-p(\boldsymbol{x}))x_j.\)

接下来，考虑有 \(n\) 个观测值的情况。我们需要对 Eq. (11.3.12) 中与每个观测值相关的每个参数的此类量求和。结合上述步骤，计算下一次迭代值的每个 \(\beta_j, j = 0, \dots, p\) 的更新方程如下

\(\beta_j^{(t+1)} = \beta_j^{(t)} - \ell \times \frac{\partial J(\boldsymbol{\beta})}{\partial \beta_j} = \beta_j^{(t)} - \ell \sum_{i=1}^n (p(\boldsymbol{x}_i) - y_i)x_{ij},\)

其中 \(\ell\) 是称为学习率的调节参数，用于控制每次迭代所需的步长，以实现平滑且快速地收敛到全局解。这仅针对一个观测值。

这些方程可以使用矩阵符号方便地表述如下。我们从 \(\boldsymbol{X}\) 开始，它是一个 \(n \times (p+1)\) 矩阵。使用初始 \(\boldsymbol{\beta}_n^{(0)}\) 值计算 \(n\) 个 logit 值，如下所示

\(\boldsymbol{z} = \boldsymbol{X}\boldsymbol{\beta}_n^{(0)}.\)

使用 Sigmoid 函数计算 \(n\) 个预测响应

\(p(\boldsymbol{X}) = \frac{1}{1 + \exp(-\boldsymbol{z})}.\)
