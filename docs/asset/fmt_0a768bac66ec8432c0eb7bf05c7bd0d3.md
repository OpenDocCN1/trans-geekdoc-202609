
The evolution in the business such as digital marketing is appeared as a part of ML revolution through its direct involvement with the stakeholders. ML is a broader and active area, merely referred to as a branch of science but not its recent state and evolution. It is crucial to understand what makes ML so reputed in the current trend and clarify the misconceptions. Particularly, NNs and DL [11–14] have hyped the ML paradigms and consequently accelerated the mystery around key-notes. In fact, markets and businesses are flourished with the demands of disruptive technologies, yet it brought confusion around terminologies because core concepts of Data Science (DS) (as illustrated in Figure 5.2) are profoundly interweaved and concerned with each other in several aspects.

We have come across several resources like blogs, articles, journals, magazines, chapters, and inferred that preliminaries are impeccably highlighted but little is known about their differences and it remains uncovered. So, let us shift the focus from palpable discussion towards demarcating and disentangling the threads of DS cornerstones.

## 5.3.1 Artificial Neural Network vs. Machine Learning

The most significant and encouraging technique for big data processing is ML. It is phenomenal in analysis with experience or newly data addition and reveals the pattern of interest. When we talk about ML, we talk about a generic term that refers to making systems learn about self-adaption. On the other hand, ANN stems from ML that can frame the algorithms that simulates human brain. It processes the data through multiple layers as mentioned above. Enormous amount of data, normally shared through ubiquitous applications and in unstructured format, is difficult to grasp. But through DL, it becomes least challenging when it comes to unravel this wealth of data. In few words, if ML builds a model around several parameters and triggers the results, those results can be served further to start building ANN model.

![Figure 5.2 Terms attach with DS.](img/fig5-2.jpg)

**Figure 5.2** Terms attach with DS.

## 5.3.2 Machine Learning vs. Deep Learning

One of the most unprecedented yet least emphasized topics of discussion is ML vs. DL. They are not poles apart; instead, they share the common umbrella of DS. In fact, DL is observed as one of the core facet of ML that sharply works on data semantics. The representation of data in DL is, however, hierarchical, and therefore best suited for unlabelled or unstructured data. It carries out data processing with nonlinear approach enabling machines to translate extracted features effortlessly. It is widely adapted for feature engineering and feature transformation. Thus, it is recommendable for developing major CV applications that can pertain to real-world data such as images, sounds, texts, or languages.

## 5.3.3 人工神经网络 vs. 深度学习

人工神经网络（NN）和深度学习（DL）都是前沿技术，在研究领域中占据重要地位。我们经常在不知不觉中将这两个词互换使用，却没有意识到它们之间的微妙差异。它们在概念上相似，但各自也有独立的特点。我们必须认识到，ANN 和 DL 之间存在一条微妙的界限。ANN 种类繁多，而 DL 是一种更复杂的 ANN 形式。区别仅仅在于网络的深度，这体现在其架构中，如图 Figure 5.3 所示。所谓“复杂”，是指信息可以在整个模型中传播的详细程度。模型越复杂，使用的内部层数越多。层数的增加不仅用于利用多余的信息，还用于优化以实现更好的性能。

![Figure 5.3 ANN serves as a base for DL.](img/fig5-3.jpg)

**Figure 5.3** ANN serves as a base for DL.

最后，深度学习（DS）的三大基石——机器学习（ML）、人工神经网络（ANN）和深度学习（DL）——在一句话中被区分开来：DL 是 ML 的一个子领域，利用层次化的 ANN 视角实现 ML 过程。

## 5.4 深度学习架构

## 5.4.1 无监督预训练网络

在基于学习的模型中，直接使用某些变体进行监督学习训练网络可能耗时且效率不高。事实上，可以通过先使用不同的无监督训练策略“预训练”，再借助监督学习算法进行微调，从而缓解这一问题。它加速了计算过程，并大幅降低了对数据的依赖。无监督学习得到的结果可用于提取许多视觉任务（如分类、检测或识别）的高层特征。它能够快速实现更好的优化和收敛，使网络适合高层表示。研究人员在受限玻尔兹曼机（RBM）[15]和自动编码器（AE）[16, 17]中采用预训练方法。Figure 5.4 展示了预训练网络的绝对流程。

![Figure 5.4 Flow for pre-trained network-based learning model [18].](images/fig5-4.jpg)

**Figure 5.4** Flow for pre-trained network-based learning model [18].

## 5.4.2 卷积神经网络

随着深度学习的发展，它提升了人工系统的潜力。它在功能多样性方面具有可扩展性，能够像人类一样观察世界、理解它、并将知识应用于多种任务（如目标检测、识别和视频摘要）。计算机视觉（CV）领域达到了新的高度，尤其是基于卷积神经网络（ConvNet/CNN）[32–35, 38–42]。传统的 CV 算法依赖于手工设计的特征，而 CNN 能够提供对图像更全面的理解，类似于人类的视觉方式。CNN 的处理流程如图 Figure 5.5 所示。它的处理时间更短，因为观测次数减少且具有偏向重用性。

![Figure 5.5 Typical CNN process [19].](images/fig5-5.jpg)

**Figure 5.5** Typical CNN process [19].

## 5.4.3 循环神经网络

前面提到的 DL 类别假设所有输入（以及输出）之间的影响最小。但如果我们想构建一个语义和语法正确的句子呢？单词在句子中隐含依赖，以形成完美句子。这需要两步过程：首先，基于实际世界中词的出现规律进行先验知识；其次，维护“记忆”状态，估算已计算信息的量，以预测句子中的下一个词。循环神经网络（RNN）[20]，其典型架构如图 Figure 5.6 所示，专为处理序列信息（如时间序列）设计。它对序列的每个元素执行相同的任务，输出高度依赖于过去的计算。RNN 能够构建语言模型[21]，并可能用于自然语言处理（NLP）或语言翻译系统（LTSs）。

![Figure 5.6 Primitive RNN architecture.](img/fig5-6.jpg)

**Figure 5.6** Primitive RNN architecture.

## 5.4.4 递归神经网络

递归神经网络（Recursive Neural Network）比 RNN 更为通用。它以层次化方式解析数据（Figure 5.7）。其主要优势在于能够处理通过树形或图形表示的模式，这与固定长度向量形成鲜明对比。向量长度固定，所有数据必须遵守相同长度；而图形则提供了灵活确定任意数量的节点和边的能力。它在 NLP 和图像分析中已取得成功[22]。具体而言，图形中的节点用于表征与实数及绝对值相关的变量向量；而节点之间的边则标记节点间信息的逻辑关联。

## 5.5 为什么 CNN 更适合计算机视觉应用？

计算机视觉（CV）是一门旨在在计算机系统中模拟人类视觉皮层（HVC）的科学分支。它处理图像并提取内在细节，类似于人脑的处理方式。CV 最初仅用于模拟 HVC，但人工智能的革命使其拓展到银行、监控、医疗和汽车等多个领域。

![Figure 5.7 Graph-based representation in recursive NN.](img/fig5-7.jpg)

**Figure 5.7** Graph-based representation in recursive NN.

传统的 ML 算法对于繁琐且难以管理的任务不足以胜任。例如，大多数问题涉及目标分类，即根据图像中物体的显著性为其赋予标签。这会导致计算时间增加或系统开销增大，从而降低吞吐量。深度学习在图像处理活动（如图像分析、分割、分类和识别）方面具有巨大的潜力，广泛嵌入 CV 模型和应用中。CNN 作为 DL 的一个类别，被全球用于辅助 CV 应用，通过分析图像模式实现此目的。其动机是通过多层卷积和池化层逐步缩小图像尺寸，直至由全连接层实现。CNN 架构围绕多种层类展开，下面将简要说明。

## 5.5.1 卷积层

该层执行卷积操作，即在输入图像矩阵上滑动一个小矩阵（通常称为卷积核、滤波器或掩码）(Figure 5.8)。滑动过程中，它将值与初始像素值相乘，然后求和得到一个数值。该过程会重复多次，遍历所有像素值。添加该层的目的在于获得比原始矩阵更小的矩阵尺寸。

## 5.5.2 非线性层

该层紧随卷积层之后，用于引入非线性或数据不一致性。如果网络缺乏非线性，则多层结构等同于单层，因此需要非线性来增强网络对复杂图像的处理能力，从而揭示新的模式。常用的非线性激活函数是 ReLU，但也存在多种激活函数可供选择。

![Figure 5.8 3 × 3 filter convolve over 6 × 6 image matrix.](img/fig5-8.jpg)

Figure 5.8 3 × 3 filter convolve over 6 × 6 image matrix.

## 5.5.3 Pooling Layer

This layer is also helpful in downsizing the image matrix. It is more helpful in reducing the number of parameters and thus, decreasing the computation overhead in the network. The most common method used for pooling is `MaxPooling` (Figure 5.9).

## 5.5.4 Fully Connected Layer

It works similar to conventional ANN and Multilayer Perceptron (MLP), given in Figure 5.10. However, only difference is that now the image matrix is more simplified, optimized and in shape due to pre-processing offered by early layers of CNN. The classification decision is driven by this layer.

By varying the number of convolutional layer, pooling layer, and fully connected layer, we can maximize the network performance for given image processing task such as restoration or classification. There exist many CNNbased architectures which are developed for accelerating training speed that ultimately leads to high accuracy and low error rate. It is bit hard to conceptualise the architecture thoroughly and beyond the scope of chapter, yet we extract some relevant information and summarize it in Table 5.1.

![Figure 5.9 Pooling reduces the size of transition matrix.](img/fig5-9.jpg)

Figure 5.9 Pooling reduces the size of transition matrix.

![Figure 5.10 Multi-layer neural network.](img/fig5-10.jpg)

Figure 5.10 Multi-layer neural network.

Table 5.1 CNN-based different architectures.

| **Architecture** | **Year** | **Group/Authors** | **Error rate (in %)** | **Activation function used** | **No. of parameters (in million)** |
| --- | --- | --- | --- | --- | --- |
| AlexNet [25] | 2012 | SuperVision | 15.3 | ReLU | 62.3 |
| GoogLeNet [26] | 2014 | Google | 6.67 | ReLU | 4 |
| VGGNet [27] | 2014 | Visual Geometry Group | 7.32 | ReLU | 138 |
| ResNet [28] | 2015 | Kaiming He *et al*. | 3.57 | ReLU | 23 |

## 5.6 Unravel Deep Learning in Medical Diagnostic Systems
