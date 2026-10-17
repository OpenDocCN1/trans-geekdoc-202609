
![Image 114](index-36_4.png)

Deep Learning Algorithms

10

**Figure 4.** 深信网络。

**玻尔兹曼机 (BM)**

BM 是一个由均匀连接的、类似神经元的单元组成的网络，负责随机地决定是否关闭或开启。

通过玻尔兹曼机解决计算问题，如搜索、优化和学习问题。在学习算法中，许多特征在训练数据集上表现出非常复杂的行为。玻尔兹曼机用于分类和降维。

**受限玻尔兹曼机 (RBM)**

RBM 于 1986 年由 Smolensky 引入：包含可见层和隐藏层，但可见-可见和隐藏-隐藏之间没有连接。它可以学习数据集的概率分布。

RBM 的应用包括特征学习、协同过滤、降维和分类。

**卷积神经网络 (CNN)**

在 CNN 中，层与输入层以及相互之间精心连接。每个神经元的后续层有一个特定的功能，例如它只负责输入的一部分。CNN 现在被广泛用于遥感、计算机视觉、音频和文本处理 [10]。

**深度自动编码器**

与其他方法类似，深度自动编码器也包含多个隐藏层。与只有一个隐藏层的简单自动编码器不同，深度自动编码器包含多个隐藏层。本书版权归Arcler所有

![Image 115](index-37_1.png)

![Image 116](index-37_2.png)

![Image 117](index-37_3.png)

Advancements In Deep Learning Theory And Applications: ...

11

隐藏层。在深度自动编码器中，训练通常比较复杂，你需要先训练一个隐藏层来重构输入数据的结构，然后再用这些数据训练其他隐藏层，以此类推。深度自动编码器的一些应用包括图像提取、图像生成、推荐系统以及序列到序列预测。

**梯度下降 (GD)**

GD 用于降低整体损失函数；它被视为一种优化算法，在机器学习中广泛用于系数函数的确定。当无法通过分析估计参数时，GD 用于计算所需的参数。

使用 GD 权重的模型在每个 epoch 中会被更新。它用于监督机器学习。

**随机梯度下降 (SGD)**

与 GD 类似，SGD 也是一种优化算法，但 GD 用于数据集较小的情况，而 SGD 通常用于数据集较大的情况，如果用于大量数据集，SGD 的成本会非常高。

**深度学习的应用**

深度学习是当前大规模应用的新兴和处于最先进的技术。深度学习（也称为差分编程或结构学习）属于机器学习的一个大类。

它是前沿技术，用于许多新兴研究领域，如下所述。

**深度学习在自动语音识别中**

自动语音识别是深度学习的一个令人信服的应用。语音识别意味着将语音作为输入输入到机器中，使输入处理变得非常容易，并且有数百种其他优势，例如 illiterate 人（文盲）也能使用技术、语音编码、文本到语音合成、语音识别、说话人识别、语音增强、语音分割、语言识别等诸多功能 [11]。语音是自然的交流形式，因此被视为一个非常有说服力的应用。

本书版权归Arcler所有

![Image 118](index-38_1.jpg)

![Image 119](index-38_2.png)

![Image 120](index-38_3.png)

![Image 121](index-38_4.png)

Deep Learning Algorithms

12

**图像识别**

基于深度学习的图像识别技术变得非常流行，并提供准确、结果导向的技术，依赖于机器的训练和经验。深度学习在图像识别和水下目标识别中的图像分类中发挥着非常重要的作用，尽管水下图像始终带有噪声和退化 [12]。MNIST 是用于图像分类最著名的例子之一，下面是 MNIST 数据集的简单数据集示例（图 5）。

**Figure 5.** 手写数字 MNIST 数据集的图像示例。

**自然语言处理**

LSTM 在语言建模和机器翻译方面帮助很大 [13]；语言建模任务是理解语言。为了实现语言，使用神经网络模型。Google 翻译是最著名且最广泛使用的应用之一；Google 翻译支持全球超过 100 种语言。它也使用 LSTM；从数百万个示例中学习，并翻译整句话，而不是逐词翻译。BERT（Google）是该领域最常用的技术之一，取得了许多基准成果，包括句子分类、句子对分类、句子对相似性、句子标记、创建上下文感知的词嵌入、问答、选择题等。2019 年还开发了其他一些基于变换器的语言模型，包括 XLNet（Google/CMU）、RoBERTa（Facebook）、Distil BERT（hugging Face）、CTRL（Salesforce）、GPT-2（OpenAI）、ALBERT（Google）和 Magatron（NVIDIA）。Magatron 是历史上最大的变换器模型，拥有 830 万个参数的变换器语言模型。XLNet 在性能方面是最佳的变换器；XLNet 在 20 个任务上通常比 BERT 表现出显著优势。ALBERT

由 Google 开发，用于通过跨层降低参数。本书版权归Arcler所有

![Image 122](index-39_1.jpg)

![Image 123](index-39_2.png)

![Image 124](index-39_3.png)

![Image 125](index-39_4.png)

Advancements In Deep Learning Theory And Applications: ...

13

参数共享。该领域的最先进状态是关于多域任务导向对话系统 [14]。2020 年，预计将结合常识推理与语言模型，将语言模型的上下文扩展到数千个词，并更加关注开放域对话（图 6）。

**Figure 6.** NLP 和深度学习。

**游戏和机器人**

机器人是人工智能代理，在现实世界中工作，取代人类。OpenAI 和 Dota 2 是知名游戏；2017 年，1v1 机器人战胜顶尖职业 Dota 2 玩家；2018 年，OpenAI Five 输掉两场比赛给顶尖 Dota 2 玩家，而 2019 年，OpenAI Five 战胜 OG 团队（2018 年的世界冠军）。OpenAI Five 在 2019 年获胜仅是因为训练计算量更大；当前版本消耗每天 800 千万次浮点运算，并经过约 45,000 年的 Dota 自我对弈，历时 10 个实时月。

当前版本的胜率为 99.9%，高于 2018 版本。这是深度学习领域中最佳的经验之一，系统学会相互玩耍并逐步改进。OpenAI Rubiks Cube  manipulation 是机器人领域的另一个例子。研究人员预计 2020 年将在真实世界交互任务的操作中实施强化学习方法。

在游戏中，专家从不同机器中获益，利用这些机器帮助人类专家发现新策略。Waymo 是一家专注于开发自动驾驶的公司，类似于 Tesla，2018 年 10 月成立；他们已在道路上行驶了 1000 万英里，到 2020 年已行驶 2000 万英里，涉及 20,000 种结构测试类别，并开始在没有安全驾驶员的情况下进行测试。

本书版权归Arcler所有

![Image 126](index-40_1<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>
