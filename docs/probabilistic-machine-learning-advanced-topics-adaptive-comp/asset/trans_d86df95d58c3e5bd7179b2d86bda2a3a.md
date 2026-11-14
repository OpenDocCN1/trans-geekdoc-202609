

variances [Min01a]:

\(\mu^t_{ijl} = \mu^{t-1}_{ijl} + \tau^{t-1}_{ijl} \frac{\partial \ln Z_t}{\partial \mu^{t-1}_{ijl}}\) (17.49)

\(\tau^t_{ijl} = \tau^{t-1}_{ijl} - (\tau^{t-1}_{ijl})^2 \left[ \left( \frac{\partial \ln Z_t}{\partial \mu^{t-1}_{ijl}} \right)^2 - 2 \frac{\partial \ln Z_t}{\partial \tau^{t-1}_{ijl}} \right]\) (17.50)

在前向传递中，我们通过将输入 \(\boldsymbol{u}_t\) 传播通过模型来计算 \(Z_t\)。由于我们对权重有一个高斯分布，而不是点估计，这会诱导隐藏单元值上的一个（近似）高斯分布。对于某些类型的激活函数（如 ReLU），相关积分（用于计算均值和方差）可以解析求解，如 GP-神经网络（第 18.7 节）所示。结果是，我们得到一个关于最终层的高斯分布，形式为 \(\mathcal{N}(\boldsymbol{\eta}_t | \boldsymbol{\mu}, \boldsymbol{\Sigma})\)，其中 \(\boldsymbol{\eta}_t = f(\boldsymbol{u}_t; \boldsymbol{w}_t)\) 是神经网络在由 \(p_t(\boldsymbol{w}_t)\) 诱导的 GLM 链接函数之前的输出。因此，我们可以使用

\(Z_t \approx \int p(\boldsymbol{y}_t | \boldsymbol{\eta}_t) \mathcal{N}(\boldsymbol{\eta}_t | \boldsymbol{\mu}, \boldsymbol{\Sigma}) d\boldsymbol{\eta}_t\) (17.51)

来近似配分函数。

我们现在讨论如何计算这个积分。在协迭分类的情况下，与 \(y \in \{-1, +1\}\)，我们有 \(p(y | \boldsymbol{x}, \boldsymbol{w}) = \Phi(y\eta)\)，其中 \(\Phi\) 是标准正态分布的累积分布函数（cdf）。我们可以使用以下解析结果

\(\int \Phi(y\eta) \mathcal{N}(h | \mu, \sigma) d\eta = \Phi \left( \frac{y\mu}{\sqrt{1+\sigma}} \right)\) (17.52)

在逻辑分类的情况下，与 \(y \in \{0, 1\}\)，我们有 \(p(y | \boldsymbol{x}, \boldsymbol{w}) = \text{Ber}(y | \sigma(\eta))\)；在这种情况下，我们可以使用第 15.3.6 节中的协迭近似。对于多类情况，其中 \(\boldsymbol{y} \in \{0, 1\}^C\)（独热编码），我们有 \(p(y | \boldsymbol{x}, \boldsymbol{w}) = \text{Cat}(\boldsymbol{y} | \text{softmax}(\boldsymbol{\eta}))\)。对于这种情况，\(\log Z_t\) 的变分下界在 [GDFY16] 中给出。

一旦我们计算出 \(Z_t\)，就可以求梯度并更新高斯后验矩，然后再进入下一步。

## 17.5.4 DNNs的在线变分推断

在线学习的一种自然方法是使用变分推断，其中先验是前一步的后验。这被称为 **流式变分贝叶斯** [Bro+13]。更详细地，在步骤 \(t\) 时，我们计算

\(\boldsymbol{\psi}_t = \underset{\boldsymbol{\psi}}{\text{argmin}} \underbrace{\mathbb{E}_{q(\boldsymbol{\theta} | \boldsymbol{\psi})} [\ell_t(\boldsymbol{\theta})] + D_\text{KL} (q(\boldsymbol{\theta} | \boldsymbol{\psi}) \| q(\boldsymbol{\theta} | \boldsymbol{\psi}_{t-1}))}_{-\mathcal{L}_t(\boldsymbol{\psi})}\) (17.53)

\(= \underset{\boldsymbol{\psi}}{\text{argmin}} \mathbb{E}_{q(\boldsymbol{\theta} | \boldsymbol{\psi})} [\ell_t(\boldsymbol{\theta}) + \log q(\boldsymbol{\theta} | \boldsymbol{\psi}) - \log q(\boldsymbol{\theta} | \boldsymbol{\psi}_{t-1})]\) (17.54)

其中 \(\ell_t(\boldsymbol{\theta}) = -\log p(\mathcal{D}_t | \boldsymbol{\theta})\) 是步骤 \(t\) 时数据批次的负对数似然（或者更一般地，某些损失函数）。

当应用于 DNNs 时，这种方法称为 **变分持续学习** 或 **VCL** [Ngu+18]。（我们在第 19.7 节讨论持续学习。）一种高效的实现，称为 **FOOBVB**（“在线变分贝叶斯的定点算子”）在 [Zen+21] 中给出。方程 (17.53) 中的 VCL 目标的一个问题是，KL 项可能导致模型变得过于稀疏，这可能阻止模型适应或学习新任务。这个问题称为 **变分过度剪枝** [TT17]。更准确地说，之所以发生这种情况，是因为：某些权重可能不需要来拟合给定的数据集，因此它们的后验将等于先验，但从这些高方差权重中采样会向似然中添加噪声；为了减少这种情况，优化方法倾向于将偏置项设置为一个大的负值，以便相应的单元被“关闭”，从而对似然没有影响。不幸的是，这些“死单元”会卡住，因此没有足够的网络容量来学习下一个任务。在 [LST21] 中，他们提出了解决这个问题的方案，称为 **广义变分持续学习** 或 **GVCL**。第一步是用因子 \(\beta < 1\) 对 KL 项进行降权，以得到

$$ \mathbf{L}_t = \mathbb{E}_{q(\boldsymbol{\theta}|\boldsymbol{\psi})} [\ell_t(\boldsymbol{\theta})] + \beta D_{\text{KL}} \big( q(\boldsymbol{\theta}|\boldsymbol{\psi}) \big\| q(\boldsymbol{\theta}|\boldsymbol{\psi}_{t-1}) \big) $$

有趣的是，可以证明在 \(\beta \to 0\) 的极限下，这恢复了几种基于黑塞矩阵拉普拉斯近似的标准方法。特别是，如果我们使用对角变分后验，这将归约为 [Sch+18] 的在线 EWC 方法；如果我们使用块对角且克罗内克分解的后验，这将归约为 [RBB18b] 的在线结构化拉普拉斯方法；如果我们使用低秩后验精度矩阵，这将归约为 [Yin+20] 的 SOLA 方法。

第二步是使用温度替代先验和后验，当模型被误设定时这很有用，如第 17.3.11 节所讨论。在高斯的情况下，将分布提升到 \(\lambda\) 次方相当于使用温度 \(\tau = 1/\lambda\) 进行温度处理，这等同于将协方差缩放 \(\lambda^{-1}\)。因此 GVCL 目标变为

$$ \mathbf{L}_t = \mathbb{E}_{q(\boldsymbol{\theta}|\boldsymbol{\psi})} [\ell_t(\boldsymbol{\theta})] + \beta D_{\text{KL}} \big( q(\boldsymbol{\theta}|\boldsymbol{\psi})^\lambda \big\| q(\boldsymbol{\theta}|\boldsymbol{\psi}_{t-1})^\lambda \big) $$

这可以使用 SGD 进行优化，假设后验是可重参数化的（见第 10.2.1 节）。

## 17.6 分层贝叶斯神经网络

在某些问题中，我们有多个相关的数据集，例如来自不同医院的一组医学图像。数据的某些方面（例如，健康细胞与患病细胞的形状）通常在数据集之间是相同的，但其他方面可能是独特或特殊的（例如，每家医院可能使用不同颜色的染料进行染色）。为了建模这一点，我们可以使用分层贝叶斯模型，其中我们允许每个数据集的参数不同（以捕捉随机效应），同时来自一个共同先验（以捕捉共享效应）。这是我们在第 15.5 节中考虑的设置，在那里我们讨论了分层贝叶斯 GLM。在本节中，我们将其扩展到基于神经网络的非线性预测器。（该设置与第 19.6.2 节讨论的域泛化非常相似，只不过这里我们关心所有领域的性能，而不仅仅是留出的目标领域。）

![](img/ca72c1626f4850f058a9edc138c1ac73_701_0.png)

图 17.17：（a）两个月亮合成数据集。（b）多任务版本，我们旋转数据以创建 18 个相关任务（组）。每个数据集有 50 个训练点和 50 个测试点。这里我们展示了前 4 个任务。由 bnn_hierarchical.ipynb 生成。

### 17.6.1 示例：多月亮分类

在本节中，我们考虑一个示例，其中我们想要求解来自 J 个不同环境或分布的多个相关非线性二元分类问题。我们假设每个环境都有其自身独特的决策边界 p(y|x, w^j)，因此这是一种概念漂移（见第 19.2.3 节）。但是我们假设每个边界的整体形状类似于一个共同的共享边界，记为 p(y|x, w^0)。我们每个环境只有少量 N_j 的样本，D^j = {(x_n^j, y_n^j) : n = 1 : N_j}，但我们可以利用它们的共同结构来比拟合 J 个独立模型做得更好。

为了说明这一点，我们为 J = 18 个任务创建了一些合成 2d 数据。我们从两个月亮数据集开始，如图 17.17a 所示。每个任务是通过以不同的量旋转 2d 输入得到的，以创建 18 个相关分类问题（参见图 17.17b）。请参见图 17.17b 了解 4 个任务的训练数据。

为了处理非线性决策边界，我们使用多层感知器。由于数据集是低维的（2d 输入），我们使用一个只有 2 个隐藏层的浅模型，每个隐藏层有 5 个神经元。我们可以为每个任务拟合一个独立的 MLP，但由于每个任务的数据有限（N_j = 50 个训练样本），这效果不好，正如我们下面所示。我们也可以汇总所有数据并拟合一个单一模型，但这效果更差，因为数据集来自不同的基础分布，因此将来自不同“概念”的数据混合在一起会使模型混淆。相反，我们采用分层贝叶斯方法。

我们的建模假设如图 17.18 所示。特别是，我们假设权重从

2. 本示例来自 https://twiecki.io/blog/2018/08/13/hierarchical_bayesian_neural_network/。关于将类似方法应用于手势识别任务的现实世界示例，请参见 [Jos+17]。

