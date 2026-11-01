
也可以训练自己的词向量；这通常是在为特定任务训练网络的同时进行的。与通用的预训练嵌入不同，为特定任务生成的词嵌入可以在精心选择的语料上训练，并倾向于强调对该任务有用的词语方面。例如，假设任务是词性标注（POS 标注）（参见 [第 24.1.6 节](#Chapter24-01.xhtml#sec24-1-6)）。请回忆，这涉及为句子中的每个词预测正确的词性。尽管这是一个简单的任务，但它并非微不足道，因为许多词可以以多种方式标注——例如，词 cut 可以是现在时动词（及物或不及物）、过去时动词、原形动词、过去分词、形容词或名词。如果附近的时态副词指的是过去，这就表明 cut 的这一特定出现是过去时动词；那么我们希望嵌入能够捕捉副词的指过去方面。

词性标注为深度学习在 NLP 中的应用提供了一个良好的入门，而不会出现像问答（参见 [第 25.5.3 节](#Chapter25-05.xhtml#sec25-5-3)）这样更复杂任务的复杂性。给定带有词性标签的句子语料，我们同时学习词嵌入和词性标注器的参数。过程如下：

1. 选择用于标注每个词的预测窗口的宽度 `w`（一个奇数词数）。典型值是 `w = 5`，意味着标签是基于该词加上左右各两个词来预测的。将语料库中的每个句子拆分为长度为 `w` 的重叠窗口。每个窗口产生一个训练示例，由 `w` 个词作为输入，中间词的词性类别作为输出。
2. 创建一个词汇表，其中包含在训练数据中出现次数超过例如 5 次的所有唯一词标记。将词汇表中的词总数记为 `v`。
3. 以任意顺序（也许按字母顺序）对该词汇表进行排序。
4. 选择一个值 `d` 作为每个词嵌入向量的大小。
5. 创建一个新的 `v`×`d` 权重矩阵，称为 `E`。这是词嵌入矩阵。`E` 的第 `i` 行是词汇表中第 `i` 个词的词嵌入。以随机方式（或从预训练向量）初始化 `E`。
6. 设置一个输出词性标签的神经网络，如 [图 25.3](#Chapter25-01.xhtml#fig25-3) 所示。第一层将由 `w` 个嵌入矩阵的副本组成。我们可能会使用两个额外的隐藏层 `z1` 和 `z2`（分别具有权重矩阵 `W1` 和 `W2`），然后是一个 `softmax` 层，输出中间词可能的词性类别上的输出概率分布 `y`：

Description  
Part (1): A vertical line is labeled image plane. Two convex lenses and a concave lens are labeled lens system. The concave lens is positioned between the two convex lenses in the lens system. The lens system is to the right side of the image plane. A candle is to the right of the lens system. The vertical distance from the flame to the end of the plane is labeled focal plane. The horizontal distance from the tip of the candle flame to the focus is labeled depth of field. Two lines toward the right from the top and bottom of the lens system meet at the tip of the candle flame. Two lines toward the left from the top and bottom of the lens system meet on the horizontal plane below its center. Part (2): A spherical section depicts the schematic representation of an eye. The outer layer on the left is labeled cornea. A convex lens is to the right of the cornea and a pair of extensions on the top and bottom of the lens is labeled iris. The innermost layer on the right end is labeled retina. A bulge toward the right of the retina is labeled optic nerve. An inclined line through the center of the lens is labeled the visual axis. A horizontal line through the center of the lens is labeled optical axis. The end of the visual axis on the retina is labeled Fovea.

×![](images/Fig-352.jpg)

图 25.3 前馈词性标注模型。该模型以 5 个词的窗口作为输入并预测中间词的标签——这里是 cut。该模型能够考虑词的位置，因为每个 5 个输入嵌入都乘以第一隐藏层的不同部分。词嵌入以及三个层的参数值在训练期间全部同时学习。

```
z[1] = σ(W[1]x)
z[2] = σ(W[2]z¹)
ŷ = softmax (W[out]z[2])
```
7. 要将 `w` 个词的序列编码为输入向量，只需查找每个词的嵌入并拼接嵌入向量。结果是一个长度为 `wd` 的实值输入向量 `x`。即使某个词出现在第一个位置、最后一个位置或中间位置，其嵌入向量也是相同的，但每个嵌入都会乘以第一隐藏层的不同部分；因此我们隐式地编码了每个词的相对位置。
8. 使用梯度下降训练权重 `E` 以及其他权重矩阵 `W1`、`W2` 和 `Wout`。如果一切顺利，中间词 cut 将被标记为过去时动词，依据窗口中的证据，包括时间过去词“yesterday”、cut 前紧邻的第三人称主语代词“they”等。

词嵌入的一种替代方案是字符级模型，其中输入是字符序列，每个字符编码为 one-hot 向量。这种模型必须学习字符如何组合成词。NLP 中的大多数工作坚持使用词级而非字符级编码。

## 25.2 用于 NLP 的循环神经网络

我们现在有了对孤立单个词的良好表示，但语言由有序的词序列组成，其中周围词的上下文很重要。对于像词性标注这样简单的任务，约五个词的小型固定窗口通常提供足够的上下文。

更复杂的任务，如问答或指代消解，可能需要数十个词作为上下文。例如，在句子“Eduardo told me that Miguel was very sick so I took him to the hospital”中，知道 him 指的是 Miguel 而不是 Eduardo 需要从 14 个词句子的第一个词到最后一个词的上下文。

### 25.2.1 使用循环神经网络的语言模型

我们将从创建具有足够上下文的语言模型的问题开始。请回忆，语言模型是词序列上的概率分布。它允许我们根据之前的所有词预测文本中的下一个词，并且常被用作更复杂任务的构建块。

使用 `n` 元语法模型（如 [第 24.1 节](#Chapter24-01.xhtml#sec24-1) 中所述）或具有固定 `n` 个词窗口的前馈网络构建语言模型可能会因上下文问题而遇到困难：所需的上下文要么超过固定窗口大小，要么模型参数过多，或两者兼有。

此外，前馈网络存在不对称问题：它所学到的关于例如词 him 作为句中第 12 个词出现的知识，必须为 him 在句子中其他位置的出现重新学习，因为每个词位置的权重不同。

在 [第 22.6 节](#Chapter22-06.xhtml#sec22-6) 中，我们介绍了循环神经网络或 RNN，它被设计用于逐个处理时间序列数据。这表明 RNN 可能适用于逐词处理语言。我们在此将 [图 22.8](#Chapter22-06.xhtml#fig22-8) 重复为 [图 25.4](#Chapter25-02.xhtml#fig25-4)。

Description

