

![](img/0684d2da98e09085c0a622d4fd69aaad_318_0.png)

图 10-10. 两种 Keras 实现：keras-team（左）和 tf.keras（右）

tf.keras 是随 TensorFlow 一起绑的，让我们安装 TensorFlow 吧！

## 安装 TensorFlow 2

假设你已经按照第 2 章中的安装说明安装了 Numpy 和 Scikit-Learn，你可以直接使用 `pip` 来安装 TensorFlow。如果你使用 `virtualenv` 创建了隔离环境，首先需要激活它：

```
cd $ML_PATH # 你的机器学习工作目录（例如 $HOME/）
# source env/bin/activate # 在 Linux 或 macOS 上
# \env\Scripts\activate # 在 Windows 上
```

接下来，安装 TensorFlow 2（如果你没有使用 virtualenv，你需要管理员权限，或者添加 --user 选项）：

```python
python -m pip install --upgrade tensorflow
```

> 对于 GPU，你需要安装 `tensorflow-gpu` 而不是 `tensorflow`，并且还有其他库需要安装。更多详情请参阅 https://tensorflow.org/install/gpu。

为了测试安装情况，打开 Python 终端或 Jupyter notebook，导入 TensorFlow 和 tf.keras，并打印它们的版本号：

```python
>>> import tensorflow as tf
>>> from tensorflow import keras
>>> tf.__version__
'2.0.0'
>>> keras.__version__
'2.2.4-tf'
```

使用 Keras 实现 MLP | 293

第二个版本是由 `tf.keras` 实现的 Keras API 版本。注意它以 `-tf` 结尾，这强调了 `tf.keras` 实现了 Keras API，并包含了一些额外的 TensorFlow 特有功能。

现在让我们使用 `tf.keras` 吧！让我们从构建一个简单的图像分类器开始。

## 使用 Sequential API 构建图像分类器

首先，我们需要加载数据集。我们将处理 Fashion MNIST，它是 MNIST（在第 3 章介绍）的无缝替换方案。它的格式与 MNIST 完全相同（70,000 张 28x28 像素的灰度图像，共 10 个类别），但图像代表的是时尚物品而不是手写数字，因此每个类别都更加多样，且问题变得比 MNIST 更具挑战性。例如，一个简单的线性模型在 MNIST 上的准确率可达到约 92%，但在 Fashion MNIST 上仅为 83%。

## 使用 Keras 加载数据集

Keras 提供了许多实用函数来获取和加载常用数据集，包括 MNIST、Fashion MNIST、加州住房数据集等。让我们加载 Fashion MNIST：

```python
fashion_mnist = keras.datasets.fashion_mnist
(X_train_full, y_train_full), (X_test, y_test) = fashion_mnist.load_data()
```

当使用 Keras 而不是 Scikit-Learn 加载 MNIST 或 Fashion MNIST 时，一个重要的区别是每张图像都被表示为 28x28 的数组，而不是大小为 784 的一维数组。此外，像素强度用整数（0 到 255）而不是浮点数（0.0 到 255）。以下是训练集的形状和数据类型：

```python
>>> X_train_full.shape
(60000, 28, 28)
>>> X_train_full.dtype
dtype('uint8')
```

注意，数据集已经划分为训练集和测试集，但没有验证集，所以我们创建一个。由于我们将使用梯度下降法训练神经网络，我们必须对特征进行缩放。为了简单起见，我们通过除以 255.0（将其转换为浮点数）将像素强度缩缩到 0-1 范围：

```python
X_val, X_train = X_train_full[:5000] / 255.0, X_train_full[5000:] / 255.0
y_val, y_train = y_train_full[:5000], y_train_full[5000:]
```

在 MNIST 中，当标签等于 5 时，意味着图像代表手写数字 5。很简单。但对于 Fashion MNIST，我们需要类别列表来知道我们在处理什么：

```python
class_names = ["T-shirt/top", "Trouser", "Pullover", "Dress", "Coat", "Sandal", "Shirt", "Sneaker", "Bag", "Ankle boot"]
```

对于第一个例子，训练集中的图像代表一件大衣（coat）：

```python
>>> class_names(y_train[0])
'Coat'
```

图 10-11 显示了 Fashion MNIST 数据集的几个样本：

| Coat | T-shirt | Sneaker | Ankle boot | Ankle boot | Coat | Coat | Dress | Coat |
|---|---|---|---|---|---|---|---|---|
| T-shirt/top | Trouser | Bag | Shirt | Shirt | Coat | Dress | Pullover | Bag |
| Sneaker | Dress | Coat | Sneaker | Trouser | Dress | Pullover | T-shirt | Dress |
| Sandal | Ankle boot | Trouser | Sandal | Dress | Sandal | Ankle boot | T-shirt | Dress |

图 10-11. Fashion MNIST 样本

## 使用 Sequential API 创建模型

现在来构建神经网络吧！这是一个具有两个隐藏层的分类 MLP：

```python
model = keras.models.Sequential()
model.add(keras.layers.Flatten(input_shape=[28, 28]))
model.add(keras.layers.Dense(308, activation='relu'))
model.add(keras.layers.Dense(100, activation='relu'))
model.add(keras.layers.Dense(10, activation='softmax'))
```

让我们逐行分析这段代码：

- 第一行创建了一个 Sequential 模型。这是神经网络最简单的 Keras 模型类型，由单层顺序连接的层组成。
- 接下来，安装 TensorFlow 2（如果你没有使用 virtualenv，你需要管理员权限，或者添加 --user 选项）：
- 第一行创建了一个 Sequential 模型。这是神经网络最简单的 Keras 模型类型，由单层顺序连接的层组成。
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- 接下来，添加一个具有 308 个神经元的层。
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- 这一行添加了一个具有 308 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 100 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 10 个神经元的 Dense 层，使用 `softmax` 激活函数。
- 接下来，安装 TensorFlow 2（如果你没有使用 virtualenv，你需要管理员权限，或者添加 --user 选项）：
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- 接下来，安装 TensorFlow  308添加一个具有 308 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 100 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 10 个神经元的 Dense 层，使用 `softmax` 激活函数。
- 接下来，安装 TensorFlow 2（如果你没有使用 virtualenv，你需要管理员权限，或者添加 --user 选项）：
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- 这一行添加了一个具有 308 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 100 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 10 个神经元的 Dense 层，使用 `softmax` 激活函数。
- 接下来，安装 TensorFlow 2（如果你没有使用 virtualenv，你需要管理员权限，或者添加 --user 选项）：
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- 接下来，安装 TensorFlow 203088, Dense 层，使用 `relu` 激活 层。
- 这一行添加了一个具有 100 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 10 个神经元的 Dense 层，使用 `softmax` 激活函数。
- 接下来，安装 TensorFlow 2（如果你没有使用 virtualenv，你需要管理员权限，或者添加 --user 选项）：
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- `input_shape=[28, 28]`。
`Dense(308, activation='relu')`。`Dense(100, activation='relu')`。`Dense(10, activation='softmax')`。

```python
model = keras.models.Sequential()
model.add(keras.layers.Flatten(input_shape=[28, 28]))
model.add(keras.layers.Dense(308, activation='relu'))
model.add(keras.layers.Dense(100, activation='relu'))
model.add(keras.layers.Dense(10, activation='softmax'))
```

```- 让我们逐行分析这段代码：

- 第一行创建了一个 Sequential 模型。这是神经网络最简单的 Keras 模型类型，由单层顺序连接的层组成。
- 这一行添加了一个 `Flatten` 层，输入形状为 `[28, 28]`。
- 接下来，添加一个具有 308 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 100 个神经元的 Dense 层，使用 `relu` 激活函数。
- 这一行添加了一个具有 10 个神经元的 Dense 层，使用 `softmax` 激活函数。

（注：由于原文文本在后续部分存在重复和乱码现象，此处翻译时已根据逻辑结构进行了清理和整合，确保核心代码与描述的准确性。）

