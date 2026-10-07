

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

对 out_vocab 运行类似的代码行会显示这些字符：

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

> 注意：如果你比较移除 OOV 标记前后的验证样本，你可能会发现差异很小或没有差异。这发生在你之前通过 `train_test_split` 划分的随机划分上，但这里的前提是成立的；你的模型在训练期间不处理标记，因此在处理包含 OOV 标记的序列时，你需要进行一些预处理。这在测试以及你的 iOS  运行时都是如此。

## 构建你的模型

在本节中，你将使用 Keras 定义一个将西班牙语翻译成英语的 seq2seq 模型。首先，你需要以下代码：

```python
import keras
from keras.layers import Dense, Input, LSTM, Masking
from keras.models import Model

# 1
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

它喜欢数据包含了良好的字符选择，但并不在意输入和输出词表之间的差异。这并不意外；毕竟，这些是两种语言的词表。

然而，理解这一点非常重要：这个词表定义了模型将处理的每一个字符。这意味着它永远不知道如何处理不在 `in_vocab` 中的输入字符，并且永远不会产生不在 `out_vocab` 中的字符的句子。

例如，西班牙语集包含括号，但英语集不包含。你知道括号在英语中应该是有效的字符，但无论在给定序列中出现多少个，你的模型永远不会产生包含它们的输出。

现在你已经知道了你的模型可以处理的标记，任何其他标记都被视为 OOV。处理 OOV 标记有多种方法，但没有一种方法是完美的。对于你的模型，你将采取最基础的方法：在处理任何输入之前，从输入中移除 OOV 标记。对于验证集——如果你有的话——你将从输入和目标输出中移除它们。

> 注意：本章的模型在字符级别处理序列，移除 OOV 标记不应从序列中移除太多信息。在下一章中，你将学习如何处理全单词标记，处理 OOV 标记将变得困难得多。

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

> 注意：如果你比较移除 OOV 标记前后的验证样本，你可能会发现差异很小或没有差异。这发生在你之前通过 `train_test_split` 划分的随机划分上，但这里的前提是成立的；你的模型在训练期间不处理标记，因此在处理包含 OOV 标记的序列时，你需要进行一些预处理。这在测试以及你的 iOS 应用运行时都是如此。

## 构建你的模型

在本节中，你将使用 Keras 定义一个将西班牙语翻译成英语的 seq2seq 模型。首先，你需要以下代码：

```python
import keras
from keras.layers import Dense, Input, LSTM, Masking
from keras.models import Model

# 1
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

张量具有特定的维度。但你的模型可以处理变长序列，对吧？那么是将变长序列存储在固定维度中吗？你稍后会看到细节，你会用零填充短序列——这本质上是为了使所有序列长度相同的无意义时间步。Masking 告诉 Keras 不要这些时间步上进行训练。这个层并不是绝对必要的，但通过注释可以进一步解释选择使用 Masking 层的原因。

- 4. 你创建了一个 LSTM 层来处理输入序列，将 `latent_dim` 传递给其输出大小。设置 `return_state=True` 使 LSTM 输出其隐藏状态和单元状态以及其常规输出；你将这些作为解码器的初始值。如果你忘记了编码器输出的作用，可以回过头来看 seq2seq 模型的内置讨论。你还使用了 `recurrent_dropout` 参数在 LSTM 的时间步之间添加 dropout。这可以帮助你的模型更好地泛化到未见数据。LSTM 初始化器有许多可用参数，因此当你深入研究时，应该探索 Keras 文档。

> 注意：你可能会遇到不使用 Masking 层但仍通过填充序列来存储批处理数据的网络示例。这些仍然有效，但它们存在一个微妙的问题：这些网络认为填充标记与真实标记一样重要。这导致了三个问题。

首先，它们在训练时看起来值较低，但这仅仅是因为它们测试的标记中很大比例是相同的填充标记，并且它们学会了输出大量的它们。

第二个更重要的问题是，它稀释了编码器存储的信息，因为权重被本质上无意义的内容修改了

