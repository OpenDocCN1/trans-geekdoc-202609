

## 反向传播过程

*   **前向传播**：在前向传播期间，输入数据逐层通过网络，并为每个神经元计算激活值。这些激活值基于输入的加权和，并通过激活函数进行处理。
*   **损失函数**：损失函数（也称为代价函数）度量预测输出与实际目标值之间的误差。常见的损失函数包括用于回归的均方误差和用于分类的交叉熵。
*   **反向传播**：在反向传播阶段，算法计算损失关于每层权重和偏置的梯度。这是通过应用微积分的链式法则来完成的。
*   **梯度下降**：计算出的梯度用于调整权重和偏置，使其朝着减小损失的方向移动。此过程称为梯度下降。
*   **迭代**：前向传播、损失计算、反向传播和权重更新会针对指定数量的轮次（epoch）重复执行，或直到收敛。

让我们逐步分解反向传播过程：

1.  **前向传播**：输入数据被送入输入层，并通过加权和与激活函数，在包括隐藏层在内的每一层中计算激活值。
2.  **计算损失**：将网络的输出与实际目标值进行比较以计算损失。
3.  **反向传播**：从输出层开始，向后通过网络计算损失关于权重和偏置的梯度。应用链式法则来计算这些梯度。
4.  **梯度下降**：梯度被用于更新每层的权重和偏置。更新的幅度由 `learning rate`（学习率）超参数控制。
5.  **重复**：步骤 1 到 4 会针对指定数量的轮次重复执行，或直到收敛，通过不断调整权重和偏置来最小化损失。

反向传播网络的示意图如 [图 8.11](#ch08.xhtml#fig8-11) 所示：

![](images/8.11.png)

**图 8.11：反向传播网络**

从头实现反向传播神经网络是一项复杂的任务。不过，我们可以通过使用 Python 和 `NumPy` 库提供一个简单的示例，帮助你理解反向传播的原理。该示例将演示针对简单二分类问题的前馈神经网络训练。

> **注意**：对于更复杂的任务和实际应用，建议使用 `TensorFlow` 或 `Keras` 等深度学习库，它们提供了构建和训练神经网络的高效工具。

使用 Python 和 `NumPy` 实现反向传播神经网络的基本示例见 [代码 8.3](#ch08.xhtml#cd8-3)。在该代码中，我们定义了 `sigmoid` 激活函数及其导数。我们创建了一个用于二分类的简单数据集（`X` 和 `y`）。我们初始化了神经网络的架构权重和偏置。我们设置了用于训练的 `learning_rate`（学习率）和 `epochs`（轮数）。

我们执行前向传播，计算损失，然后进行反向传播以更新权重和偏置。训练完成后，我们通过进行预测来测试网络。请参考以下代码以便更好地理解：

**代码 8.3：反向传播网络的实现**

```python
import numpy as np

# Define the sigmoid activation function and its derivative
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def sigmoid_derivative(x):
    return x * (1 - x)

# Define the dataset
X = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])
y = np.array([[0], [1], [1], [0]])

# Initialize the neural network architecture
input_size = 2
hidden_size = 4
output_size = 1

# Initialize weights and biases
input_layer = np.random.rand(input_size, hidden_size)
output_layer = np.random.rand(hidden_size, output_size)
hidden_layer_bias = np.zeros((1, hidden_size))
output_layer_bias = np.zeros((1, output_size))

# Set learning rate and number of epochs
learning_rate = 0.1
epochs = 10000

# Training the neural network
for epoch in range(epochs):
    # Forward pass
    hidden_layer_input = np.dot(X, input_layer) + hidden_layer_bias
    hidden_layer_output = sigmoid(hidden_layer_input)
    output_layer_input = np.dot(hidden_layer_output, output_layer) + output_layer_bias
    output_layer_output = sigmoid(output_layer_input)

    # Calculate the loss
    error = y - output_layer_output

    # Backpropagation
    d_output = error * sigmoid_derivative(output_layer_output)
    error_hidden_layer = d_output.dot(output_layer.T)
    d_hidden_layer = error_hidden_layer * sigmoid_derivative(hidden_layer_output)

    # Update weights and biases
    output_layer += hidden_layer_output.T.dot(d_output) * learning_rate
    output_layer_bias += np.sum(d_output, axis=0, keepdims=True) * learning_rate
    input_layer += X.T.dot(d_hidden_layer) * learning_rate
    hidden_layer_bias += np.sum(d_hidden_layer, axis=0, keepdims=True) * learning_rate

    if epoch % 1000 == 0:
        loss = np.mean(np.abs(error))
        print(f"Epoch {epoch}: Loss {loss}")

# Testing the trained network
hidden_layer_input = np.dot(X, input_layer) + hidden_layer_bias
hidden_layer_output = sigmoid(hidden_layer_input)
output_layer_input = np.dot(hidden_layer_output, output_layer) + output_layer_bias
predicted_output = sigmoid(output_layer_input)

print("Predicted Output:")
print(predicted_output)
```

代码输出请参考 [图 8.12](#ch08.xhtml#fig8-12)：

![](images/8.12.png)

**图 8.12：代码 8.3 的输出**

## 卷积神经网络

**卷积神经网络（CNN）** 是一种专门的深度神经网络类型，旨在处理涉及视觉数据的任务，例如图像识别和分类。CNN 之所以非常有效，是因为它们采用了一种独特的架构，利用卷积层以适合图像的方式处理数据。我们将解释 CNN 的关键组件，随后提供一个使用 `TensorFlow`/`Keras` 进行图像分类的简单 Python 代码示例。

### 卷积神经网络的关键组件

CNN 的关键组件描述如下：

*   **卷积层**：这些层使用可学习的滤波器（核）对输入数据应用卷积操作。这些滤波器在输入上滑动，提取特征和模式。
*   **激活函数**：类似于 `ReLU`，它们向网络引入非线性，并有助于捕捉复杂模式。
*   **池化层**：它们在保留重要信息的同时减小特征图的空间维度。常见的池化方法包括最大池化和平均池化。
*   **全连接层（密集层）**：这些层执行高级推理和分类。它们接收展平的特征图并将其连接到输出层。
*   **输出层**：它为分类任务生成类别概率。

[图 8.13](#ch08.xhtml#fig8-13) 展示了 CNN 的示意图：

![](images/8.13.png)

**图 8.13：卷积神经网络**

创建 CNN 涉及使用 `TensorFlow` 或 `PyTorch` 等深度学习框架。以下 [代码 8.4](#ch08.xhtml#cd8-4) 是一个使用 `TensorFlow` 和 `Keras` 在 `MNIST` 数据集上构建基本 CNN 的示例：

**代码 8.4：卷积神经网络的实现**

```python
import tensorflow as tf
from tensorflow.keras import layers, models
from tensorflow.keras.datasets import mnist
from tensorflow.keras.utils import to_categorical

# Load and preprocess the MNIST dataset
(train_images, train_labels), (test_images, test_labels) = mnist.load_data()
train_images = train_images.reshape((60000, 28, 28, 1)).astype('float32') / 255
test_images = test_images.reshape((10000, 28, 28, 1)).astype('float32') / 255
train_labels = to_categorical(train_labels)
```

