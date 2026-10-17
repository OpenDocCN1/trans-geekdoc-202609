
# 机器学习

## 第 15 章：自然语言转换，第一部分

```
['\é', '\'1', '\'2', '\'3', '\'4', '\'5', '\'6', '\'7', '\'8', '\'9', \
  '\\'', '\'0', '\'A', '\'B', '\'C', '\'D', '\'E', '\'F', '\'G', '\'H', '\'I', '\'J', '\'K', \
  '\'M', '\'N', '\'O', '\'P', '\'Q', '\'R', '\'S', '\'T', '\'U', '\'V', '\'W', '\'X', '\'Y', \
  \''Z', '\'z', '\'a', '\'b', '\'c', '\'d', '\'e', '\'f', '\'g', '\'h', '\'i', '\'j', '\'k', \
  \''l', '\'m', '\'n', '\'o', '\'p', '\'q', '\'r', '\'s', '\'t', '\'u', '\'v', '\'w', '\'x', \
  \''y', '\'z', '\'é', '\'í', '\'ñ', '\'ö', '\'ü', '\'ù', '\'ý', '\'ç', '\'€']
```

对 `out_vocab` 运行类似的代码行会显示这些字符：

```
['\t', '\n', '\'', \
  \''0', '\'1', '\'2', '\'3', '\'4', '\'5', '\'6', '\'7', '\'8', '\'9', '\'/', \
  \''A', '\'B', '\'C', '\'D', '\'E', '\'F', '\'G', '\'H', '\'I', '\'J', '\'K', '\'M', \
  \''N', '\'O', '\'P', '\'Q', '\'R', '\'S', '\'T', '\'U', '\'V', '\'W', '\'X', '\'Y', '\'Z', \
  \''a', '\'b', '\'c', '\'d', '\'e', '\'f', '\'g', '\'h', '\'i', '\'j', '\'k', '\'l', '\'m', \
  \''n', '\'o', '\'p', '\'q', '\'r', '\'s', '\'t', '\'u', '\'v', '\'w', '\'x', '\'y', '\'z', \
  \''à', '\'á', '\'â', '\'é', '\'í', '\'ó', '\'ù', '\'ý']
```

它喜欢数据中包含了良好的字符选择，但并不在意输入和输出词表之间存在差异。这并不意外；毕竟，这些是两种不同语言的词表。

然而，理解这一点非常重要：这个词表定义了模型将处理的每一个字符。这意味着它永远不知道如何处理不在 `in_vocab` 中的输入字符，并且永远不会产生不在 `out_vocab` 中的字符的句子。

例如，西班牙语集包含括号，但英语集不包含。你知道括号在英语中应该是有效的字符，但无论在给定序列中出现多少个，你的模型永远不会产生包含它们的输出。

现在你已经知道了你的模型可以处理的标记（tokens），任何其他标记都被视为 OOV（表外词）。处理 OOV 标记有多种方法，但没有一种方法是完美的。对于你的模型，你将采取最基础的方法：在处理任何输入之前，从输入中移除 OOV 标记。对于验证集——如果你有的话，还有测试集——你将从输入和目标输出中移除它们。

> 注意：本章的模型在字符级别处理序列，移除 OOV 标记不应从序列中移除太多信息。在下一章中，你将学习如何处理全单词标记，那时处理 OOV 标记将变得困难得多。

当你在 iOS 中使用模型时，你会在将每个序列传递给模型之前对其进行预处理。在训练期间，你每个 epoch 都会对验证集进行测试，预先处理所有数据会更高效。运行以下单元格从验证集中移除 OOV 标记：

```python
tmp_samples = []
for in_seq, out_seq in valid_samples:
    tmp_in_seq = [c for c in in_seq if c in in_vocab]
    tmp_out_seq = [c for c in out_seq if c in out_vocab]
    tmp_samples.append(("".join(tmp_in_seq), "".join(tmp_out_seq)))
valid_samples = tmp_samples
```

在这里，你遍历了验证样本并创建了只包含对应词表中字符的新序列——西班牙语输入对应 `in_vocab`，英语输出对应 `out_vocab`。

> 注意：如果你比较移除 OOV 标记前后的验证样本，你可能会发现差异很小或没有差异。这发生在你之前通过 `train_test_split` 划分的随机划分上，但这里的前提是成立的；你的模型在训练期间不处理标记，因此在处理包含 OOV 标记的序列时，你需要进行一些预处理。这在测试以及你的 iOS 运行时都是如此。

### 构建你的模型

在本节中，你将使用 Keras 定义一个将西班牙语翻译成英语的 seq2seq 模型。首先，你需要以下代码：

```python
import keras
from keras.layers import Dense, Input, LSTM, Masking
from keras.models import Model

### 1
latent_dim = 256
# 2
encoder_in = Input(shape=(None, vocab_size), name="encoder_in")
# 3
encoder_mask = Masking(name="encoder_mask")(encoder_in)
# 4
encoder_lstm = LSTM(latent_dim, return_state=True, recurrent_dropout=0.3, name="encoder_lstm")
# 5
encoder_h, encoder_c = encoder_lstm(encoder_mask)
```

张量具有特定的维度。但你的模型可以处理变长序列，对吧？那么是将变长序列存储在固定维度中吗？你稍后会看到细节，你会用零填充短序列——这本质上是为了使所有序列长度相同的无意义时间步。`Masking` 告诉 Keras 不要这些时间步上进行训练。这个层并不是绝对必要的，但通过注释可以进一步解释选择使用 `Masking` 层的原因。

- 4. 你创建了一个 `LSTM` 层来处理输入序列，将 `latent_dim` 传递给其输出大小。设置 `return_state=True` 使 LSTM 输出其隐藏状态和单元状态以及其常规输出；你将这些作为解码器的初始值。如果你忘记了编码器输出的作用，可以回过头来看 seq2seq 模型的内置讨论。你还使用了 `recurrent_dropout` 参数在 LSTM 的时间步之间添加 dropout。这可以帮助你的模型更好地泛化到未见数据。`LSTM` 初始化器有许多可用参数，因此当你深入研究时，应该探索 Keras 文档。

> 注意：你可能会遇到不使用 `Masking` 层但仍通过填充序列来存储批处理数据的网络示例。这些仍然有效，但它们存在一个微妙的问题：这些网络认为填充标记与真实标记一样重要。这导致了三个问题。

首先，它们在训练时看起来值较低，但这仅仅是因为它们测试的标记中很大比例是相同的填充标记，并且它们学会了输出大量的它们。

第二个更重要的问题是，它稀释了编码器存储的信息，因为权重被本质上无意义的内容修改了

tokens。这降低了你的编码器的能力。如果这还不清楚，别担心，在本章节结束时你会明白。

最后，为了让这些网络产生预期的结果，它们在推理时需要相同的填充（padding）。例如，如果你训练了一个模型使用一组长度为 10 个字符的序列来翻译“Hola”，那么你会有五个填充 token。

如果你尝试使用这些相同的填充 token 进行翻译，你的模型可能只有在推理期间才会产生正确的结果，因为如果没有这些填充 token，相同的字母的编码方式会不同，并且可能翻译出错误的内容。

使用 `Masking` 层的一个缺点是 Core ML 实际上并不支持它。这对这个项目来说不是问题——你稍后会看到——这意味着你将无法在 iOS 中进行批量翻译，因为你不太可能在没有填充的情况下创建一个等长度的序列批。

你的解码器定义看起来与编码器非常相似，只有几处细微的区别。运行带有以下代码的单元格：

```python
### 1
decoder_in = Input(
shape=(None, out_vocab_size), name="decoder_in")
decoder_mask = Masking(name="decoder_mask")(decoder_in)
# 2
decoder_lstm = LSTM(
latent_dim, return_sequences=True, return_state=True,
dropout=0.2, recurrent_dropout=0.3, name="decoder_lstm")
# 3
decoder_out, _ = decoder_lstm(
decoder_mask, initial_state=[encoder_h, encoder_c])
# 4
decoder_dense = Dense(
out_vocab_size, activation="softmax", name="decoder_out")
decoder_out = decoder_dense(decoder_lstm_out)
```

以下是和你为编码器编写的代码的区别：

- 1. 解码器从一个通过 `Masking` 层的输入层开始，就像编码器一样。区别是它的尺寸是为输出词表设计的。

- 2. 它使用了与编码器类似的 `LSTM` 层，但增加了一个额外的 dropout 参数。与只作用于在时间步之间传递的值的 recurrent dropout 不同，这个 dropout 值会影响从编码器传入的原始输入。这只是额外的正则化，可能会提高你的模型对未见数据的泛化能力。

- 3. 你将掩码层作为输入连接到 `LSTM`，并设置 `LSTM` 的初始状态为编码器 `LSTM` 的输出状态。解码器在训练期间不需要访问其隐藏状态或单元状态——它内部已经可以访问这些状态——所以通过将它们赋值给下划线变量来忽略它们。你在 `decoder_lstm_out` 中获取其余输出。

- 4. 你将 `LSTM` 的输出传递到解码器的最后一个全连接层。它为输出词表中的每个 token 都配有一个节点，并使用 softmax 激活函数产生它们之间的概率分布。你将用它来预测输出序列中的下一个字符。

定义好编码器和解码器后，按照代码将它们组合成 seq2seq 模型：

```python
### 1
seq2seq_model = Model([encoder_in, decoder_in], decoder_out)
# 2
seq2seq_model.compile(
optimizer="rmprop", loss="categorical_crossentropy")
```

以下是如何组合编码器和解码器以准备训练的：

- 1. 你构建了一个包含编码器和解码器输入层以及解码器输出层的 Keras 模型。由于你有多个输入层，因此你以列表的形式将它们组合。

- 2. RMSprop 优化器使用自适应的逐参数学习率。我们不会详细介绍它；只需知道它是训练循环神经网络的良好选择就足够了。正如你在书中创建的其他分类模型中所看到的，当你的输出代表跨类别的概率分布时，分类交叉熵是一个很好的损失函数；在这种情况下，类别就是输出词表中的 token。

运行以下行来显示模型中层连接连接的摘要：

```python
seq2seq_model.summary()
```

你将看到：

| Layer (type) | Output Shape | Param # | Connected to |
|---|---|---|---|
| encoder_in (InputLayer) | (None, None, 101) | 0 |  |
| decoder_in (InputLayer) | (None, None, 87) | 0 |  |
| encoder_mask (Masking) | (None, None, 101) | 0 | encoder_in[0][0] |
| decoder_mask (Masking) | (None, None, 87) | 0 | decoder_in[0][0] |
| encoder_lstm (LSTM) | (None, None, 256) | 366592 | encoder_mask[0][0] |
| decoder_lstm (LSTM) | (None, None, 256) | 352256 | decoder_mask[0][0], encoder_lstm[0][1], encoder_lstm[0][2] |
| decoder_out (Dense) | (None, None, 87) | 22359 | decoder_lstm[0][0] |

**Total params:** 741207

**Trainable params:** 741207

**Non-trainable params:** 0

## 第 15 章：自然语言转换，部分 1

编码为 5 吗？

不，你没有这样做，但机器学习算法无法得知这一点。对于给定的特征，较大的值对模型计算的影响比较小的值大。最坏的情况下，这会破坏你的模型；但最好的情况下，它会减慢训练过程，因为模型会尝试消除这些隐含的联系。

解决这个编码问题有几种方法。在下一章中，你将看到另一种选择，在那里你会将标记的整数值转换为所谓的“独热编码”（one-hot encoding）。

对特征进行独热编码涉及将每个值替换为长度与所有可能值数量相同的向量。这些向量在除一个位置外的所有位置都填充为 0，该位置填充为 1。假设你想将周一到周五作为模型的可能输入。

下面的图片显示了独热编码值后的形式：

| 周一 | 1 | 0 | 0 | 0 | 0 |
| 周二 | 0 | 1 | 0 | 0 | 0 |
| 周三 | 0 | 0 | 1 | 0 | 0 |
| 周四 | 0 | 0 | 0 | 1 | 0 |
| 周五 | 0 | 0 | 0 | 0 | 1 |

> 独热编码值
