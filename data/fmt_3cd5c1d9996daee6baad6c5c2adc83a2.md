
既然我们现在有了一个评估特定动作质量的方程，我们现在对上一个方程进行微调。现在，我们可以说 `V(S)` 是所有可能的 `Q` 值的最大值。让我们使用这个方程并将 `V(S)` 替换为 `Q 学习`。

![](img/9781681089409-C5-EQ9.jpg)

### 5.2.4.2. 时差

时差将帮助计算机响应环境的变化计算 `Q` 值。考虑到计算机现在处于指定的状态。我们使用相同的公式计算新的 `Q(S,a)` 并减去之前计算的 `Q(S,a)`。

![](img/9781681089409-C5-EQ10.jpg)

上述方程计算 `Q` 值的时差，这有助于捕捉环境可能引入的随机变化。“新的” `Q(S,a)` 修改如下：

![](img/9781681089409-C5-EQ11.jpg)

在上述方程中，如果我们把 `TDt` 替换为其完整形式，最终方程将是：

![](img/9781681089409-C5-EQ12.jpg)

在上述方程中，`α` 学习率。`Qt` 是当前状态的 `Q` 值，`Qt-1` 是较早阶段的 `Q` 值。

### 5.2.4.3. 强化学习的实例

让我们来看一个自动移动机器人的例子，它被放置在一个充满区块的房间里并被建议到达目标（图 **5.3**）。

它被指示只能向四个方向移动：上、下、左、右。不允许对角移动。

![](img/9781681089409-C5-F3.jpg)

**图 (5.3)** 显示强化学习示例的目标和路径。

它在区块位置 `[4,3]` 处将获得 `+5` 的奖励 `R`，如果到达区块位置 `[4,2]`，则奖励将减去 `-5`。对于每移动一步，机器人将获得 `-0.04` 的奖励，即机器人的目标是到达目标并并用尽可能少的步数。

我们的目标是找到一个合适的解决方案，让机器人到达目标、获得最大奖励，并维持状态、动作和奖励。正如所知，在强化学习中，动作是随机的，而策略是从每个状态到动作的映射。

机器人将执行一些概率步骤以穿过带有方块的房间获取奖励。然而，最优步骤可能与下面提到的步骤相似。下图显示了机器人在`步进奖励为 -0.04`时跨越房间的移动情况（图 **5.4**）。

![](img/9781681089409-C5-F4.jpg)

**图 (5.4)** 奖励为 `-0.04` 的概率步骤。

- 当步进奖励 = `-0.04` 时

正如所知，最优解并不是容易实现的。现在，让我们看看如果我们不断改变“步进奖励”，会出现哪些概率步骤（图 **5.5**）。

- 当步进奖励 = `-2` 时

![](img/9781681089409-C5-F5.jpg)

**图 (5.5)** 奖励为 `-2` 的概率步骤。

- 当步进奖励 = `-0.1` 时（图 **5.6**）。

![](img/9781681089409-C5-F6.jpg)

**图 (5.6)** 奖励为 `-0.1` 的概率步骤。

- 当步进奖励 = `-0.01` 时（图 **5.7**）。

![](img/9781681089409-C5-F7.jpg)

**图 (5.7)** 奖励为 `-0.01` 的概率步骤。

- 当步进奖励 = `+0.01` 时（图 **5.8**）。

![](img/9781681089409-C5-F8.jpg)

**图 (5.8)** 奖励为 `+0.01` 的概率步骤。

## 5.3. 强化学习任务的现实世界示例

到目前为止，我们学习了强化学习的基础知识及其详细架构。在理解了强化学习的工作原理后，我们现在来看一些强化学习的现实生活应用，我们将简要逐一介绍。以下是我们可以构建、开发和改进的应用。

### 1. 控制行走机器人

在此应用中，可以通过根据其奖励优化策略，教导机器人更有效地移动。

- **智能体**：行走机器人控制程序。
- **环境**：机器人周围的真实物理世界。
- **动作**：四种运动之一：(1)向前移动，(2) 向后移动，(3) 左转和 (4) 右转。
- **奖励**：当到达目标时会增加奖励值。如果它向错误的方向移动、停止或跌倒，它将失去相应的奖励分数。

### 2. 开发定制化学习系统

该应用具有增加定制课程系统价值的潜力。例如，更有效的学习可以帮助用户，更成功的广告可以使系统受益。

- **智能体**：在在线学习目录中，程序决定下一个显示什么内容。
- **环境**：学习系统即为环境。
- **动作**：动作现在是显示新的课程视频以及广告。
- **奖励**：如果用户决定点击课程视频，奖励为正；如果用户决定点击广告，奖励更广泛；如果用户决定离开，奖励为负。

### 3. 在网页上选择广告位置

在此应用中，该场景中的智能体监控周围环境并确定其当前状态。该状态可以表示页面上目前有多少个广告，以及是否可以添加额外的广告。智能体随后在每个阶段选择三个选项之一。如果它被设计为在收入增加时获得正向激励、在收入减少时获得负向激励，它就可以设计出有效的策略。

- **智能体**：决定特定页面适合多少广告的程序。
- **环境**：网站。
- **动作**：三个选项之一：(1) 在页面上添加新广告，(2) 删除广告，(3) 保留广告。

- 在现实设置中，可能存在部分观测的环境。
- 过多的强化可能导致状态过剩，从而降低输出质量。
- 在现实设置中，可能存在非平稳情况。

## 5.5. 强化学习的编程方法

![](img/9781681089409-C5-F9.jpg)![](img/9781681089409-C5-F10.jpg)![](img/9781681089409-C5-F11.jpg)![](img/9781681089409-C5-F12.jpg)![](img/9781681089409-C5-F13.jpg)![](Images/9781681089409-C5-F14.jpg)![](Images/9781681089409-C5-F15.jpg)![](Images/9781681089409-C5-F16.jpg)![](Images/9781681089409-C5-F17.jpg)

## 结语

强化学习（RL）是机器学习的一个分支，与监督学习或无监督学习相似，但在许多方面有所不同。它在应用于真实的业务场景时更为困难，因为它需要模拟数据和环境。另一方面，强化学习技术前景良好，因为其学习过程本质上适用于序列决策设定。

## 参考文献

| | |
| --- | --- |
| [1] | Russell S., Norvig P.. Artificial intelligence: a modern approach. 3rd edPearson 2011 |
| [2] | 2021[理解四种人工智能](https://www.govtech.com/computing/understanding-the-four-types-of-artificial-intelligence.html)(https://www.govtech.com/computing/understanding-the-four-types-of-artificial-intelligence.html) |
| [3] | Theobald O.. Machine Learning For Absolute Beginners: A Plain English Introduction 2017 |
| [4] | Fenner M.. Machine learning with Python for Everyone. Addison-Wesley Professional 2019 |
| [5] | Theobald O.. Machine Learning For Absolute Beginners: A Plain English Introduction 2017 |
| [6] | Conway D., White J.M.. Machine Learning for Hackers: Case Studies and Algorithms to Get You Started. 1st edO’Reilly 2012 |
| [7] | Mueller J.P., Massaron L.. Data Science Programming All-in-One For Dummies. 1st edFor Dummies 2020 |
| [8] | [线性回归中的预测](https://ml-cheatsheet.readthedocs.io/en/latest/linear_regression.html#making-predictions)(https://ml-cheatsheet.readthedocs.io/en/latest/linear_regression.html#making-predictions) |
| [9] | [机器学习中的线性回归](https://www.javatpoint.com/linear-regression-in-machine-learning)(https://www.javatpoint.com/linear-regression-in-machine-learning) |
| [10] | Brownlee J.. Linear Regression for Machine Learning 2021[用于机器学习的线性回归](https://machinelearningmastery.com/linear-regression-for-machine-learning/)(https://machinelearningmastery.com/linear-regression-for-machine-learning/) |
| [11] | 2021 |
| [12] | Ye A.. 强化学习中的马尔可夫决策过程：你需要的一切。2021[强化学习中的马尔可夫决策过程](https://neptune.ai/blog/markov-decision-process-in-reinforcement-learning)(https://neptune.ai/blog/markov-decision-process-in-reinforcement-learning) |
| [13] | Choudhary A.. 强化学习的核心：使用动态规划。2021[基于模型的规划规划](https://www.analyticsvidhya.com/blog/2018/09/reinforcement-learning-model-based-planning/)(https://www.analyticsvidhya.com/blog/2018/09/reinforcement-learning-model-based-planning/) |
| [14] | Paul S.. Q-学习简介。2020[Q-学习简介](https://blog.floydhub.com/an-introduction-to-q-learning/)(https://blog.floydhub.com/an-introduction-to-q-learning/) |
| [15] | Howard J., Gugger S.. 使用 Fastai 和 PyTorch 进行深度学习：面向编码者。1st edO’Reilly Media 2019 |
| [16] | Le J.. 机器学习研究人员需要学习 8 种神经网络架构](https://www.kdngets.com/2018/02/8-neural-architectures-machine-learning.html)(https://www.kdngets.com/2018/02/8-neural-architectures-machine-learning.html) |
| [17] | [人工智能中的机器学习架构](https://developer.ibm.com/technologies/artificial-intelligence/articles/cc-machine-learning/)(https://developer.ibm.com/technologies/artificial-intelligence/articles/cc-machine-learning/) |
| [18] | [神经网络应用](https://www.xenonstack.com/blog/artificial-network-applications)(https://www.xenonstack.com/blog/artificial-network-applications) |
| [19] | [`hackernoon.com/`](https://hackernoon.com/) |
| [20] | [多层感知器](https://d2l.ai/multilayer-perceptrons/backprop)(https://d2l.ai/multilayer-perceptrons/backprop) |
| [21] | Ruder S.. 梯度下降概述](https://ruder.io/optimizing-descent/)(https://ruder.io/optimizing-descent/) |
| [22] | [卷积神经网络](https://cs231n.github.io/convolutional-networks/)(https://cs231n.github.io/convolutional-networks/) |
| [23] | [卷积神经网络](https://www.analyticsvidhya.com/blog/2021/05/convolutional-neural-cnn/)(https://www.analyticsvidhya.com/blog/2021/05/convolutional-neural-cnn/) |
| [24] | [`stanford.edu/`](https://stanford.edu/) |
| [25] | [`wiki.pathmind.com/lstm`](https://wiki.pathmind.com/lstm) |
| [26] | Zheng A., Casari A.. 机器学习特征工程：数据科学家的原理与技术。1st edO’Reilly Media 2018 |
| [27] | Kaushik S.. 2020[特征选择方法：如何选择变量](https://www.analyticsvidhya.com/blog/2016/12/introduction-to-feature-selection-methods-with-an-example-how-to-select-variables/)(https://www.analyticsvidhya.com/blog/2016/12/introduction-to-feature-selection-methods-with-an-example-how-to-select-variables/) |
| [28] | [Z 检验](https://www.investopedia.com/terms/z-test.asp)(https://www.investopedia.com/terms/z-test.asp) |
| [29] | Meena S.. 分析与数据科学统计：假设检验和 Z 检验与 T 检验。2020[`www.analyticsvidhya.com/blog/2020/06/statistics-analytics-testing-z-test-t-test/`](https://www.analyticsvidhya.com/blog/2020/06/statistics-analytics-testing-z-test-t-test/) |
| [30] | Thakur M.. Z 检验与 T 检验 2021[`www.wallstreetmojo.com/z-test-vs-t-test/`](https://www.wallstreetmojo.com/z-test-vs-t-test/) |
| [31] | 2021[方差分析](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/anova/)(https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/anova/) |
| [32] | [多元变量方差分析](https://www.statisticssolutions.com/free-resources/directory-of-statistical-analyses/manova/?__cf_chl_jschl_tk__=pmd_16d7d4fa1acf6d3f445cd2769d8972412bcb64ea-1626714547-0-gqNtzNAg2jcnszQki)(https://www.statisticssolutions.com/free-resources/directory-of-statistical-analyses/manova/?__cf_chl_jschl_tk__=pmd_16d7d4fa1acf6d3f445cd2769d8972412bcb64ea-1626714547-0-gqNtzNAg2jcnszQki) |
| [33] | [卡方检验特征选择的数学原理](https://www.geeksforgeeks.org/chi-square-test-for-feature-selection-mathematical-explanation/)(https://www.geeksforgeeks.org/chi-square-test-for-feature-selection-mathematical-explanation/) |
