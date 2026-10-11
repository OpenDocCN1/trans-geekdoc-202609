

## 输入层
输入层接收序列输入数据，这与其他神经网络类似。

## 隐藏状态（输出）
与 LSTM 类似，GRU 维护一个隐藏状态，它捕获序列中前几个时间步的信息。

## 重置门
GRU 中的重置门有助于控制来自过去的哪些信息应该在当前状态中被遗忘或重置。它决定遗忘什么。

## 更新门
GRU 中的更新门控制从前一个隐藏状态到当前隐藏状态的信息流。它决定应保留多少前一个状态以及更新多少。

## 候选隐藏状态
它表示可能添加到隐藏状态的新信息。GRU 的图示表示见 [图 8.19](#ch08.xhtml#fig8-19)：

![](images/8.19.png)

**图 8.19：门控循环单元网络**

## 门控循环单元网络中的学习
训练涉及使用 `BPTT` 调整权重和偏置。GRU 在捕获长期依赖关系和计算效率之间取得了平衡，使其适用于各种序列任务。

GRU 网络在需要跨序列建模依赖关系的任务中已被证明是有效的，例如自然语言处理、语音识别和时间序列分析。其简化的架构使其在保持强大性能的同时具有计算效率。

创建 GRU 网络涉及使用像 `TensorFlow` 或 `PyTorch` 这样的深度学习框架。[代码 8.7](#ch08.xhtml#cd8-7) 是一个使用 `TensorFlow` 和 `Keras` 在合成数据集上实现基本 GRU 的示例：

**代码 8.7：门控循环单元网络的实现**

```python
import numpy as np

import tensorflow as tf

from tensorflow.keras.models import Sequential

from tensorflow.keras.layers import GRU, Dense

# Generate synthetic data
np.random.seed(42)

timesteps = 10
input_features = 1
X_train = np.random.random((1000, timesteps, input_features))
y_train = np.sin(np.arange(1000) / 10).reshape(-1, 1)

# Build the GRU model
model = Sequential()
model.add(GRU(32, activation='relu', input_shape=(timesteps, input_features)))
model.add(Dense(1))

# Compile the model
model.compile(optimizer='adam', loss='mse', metrics=['mae'])

# Train the model
model.fit(X_train, y_train, epochs=10, batch_size=32, validation_split=0.2)

# Generate test data
X_test = np.random.random((100, timesteps, input_features))
y_test = np.sin(np.arange(1000, 1100) / 10).reshape(-1, 1)

# Evaluate the model on the test set
test_loss, test_mae = model.evaluate(X_test, y_test)
print(f"Test Mean Absolute Error: {test_mae}")
```

请参考 [图 8.20](#ch08.xhtml#fig8-20) 查看代码输出：

![](images/8.20.png)

**图 8.20：代码 8.7 的输出**

此代码创建一个包含一个 GRU 层和一个密集输出层的 GRU 网络。它在代表正弦波的合成数据上进行训练。

## 自编码器
自编码器是一种神经网络架构，旨在用于无监督学习和降维。自编码器的主要目标是将输入数据编码为压缩表示，然后将其解码回原始数据，并尽可能准确。这一过程迫使网络学习输入数据的有意义且高效的表示。自编码器由编码器和解码器组成，网络经过训练以最小化输入与解码输出之间的重构误差。自编码器的图示表示见 [图 8.21](#ch08.xhtml#fig8-21)，其工作原理如下：

### 编码器
它接收输入数据并将其映射到低维表示。它将输入压缩到一个降维的特征空间中，捕获基本特征。

### 编码表示
这是输入数据的压缩表示。它是一个瓶颈层，保存着来自输入的信息的浓缩形式。

### 解码器
它接收编码表示并尝试重构原始输入数据。它将压缩表示映射回原始特征空间。

## 自编码器架构
自编码器的层如下：

### 输入层
自编码器的初始层接收输入数据。

### 编码器层
多个层降低输入数据的维度，提取重要特征并创建编码表示。

### 编码层（瓶颈）
该层代表输入数据的压缩版本。

### 解码器层
对称结构的层，从编码表示重构原始数据。

### 输出层
最终层生成重构输出。

自编码器的图示表示如下所示：

![](images/8.21.png)

**图 8.21：自编码器**

## 自编码器中的学习
训练自编码器涉及最小化重构误差，通常通过使用均方误差 (`MSE`) 等损失函数来衡量。反向传播用于调整权重和偏置，以最小化输入与重构输出之间的差异。自编码器的主要应用包括以下内容：

*   **降维**：自编码器能有效地在低维空间中捕获高维数据的基本特征。
*   **数据去噪**：通过在带噪输入和干净目标对上训练，可用于去除数据中的噪声。
*   **异常检测**：自编码器可以学会重构正常模式，从而有效识别数据中的异常。
*   **特征学习**：自编码器可以在无需人工特征工程的情况下，自动从原始数据中学习相关特征。
*   **生成建模**：变分自编码器 (`VAEs`) 是自编码器的一种变体，可以生成与训练集相似的新数据样本。

自编码器在图像处理、信号处理和自然语言处理等各个领域都有应用，在这些领域中捕获数据的有意义表示至关重要。

创建自编码器涉及使用像 `TensorFlow` 或 `PyTorch` 这样的深度学习框架。下面给出了一个使用 `TensorFlow` 和 `Keras` 实现基本自编码器的示例：

**代码 8.8：自编码器的实现**

```python
import numpy as np

import tensorflow as tf

from tensorflow.keras.layers import Input, Dense
from tensorflow.keras.models import Model

# Generate synthetic data
np.random.seed(42)
data = np.random.random((1000, 100))

# Build the autoencoder model
input_layer = Input(shape=(100,))
encoded = Dense(50, activation='relu')(input_layer)
decoded = Dense(100, activation='sigmoid')(encoded)
autoencoder = Model(input_layer, decoded)

# Compile the autoencoder
autoencoder.compile(optimizer='adam', loss='binary_crossentropy')

# Train the autoencoder
autoencoder.fit(data, data, epochs=10, batch_size=32, validation_split=0.2)

# Encode and decode the data
encoded_data = autoencoder.predict(data)

# Display original and reconstructed data
print("Original Data:")
print(data[0])
print("Reconstructed Data:")
print(encoded_data[0])
```

请参考 [图 8.22](#ch08.xhtml#fig8-22) 查看代码输出：

![](images/8.22.png)

**图 8.22：代码 8.8 的输出**

此代码创建一个包含一个编码层和一个解码层的简单自编码器。它在合成数据上进行训练，并打印原始数据和重构数据以展示自编码器的性能。

## 结论

