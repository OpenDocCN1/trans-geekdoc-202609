

```
model.compile(optimizer='rmsprop', loss='categorical_crossentropy', metrics=['accuracy'])
model.fit([input_data_1, input_data_2], targets)  # we pass one data array per model input
```

## 自己动手

### 步骤 1：获取数据 - MNIST

```
# let's load MNIST data as we did in the exercise on MNIST with FC Nets
```

```
# %load ../solutions/sol_821.py
```

### 步骤 2：创建多输入网络

```
## try yourself
```

```
## `evaluate` the model on test data
```

Keras 支持不同的合并策略：

*   `add`: 按元素求和

*   `concatenate`: 张量拼接。你可以通过参数 `concat_axis` 指定拼接轴。

*   `multiply`: 按元素相乘

*   `average`: 张量平均值

*   `maximum`: 输入的按元素最大值。

*   `dot`: 点积。你可以通过参数 `dot_axes` 指定沿哪些轴进行归约。你也可以指定应用任何归一化。在这种情况下，点积的输出是两个样本之间的余弦相似度。

你也可以将函数作为 `mode` 参数传递，允许任意转换：

```
merged = Merge([left_branch, right_branch], mode=lambda x: x[0] - x[1])
```

* * *

# 更有趣的用例

这里有一个使用函数式 API 的好例子：具有多个输入和输出的模型。

函数式 API 使操作大量交织的数据流变得容易。

让我们考虑以下模型（来自：[https://keras.io/getting-started/functional-api-guide/](https://keras.io/getting-started/functional-api-guide/)）

## 问题与数据

我们希望预测新闻标题在 Twitter 上会收到多少条转发和点赞。

模型的主要输入将是标题本身，作为一系列单词，但为了增加趣味性，我们的模型还将有一个辅助输入，接收额外数据，例如发布标题的时间等。

该模型还将通过两个损失函数进行监督。

在模型中较早使用主损失函数是深度模型的一个良好正则化机制。

![](c260610f.png)

```
from keras.layers import Input, Embedding, LSTM, Dense
from keras.models import Model

# Headline input: meant to receive sequences of 100 integers, between 1 and 10000.
# Note that we can name any layer by passing it a "name" argument.
main_input = Input(shape=(100,), dtype='int32', name='main_input')

# This embedding layer will encode the input sequence
# into a sequence of dense 512-dimensional vectors.
x = Embedding(output_dim=512, input_dim=10000, input_length=100)(main_input)

# A LSTM will transform the vector sequence into a single vector,
# containing information about the entire sequence
lstm_out = LSTM(32)(x)
```

```
Using TensorFlow backend.
```

在这里我们插入辅助损失，允许 LSTM 和 Embedding 层被平滑地训练，尽管模型中的主损失会高得多。

```
auxiliary_output = Dense(1, activation='sigmoid', name='aux_output')(lstm_out)
```

此时，我们将辅助输入数据馈入模型，通过将其与 LSTM 输出拼接：

```
from keras.layers import concatenate

auxiliary_input = Input(shape=(5,), name='aux_input')
x = concatenate([lstm_out, auxiliary_input])

# We stack a deep densely-connected network on top
x = Dense(64, activation='relu')(x)
x = Dense(64, activation='relu')(x)
x = Dense(64, activation='relu')(x)

# And finally we add the main logistic regression layer
main_output = Dense(1, activation='sigmoid', name='main_output')(x)
```

### 模型定义

```
model = Model(inputs=[main_input, auxiliary_input], outputs=[main_output, auxiliary_output])
```

我们编译模型并为辅助损失分配 0.2 的权重。

要为每个不同的输出指定不同的 `loss_weights` 或 `loss`，你可以使用列表或字典。这里我们将单个损失作为 `loss` 参数传递，因此相同的损失将用于所有输出。

#### 注意：

由于我们的输入和输出是命名的（我们传递了 "name" 参数），我们可以通过以下方式编译和拟合模型：

```
model.compile(optimizer='rmsprop',
              loss={'main_output': 'binary_crossentropy', 'aux_output': 'binary_crossentropy'},
              loss_weights={'main_output': 1., 'aux_output': 0.2})
```

```
# And trained it via:
model.fit({'main_input': headline_data, 'aux_input': additional_data},
          {'main_output': labels, 'aux_output': labels},
          epochs=50, batch_size=32)
```

# 结论

*   Keras 是一个功能强大且包含电池的 Python 深度学习框架

*   Keras 使用 `simple` 简单。

*   ...但它 `not` 不适合简单的事情！

![](keras_rank.jpg)

![](keras_rank_details.jpg)

## 一些参考资料

### 前沿技术

*   Fractal Net Implementation with Keras: [https://github.com/snf/keras-fractalnet](https://github.com/snf/keras-fractalnet) -

*   请查看：[https://github.com/fchollet/keras-resources](https://github.com/fchollet/keras-resources)

### Hyper-Cool

*   Hyperas: [https://github.com/maxpumperla/hyperas](https://github.com/maxpumperla/hyperas) 

    *   Keras 模型的 Web 仪表板

### Super-Cool

*   Keras.js: [https://github.com/transcranial/keras-js](https://github.com/transcranial/keras-js) 

    *   你的 Keras 模型 `inside your Browser`

    *   展示：[https://transcranial.github.io/keras-js/](https://transcranial.github.io/keras-js/)

