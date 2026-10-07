
其他。

- 使用大小相近的序列批量加速训练，以减少填充（padding）。
- 在翻译语言时，你总是需要某种方法获取 OOV（未登录）标记。在本章中，你直接丢弃它们，但下一章将考虑其他选项。
- 你可以类别特征（如文本中的字符）进行独热编码，以表示它们而不暗示任何序数关系。
- 用于选择解码器预测标记的贪心算法并不总是产生最好的结果。下一章将简要描述一种替代方案。
- Core ML 和 coremtools Python 包正在积极演进，你有时需要一些变通。例如，coremtools 目前无法转换包含共享层的 Keras 模型，这要求你构建新的编码器和解码器模型，并从你训练的 seq2seq 模型中设置它们的权重。
- 将模型权重从 32 位浮点转换为 16 位浮点数，以减小应用的大小。
- 总结来说，Xcode 将顺序输入显示为序列中一个元素的 MLMultiArray，但模型实际上可以接受任何长度的序列。要将序列传递给模型，请使用形状为 `SEQUENCE_LENGTH x 1` 的三维 MLMultiArray。在独热编码时，ITEM_SIZE 是本章中使用的可能值的数量。

## 从这里开始

本章介绍了序列到序列模型，并向你展示了如何构建一个可以翻译西班牙语文本的模型。下一章将接续本章内容，探索更高级的选项以提高翻译的质量。

## 第 16 章：自然语言转换，第 2 部分
作者：Chris Lar

**更新说明：** Apple 喜欢等待。在编写本文时，所需的 CoreML API 尚未完全准备就。随着 Apple 发布新的 API，我们将继续更新。我们还会通知你并让你知道如何访问更新版本。

上一章介绍了序列到序列模型，你并构建了一个将西班牙语翻译成英语的模型。本章引入了其他可以提高性能的技术。它接续了你之前的进度，所以请继续使用你已经创建的环境。如果不完成上一章的内容，很难读懂本章，但如果你想要一个更整洁的起点，可以使用第 15 章中的最终版本。

## 双向 RNN (Bidirectional RNNs)

你原始的模型仅使用句子中出现在它之前的字符来预测下一个字符。但这真的是人们阅读的方式吗？考虑以下两个句子及其西班牙语翻译（根据 Google）：

### 上下文至重要的示例

| 英语 | 西班牙语 |
| :--- | :--- |
| She waited by the bank of the river. | Ella esperó la orilla del río. |
| She waited by the bank until he came out with the money. | Ella esperó junto hasta que salió del dinero. |

英语句子的前五个单词是相同的，但前两个词出现在不同的西班牙语翻译中。这是因为“bank”一词在每个句子中的含义不同，因此在阅读完整上下文（包括前后的词）之前，你无法知道它的含义。

为了考虑每个标记周围的完整上下文，你可以使用所谓的**双向循环网络**（BRNN），它像下面这样从两个方向处理序列：

![](img/5720be5c3cca252e12448e68d25607b5527_0.png)

如图所示，双向 RNN 由两个循环层组成：一个一个从左到右处理序列，另一个从右到左处理。这些层相互独立运行，但它们的输出会被合并成单个向量。在本章中，你将它们拼接（concatenate），但其他合并选项（如求和或平均）也可以有效。你的双向层输出中的单元数量将是其循环层数量的两倍。

正向层和反向层本身可以是任何循环类型，例如你在书中其他地方过的 LSTM。然而，在本章中，你将使用一种名为**门控循环单元**（gated recurrent unit，GRU）的新类型。

GRU 在 LSTM 之后发明，旨在实现在更快的同时学习更长期关系。在内部，它们的实现方式与 LSTM 不同，但从用户的角度来看，主要区别是它们没有独立的隐藏状态（hidden states）和单元状态（cell states）。它们只有隐藏状态，这当你必须直接管理状态时（例如在 seq2seq 模型中管理解码器那样），处理起来会稍微简单一点。

现在，你将尝试你在上一章中训练的模型的新版本——一个包含双向编码器的模型。本节的 Python 代码与你为第一个 seq2seq 模型编写的代码几乎相同。因此，该章节的资源包含一个预填充的 Jupyter notebook，运行在 `notebooks/Bidir-Char-Seq2seq-Starter.ipynb`。或者，你可以查看 `notebooks/Bidir-Char-Seq2seq-Complete.ipynb` 的内容，它显示了用于构建包含 `notebooks/pre-trained/Bidir-CharModel/` 文件夹中的预训练双向模型的运行输出。

本节的其余部分将介绍重要的区别。

该模型与之前的模型之间的主要区别并非出于必要，但此模型使用了更大的 `latent_dim` 值：

```python
latent_dims = 512
```

之前的模型使用 256 维，这意味着编码器为解码器产生 256 维的特征——一个用于隐藏状态，一个用于单元状态。GRU 层没有单元状态，因此它们只返回一个长度为 `latent_dim` 的单个向量。为了不向解码器发送一半的信息，作者选择了增加 GRU 的大小。

该模型最大的区别在于编码器，让我们看看它的定义：

```python
# 1
encoder_in = Input(
shape=(None
```

![](img/5720be5c3cca252e12448e68d25607b5528_0.png)

## 机器学习
第 16 章：自然语言转换，第 2 部分

此编码器使用了带有 GRU 层的双向 RNN。以下是设置方法：

- 1. Input 和 Masking 层与上一章相同。
- 2. 你不是创建一个循环层，而是创建两个层——一个正常处理序列，另一个反向处理，你设置 `go_backwards=True`。
- 3. 最后，将两个 GRU 层的输出拼接在一起，以便编码器将它们输出。

至于解码器，一个重要的区别在于它接受的输入的大小。我们像这样定义了一个名为 `decoder_latent_dim` 的新变量：

```python
decoder_latent_dim = latent_dim * 2
```

解码层需要的单元与编码器一样，因为它接受一个包含正向和反向状态的向量。再次，你使用 GRU 层代替 LSTM，但使用 `decoder_latent_dim` 代替 `latent_dim` 以涵盖来自编码器的正向和反向状态。解码器的其他区别在以下几行：

```python
decoder_gru = GRU(decoder_latent_dim, return_sequences=True, return_state=True, dropout=0.2, recurrent_dropout=0.3, name="decoder_gru")
decoder_gru_out, _ = decoder_gru(decoder_mask, initial_state=decoder_out)
```

注意：一个重要的细节是解码器并没有像编码器那样实现双向网络。这是因为解码器实际上并没有处理整个序列——它只接收单个字符以及状态信息。

