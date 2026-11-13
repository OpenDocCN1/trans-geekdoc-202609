

要对一组连续值向量进行回归，请在层堆栈的末尾添加一个 Dense 层，其单元数等于您要预测的值的数量（通常只有一个，例如房屋价格），且不使用激活函数。回归可以使用多种损失函数——最常用的是 mean_squared_error (MSE)：

```python
inputs = keras.Input(shape=(num_input_features,))
x = layers.Dense(32, activation="relu")(inputs)
x = layers.Dense(32, activation="relu")(x)
outputs = layers.Dense(num_values)(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="mse")
```

## 卷积网络

卷积层通过对输入张量中不同的空间位置（补丁）应用相同的几何变换，来观察空间局部模式。这会产生具有平移不变性的表示，使卷积层具有高度的数据效率和模块化。这一思想适用于任意维度的空间：1D（连续序列）、2D（图像）、3D（体数据）等等。你可以使用 Conv1D 层处理序列，使用 Conv2D 层处理图像，使用 Conv3D 层处理体数据。作为卷积层更精简、更高效的替代方案，你还可以使用深度可分离卷积层，例如 SeparableConv2D。

卷积网络（或称卷积神经网络）由卷积层和最大池化层的堆栈组成。池化层允许你对数据进行空间下采样，这对于在特征数量增加时保持特征图的合理大小是必需的，同时也能让后续的卷积层“看到”更大范围的输入空间。卷积网络通常以 Flatten 操作或全局池化层结束，将空间特征图转换为向量，随后接上 Dense 层以实现分类或回归。

这里是一个典型的图像分类网络（在此例中为分类分类），使用了 SeparableConv2D 层：

```python
inputs = keras.Input(shape=(height, width, channels))
x = layers.SeparableConv2D(32, 3, activation="relu")(inputs)
x = layers.SeparableConv2D(64, 3, activation="relu")(x)
x = layers.MaxPooling2D(2)(x)
x = layers.SeparableConv2D(64, 3, activation="relu")(x)
x = layers.SeparableConv2D(128, 3, activation="relu")(x)
x = layers.MaxPooling2D(2)(x)
x = layers.SeparableConv2D(64, 3, activation="relu")(x)
x = layers.SeparableConv2D(128, 3, activation="relu")(x)
x = layers.GlobalAveragePooling2D()(x)
x = layers.Dense(32, activation="relu")(x)
outputs = layers.Dense(num_classes, activation="softmax")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="categorical_crossentropy")
```

构建非常深的卷积网络时，通常会添加批量归一化层以及残差连接——这两种架构模式有助于梯度信息在网络中平稳流动。

## 循环神经网络

循环神经网络（RNN）通过一次处理一个时间步的输入序列，并在整个过程中维护一个状态（状态通常是一个向量或一组向量）来工作。在感兴趣的模式不随时间平移而不变的序列情况下，应优先使用 RNN 而非 1D 卷积网络（例如，近期过去比遥远过去更重要的时间序列数据）。

Keras 中提供了三种 RNN 层：`SimpleRNN`、`GRU` 和 `LSTM`。对于大多数实际用途，你应该使用 GRU 或 LSTM 之一。LSTM 在两者中更强大，但代价也更高；你可以将 GRU 视为它的一种更简单、更便宜的替代方案。

为了将多个 RNN 层相互堆叠，堆栈中除最后一层外的每一层都应返回其完整的输出序列（每个输入时间步都对应一个输出时间步）。如果你不再堆叠其他 RNN 层，则通常只返回最后一个输出，它包含了关于整个序列的信息。

以下是用于向量序列二分类的单层 RNN：

```python
inputs = keras.Input(shape=(num_timesteps, num_features))
x = layers.LSTM(32)(inputs)
outputs = layers.Dense(num_classes, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="binary_crossentropy")
```

这是用于向量序列二分类的堆叠 RNN：

```python
inputs = keras.Input(shape=(num_timesteps, num_features))
x = layers.LSTM(32, return_sequences=True)(inputs)
x = layers.LSTM(32, return_sequences=True)(x)
x = layers.LSTM(32)(x)
outputs = layers.Dense(num_classes, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="binary_crossentropy")
```

## 变换器

变换器（Transformer）会观察一组向量（例如词向量），并利用 _神经注意力_ 将每个向量转换为能够感知集合中其他向量所提供的 _上下文_ 的表示。当所涉及的集合是有序序列时，你还可以利用 _位置编码_ 来创建能够同时考虑全局上下文和词序的变换器，其处理长文本段落的效果远优于 RNN 或 1D 卷积网络。

变换器可用于任何集合处理或序列处理任务，包括文本分类，但它们尤其擅长 _序列到序列学习_，例如将源语言中的段落翻译成目标语言。

序列到序列变换器由两部分组成：

- 一个 `TransformerEncoder`，它将输入向量序列转换为感知上下文和顺序的输出向量序列
- 一个 TransformerDecoder，它接收 TransformerEncoder 的输出以及目标序列，并预测目标序列中接下来应出现的内容

如果你只处理单个序列（或集合）的向量，那么只会使用 TransformerEncoder。

以下是用于将源序列映射到目标序列的序列到序列变换器（此设置例如可用于机器翻译或问答）：

```python
encoder_inputs = keras.Input(shape=(sequence_length,), dtype="int64")
x = PositionalEmbedding(
    sequence_length, vocab_size, embed_dim
)(encoder_inputs)
encoder_outputs = TransformerEncoder(embed_dim, dense_dim, num_heads)(x)
decoder_inputs = keras.Input(shape=(None,), dtype="int64")
x = PositionalEmbedding(
    vocab_size, embed_dim
)(decoder_inputs)
x = TransformerDecoder(embed_dim, dense_dim, num_heads)(x, encoder_outputs)
decoder_outputs = layers.Dense(vocab_size, activation="softmax")(x)
transformer = keras.Model(
    [encoder_inputs, decoder_inputs], decoder_outputs
)
transformer.compile(optimizer="rmsprop", loss="categorical_crossentropy")
```

这是用于整数序列二分类的单个 TransformerEncoder：

```python
inputs = keras.Input(shape=(sequence_length,), dtype="int64")
x = PositionalEmbedding(sequence_length, vocab_size, embed_dim)(inputs)
x = TransformerEncoder(embed_dim, dense_dim, num_heads)(x)
x = layers.GlobalMaxPooling1D()(x)
outputs = layers.Dense(1, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="binary_crossentropy")
```

TransformerEncoder、TransformerDecoder 和 PositionalEmbedding 层的完整实现在第 11 章中提供。

### 14.1.7 可能性的空间

你将使用这些技术构建什么？请记住，构建深度学习模型就像玩乐高积木一样：只要你拥有合适的训练数据，并且该映射可以通过合理复杂度的连续几何变换来实现，层就可以相互插拔，从而将基本上任何东西映射到任何东西。可能性的空间是无限的。本节提供了一些示例，以激发你超越传统上一直是机器学习基础的分类和回归任务进行思考。

我按输入和输出模态对建议的应用进行了分类，如下列表所示。请注意，其中有不少应用突破了可能性的极限——尽管模型可以在这些所有任务上进行训练，但在某些情况下，这样的模型可能无法远远超越其训练数据进行泛化。14.2 节至 14.4 节将探讨未来如何克服这些限制：

