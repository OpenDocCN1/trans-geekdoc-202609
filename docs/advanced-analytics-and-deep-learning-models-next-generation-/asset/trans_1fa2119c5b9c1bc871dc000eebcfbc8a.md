

实现所用的数据集包含如 [图 7.1A](#c07.xhtml#fig7-1a) 和 [B](#c07.xhtml#fig7-1b) 所示的卡纳达语主 aksharas 和 vattaksharas。主 aksharas 有 340 个类别，vattaksharas 有 32 个类别。每个类别收集的样本平均数量为 50。输入扫描图像被分割为行、单词和字符，分割后的字符被收集以构建主 aksharas 和 vattaksharas 的数据库。这些训练样本被输入到相应的 CNN 模型中。模型使用批量大小为 32，训练 15 个 epoch。权重使用 RMS prop 优化器和交叉熵损失函数进行更新。训练好的模型被保存，然后用于测试。在测试阶段，如 [图 7.3A](#c07.xhtml#fig7-3a) 所示的样本图像被输入系统以提取行、单词和字符，单个字符由训练好的模型识别，然后转换为可输出的文本，如 [图 7.3B](#c07.xhtml#fig7-3b) 所示。系统获得的错误被突出显示。该设计的模型在不同段落上进行测试，预测准确率被记录并在 [表 7.1](#c07.xhtml#tab7-1) 中列出。该模型的总体准确率为 81.76%。

![Figure 7.3 (A) Sample image.](images/fig7-3a.jpg)

[**Figure 7.3 (A)**](#c07.xhtml#rfig7-3a) Sample image.

![Figure 7.3 (B) Output edible text.](images/fig7-3b.jpg)

[**Figure 7.3 (B)**](#c07.xhtml#rfig7-3b) Output edible text.

### 7.2.4 Merits and Demerits

该系统能够为任何字体大小生成可输出的文本，但如果字符图像中包含两个 Aksharas（理想情况下应进一步分割为独立的 Aksharas），会导致 CNN 出现误预测，从而产生错误输出。此外，在罕见的两个 Vatt Aksharas 同时存在的情况下，字符分割同样会生成包含两者的图像，而不是分开的图像。

[**Table 7.1**](#c07.xhtml#rtab7-1) Model prediction accuracy.

| **Input paragraph no.**  || **No. of input words** || **Correct output** || **Incorrect output** || **Accuracy (in %)** |

| --- | --- | --- | --- | --- |

| 1 || 82 || 73 || 09 || 89.02 |

| 2 || 40 || 34 || 06 || 85 |

| 3 || 42 || 34 || 08 || 80.95 |

| 4 || 52 || 41 || 11 || 78.84 |

| 5 || 24 || 18 || 06 || 75 |

| Overall || 81.76 |

### 7.2.5 Applications

可以开发以卡纳达语为中心的语言翻译应用程序，将卡纳达语内容翻译成任何其他语言，反之亦然。这些应用程序对于生活在卡纳塔克邦且不懂本地语言的人将非常有用。

## 7.3 Recurrent Neural Network

人工神经网络（ANN）的卓越洞察力被用于计算人类神经系统的认知模型。ANN 在图像感知与分类、自动驾驶汽车、数据分析与预测以及动画游戏等多种应用中的发展证明，ANN 模型的性能等同于或优于人类。ANN 的基本架构接受依赖的多维数据，并根据应用需求调整其结构。基于循环神经网络（RNN）的深度学习架构的发展，在时间序列、生物学以及语音转文本转换等许多应用中实现了创新，这些应用涉及具有序列依赖性的数据。RNN 既处理真实值（时间序列），也处理变长输入的符号值。利用时间分层 RNN 结构对文本进行语义解释，催生了情感分析、机器翻译和信息分析等新兴研究领域 \[8–15, 27–30\]。

RNN 以隐藏层的形式保存记忆。在 RNN 中，信息在网络的各个层和序列位置之间传递。虽然传统的 ANN 在处理单层变长输入时会感到困惑，但 RNN 接收对应序列每个位置的多层单输入。每一层的输入都具有相关的建模参数，这些参数在整个网络中重复出现，因此，“循环神经网络”被定义为隐藏层神经元中的自环，使前一输出能够循环。RNN 的隐藏神经元保存同一序列中先前输入的摘要，这使其区别于其他前馈网络。

### 7.3.1 Architecture

RNN 是一种模型，其中第一层的输出作为输入传递给下一层神经元，如 [图 7.4](#c07.xhtml#fig7-4) 所示。在传统神经网络中，所有神经元的输入和输出都是相互独立的。在需要预测句子下一个词的情况下，需要记住前面的词。因此，选择 RNN 使用隐藏层来满足这一需求。该模型的主要且最重要的特征是隐藏状态，它能够记住关于序列的一些信息。

![Figure 7.4 Recurrent neural network architecture.](images/fig7-4.jpg)

[**Figure 7.4**](#c07.xhtml#rfig7-4) Recurrent neural network architecture.

### 7.3.2 Types of Recurrent Neural Networks

基于工作原理，RNN 分为三种类型：a) Simple RNN，b) Gated Recurrent Units (GRUs)，和 c) Long Short-Term Memory (LSTM) Networks。

#### *7.3.2.1 Simple Recurrent Neural Networks*

Simple RNN 有三层：输入层、隐藏层和输出层。基于架构，Simple RNN 分为两种类型：i) Elman Networks 和 ii) Jordan Networks。在 Elman Networks 中，来自隐藏层的一组上下文单元被连接，可以存储前一隐藏层单元的值和序列预测。而 Jordan Network 的输出层则反馈一组上下文单元，如 [图 7.5](#c07.xhtml#fig7-5) 所示。

让我们考虑

> x[t]: input vector  

> h[t]: hidden layer vector  

> o[t]: output vector  

> y[t]: target vector  

> b[x]: bias vector (input layer)  

> b[h]: bias vector (hidden layer)  

> b[o]: bias vector (output layer)  

> W[x,] W[h]: weight parameter matrix  

> e(^.), f(^.): a nonlinear Activation function (e.g., tanh and sigmoidal)

![Figure 7.5 Simple RNN.](images/fig7-5.jpg)

[**Figure 7.5**](#c07.xhtml#rfig7-5) Simple RNN.

对于总时间步数 T：

*Feedforward Phase (h[t], y[t], L[t], L):* 对于给定的序列输入，RNN 按如下方式计算隐藏状态输出和模型输出：

(7.4)![](images/eq7-4.jpg)(7.5)![](images/eq7-5.jpg)(7.6)![](images/eq7-6.jpg)(7.7)![](images/eq7-7.jpg)

在梯度消失的情况下，遥远时间步的贡献会变得混乱，因此认知仅使用更近期的时间步信息来实现。具有这种局限性的 RNN 不适合具有长期依赖性的序列。如果损失函数的归一化梯度呈指数级上升，那么在梯度爆炸条件下，乘积将不会是标量。具有这种局限性的 RNN 认知变得不稳定，网络可能会崩溃。隐藏状态中的层数（k）越多，归一化标量值就越形成谱矩阵形式，这使得认知变得复杂和困难。然后，利用链式法则计算所有矩阵的范数以学习梯度问题。因此，RNN 模型简单而强大，且 RNN 的训练在具有许多深层结构时存在梯度消失和梯度爆炸的限制。

梯度限制已通过延迟神经网络、优化方法、惩罚、正则化技术、梯度裁剪、分级泄漏单元、LSTMs 和 GRUs 得到处理。

#### *7.3.2.2 Long Short-Term Memory Networks*

