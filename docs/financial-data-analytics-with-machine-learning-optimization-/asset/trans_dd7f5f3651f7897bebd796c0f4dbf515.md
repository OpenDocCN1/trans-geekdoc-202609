

14. 根据 `K`‐means 聚类的设计，人工聚类的位置由球 `B Subscript k` 的位置驱动。确实，当 `L less-than K` 时，根据鸽巢原理，至少有一个人工聚类包含多个球的部分，从而证明了 `script upper A 3` 的非空性。此外，由 `K`‐means 聚类产生的这种人工聚类通常包含两个球的相当比例，这就是为什么 `p overTilde Subscript k l` 和 `p overTilde Subscript k prime l` 被假设具有下界，且概率趋近于 1，当 `n right-arrow infinity` 时。

# CHAPTER 15  

金融中的深度学习应用

前几章介绍的二元逻辑回归、多元 Logit 模型和分类树是常见的统计分类器。一种完全不同的方法基于神经网络（NNs），旨在模拟人脑的运作机制。尽管人脑如何记忆、识别模式和概括概念尚未被完全理解，但神经科学家对其一些方面有深入了解，这有助于构建人脑作为神经网络的可行模型。

1943 年，McCulloch 和 Pits [\[18\]](#c15.xhtml#c15-bib-0018) 提出了一个简单的数学模型来解释生物神经元的工作原理。此后，直到 1970 年现代计算机首次发明，才取得了很大进展。在 1970 年代，*Linnainmaa Seppo* 发明了 *backpropagation* 算法来训练神经网络，以尽可能使拟合输出与观测响应匹配 [\[13](#c15.xhtml#c15-bib-0013), [14\]](#c15.xhtml#c15-bib-0014)。随后，实验室中出现了许多成功的示例和应用。在 1980 年代，研究从实验室转向商业世界，典型应用包括欺诈信用卡交易检测、房地产评估和数据挖掘。在深入研究 NNs 之前，我们先介绍人脑的一些典型结构。

## 15.1 HUMAN BRAINS AND ARTIFICIAL NEURONS

我们的大脑由约 860 亿个称为神经元的特殊细胞组成。这些神经元中的每一个通常与成千上万个其他神经元相连。最重要的是，与其他细胞不同，这些神经元不会再生。普遍认为，这些神经元负责我们记忆、学习、概括概念和思考的能力。每个神经元内部有四个基本组件：*dendrites*（树突）、*cell body*（细胞体）、*axon*（轴突）和 *synapses*（突触）；参见 [Figure 15.1](#c15.xhtml#c15-fig-0001)。这些神经元相互连接形成一个巨大的网络。尽管这些神经元的确切功能仍然是个谜，但模拟这些神经元的简单数学模型在图像处理和文本挖掘中的模式识别、分类和预测问题上表现出惊人的性能。

![FIGURE 15.1 An illustration of the analogy between actual neurons and abstract ones. (Source: https://stock.adobe.com/in/images/cerebral-cortex-pyramidal-neuron/653658834)](images/c15f001.png)

[**FIGURE 15.1**](#c15.xhtml#R_c15-fig-0001) 实际神经元与抽象神经元之间类比的示意图。（来源：[https://stock.adobe.com/in/images/cerebral-cortex-pyramidal-neuron/653658834](https://stock.adobe.com/in/images/cerebral-cortex-pyramidal-neuron/653658834)）

![FIGURE 15.2 An artificial neuron.](images/c15f002.png)

[**FIGURE 15.2**](#c15.xhtml#R_c15-fig-0002) 人工神经元。

树突负责接收来自其他神经元的信息；细胞体用于处理收集的信息；轴突放大处理后信息携带的信号并传递给其他神经元；突触是轴突末端与其他神经元树突之间的连接点。为了模拟神经元的功能，我们参考如 [Figure 15.2](#c15.xhtml#c15-fig-0002) 所示的人工神经元。

这里 `x 1 comma ellipsis comma x Subscript p Baseline` 是从其他神经元或外部环境接收到的输入。总输入 `h` 由这些输入与权重 `w 1 comma ellipsis comma w Subscript p Baseline` 的线性组合构成，并加上作为 *bias*（偏置）项的 `w 0`。*transfer function*（传递函数，或称 *activation function*（激活函数））将 `bold-italic x` 的输入 `h` 转换为输出 `h prime equals f left-parenthesis h right-parenthesis`。随后，该输出 `h prime` 可能作为输入传递给其他神经元。轴突的一些常用传递函数如 [Figure 15.3](#c15.xhtml#c15-fig-0003) 所示。

![FIGURE 15.3 Commonly used activation functions for an axon.](images/c15f003.png)

[**FIGURE 15.3**](#c15.xhtml#R_c15-fig-0003) 轴突常用的激活函数。

通常使用逻辑传递函数，这就是为什么人工神经网络被视为逻辑回归的重要扩展。

## 15.2 FEEDFORWARD NETWORK

这些人工神经元从一层连接到另一层，形成一个网络。

![FIGURE 15.4 Illustration of a 4‐3‐2 ANN.](images/c15f004.png)

[**FIGURE 15.4**](#c15.xhtml#R_c15-fig-0004) 4‐3‐2 人工神经网络（ANN）示意图。

参考 [Figure 15.4](#c15.xhtml#c15-fig-0004)，有三层：输入层、隐藏层和输出层。输入层、隐藏层和输出层中的神经元数量分别为 4、3 和 2，因此被称为 4‐3‐2 人工神经网络（ANN）。

1. 对于标准 ANN，只有一个隐藏层。如果有多个隐藏层，则称为多层感知器（MLP）；有关后者的更详细讨论请参见 [Section 15.7](#c15.xhtml#c15-sec-0008)。

2. 输入层和输出层中的神经元数量由问题的性质决定，而隐藏层中的神经元数量由用户定义。

