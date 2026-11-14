
## Autoregressive process

**Autocorrelated time series**，如第 [3.4](#Chp003_49-60_B9780443218576000072.xhtml) 节所述。连续时间版本包括 **Gaussian processes** 和 **Brownian motions**，而 **random walks** 是离散示例；也存在二维版本。这些过程本质上是积分的 **white noise**。

## Binning

特征分箱是将特征的值聚合到少量的箱中，以避免过拟合并减少 `naive Bayes`、神经网络或 `decision tree` 等方法中的 `nodes` 数量。分箱可以同时应用于两个或更多特征。本书讨论了 `optimum binning`。

## Boosted model

融合多个模型以取长补短，也称为集成方法。本书通过 `hidden decision trees` 说明该概念。其他流行示例包括 `gradient boosting` 和 `AdaBoost`。

## Bootstrapping

一种数据驱动、无模型的技术，用于估计参数值、优化拟合优度指标。与交叉验证背景下的重采样相关。本书讨论了在模仿实际观测的合成数据上的 `parametric bootstrap`。

## Confidence Region

水平为 `γ` 的置信区域是覆盖二元概率分布 `γ` 比例质量的最小面积二维集合。它是 `confidence intervals` 的二维推广。本书还讨论了 `dual confidence regions`——即贝叶斯推断中的 `credible regions` 的类比。

## Cross-validation

引导法中使用的标准程序，也用于测试和验证模型，通过将数据拆分为训练集和验证集。参数基于训练集数据估计。交叉验证的替代方案是在具有已知响应的合成数据上测试模型。

## Decision trees

一种简单、直观的非线性建模技术，用于分类问题。它可以处理缺失数据和分类数据，以及大量特征，但需要适当的特征分箱。通常混合多棵二叉树，每棵树只有少量 `nodes`，以提升性能。

## Dimension reduction

一种在最小化预测能力损失的同时减少数据集特征数量的技术。最著名的是 `principal component analysis` 和特征选择，以最大化拟合优度指标。

## Empirical distribution

附加在统计量（例如最近邻距离）上的累积频率直方图，基于观测值。当观测数量趋于无穷大且箱大小趋于零时，该阶梯函数趋于相关统计量的理论累积分布函数。

## Ensemble methods

一种将多个模型融合在一起的技术，例如许多 `decision trees` 与逻辑回归，以取长补短，并优于单独使用的每种方法。示例包括 boosting、bagging 和 `AdaBoost`。本书讨论了 `hidden decision trees`。

## Explainable AI

易于解释的自动化机器学习技术称为可解释机器学习或可解释人工智能。本书讨论的方法尽可能属于这一类别。目标是设计不太可能产生意外结果和非预期后果的黑箱系统。

## Feature selection

特征——相对于模型响应——也称为自变量或预测变量。特征选择类似于降维，旨在找到具有足够预测能力的最小变量子集。它也用于消除冗余特征并发现 `causality`（通常使用 `hierarchical Bayesian models`），而不仅仅是相关性。有时，两个特征单独考虑时预测能力较差，但组合在一起时能提供改进的预测。

## Generative model

贝叶斯高斯混合模型 (`GMM`) 结合核密度估计和 `EM algorithm` 是经典建模工具。本书改用 `m-interlacings`。生成对抗网络 (`GAN`) 工作原理如下：生成器创建新观测值，判别器测试新观测值是否在统计上与训练集数据无法区分。当达到此目标时，新观测值即为合成数据。新观测值也可通过 `parametric bootstrap` 生成。

## Goodness-of-fit

一种 `model fitting` 准则或指标，用于评估模型或子模型对数据集的拟合程度，或衡量其在验证集上的预测能力。示例包括 R-squared、Chi-squared、Kolmogorov–Smirnov、错误率（如假阳性）及本书讨论的其他指标。

## Gradient methods

寻找函数最小值或最大值的迭代优化技术，例如 `maximum likelihood`。当存在众多局部极小值或极大值时，使用 `swarm optimization`。梯度方法（例如随机梯度下降或牛顿法）假设函数可微。如果不可微，可使用 `Monte Carlo simulations` 或 `fixed-point algorithm` 等其他技术。约束优化涉及使用 `Lagrange multipliers`。

## Graph structures

图存在于决策树、神经网络（`neurons` 间的连接）、`nearest neighbors methods`（`NN graphs`）、`hierarchical Bayesian models` 等中。

## Hyperparameter

超参数用于控制学习过程：例如维度、特征数量、参数、层数（神经网络）或簇数（聚类问题），或图像处理中滤波窗口的宽度。相比之下，其他参数的值（通常是神经网络中的节点权重或回归系数）通过训练得出。

## Link function

链接函数将非线性关系映射为线性关系，以便拟合线性模型，然后使用反函数映射回原始形式。例如，`logit link function` 用于逻辑回归。推广包括 `quantile` 函数和神经网络中的反 `sigmoids`，以处理加性（线性）参数。

## Logistic regression

一种广义线性回归方法，通过 logistic 链接函数将二元响应（欺诈/非欺诈或癌症/非癌症）建模为概率。本书讨论了迭代最大似然解的替代方案。

## Neural network

一种用于预测、优化或模式识别的黑箱系统，尤其在计算机视觉中。它由层、每层中的 `neurons`、用于建模非线性交互的链接函数、参数（与 `neurons` 间连接相关的权重）和超参数组成。具有多层的网络称为 `deep neural networks`。此外，`neurons` 有时称为节点。

## NLP

自然语言处理是一组处理非结构化文本数据的技术，如电子邮件、自动客服或通过爬虫下载的网页。第 [18.5](#Chp018_361-386_B9780443218576000229.xhtml) 节讨论的示例涉及基于解析 Google 搜索结果页面创建关键词分类法。文本生成称为 NLG 或 `natural language generation`，使用 `large language models` (`LLM`)。

## Numerical stability

该问题发生在不稳定的优化问题中，通常伴随多个极小值或极大值，经常被忽视，导致预测不佳或高波动性。有时称为 `ill-conditioned problems`。本书通过多个示例解释如何修复它，例如第 [3.4.2](#Chp003_49-60_B9780443218576000072.xhtml) 节。不要与数值精度混淆。
