

构成 $J$ 个终端节点，且 $I(\cdot)$ 是通常的指示函数，当其参数为真时取 1（否则取 0）。通过拟合一个模型——在此情况下为回归树——到观测到的负梯度，我们可以在新数据点上定义它。使用回归树，更新变为

```
f_b (\boldsymbol{x}) = f_{b-1} (\boldsymbol{x}) + \gamma_b \sum_{j=1}^J \theta_j I(\boldsymbol{x} \in R_{jb})
= f_{b-1} (\boldsymbol{x}) + \sum_{j=1}^J \gamma_j I(\boldsymbol{x} \in R_{jb}) .
```

因此，为选择步长 $\gamma_b$ 而进行的线搜索等同于使用指定损失函数更新终端节点估计：

```
\{\gamma_{jb}\}_{j=1}^J = \arg \min_{\{\gamma_j\}_{j=1}^J} \sum_{i=1}^N L \left[ y_i, f_{b-1} (\boldsymbol{x}_i) + \sum_{j=1}^J \gamma_j I (\boldsymbol{x} \in R_{jb}) \right] . \quad (8.4)
```

根据 Friedman [2001]，由于 $J$ 个终端节点区域互不相交，我们可以将 (8.4) 改写为

```
\gamma_{jb} = \arg \min_{\gamma} \sum_{\boldsymbol{x}_i \in R_{jb}} L[y_i, f_{b-1} (\boldsymbol{x}_i) + \gamma] , \quad (8.5)
```

这是基于指定损失函数 $L$ 和当前迭代 $f_{b-1}(\boldsymbol{x}_i)$ 对每个终端节点区域 $\{R_{jb}\}_{j=1}^J$ 进行的最优常数更新。求解 (8.5) 等同于带有 *偏移量*（offset）的 *广义线性模型*（generalized linear model）拟合 [Efron and Hastie, 2016, p. 349]。此步骤非常重要，因为对于某些损失函数，原始终端节点估计可能不够准确。例如，使用 *最小绝对偏差*（least absolute deviation，LAD）损失（参见第 8.2.0.1 节）时，观测到的负梯度 $\boldsymbol{g}_b$ 仅取 $\{-1, 1\}$ 中的整数值；因此，拟合值不太可能非常准确。总之，“线搜索”步骤 (8.5) 修改当前拟合的终端节点估计以最小化损失。

c 粗略地说，偏移量（offset）是一个调整项（在此情况下为固定常数），用于添加到模型的预测中；这在广义线性模型中更为常见，其中它以固定系数 1（而非估计系数）添加到 *线性预测器*（linear predictor）中。

对于 LS 损失，(8.5) 变为

```
\gamma_{jb} = \arg \min_{\gamma} \sum_{x_i \in R_{jb}} ((y_i - f_{b-1}(x_i)) - \gamma)^2
= \arg \min_{\gamma} \sum_{x_i \in R_{jb}} (r_{i,b-1} - \gamma)^2
= \frac{1}{N_{jb}} \sum_{x_i \in R_{jb}} r_{i,b-1}
```

其中 \( r_{i,b-1} \) 和 \( N_{jb} \) 分别是第 $b$ 次迭代中第 $j$ 个终端节点的第 $i$ 个残差和观测数量。这得到第 $b$ 次迭代中每个终端节点的残差均值，这正是原始回归树在第 $b$ 次迭代中用于预测的内容（即，终端节点摘要）。换句话说，对于 LS 损失的特殊情况，第 $b$ 次迭代的原始终端节点估计已经是最优的，因此不需要更新（即线搜索）。

对于 LAD 损失，\( L(f) = |y - f(x)| \)，(8.5) 得到第 $b$ 次迭代中第 $j$ 个终端节点当前残差的中位数。对于一般损失函数（如常用于二元或多类分类设置的损失函数），求解 (8.5) 可能比较困难，通常会采用快速近似（参见第 8.2.0.1 节）。

完整的梯度提升树算法在算法 8.1 中给出。请注意，这是 Friedman [2001] 提出的原始梯度提升树算法。文献中已提出多种变体，各有其自身的改进，我将在后续章节中讨论其中一些修改。

### 8.2.0.1 损失函数

通过在算法 8.1 中指定不同的（代理）损失函数 \( L(y, f) \)，可以定义各种提升算法。虽然它不是调参参数，但为手头问题使用合适的损失函数很重要——例如，LS 损失并不适用于每个回归问题。GBM 及其实现中常用的几种损失函数，其中一部分在表 8.1 中有所描述。

对于回归，LS 和 LAD 损失是常见选择。LAD 损失的优点在于对长尾误差分布和响应异常值具有鲁棒性。无论损失函数如何，梯度提升树由于单个基学习者（在此情况下为回归树）的鲁棒性，已对特征空间中的长尾分布或异常值具有鲁棒性。请回顾，树对预测变量的严格单调变换具有不变性（例如，对第 $j$ 个预测变量使用 \( x_j \)、\( e^{x_j} \) 或 \( \log(x_j) \) 都会产生相同的结果）。

## 算法 8.1 标准梯度提升树算法。

- 1) 初始化 $f_0(\boldsymbol{x}) = \arg \min_\theta \sum_{i=1}^N L(y_i, \theta)$（一个常数）。
- 2) 对 $b$ 在 $1, \dots, B$ 中执行以下操作：
- a) 计算在训练数据上评估的负梯度，作为当前工作响应
- $y_{ib}^* = - \left[ \frac{\partial L(y_i, f(\boldsymbol{x}_i))}{\partial f(\boldsymbol{x}_i)} \right]_{f(\boldsymbol{x}_i)=f_{b-1}(\boldsymbol{x}_i)}, \quad i=1, 2, \dots, N.$
- b) 使用 CART 的分层树生长策略拟合带有 $J_b$ 个终端节点区域的回归树：$R_{jb}, j=1, 2, \dots, J_b$。
- c) 使用以下公式更新终端节点预测
- \(\gamma_{jb} = \arg \min_\gamma \sum_{\boldsymbol{x}_i \in R_{jb}} L(y_i, f_{b-1}(\boldsymbol{x}_i) + \gamma), \quad j=1, 2, \dots, J_b.\)
- d) 将 $f_b(\boldsymbol{x})$ 更新为
- \(f_b(\boldsymbol{x}) \leftarrow f_{b-1}(\boldsymbol{x}) + \sum_{j=1}^{J_b} \gamma_{jb} I(\boldsymbol{x} \in R_{jb}).\)
- 3) 返回 \(\widehat{f}(\boldsymbol{x}) = f_B(\boldsymbol{x})\)。

因此，在大多数基于树的集成中，几乎不需要担心特征的变换。对于误差服从正态分布（或近似正态分布）的结果，LAD 损失的效率将低于 LS 损失，泛化性能会下降。Friedman [2001] 和 Hastie et al. [2009, p. 360] 中描述的 Huber M-回归的 Huber 损失函数提供了一个令人满意的折中方案。Huber 损失函数对异常值和长尾误差分布具有抗性，同时在误差更接近正态分布的情况下保持高效率。

与指数损失（第 5.2.4 节）相比，对二元结果使用二项偏差（或对数损失）对标记错误的示例具有一定的鲁棒性 [Hastie et al., 2009, Section 10.6]。对于 $y \in \{0, 1\}$ 的二元情况，二项偏差可写为

\(L(y, f) = - [y \log(p) + (1-y) \log(1-p)]
= \log [1 + \exp(-2y\tilde{f})],\)

其中 \(\tilde{y} = 2y - 1 \in \{-1, +1\}^d\)，且 \(f\) 是 $y=+1$ 时对数几率的一半。使用二项偏差时，算法 8.1 中线搜索 (8.5) 没有闭式解，通常使用近似。例如，单步 Newton-Raphson 迭代得到

\(\gamma_{jb} = \sum_{\boldsymbol{x}_i \in R_{jb}} \tilde{y}_i / \sum_{\boldsymbol{x}_i \in R_{jb}} |\tilde{y}_i| (2 - |\tilde{y}_i|) \)。

最终近似 \(\widehat{f}(\boldsymbol{x})\)，即 $y=+1$ 时对数几率的一半，可以反转以生成预测概率。二项偏差也可推广到多类分类情况 [Friedman, 2001]。

在处理其他类型的结果变量时，也存在更专门的损失函数。例如，在建模计数（始终为正整数）时可以使用 Poisson 损失（表 8.1）。Ridgeway [1999] 展示了如何通过基于似然的损失函数将梯度提升扩展到指数族\(^e\)，以及用于删失结果的 Cox 比例风险回归模型。Greg Ridgeway 也是 R 包 **gbm** 的原始创建者，该包可以说是第一个开源的梯度提升决策树实现。

## 表 8.1：梯度提升树常用损失函数。顶部和底部部分分别列出了用于有序结果和二元结果的常用损失函数。

| 损失名称 | 损失函数 | 负梯度 |
|---|---|---|
| 最小二乘 | \(\frac{1}{2} [y_i - f(\boldsymbol{x}_i)]^2\) | \(y_i - f(\boldsymbol{x}_i)\) |
| 最小绝对偏差 | \(|y_i - f(\boldsymbol{x}_i)|\) | \(\text{sign } [y_i - f(\boldsymbol{x}_i)]\) |
| 波森偏差\(^f\) | \(y_i f(\boldsymbol{x}_i) - e^{f(\boldsymbol{x}_i)}\) | \(y_i - e^{f(\boldsymbol{x}_i)}\) |
| 指数 | \(\exp [-y_i f(\boldsymbol{x}_i)]\) | \(y_i \exp [-y_i f(\boldsymbol{x}_i)]\) |
| 二项偏差\(^g\) | \(\log [1 + \exp (-2\tilde{y}_i f(\boldsymbol{x}_i))]\) | \(2\tilde{y}_i / (1 + \exp [2\tilde{y}_i f(\boldsymbol{x}_i)])\) |

\(^d\)这种重新编码是为了计算效率，并且也导致与指数损失相同的总体最小化器（即第 5.2.4 节中的 Adaboost.M1）；详情见 Bühlmann and Hothorn [2007]。\(^e\)指数族包含许多常用损失函数作为特例；例如，高斯家族等同于使用 LS 损失，拉普拉斯分布等同于使用 LAD 损失，伯努利/二项家族等同于使用二项偏差（或对数损失）。\(^f\)这里，\(y_i \in \{0, 1, 2, ...\}\) 是非负整数（例如，普鲁士军队每年被骡子或马踢死的人数，或特定日客户支持中心的呼叫数量。\(^g\)这里，\(\tilde{y}_i \in \{-1, 1\}\) 且 \(f(\boldsymbol{x}_i)\) 是 $y=+1$ 时对数几率的一半。

