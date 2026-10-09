
Colab 的文本单元格还允许你更好地描述程序的输出。

### 1.2.3. 使用 Colab 进行可视化简介

使用 Colab 进行可视化的方法有很多种。

- 1. 使用 Matplotlib 进行可视化 [6]：Matplotlib 是 Colab 预装的 Python 数据可视化最常用库。Matplotlib 允许你绘制各种图表，例如折线图、散点图和条形图。
- 2. 使用 Seaborn 进行可视化 [7]：Seaborn 是一个基于 Matplotlib 的数据可视化库，允许你轻松绘制美观的图表。
- 3. 使用 Plotly 进行可视化 [8]：Plotly 是一个可用于创建交互式图表的 Python 库。Plotly 允许你绘制美观且交互式的图表。
- 4. 使用 Folium 进行地图可视化 [9]：Folium 是一个 Python 地图可视化库，允许你在地图上显示标记、多边形等。

例如，你可以编写以下代码来使用 Matplotlib 绘制折线图：

```
< Start >
import matplotlib.pyplot as plt
# X-axis value
x = [1, 2, 3, 4, 5]
# Y-axis value
y = [10, 20, 30, 40, 50]
# Draw a line chart
plt.plot(x, y)
# Chart title
plt.title("Line Plot")
# X-axis label
plt.xlabel("X-axis")
# Y-axis label
plt.ylabel("Y-axis")
# Display chart
plt.show()
< End >
```

![](img/fa57e7010b16a211d5cf69ebb17e416e_27_0.png)

上述代码将 X 轴和 Y 轴的值分别存储在 `x` 和 `y` 中，并使用 **plt.plot**() 函数绘制折线图。**plt.title**()、**plt.xlabel**() 和 **plt.ylabel**() 函数分别用于设置图表标题、X 轴标签和 Y 轴标签。最后，使用 **plt.show**() 函数显示图表。如上所述，Matplotlib 允许你轻松绘制折线图（图 1.15）。

### 1.2.4. 使用 Colab 进行深度学习简介

要在 Colab 上进行深度学习，你可以执行以下步骤：

- 1. 创建一个 Colab notebook。
- 2. 安装你的 notebook 所需的库，例如 TensorFlow 和 Keras。
- 3. 将学习所需的数据上传到 Colab。
- 4. 构建用于学习的 NN（神经网络）。
- 5. 使用学习数据训练 NN。
- 6. 使用训练好的模型进行预测。

Colab 预装了深度学习所需的库，例如 TensorFlow 和 Keras，因此只需导入这些库即可立即开始深度学习。Colab 还免费提供 GPU，因此可以使用大量数据进行高速训练。值得注意的是，Colab 是 Google 提供的云服务；因此，必须在连接互联网的情况下使用它，数据存储是用户的责任。

作为一个示例，我们将介绍一个 TensorFlow 程序，该程序使用修改后的美国国家标准与技术研究院（MNIST）手写数字数据集训练 NN 以识别手写数字。MNIST 是美国国家标准与技术研究院提供的原始数据集的修改版本。MNIST 手写数字数据集是一个包含手写数字 0 到 9 的图像数据集，每个都是 28 × 28 像素的灰度图像。该数据集包含 60,000 张用于训练和 10,000 张用于测试的图像。MNIST 被广泛用作开发和评估机器学习算法和模型的基准。

```
< Start >
# Importing Tensorflow and MNIST
import tensorflow as tf
from tensorflow import keras
# Reading MNIST data
(x_train, y_train), (x_test, y_test) = keras.datasets.mnist.load_data()
# Building a model
model = keras.Sequential([
      keras.layers.Flatten(input_shape=(28, 28)),
      keras.layers.Dense(128, activation='relu'),
      keras.layers.Dense(10, activation='softmax')
])
# Compiling the model
model.compile(optimizer='adam',
        loss='sparse_categorical_crossentropy',
        metrics=['accuracy'])
# Training
model.fit(x_train, y_train, epochs=5)
# Evaluation
test_loss, test_acc = model.evaluate(x_test, y_test, verbose=2)
print('\nTest accuracy:', test_acc)
< End >
```

上述代码使用 Tensorflow 的 keras API 读取 MNIST 数据并构建、训练和评估一个 NN。

MNIST 数据读取：**keras.datasets.mnist.load_data()** 是一个用于下载和读取 MNIST 数据集的 Keras 函数。MNIST 是一个手写数字图像数据集，包含 60,000 张训练图像和 10,000 张测试图像。

**(x_train, y_train)**、**(x_test, y_test)** 是接收函数返回的四个 NumPy 数组的变量类型。**x_train** 和 **y_train** 是代表训练图像及其对应标签（数字）的 NumPy 数组。同样，**x_test** 和 **y_test** 代表测试图像及其对应标签。

更具体地说，**x_train** 是一个包含 60,000 个元素的 NumPy 数组，每个元素代表一个 $28 \times 28$ 像素的灰度图像，且为 0 到 255 之间的整数值。**y_train** 是一个包含 60,000 个元素的 NumPy 数组，每个元素是 0 到 9 之间的整数，代表对应图像中写入的数字。因此，**x_test** 和 **y_test** 类似，其中每个 NumPy 数组包含 10,000 个测试数据。

这些数组用于在 Keras 中定义和训练模型。

在模型构建中，使用 Keras 定义一个 NN 模型，上述编码中的每条指令具有以下含义：

- **keras.Sequential()**：用于创建 Sequential 模型的类。这是一个可以线性堆叠的简单模型。
- **keras.layers.Flatten(input_shape=(28, 28))**：定义一个展平层，将 $28 \times 28$ 像素的二维数组转换为作为输入层的一维平坦数组。这意味着你可以将图像排成一行并作为输入处理。
- **keras.layers.Dense(128, activation='relu')**：定义密集层，每层具有 128 个神经元。这些是全连接层，前一层的所有单元都连接到下一层的所有单元。对这些层应用 ReLU 激活函数以引入非线性，使模型能够学习更复杂的函数。
- **keras.layers.Dense(10, activation='softmax')**：定义一个具有 10 个神经元的密集层。这是最终输出层，输出 10 个类别的概率分布。这些概率由 softmax 函数计算。

将这些层堆叠在 Sequential 模型上，定义了从输入层到隐藏层再到输出层的 NN。该模型接收 $28 \times 28$ 像素的手写数字图像作为输入，并训练将其分类为 10 个类别之一。

在模型编译中，使用 Keras 编译 NN 模型，上述编码中的每条指令具有以下含义：

- **optimizer='adam'**：指定使用 Adam 优化器作为优化算法来更新模型参数。Adam 是一种基于梯度下降法的优化算法类型，具有速度快和收敛快的特点。
- **loss='sparse_categorical_crossentropy'**：设置模型的损失函数。在这种情况下，使用稀疏版本的交叉熵损失用于分类任务。当正确答案标签每个都表示为标量值并编码为类索引时，使用此版本。
- **metrics=['accuracy']**：设置评估模型的指标。在这种情况下，这指定使用正确率来评估模型的性能。正确率代表预测与正确答案匹配的样本百分比。

这些设置定义了模型如何学习，并确定了优化算法、损失函数和评估指标。

在模型训练中，使用 Keras 训练 NN 模型，上述编码中的每条指令具有以下含义：

- **x_train**：代表用于训练的输入数据。在这种情况下，它包含来自 MNIST 数据集的手写数字图像数据。输入数据输入到 NN 的输入层。
- **y_train**：代表用于训练的正确答案数据。在这种情况下，它包含来自 MNIST 数据集的手写数字标签数据。正确答案数据以与 NN 输出层节点数对应的格式表示，并在训练模型时使用。
- **epochs=5**：指定模型训练操作的次数。一个 epoch 意味着模型使用整个训练数据集训练一次。在这种情况下，模型训练五个 epoch。

**The model.fit()** 方法使用给定的训练数据集训练模型。更具体地说，训练数据被分割成小批量，并且对每个小批量使用梯度下降法来更新模型参数。然后，计算模型的损失函数和评估指标以报告训练进度。将训练数据分割成小批量意味着将大型数据集分割成几个较小的批次，以便为每个小批量更新模型参数。这使得
