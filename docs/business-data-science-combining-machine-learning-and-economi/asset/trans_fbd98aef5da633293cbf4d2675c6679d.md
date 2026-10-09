
## 10.3 随机梯度下降

这些早期层的输出随后通过一系列经典神经网络节点进行处理，如公式 10.1 所示。这些后续的网络层表现得像传统的非参数回归：它们扩展早期层的输出，以近似响应变量中任意函数形式。因此，深度神经网络（DNN）将限制性降维与灵活函数近似结合起来。关键在于这两个组件是联合学习的。

![](img/315929ad4bddd26368466d02e06e2385_406_0.png)

图 10.7：深度神经网络的示意图，输入包括图像、结构化数据 $x_1 \ldots x_{big}$ 以及原始文档文本。

我们只涵盖了深度学习领域的一小部分。工业界和学术界涌现出大量令人兴奋的新材料。若想一窥该领域的最新动态，请访问顶级机器学习会议——神经信息处理系统大会（NeurIPS）的最新会议论文集，网址为 https://NeurIPS.cc。你会很快看到其研究的广度之大。当前热门的一个话题是深度神经网络的不确定性量化。另一个话题是理解训练数据中的不平衡如何导致潜在的预测偏差。随着深度神经网络从学术竞赛转向实际应用，这类话题日益受到重视。随着该领域的发展，以及深度神经网络模型构建从一门科学学科转变为工程学科，我们将更加需要此类研究，以告知我们在何时以及多大程度上可以信任深度神经网络。

为了全面介绍深度学习，我们需要描述用于训练所有模型的算法：随机梯度下降（SGD）。SGD 优化是梯度下降（GD）的变体，后者曾是任何可微分函数最小化问题的主导方法。给定最小化目标 $\mathcal{L}(\Omega)$，其中 $\Omega$ 是完整的模型参数集合，梯度下降例程的每次迭代根据当前参数 $\Omega_t$ 进行如下更新：

$$\Omega_{t+1} = \Omega_{t} - C_{t} \nabla\mathcal{L}|_{\Omega_{t}}.$$
(10.2)

这里，$\nabla\mathcal{L}|_{\Omega_{t}}$ 是在当前参数处评估的 $\mathcal{L}$ 的梯度，$C_{t}$ 是一个投影矩阵，决定在 $\nabla\mathcal{L}$ 所暗示的方向上采取的步骤大小。我们在 $C_{t}$ 上添加下标 $t$，是因为该投影可以在优化过程中进行更新。例如，牛顿算法使用目标函数二阶导数的矩阵 $\nabla^2\mathcal{L}|_{\Omega_{t}}$ 作为 $C_{t}$。

通常人们会说神经网络是通过“反向传播”来训练的，这并不完全正确。相反，它们是通过梯度下降的变体进行训练的。反向传播，简称 backprop，是一种计算网络参数梯度的方法。具体而言，backprop 只是微积分中链式法则的一种算法实现。在公式 10.1 所示的简单神经元上下文中，单个权重 $\omega_{hj}$ 的梯度计算为

$$\frac{\partial\mathcal{L}}{\partial\omega_{hj}} = \sum_{i=1}^{n}\frac{\partial\mathcal{L}}{\partial z_{ij}^{h}} \frac{\partial z_{ij}^{h}}{\partial\omega_{hj}} = \sum_{i=1}^{n}\frac{\partial\mathcal{L}}{\partial z_{ij}^{h}} z_{ij}^{h-1}[0<\Sigma_{j}\omega_{nj}^{h-1}] .$
(10.3)

链式法则的另一个应用可以将 $\partial\mathcal{L}/\partial z_{ij}^{h}$ 展开为 $\partial\mathcal{L}/\partial z_{ij}^{h+1} \times \partial z_{ij}^{h+1}/\partial z_{ij}^{h}$，依此类推，直到将完整梯度写成特定层操作的乘积。网络的有向结构允许你从响应层逐层向前追溯到输入层，高效地计算所有梯度。这种链式法则的递归应用及其相关计算方案构成了通用的反向传播算法。

在统计估计和机器学习模型训练中，$\mathcal{L}$ 通常涉及对数据观测值求和的损失函数。例如，假设对参数施加 $L_2$（岭）正则化惩罚，对应于 $n$ 个独立观测值 $z_i$（例如，对于回归，$z_i = [x_i, y_i]$）的正则似然最大化最小化目标可以写为

$$\mathcal{L}(\Omega) \equiv \mathcal{L}(\Omega;\{z_i\}_{i=1}^n) = \sum_{i=1}^n \big[ -\log \mathrm{p}(z_i \mid \Omega) + \lambda \| \Omega \|_2^2 \big]. \tag{10.4}$$

这里，$\| \Omega \|_2^2$ 是 $\Omega$ 中所有参数平方的总和。更一般地，$\mathcal{L}(\Omega;\{z_i\}_{i=1}^n)$ 可以由任何涉及对观测值求和的损失函数组成。例如，为了对预测不确定性建模，我们经常使用分位数损失。定义 $\tau_q(x; \Omega)$ 为由 $\Omega$ 参数化的*分位数函数*，它将协变量 $x$ 映射到响应 $y$ 的第 $q$ 分位数：

$$\mathrm{p}\left(y < \tau_q(\boldsymbol{x}; \Omega) \mid \boldsymbol{x}\right) = q. \tag{10.5}$$

你拟合 $\tau_q$ 以最小化正则化分位数损失函数（再次假设岭惩罚）：

$$\mathcal{L}(\Omega;\{z_i\}_{i=1}^n) = \sum_{i=1}^n \left[\big(y_i - \tau_q(\boldsymbol{x}_i; \Omega)\big) \left(q - \mathbb{1}_{[y_i < \tau_q(x_i; \Omega)]}\right) + \lambda \| \Omega \|_2^2 \right]. \tag{10.6}$$

常见的“误差平方和”准则，可能经过正则化，是另一种符合这种对观测值求和模式的损失函数。

在所有这些案例中，公式 10.2 中更新所需的梯度计算涉及对所有 $n$ 个观测值的求和。也就是说，每次计算 $\nabla \mathcal{L}$ 需要 $n$ 量级的计算。例如，在带有岭惩罚的线性回归中，若 $\Omega = \beta$ 为回归系数向量，则第 $j$ 个梯度分量为

$$\frac{\partial \mathcal{L}}{\partial \beta_j} = \sum_{i=1}^n \big[ (y_i - \boldsymbol{x}_i^t \beta) x_{ij} + \lambda \beta_j \big]. \tag{10.7}$$

对于大规模数据集，问题在于当 $n$ 非常大时，这些计算变得极其昂贵。当 $\Omega$ 维度很高，并且每个梯度加项都需要复杂计算时（如深度神经网络那样），问题更加严重。梯度下降是我们拥有的最佳优化工具，但对于大规模数据集而言，它在计算上是不可行的。

解决方案是用基于数据子集的梯度估计来替代公式 10.2 中的实际梯度。这就是 SGD 算法。它有着悠久的历史，可追溯到 1951 年由两位统计学家提出的 Robbins-Munro 算法。在 SGD 的最常见版本中，全样本梯度简单地被较小子样本上的梯度所替代。我们不再根据全样本损失 $\mathcal{L}(\mathbf{\Omega};\{z_i\}_{i=1}^n)$ 计算梯度，而是根据子样本计算进行下降，

\begin{equation} \mathbf{\Omega}_{t+1} = \mathbf{\Omega}_t - C_t \nabla \mathcal{L}(\mathbf{\Omega}; \{z_{i_b}\}_{b=1}^B)\big|_{\mathbf{\Omega}_t} \tag{10.8}\end{equation}

这里，$\{z_{i_b}\}_{b=1}^B$ 是一个包含 $B \ll n$ 个观测值的*小批量*（mini-batch）。SGD 背后的关键数学结果是，只要 $C_t$ 矩阵序列满足一些基本要求，SGD 算法将收敛到局部最优值，前提是 $\nabla \mathcal{L}(\mathbf{\Omega}; \{z_{i_b}\}_{b=1}^B)$ 是全样本梯度的*无偏*估计。也就是说，SGD 的收敛依赖于以下性质：

\begin{equation} \mathbb{E}\left[\frac{1}{B}\nabla \mathcal{L}\left(\mathbf{\Omega}; \{z_{i_b}\}_{b=1}^B\right)\right] = \mathbb{E}\left[\frac{1}{n}\nabla \mathcal{L}(\mathbf{\Omega}; \{z_i\}_{i=1}^n)\right] = \mathbb{E}\nabla \mathcal{L}(\mathbf{\Omega}; z). \tag{10.9}\end{equation}

这里，最后一项指的是*总体*期望梯度——即从真实数据生成过程中抽取的观测值 $z$ 的平均梯度。

要理解为什么 SGD 比 GD 更适合机器学习，有助于讨论计算机科学家如何看待估计中的*约束*。统计学家和经济学家往往将样本量（即数据缺乏）视为其估计量的约束条件。相比之下，在许多机器学习应用中，数据实际上是无限的，并在系统部署期间持续增长。尽管数据如此丰富，但存在固定的计算预算（或者对于流式数据需要近乎实时的更新需求），导致你在处理数据时只能执行有限数量的操作。因此，在机器学习中，约束条件是计算量而非数据量。

SGD 以更快的更新速度换取了较慢的单次更新收敛率。正如 Bousquet 和 Bousquet 在 2008 年的一篇论文中解释的那样，当更快的更新允许模型接触比原本可能更多的数据时，这种权衡是值得的。为了看到这一点，请注意小批量梯度 $B^{-1}\nabla \mathcal{L}(\mathbf{\Omega};\{z_{i_b}\}_{b=1}^B)$ 的方差远高于全-

