

在本章的以下部分中，讨论了 `DL`、机器学习（`ML`）和 `AI` 之间的关系。第 1.3 节简要介绍了人工神经网络（`ANN`）及其分类和不同的学习技术。作为 `ANN` 分类的一部分，讨论了前馈神经网络（`FFNNs`）和循环神经网络（`RNNs`）及其用途。而在学习技术部分，简要考虑了监督学习、无监督学习和强化学习。第 1.4 节保留用于讨论 `DL`。本节清楚地说明了为什么使用“深度”一词。已识别出多个要点，使 `DL` 成为最先进的技术。在第 1.6 节中，详细描述了不同的激活函数，例如 sigmoid 激活函数、双曲正切激活函数、修正线性单元（`ReLU`）激活函数和 softmax 激活函数。文献中有许多 `DL` 架构可供使用。其中少数变得非常流行，并提供高精度，从而实现更好的性能。本节讨论了受限玻尔兹曼机（`RBM`）、深度置信网络（`DBN`）、自编码器（`AE`）和卷积神经网络（`CNN`）的概念。在第 1.6 节中，介绍了来自不同组织的多个 `ML` 平台。它们都提供带有高性能图形处理单元（`GPUs`）的云基础设施，以加快 `DL` 网络对海量数据的训练，从而将训练时间从几周缩短到几小时。本章的最后一节专门用于描述使用 IBM `ML` 平台——IBM Watson Studio（以前称为数据科学体验或 `DSX`）的不同步骤。

## 1.2 AI versus ML versus DL

`AI` 是计算机科学的一个子类别，用于处理计算机中智能活动的模拟。`AI` 是一种计算机系统，可以完成通常需要人类洞察力的任务。通常，规则引擎主导 `AI` 系统，一个好的 `AI` 系统应当具备基于一系列有意义的 IF–THEN 语句的智能规则引擎。自 20 世纪 50 年代以来，`AI` 已成功应用于视觉感知、语音识别、决策以及语言之间的翻译。`AI` 和 `ML` 经常被混用，尤其是在大数据领域。

如 [图 1.1](#bodymatter-001.xhtml#b_9783110670905-001_fig_001) 所示，`DL` 被视为 `ML` 的一个子类别，而 `ML` 又是 `AI` 的一个子类别。换句话说，所有 `DL` 都是 `ML`，但并非所有 `ML` 都是 `DL`，以此类推。

![Figure 1.1: Relationship between AI, ML, and DL.](graphic/converted/b_9783110670905-001_fig_001.png)

Figure 1.1: Relationship between AI, ML, and DL.

`ML` 兴起于 20 世纪 80 年代，是 `AI` 的一个子集，但具有动态性，不需要人工干预即可进行某些更改。符号逻辑是 `AI` 的一个示例，但不被视为 `ML`。根据 Tom Mitchel 给出的定义 \[[6](#bodymatter-001.xhtml#b_9783110670905-001_ref_006)，“如果计算机程序在任务类别 T 和性能度量 P 方面，其在 T 中的任务上的性能（由 P 衡量）随着经验 E 的增加而提高，则称其从经验 E 中学习。” 在 `ML` 程序中，无需遵循 IF–THEN 规则引擎，而是可以根据所接触的数据自行调整，这被称为学习。学习可分为三种类型，如后续部分所述。

由于 `DL` 是 `AI` 和 `ML` 的子集，`AI` 和 `ML` 的所有特性都固有地传播到 `DL`。它处理应用于 `ANN` 的大量数据。统计数据表明，累积的数据量将从 4.4 波特字节增长到 2020 年的大约 44 波特字节。这就是为什么有时它被称为深度神经网络。

## 1.3 Artificial neural network

`ANN` 是一种信息处理系统，与生物神经元具有多种共同的性能特征。`ANN` 的特征如下 \[[7](#bodymatter-001.xhtml#b_9783110670905-001_ref_007)\]

1. 神经元之间的设计模式，称为架构；

2. 确定连接权重的技术，称为学习算法；

3. 其激活函数。

如 [图 1.2](#bodymatter-001.xhtml#b_9783110670905-001_fig_002) 所示的人工神经元是 `ANN` 的基本构建块或处理单元。

![Figure 1.2: An artificial neuron.](graphic/converted/b_9783110670905-001_fig_002.png)

Figure 1.2: An artificial neuron.

### 1.3.1 Classification of ANN

主要，`ANN`s 可分为两类 \[[7](#bodymatter-001.xhtml#b_9783110670905-001_ref_007)\]: `FFNN`s 和 `RNN`s。

#### 1.3.1.1 Feedforward neural network

`FFNN` 中信号的移动仅在前向路径上进行。由于没有反馈回路，其行为独立于历史输入，仅对当前输入做出反应。`FFNN` 主要有两种类型，如下所示。

##### 1.3.1.1.1 Single-layer feedforward network

这是分层网络的最简单形式（[图 1.3](#bodymatter-001.xhtml#b_9783110670905-001_fig_003)），只有一个源节点的输入层，映射到计算节点的输出层。其输入通过一系列单层权重与输出相关联。自适应线性神经元、Hopfield 网络和学习向量量化是单层前馈网络的常见示例。

![Figure 1.3: Single-layer feedforward network.](graphic/converted/b_9783110670905-001_fig_003.png)

Figure 1.3: Single-layer feedforward network.

##### 1.3.1.1.2 Multilayer feedforward network

这种前馈网络具有一个输入层、一个输出层和一个或多个隐藏层。通过如 [图 1.4](#bodymatter-001.xhtml#b_9783110670905-001_fig_004) 所示连接这些神经元，网络能够评估更高阶的信息。

![Figure 1.4: Multilayer feedforward network.](graphic/converted/b_9783110670905-001_fig_004.png)

Figure 1.4: Multilayer feedforward network.

#### 1.3.1.2 Recurrent neural network

在 `RNN` 的架构中（[图 1.5](#bodymatter-001.xhtml#b_9783110670905-001_fig_005)），应至少有一个反馈回路（也可以是自反馈）。基于反馈模式，有多种循环网络。在特定情况下，网络可以具有一个神经元层，每个神经元将其输出信号反馈到所有其他神经元的输入。其他类型的循环网络可能具有带有隐藏神经元的自反馈回路。Hopfield 网络、双向联想记忆、盒中脑状态和自适应共振理论是 `RNN` 的几个示例。

![Figure 1.5: Recurrent network.](graphic/converted/b_9783110670905-001_fig_005.png)

Figure 1.5: Recurrent network.

### 1.3.2 ANN learning

从环境中获取知识并通过学习提高网络性能是神经网络（`NN`）最重要的特性。该过程指示以下操作顺序 \[[7](#bodymatter-001.xhtml#b_9783110670905-001_ref_007)\]:

* 受环境刺激

* 作为刺激的结果改变自由参数

* 以更好的方式响应环境

#### 1.3.2.1 Unsupervised learning

