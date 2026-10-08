

# 总结

在本章中，我们涵盖了深度学习的基础知识。本章介绍的词汇将贯穿本书，因此你可以经常参考本章。我们还通过示例展示了计算机视觉的应用。此外，还涵盖了用于各种平台开发环境的所有软件软件包的安装。

在下一章中，我们将讨论如何同时使用 Keras 和 TensorFlow 在数据集上训练分类模型。我们将研究如何使用更大的模型以及其他技术（如增强、微调等）来提高准确率。然后，我们将看到世界各地许多人士提出的若干先进模型，这些模型在竞赛中取得了最佳准确率。

# 2 图像分类

图像分类是将整幅图像分类为单个标签的任务。例如，如果给定一张图像是狗或猫，图像分类任务就可以将其标记为狗或猫。在本章中，我们将学习如何使用 TensorFlow 构建此类的图像分类模型，并学习提高准确率的技巧。

本章将涵盖以下主题：

-   在 TensorFlow 中训练 MNIST 模型
-   在 Keras 中训练 MNIST 模型
-   其他流行的图像测试数据集
-   更大的深度学习模型
-   训练一个猫狗分类模型
-   开发现实世界的应用

## 在 TensorFlow 中训练 MNIST 模型

在本节中，我们将学习修改后的美国标准技术学院（MNIST）数据库数据，并构建一个简单的分类模型。本节的目标是学习深度学习的通用框架并使用 TensorFlow 实现它。首先，我们将构建一个感知机或逻辑回归模型。然后，我们将训练一个 CNN 以获得更好的准确率。我们还将看到 TensorBoard 如何帮助可视化训练过程并理解参数。

# 第 2 章

## MNIST 数据集

MNIST 数据包含 0–9 的手写数字，共有 60,000 张训练图像和 10,000 张测试图像。该数据库被广泛用于在进行最少预处理的情况下尝试算法。它是学习机器学习算法的一个良好且紧凑的数据库。它是图像分类问题中最著名的数据库。这里展示了一些示例：

| label = 5 | label = 0 | label = 4 | label = 9 |
| :---: | :---: | :---: | :---: |
| ![5](link) | ![0](link) | ![4](link) | ![9](link) |
| label = 2 | label = 1 | label = 3 | label = 4 |
| :---: | :---: | :---: | :---: |
| ![2](link) | ![1](link) | ![3](link) | ![4](link) |
| label = 3 | label = 5 | label = 3 | label = 6 |
| :---: | :---: | :---: | :---: |
| ![3](link) | ![5](link) | ![3](link) | ![6](link) |
| label = 3 | label = 2 | label = 6 | label = 1 |
| :---: | :---: | :---: | :---: |
| ![3](link) | ![2](link) | ![6](link) | ![1](link) |
| label = 7 | label = 8 | label = 6 | label = 9 |
| :---: | :---: | :---: | :---: |
| ![7](link) | ![8](link) | ![6](link) | ![9](link) |

如上图所示，这些手写字符有 10 个标签。图像被归一化为 28x28 像素的大小，转换为灰度尺寸，并居中到固定大小。这是一个小型的数据集，可以在上面快速测试算法。在下一节中，我们将看到如何加载此数据集供 TensorFlow 使用。

## 加载 MNIST 数据

直接从 TensorFlow 加载 MNIST 数据。注意，我们在加载数据时指定了独热编码（one hot encoding）作为参数。标签以整数形式存储，但为了训练，应以独热编码的形式加载。假设读者从现在起开始在带有 TensorFlow tf 的编辑器中运行代码。以下是加载 MNIST_data 的代码段：

```
from tensorflow.examples.tutorials.mnist import input_data
mnist_data = input_data.read_data_sets('MNIST_data', one_hot=True)
```

第一次运行时，数据将被下载并可能需要一些时间。从第二次运行开始，将利用缓存的数据。在下一节中，我们将构建一个感知机来分类数字。

## 构建感知机

感知机是一个单层神经网络。本章涵盖的概念，如全连接层、激活函数、随机梯度下降、logits、独热编码、softmax 和交叉熵将是非常有用的。你将学习如何在 TensorFlow 中定义这些神经网络组件，并使用网络训练 MNIST 数据。

## 为输入数据和目标定义占位符

占位符（placeholder）是传递数据的张量。占位符不是特定值，而是在计算期间接收输入。首先声明感知机的输入大小、类别数量、批大小（batch size）以及总迭代次数或批总数。x_input 是稍后输入图像的输入。y_input 是按如下方式提供独热标签或目标的占位符：

```
input_size = 784
no_classes = 10
batch_size = 100
total_batches = 200
```

```
x_input = tf.placeholder(tf.float32, shape=[None, input_size])
y_input = tf.placeholder(tf.float32, shape=[None, no_classes])
```

shape 参数中的 `None` 表示它可以是任何大小，因为我们还没有定义批大小。第二个参数是 x_input 的张量大小和 y_input 的类别数量。根据占位符的大小，我们将数据以浮点数的形式发送。接下来，我们可以定义感知机。

## 为全连接层定义变量

让我们通过解释权重（weights）和偏置（bias）等变量来定义简单的线性分类器或感知器。这些变量的值将在计算过程中学习。这些变量也称为模型的参数。权重变量用输入形状和类别数量的正态分布初始化。这里输入大小为 784 作为类别数量。

```python
weights = tf.Variable(tf.random_normal([input_size, no_classes]))
bias = tf.Variable(tf.random_normal([no_classes]))
logits = tf.matmul(x_input, weights) + bias
```
（此处省略重复的 logits 描述，保持逻辑一致）

