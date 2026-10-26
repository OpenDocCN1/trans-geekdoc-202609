

## 神经网络的贝叶斯学习

- 变分推断（简而言之）：
  $$\min_q F(D, \boldsymbol{\theta}) = \mathrm{KL}(q(\boldsymbol{\theta}) \| p(\boldsymbol{\theta}|D)) - \mathbb{E}_{q(\boldsymbol{\theta})}[\log p(D|\boldsymbol{\theta})]$$
  $$\min_q F(D, \boldsymbol{\theta}) = \mathrm{KL}(q(\boldsymbol{\theta}) \| p(\boldsymbol{\theta}|D)) - \sum_i \log p(D|\boldsymbol{\theta}_i)$$
  其中 $\boldsymbol{\theta}_i \sim q(\boldsymbol{\theta})$；KL 项也可以用类似方式近似
- 我们可以将 $q(\boldsymbol{\theta})$ 定义为对角高斯分布或全协方差高斯分布
- 或者，$q(\boldsymbol{\theta})$ 可以隐式定义，例如通过 dropout [Gal & Ghahramani, 2016]
  $$\boldsymbol{\theta} = \boldsymbol{M} \cdot \mathrm{diag}(\boldsymbol{z}),$$
  $$\boldsymbol{z} \sim \mathrm{Bernoulli}(p)$$
- 丢弃神经元等价于将参数矩阵（即权重）的对应列置零
- $z_i = 0$ 对应于 $\boldsymbol{M}$ 的第 $i$ 列被丢弃
  $\Rightarrow$ 该过程等价于对单元 $i$ 进行 dropout [Hinton et al., 2012]
- 变分参数为 $\{\boldsymbol{M}, \boldsymbol{p}\}$

![](img/cb490ed30bca4eda5fbba81c52a2c173_79_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_79_1.png)

## “无限宽”深度模型

- 我们已经看到，一个“无限深”的网络可以用合适的图模型来解释。那么“无限宽”的网络呢？
- 考虑一个权重上具有高斯先验且中间层有无限多个隐藏神经元的神经网络。
- 事实证明，如果我们在这种无限网络的权重上施加某种高斯先验，它将等价于一个高斯过程 [Neal 1996]。
- 高斯过程（GP）是函数上的分布：
  $$m(\mathbf{x}) = \mathbb{E}[f(\mathbf{x})],$$
  $$k(\mathbf{x}, \mathbf{x}') = \mathbb{E}[(f(\mathbf{x}) - m(\mathbf{x}))(f(\mathbf{x}') - m(\mathbf{x}'))],$$
  $$f(\mathbf{x}) \sim \mathcal{GP}(m(\mathbf{x}), k(\mathbf{x}, \mathbf{x}')).$$
- 当用于预测时，高斯过程会考虑数据点之间的相关性，并能输出校准良好的预测不确定性估计。

![](img/cb490ed30bca4eda5fbba81c52a2c173_80_0.png)

无限多个隐藏单元

## 高斯过程与深度核学习

- 考虑一个权重上具有高斯先验且中间层有无限多个隐藏神经元的神经网络。
- 某些类别的高斯先验条件下，具有无限多个隐藏单元的神经网络会收敛到高斯过程 [Neal 1996]
- 深度核 [Wilson et al., 2016]
  - 将深度模型架构的归纳偏置与高斯过程的非参数灵活性相结合
    $k(x_i, x_j | \phi) \rightarrow k(g(x_i, \theta), g(x_j, \theta) | \phi, \theta)$，其中 $K_{ij} = k(x_i, x_j)$
  - 从基础核 $k(x_i, x_j | \phi)$ 出发，对输入 $x$ 进行变换
    $p(f | \phi) = \mathcal{N}(f | m(x), K)$
    $p(y | f) = \mathcal{N}(y | f, \beta^{-1})$
  - 通过优化边际对数似然（或其变分下界），联合学习核参数和神经网络参数 $\{\phi, \theta\}$。
  - 通过局部核插值、结构化诱导点和蒙特卡洛近似实现快速学习与推断

![](img/cb490ed30bca4eda5fbba81c52a2c173_81_0.png)

## 高斯过程与深度核学习

- 将高斯过程作为一层添加到深度神经网络中，我们可以将其视为添加了一个具有特定权重先验的无限隐藏层
- 深度核学习 [Wilson et al., 2016]
  - 将深度模型的归纳偏置与高斯过程的非参数灵活性相结合
  - 高斯过程为网络增加了强大的正则化
  - 此外，它们还提供了预测不确定性估计

![](img/cb490ed30bca4eda5fbba81c52a2c173_82_0.png)

## 序列数据上的深度核学习

答案是肯定的！

通过将高斯过程层添加到循环网络中，我们可以有效地关联不同时间点的样本，并获得带有良好校准的不确定性估计的预测。

然而，要使用随机技术训练这样的模型需要额外的注意（参见我们的论文）。

![](img/cb490ed30bca4eda5fbba81c52a2c173_84_0.png)

## 序列数据上的深度核学习

前车预测：LSTM 与 GP-LSTM 对比

![](img/cb490ed30bca4eda5fbba81c52a2c173_86_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_87_0.png)

## 结论

- 深度学习与图模型：这两个领域在初期很相似（结构、能量等），随后分化到各自特有的流程中
- 深度学习：大部分精力用于比较不同架构及其组件（模型通过在下游任务上的经验性能来驱动评估）
  - 深度学习模型擅长从数据中学习稳健的层次化表示，并适用于简单推理（可称为“低层认知”）
- 图模型：精力集中于提高推断精度和收敛速度
  - 图模型最适合可证明正确的推断，并适用于高层复杂推理任务（可称为“高层认知”）
- 两个领域的融合前景广阔！
  - 下一部分：以图模型解释统一视角看待深度生成模型

## 第二部分

深度生成模型的统一框架

![](img/cb490ed30bca4eda5fbba81c52a2c173_89_0.png)

## 计划

- 深度学习的统计与算法基础及洞见
- 深度生成模型的统一框架
- 计算机制：编程平台与分布式深度学习架构

## 大纲

- 深度生成模型进展概述
- 深度生成模型的理论基础
  - 清醒-睡眠算法
  - 变分自编码器
  - 生成对抗网络
- 深度生成模型的统一视角
  - 深度生成模型的新表述
  - 隐变量与可见变量的对称建模

![](img/cb490ed30bca4eda5fbba81c52a2c173_90_0.png)

## 大纲

![](img/cb490ed30bca4eda5fbba81c52a2c173_91_0.png)

- 深度生成模型进展概述
- 深度生成模型的理论基础
  - 清醒-睡眠算法
  - 变分自编码器
  - 生成对抗网络
- 深度生成模型的统一视角
  - 深度生成模型的新表述
  - 隐变量与可见变量的对称建模

## 深度生成模型

- 对一组变量定义概率分布
- “深度”意味着多层隐藏变量！

![](img/cb490ed30bca4eda5fbba81c52a2c173_92_0.png)

## 早期形式的深度生成模型

- 层次贝叶斯模型
  - Sigmoid 信念网络 [Neal 1992]
- 神经网络模型
  - Helmholtz 机 [Dayan et al.,1995]

![](img/cb490ed30bca4eda5fbba81c52a2c173_94_0.png)

## 深度生成模型的复兴

- 受限玻尔兹曼机（RBM）[Smolensky, 1986]
  - 深度概率模型的基本构建块

![](img/cb490ed30bca4eda5fbba81c52a2c173_97_0.png)

## 深度生成模型的复兴

- 受限玻尔兹曼机（RBM）[Smolensky, 1986]
  - 深度概率模型的基本构建块
- 深度信念网络（DBN）[Hinton et al., 2006]
  - 混合图模型
  - 由于解释消除效应，DBN 中的推断存在困难
- 深度玻尔兹曼机（DBM）[Salakhutdinov & Hinton, 2009]
  - 无向模型

![](img/cb490ed30bca4eda5fbba81c52a2c173_98_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_100_0.png)

## 深度生成模型的复兴

- 变分自编码器（VAE）[Kingma & Welling, 2014] / 神经变分推断与学习（NVIL）[Mnih & Gregor, 2014]
- 生成对抗网络（GAN）[Goodfellow et al., 2014]

![](img/cb490ed30bca4eda5fbba81c52a2c173_100_1.png)

$G_\theta$：生成模型
$D_\phi$：判别器

