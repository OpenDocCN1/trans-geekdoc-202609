
9. Si, X.H. and Wang, Y. (2019) 基于 CNN 和 BLSTM 的短文本情感倾向分析研究. 软件学报, 18, 15-20.

10. Lu, C. (2017) 基于深度学习的情感分析方法研究. 湖南大学, 长沙.

11. Ji, L.Z. (2019) 基于深度学习的文本情感分析技术研究. 北京邮电大学, 北京.

本书版权归Arcler所有

![Image 1727](index-377_1.png)

![Image 1728](index-377_2.png)

![Image 1729](index-377_3.png)

Review of Research on Text Sentiment Analysis Based on Deep Learning 351

12. Hochreiter, S. and Schmidhuber, J. (1997) 长短期记忆网络. 神经计算, 9, 1735-1780. https://doi.org/10.1162/neco.1997.9.8.1735

13. Cho, K., Van Merrienboer, B., Gulcehre, C., et al. (2014) 使用 RNN 编码器-解码器学习短语表示用于统计机器翻译. arXiv 预印本 arXiv:1406.1078. https://doi.org/10.3115/v1/D14-1179

本书版权归Arcler所有

![Image 1730](index-378_1.png)

![Image 1731](index-378_2.png)

![Image 1732](index-378_3.png)

**CHAPTER 17**

**CLASSIFYING HAND**

**WRITTEN DIGITS WITH**

**DEEP LEARNING**

**Ruzhang Yang**

上海外国语学校, 中国上海

**ABSTRACT**

识别自然图像中的数字是计算机视觉的重要任务，在支票阅读、街道号码识别、图像文本转录等实际应用中具有广泛意义。传统的机器学习方法依赖于人工设计的特征，但这些特征难以设计并难以推广到新的情境。

近年来，深度学习通过自动学习良好特征，在众多机器学习任务中取得了卓越的性能。本文研究了利用深度学习进行手写数字识别。

我们表明，使用简单的网络即可在 MNIST 数据集上达到 99.3% 的准确率。此外，我们使用深度网络检测包含多个数字的图像，并表明深度网络不仅能够分类数字，还能够定位它们。

我们在 MNIST 数据集 \[18\] 上测试了我们的方法。该数据集包含 50,000 张训练图像和 10,000 张测试图像，是深度学习方法的重要基准数据集。数据集中的样本图像如图 1 所示。在该数据集上，我们在测试集上实现了 99.3% 的准确率。

我们还研究了多数字分类问题，即图像中包含多个数字的情况。如图所示的示例所示。虽然数字的数量和位置事先未知，但我们的方法仍能准确地定位并分类图像中的所有数字。

**DIGIT CLASSIFICATION WITH DEEP NETWORKS**

**Supervised Learning**

监督学习任务由两个组成部分组成，输入 x 和标签 y。例如，输入可以是手写数字图像或自然物体图像，标签是对应的数字类别或物体类别。目标是学习从输入 x 到标签 y 的正确映射函数 f。为了实现这一点，学习者会得到人类注释者提供的正确映射示例。

![Image 1739](index-381_1.jpg)

![Image 1740](index-381_2.jpg)

![Image 1741](index-381_3.jpg)

![Image 1742](index-381_4.jpg)

![Image 1743](index-381_5.jpg)

![Image 1744](index-381_6.jpg)

![Image 1745](index-381_7.jpg)

![Image 1746](index-381_8.jpg)

![Image 1747](index-381_9.jpg)

![Image 1748](index-381_10.png)

![Image 1749](index-381_11.png)

![Image 1750](index-381_12.png)

Classifying Hand Written Digits with Deep Learning

355

其中 x 是示例输入，y 是人类注释者提供的对应标签。理想情况下，学习后的 f 应该能够将数据集中的每个输入映射到正确的标签，即

The

hope is that the learner can learn the correct mapping between x and y based on these examples, so that on unseen data, the learner f can also correctly classify.

' #

例如，函数类可以是二次函数 **Figure** 1。MNIST 数据集中的样本。

**Figure 2**. 多数字分类。

in this example,

are the parameters. We will denote the

function selected by a parameter choice as f .

To encourage the learner to select a f that maps each x to the correct y

i

i

In general any loss function that takes a smaller value when f(x ) is i

closer to y # ?

i

functions f that outputs a probability distribution. That is for each

is the probability the input belongs to the j-th class. Then we can use the cross-entropy loss

本书版权归Arcler所有

![Image 1751](index-382_1.jpg)

![Image 1752](index-382_2.png)

![Image 1753](index-382_3.png)

![Image 1754](index-382_4.jpg)

![Image 1755](index-382_5.jpg)

![Image 1756](index-382_6.jpg)

![Image 1757](index-382_7.jpg)

![Image 1758](index-382_8.png)

![Image 1759](index-382_9.png)

![Image 1760](index-382_10.png)

Deep Learning Algorithms

356

where K is the number of classes, and

if

and equals to 0

otherwise.

To train the model, we use gradient descent on the loss function L . This

is described by the following process:

{|

¨ # #

2)

We compute the gradient of the loss function ׏ L . Computation

of this gradient is discussed in the next section.

3)

We update the parameters by

<

direction that minimizes the loss L

! < !

However, step size that is too large may lead to instability or

<

\# #

|

¨

The above algorithm reduces L during each iteration. The hope is that

when L is minimized, f (x ) will be close to y , that is, the function f we

i

i

selected can correctly predict the label yi given xi on the training set.

However, even if f correctly predicts every example we provided, this

does not mean that f will classify correctly on new data. For example, f

may have only memorized the training dataset. Therefore we need additional examples

that the learner has not seen during training. The

learner should only be able to classify these new examples correctly if it has learned the correct mapping between x and y. We can compute the testing accuracy by dividing the number of examples f #

\# ' <

we use to evaluate our learner.

**Deep Networks**

在前一节中，我们留下了一个问题：在训练过程中应该选择哪类函数 {f }。本节介绍了一种重要的函数类——深度网络 \[19\] \[20\] \[21\]。
