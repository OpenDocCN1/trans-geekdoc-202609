
虽然一些移动性属性是通过数据拟合发现的，但这些结果很大程度上取决于所选数据集，导致不同研究中得出不一致的结论。此外，更为关键的是要了解用户特定的移动轨迹或不同小区中移动用户数量的变化趋势。然而，这种信息无法直接从这些具有统计显著性的属性中获取。幸运的是，人类移动性在一定程度上已被证明是可预测的。Song 等人（[2010](#c07.xhtml#c07-bib-0024)）利用信息论定量分析了移动轨迹的规律性。他们发现，通过计算一个用户运动历史的位置序列的条件熵，用户移动性包含 93% 的潜在可预测性，这说明了通过历史轨迹信息学习用户移动模式的可行性。为了预测用户的未来位置，传统的 `ML` 技术如 K-最近邻（`KNN`）、线性回归、决策树和关联规则是明显的候选应用方法 Liao 等人（[毛伊岛，美国，2012年4月](#c07.xhtml#c07-bib-0016)） Tkačík 和 Kordík（[温哥华，加拿大，2016年7月](#c07.xhtml#c07-bib-0025)）。此外，值得我们参考的是，以循环神经网络（`RNNs`）为代表的一些 `DL` 方法已被用于时间序列问题，包括预测交通 Zhang 和 Patras（[洛杉矶，美国，2018年6月](#c07.xhtml#c07-bib-0033)）和行人轨迹 Alahi 等人（[拉斯维加斯，美国，2016年6月-7月](#c07.xhtml#c07-bib-0001)）。然而，Alahi 等人（[拉斯维加斯，美国，2016年6月-7月](#c07.xhtml#c07-bib-0001)）的工作只能通过特定小范围场景（如酒店或交叉路口）中的静态图像预测人类轨迹，这与所需蜂窝网络场景的情况不同。

## 7.3 数学背景

在本节中，我们讨论了本章其余部分 heavily used 的基本数学工具。特别是，我们概述了 `ANNs` 和 `LSTM`。

`ANNs` 被构建为一类 `ML` 模型，可以消除基于规则编程的传统学习算法的缺点 LeCun 等人（[2015](#c07.xhtml#c07-bib-0012)）。`ANNs` 可分为两大类：前馈神经网络（`FFNNs`）和 `RNNs`。`FFNNs` 通常由输入层、输出层和隐藏层（如有必要）组成。每一层由若干个神经元和一个激活函数组成。`FFNNs` 的简单示意图如图 [图 7.1](#c07.xhtml#c07-fig-0001)a 所示。在 `FFNNs` 中，同一层内的神经元之间没有连接，且神经元不能跨层连接，这意味着信息从输入层单向流动，经过隐藏层（如有），到达输出层。`FFNNs` 广泛应用于数据分类、目标识别和图像处理等各个领域。然而，受其内部结构限制，`FFNNs` 不适合处理历史依赖关系。

`RNNs` 作为另一种类型的 `ANNs`，在神经层结构上与 `FFNNs` 相似，但允许同一隐藏层内神经元之间的连接。`RNN` 的示意图如图 [图 7.1](#c07.xhtml#c07-fig-0001)b 左侧所示。此外，[图 7.1](#c07.xhtml#c07-fig-0001)b 的右侧是 `RNN` 模型的展开形式，表明 `RNNs` 根据当前时刻的输入 ![images](images/c07-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi mathvariant="bold">x</mi><mi>t</mi></msub></mrow></math> 和前一时刻的隐藏状态 ![images](images/c07-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi mathvariant="bold">h</mi><mrow><mi>t</mi><mo>&#8722;</mo><mn>1</mn></mrow></msub></mrow></math> 计算当前时刻的输出。因此，`RNNs` 允许历史输入信息存储在网络的内部状态中，从而能够将所有历史输入数据映射到最终输出。理论上，`RNNs` 有能力处理这种长程依赖。然而，实践中，`RNNs` 似乎无法完成期望的任务。这一现象已被 Hochreiter 和 Schmidhuber（[1997](#c07.xhtml#c07-bib-0009)）深入探讨，他们解释了一些导致此类学习可能困难的根本原因。为解决这一问题，`LSTM` 通过改变传统 `RNNs` 中隐藏神经元的结构而被革命性地开发出来 Hochreiter 和 Schmidhuber（[1997](#c07.xhtml#c07-bib-0009)）。

![图 7.1 一个 FFNN 和一个 RNN 的示意图。](images/c07f001.jpg)

[图 7.1](#c07.xhtml#R_c07-fig-0001) 一个 FFNN 和一个 RNN 的示意图。

![图 7.2 一个 LSTM 记忆块的示意图。](images/c07f002.jpg)

[图 7.2](#c07.xhtml#R_c07-fig-0002) 一个 LSTM 记忆块的示意图。

更具体地说，`LSTM` 神经网络由多个基本记忆块的副本组成，每个记忆块包含一个记忆单元和三种类型的门（输入门、输出门和遗忘门），如图 [图 7.2](#c07.xhtml#c07-fig-0002) 所示。记忆单元是 `LSTM` 的关键组件，负责不同时间步的信息传递。与此同时，这三个门各自包含一个 sigmoid 层，可选择性地传递信息，负责保护和控制单元状态。顾名思义，输入门控制输入的哪一部分将被用于更新单元状态。类似地，遗忘门控制旧单元状态的哪一部分将被丢弃，而输出门决定新单元状态的哪一部分将被输出。

对于时间步 ![images](images/c07-i0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>t</mi></mrow></math> 的记忆块，我们使用 ![images](images/c07-i0004.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>f</mi><mi>t</mi></msub></mrow></math>、![images](images/c07-i0005.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>i</mi><mi>t</mi></msub></mrow></math> 和 ![images](images/c07-i0006.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>o</mi><mi>t</mi></msub></mrow></math> 分别表示遗忘、输入和输出门。假设 ![images](images/c07-i0007.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>x</mi><mi>t</mi></msub></mrow></math> 和 ![images](images/c07-i0008.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>h</mi><mi>t</mi></msub></mrow></math> 表示当前时间步的输入和输出，![images](images/c07-i0009.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>h</mi><mrow><mi>t</mi><mo>&#8722;</mo><mn>1</mn></mrow></msub></mrow></math> 是前一时间步的输出，![images](images/c07-i0010.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>&#963;</mi></mrow></math> 表示 sigmoid 激活函数，且 ![images](images/c07-i0011.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mo>&#8855;</mo></mrow></math> 表示 Hadamard 积，`LSTM` 方案的关键方程如下给出：
