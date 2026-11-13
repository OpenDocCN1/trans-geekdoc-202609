

```python
model = keras.models.load_model("jena_lstm.keras")
print(f"Test MAE: {model.evaluate(test_dataset)[1]:.2f}")
```

图 10.5 显示了结果。好多了！我们的验证 MAE 低至 2.36 度，测试 MAE 为 2.55 度。基于 LSTM 的模型终于可以战胜常识基线（目前只是略胜一筹），展示了机器学习在这项任务上的价值。

![](img/ab452ecf572a1f1372915be13bd8088f_317_0.png)

图 10.5 基于 LSTM 模型的 Jena 温度预测任务上的训练和验证 MAE（请注意，我们省略了此图中的第 1 个 epoch，因为第 1 个 epoch 的高训练 MAE（7.75）会扭曲图表的坐标轴）

但为什么 LSTM 模型的表现明显优于全连接网络或卷积网络？我们又该如何进一步改进该模型？为了回答这个问题，让我们更仔细地研究一下循环神经网络。

## 10.3 理解循环神经网络

你迄今所见的所有神经网络（例如全连接网络和卷积网络）的一个主要特点是，它们没有记忆。展示给它们的每个输入都会被独立处理，输入之间不保留任何状态。对于这类网络，若要处理序列或一组时间序列数据点，必须一次性将整个序列展示给网络：将其转换为单个数据点。例如，在全连接网络示例中，我们就把五天的数据展平为一个大向量，一次性处理。此类网络称为前馈网络。

相比之下，当你阅读本句时，你是一个词一个词地处理它——或者更准确地说，是一次次眼动跳跃地处理它——同时保留着之前内容的记忆；这使你对句子所传达的意义有了流畅的表征。

生物智能在处理信息时会逐步推进，并维护一个内部模型来表示正在处理的内容，该模型由过去的信息构建而成，并在新信息到来时不断更新。

循环神经网络（RNN）采用了同样的原则，只是版本极其简化：它通过遍历序列元素并维护一个包含目前为止所见信息的状态来处理序列。实际上，RNN 是一种具有内部循环的神经网络（参见图 10.6）。

![](img/ab452ecf572a1f1372915be13bd8088f_318_0.png)

图 10.6 循环网络：一个带有循环的网络

在处理两个不同的独立序列（例如批次中的两个样本）之间，RNN 的状态会被重置，因此你仍然将一个序列视为单个数据点：网络的单个输入。变化之处在于，这个数据点不再在单个步骤中处理：相反，网络在内部遍历序列元素。

为了让循环和状态这些概念变得清晰，让我们实现一个玩具 RNN 的前向传播。该 RNN 接收一系列向量作为输入，我们将其编码为形状为 (timesteps, input_features) 的二阶张量。它遍历时间步，在每个时间步，它会考虑当前时刻 t 的状态和时刻 t 的输入（形状为 (input_features,)），并将二者结合以得到时刻 t 的输出。然后，我们将下一步的状态设置为这个前一个输出。对于第一个时间步，前一个输出未定义；因此没有当前状态。所以我们将状态初始化为一个全零向量，称为网络的初始状态。

伪代码中的 RNN 如下。

```
Listing 10.13 Pseudocode RNN

state_t = 0
for input_t in input_sequence:
    output_t = f(input_t, state_t)
    state_t = output_t
```

你甚至可以具体实现函数 f：将输入和状态转换为输出的过程将由两个矩阵 W 和 U 以及一个偏置向量参数化。这与前馈网络中全连接层所执行的变换类似。

```
Listing 10.14 More-detailed pseudocode for the RNN

state_t = 0
for input_t in input_sequence:
    output_t = activation(dot(W, input_t) + dot(U, state_t) + b)
    state_t = output_t
```

为了让这些概念绝对明确，让我们编写一个简单 RNN 前向传播的天真 NumPy 实现。

### 列表 10.15 简单 RNN 的 NumPy 实现

```
Input data: random noise for the sake of the example
import numpy as np
timesteps = 100
input_features = 32
output_features = 64
inputs = np.random.random((timesteps, input_features))
state_t = np.zeros((output_features,))
W = np.random.random((output_features, input_features))
U = np.random.random((output_features, output_features))
b = np.random.random((output_features,))
successive_outputs = []
for input_t in inputs:
    output_t = np.tanh(np.dot(W, input_t) + np.dot(U, state_t) + b)
    successive_outputs.append(output_t)
    state_t = output_t
final_output_sequence = np.stack(successive_outputs, axis=0)
```

这还算简单。总结来说，RNN 就是一个 for 循环，它重复使用上一次循环迭代中计算出的量，仅此而已。当然，你可以构建许多符合此定义的不同 RNN——这个示例是最简单的 RNN 表述之一。RNN 由其步进函数所特征，例如本例中的以下函数（参见图 10.7）。

```
output_t = np.tanh(np.dot(W, input_t) + np.dot(U, state_t) + b)
```

![](img/ab452ecf572a1f1372915be13bd8088f_319_0.png)

图 10.7 随时间展开的简单 RNN

注意 在本示例中，最终输出是一个形状为 `(time_steps, output_features)` 的二阶张量，其中每个时间步都是循环在时刻 t 的输出。输出张量中的每个时间步 t 包含关于输入序列中时间步 0 到 t 的信息——即关于整个过去的信息。出于这个原因，在许多情况下，你不需要这一完整的输出序列；你只需要最后一个输出（循环结束时的 `output_t`），因为它已经包含了关于整个序列的信息。

### 10.3.1 Keras 中的循环层

我们刚才在 NumPy 中天真实现的过程对应于一个实际的 Keras 层——`SimpleRNN` 层。

有一个细微的区别：`SimpleRNN` 处理的是一批序列，与其他所有 Keras 层一样，而不是 NumPy 示例中的单个序列。这意味着它接收形状为 `(batch_size, timesteps, input_features)` 的输入，而不是 `(timesteps, input_features)`。在指定初始 `Input()` 的 `shape` 参数时，请注意可以将 `timesteps` 条目设置为 `None`，这样你的网络就可以处理任意长度的序列。

### 列表 10.16 可处理任意长度序列的 RNN 层

```
num_features = 14
inputs = keras.Input(shape=(None, num_features))
outputs = layers.SimpleRNN(16)(inputs)
```

如果你的模型旨在处理长度不一的序列，这尤其有用。但是，如果你的所有序列长度都相同，我建议指定完整的输入形状，因为这样可以让 `model.summary()` 显示输出长度信息（这总是不错的），并且可以解锁一些性能优化（参见本章稍后的“RNN 运行时性能”侧边栏）。

Keras 中的所有循环层（`SimpleRNN`、`LSTM` 和 `GRU`）都可以以两种不同的模式运行：它们可以返回每个时间步的完整连续输出序列（形状为 `(batch_size, timesteps, output_features)` 的三阶张量），也可以只返回每个输入序列的最后一个输出（形状为 `(batch_size, output_features)` 的二阶张量）。这两种模式由 `return_sequences` 构造函数参数控制。让我们看一个使用 `SimpleRNN` 且只返回最后一个时间步输出的示例。

### 列表 10.17 仅返回其最后一个输出步骤的 RNN 层

```
>>> num_features = 14
>>> steps = 120
>>> inputs = keras.Input(shape=(steps, num_features))
>>> outputs = layers.SimpleRNN(16, return_sequences=False)(inputs)
>>> print(outputs.shape)
(None, 16)
```

> 请注意，`return_sequences=False` 是默认值。

