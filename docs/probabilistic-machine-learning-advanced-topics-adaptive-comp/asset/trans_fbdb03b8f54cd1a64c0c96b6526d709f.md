

![](img/ca72c1626f4850f058a9edc138c1ac73_612_0.png)

图 14.5: (a) 自适应预测集示意图。引用自 [AB21] 中的图 5。特感谢 Anastasios Angelopoulos 允许使用。(b) 合格化分位数回归示意图。引用自 [AB21] 中的图 6。特感谢 Anastasios Angelopoulos 允许使用。(c) 针形损失函数示意图。

### 14.3.1 合格化分类

将合格预测应用于多类分类的最简单方法是，根据分配给标签的 softmax 分数推导合格分数，使用 \(s(\boldsymbol{x}, y) = 1 - f(\boldsymbol{x})_y\)，因此大值被认为比小值不太可能。我们按上述方法计算阈值 \(\hat{q}\)，然后定义预测集为 \(\mathcal{T}(\boldsymbol{x}) = \{y : f(\boldsymbol{x})_y \ge 1 - \hat{q}\}\)，这与公式 (14.49) 匹配。也就是说，我们取所有高于指定阈值的类别标签组成集合，如图 14.4 所示。虽然上述方法生成的预测集平均大小最小（如 [SLW19] 所证明），但对于容易示例，集合大小往往过大；对于困难示例，则过小。我们现在介绍一种改进方法，称为 **自适应预测集**，由 [RSC20] 提出，它解决了这个问题。其思想很简单：我们将所有 softmax 分数 \(f(\boldsymbol{x})_c\)（其中 \(c = 1 : C\)）排序，得到排列 \(\pi_{1:C}\)，然后定义 \(s(\boldsymbol{x}, y)\) 为直到达到标签 \(y\) 为止的分数累积和：\(s(\boldsymbol{x}, y) = \sum_{c=1}^k f(\boldsymbol{x})_{\pi_j}\)，其中 \(k = \pi_y\)。我们现在像以前一样计算 \(\hat{q}\)，并将预测集 \(\mathcal{T}(\boldsymbol{x})\) 定义为所有标签的集合，按降序概率排序，直到覆盖 \(\hat{q}\) 的概率质量。请参见图 14.5a 以了解示意图。该方法使用模型输出的所有 softmax 分数，而不仅仅是最高分，因此性能更好。

### 14.3.2 合格化回归

在本节中，我们考虑合格化回归问题。由于现在 \(y \in \mathbb{R}\)，计算公式 (14.49) 中的预测集代价高昂，因此我们将改为计算预测区间，由下界和上界指定。

### 14.3.2.1 合格化分位数回归

在本节中，我们使用 **分位数回归** 来计算下界和上界。我们首先拟合形式为 \(t_\gamma(\boldsymbol{x})\) 的函数，它预测 cdf \(P_Y(Y) = p(Y|\boldsymbol{x})\) 的 \(\gamma\) 分位数。例如，如果设置 \(\gamma = 0.5\)，则得到中位数。如果使用 \(\gamma = 0.05\) 和 \(\gamma = 0.95\)，可以使用 \([t_{0.05}(\boldsymbol{x}), t_{0.95}(\boldsymbol{x})]\) 获得近似 90% 预测区间，如图 14.5b 中的灰色线所示。要拟合分位数回归模型，只需将平方损失替换为 **分位数损失**，也称为 **针形损失**，其定义如下

\(\ell_\gamma(y, \hat{t}) = (\gamma - \mathbb{I}(y < \hat{t}))(y - \hat{t}) = (y - \hat{t})\gamma \mathbb{I}(y > \hat{t}) + (\hat{t} - y)(1 - \gamma) \mathbb{I}(y < \hat{t})\quad (14.53)\)

其中 $y$ 是真实输出，$\hat{t}$ 是分位数 $\gamma$ 处的预测值。请参见图 14.5c 以了解示意图。该损失函数的关键属性是其极小值点是分布 $P_Y$ 的 $\gamma$-分位数，即：

\(\text{argmin}_t \mathbb{E}_{P_Y(y)} [\ell_\gamma(y, \hat{t})] = P_Y^{-1}(\gamma)\)

然而，回归分位数通常仅近似为 90% 区间，因为模型可能与真实分布不匹配。不过，我们可以使用合格预测来修正这个问题。具体来说，让我们定义合格分数为

\(s(\boldsymbol{x}, y) = \max \left( \hat{t}_{\alpha/2}(\boldsymbol{x}) - y, y - \hat{t}_{\alpha/2}(\boldsymbol{x}) \right)\)

换句话说，$s(\boldsymbol{x}, y)$ 是一个正度量，表示值 $y$ 超出预测区间的距离；如果 $y$ 在预测区间内，则为负度量。我们像以前一样计算 \(\hat{q}\)，并将合格预测区间定义为

\(\mathcal{T}(\boldsymbol{x}) = [\hat{t}_{\alpha/2}(\boldsymbol{x}) - \hat{q}, \hat{t}_{\alpha/2}(\boldsymbol{x}) + \hat{q}]\)

如果 \(\hat{q}\) 为正（基础方法过度自信），这会使分位数回归区间变宽；如果 \(\hat{q}\) 为负（基础方法自信不足），则区间变窄。请参见图 14.5b 以了解示意图。这种方法称为 **合格化分位数回归** 或 **CQR** [RPC19]。

### 14.3.2.2 合格化预测方差

定义不确定性分数 $u(\boldsymbol{x})$ 的方法有很多，例如预测标准差，我们可以使用

\(\mathcal{T}(\boldsymbol{x}) = [f(\boldsymbol{x}) - u(\boldsymbol{x})\hat{q}, f(\boldsymbol{x}) + u(\boldsymbol{x})\hat{q}]\)

这里 \(\hat{q}\) 源自以下合格分数的分位数

\(s(\boldsymbol{x}, y) = \frac{|y - f(\boldsymbol{x})|}{u(\boldsymbol{x})}\)

此方法产生的区间往往比 CQR 计算的区间更宽，因为它在预测值 $f(\boldsymbol{x})$ 上下各延伸相同的量。此外，不确定性度量 $u(\boldsymbol{x})$ 可能无法与 \(\alpha\) 适当缩放。尽管如此，这是一种简单的事后方法，可以应用于许多回归方法而无需重新训练它们。

## 15 广义线性模型

### 15.1 引言

广义线性模型（GLM）[MN89] 是指数分布族的条件版本（第 2.4 节）。更准确地说，模型具有如下形式：

\(p(y_n|\mathbf{x}_n, \mathbf{w}, \sigma^2) = \exp \left[ \frac{y_n \eta_n - A(\eta_n)}{\sigma^2} + \log h(y_n, \sigma^2) \right]\)

其中 \(\eta_n = \mathbf{w}^\mathsf{T} \mathbf{x}_n\) 是分布的自然参数，\(A(\eta_n)\) 是 log 归一化因子，\(\mathcal{T}(y) = y\) 是充分统计量，\(\sigma^2\) 是离散项。根据第 2.4.3 节的结果，我们可以证明响应变量的均值和方差如下：

\(\mu_n \triangleq \mathbb{E} \left[ y_n | \mathbf{x}_n, \mathbf{w}, \sigma^2 \right] = A'(\eta_n) \triangleq \ell^{-1}(\eta_n)\\ \mathbb{V} \left[ y_n | \mathbf{x}_n, \mathbf{w}, \sigma^2 \right] = A''(\eta_n) \sigma^2\)

我们将使用 \(\mu_n = \ell^{-1}(\eta_n)\) 表示从线性输入到输出均值的映射，其中函数 \(\ell\) 称为 **链接函数**，\(\ell^{-1}\) 称为 **均值函数**。此关系通常写作如下：

\(\ell(\mu_n) = \eta_n = \mathbf{w}^\mathsf{T} \mathbf{x}_n\)

由于线性假设，GLM 的预测能力相当有限（尽管我们可以始终对 \(\mathbf{x}_n\) 使用基函数展开以提高灵活性）。然而，GLM 在统计文献中的主要用途不是用于预测，而是用于假设检验，如第 3.10.3 节所述。这依赖于计算后验 \(p(\mathbf{w}|\mathcal{D})\) 的能力，我们将在第 15.1.4 节中讨论。我们可以使用此来得出结论：任何输入（例如，代表不同组）是否对输出有显著影响。

### 15.1.1 一些常用的 GLM

在本节中，我们给出一些广泛使用的 GLM 示例。

#### 15.1.1.1 线性回归

回顾线性回归的形式为

\(p(y_n|\mathbf{x}_n, \mathbf{w}, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp(-\frac{1}{2\sigma^2}(y_n - \mathbf{w}^\mathsf{T} \mathbf{x}_n)^2)\)

因此

$$ \log p(y_n | \boldsymbol{x}_n, \boldsymbol{w}, \sigma^2) = -\frac{1}{2\sigma^2}(y_n - \eta_n)^2 - \frac{1}{2} \log(2\pi\sigma^2) $$ (15.6)

其中 \(\eta_n = \boldsymbol{w}^T \boldsymbol{x}_n\)。我们可以将其写成 GLM 形式如下：

$$ \log p(y_n | \boldsymbol{x}_n, \boldsymbol{w}, \sigma^2) = \frac{y_n \eta_n - \frac{\eta_n^2}{2}}{\sigma^2} - \frac{1}{2} \left( \frac{y_n^2}{\sigma^2} + \log(2\pi\sigma^2) \right) $$ (15.7)

我们可以看到 \(A(\eta_n) = \eta_n^2/2$，因此

$$ \mathbb{E}[y_n] = \eta_n = \boldsymbol{w}^T \boldsymbol{x}_n $$ (15.8)

$$ \mathbb{V}[y_n] = \sigma^2 $$ (15.9)

有关线性回归的详细信息，请参见第 15.2 节。

#### 15.1.1.2 二项回归

如果响应变量是 $N_n$ 次试验中的成功次数，$y_n \in \{0, \dots, N_n\}$，则可以使用 **二项回归**，其定义为

$$ p(y_n | \boldsymbol{x}_n, N_n, \boldsymbol{w}) = \text{Bin}(y_n | \sigma(\boldsymbol{w}^T \boldsymbol{x}_n), N_n) $$ (15.10)

我们可以看到，当 $N_n = 1$ 时，二进制逻辑回归是特例。对数 pdf 由以下给出

$$ \log p(y_n | \boldsymbol{x}_n, N_n, \boldsymbol{w}) = y_n \log \mu_n + (N_n - y_n) \log(1 - \mu_n) + \log \binom{N_n}{y_n} $$ (15.11)

$$ = y_n \log \left( \frac{\mu_n}{1 - \mu_n} \right) + N_n \log(1 - \mu_n) + \log \binom{N_n}{y_n} $$ (15.12)

其中 \(\mu_n = \sigma(\eta_n)\)。要将其改写为 GLM 形式，让我们定义

$$ \eta_n \triangleq \log \left[ \frac{\mu_n}{(1 - \mu_n)} \right] = \log \left[ \frac{1}{1 + e^{-\boldsymbol{w}^T \boldsymbol{x}_n}} \frac{1 + e^{-\boldsymbol{w}^T \boldsymbol{x}_n}}{e^{-\boldsymbol{w}^T \boldsymbol{x}_n}} \right] = \log \frac{1}{e^{-\boldsymbol{w}^T \boldsymbol{x}_n}} = \boldsymbol{w}^T \boldsymbol{x}_n $$ (15.13)

因此我们可以将二项回归写成 GLM 形式如下

$$ \log p(y_n | \boldsymbol{x}_n, N_n, \boldsymbol{w}) = y_n \eta_n - A(\eta_n) + h(y_n) $$ (15.14)

其中 \(h(y_n) = \log \binom{N_n}{y_n}\) 且

$$ A(\eta_n) = -N_n \log(1 - \mu_n) = N_n \log(1 + e^{\eta_n}) $$ (15.15)

因此

$$ \mathbb{E}[y_n] = \frac{dA}{d\eta_n} = \frac{N_n e^{\eta_n}}{1 + e^{\eta_n}} = \frac{N_n}{1 + e^{-\eta_n}} = N_n \mu_n $$ (15.16)

