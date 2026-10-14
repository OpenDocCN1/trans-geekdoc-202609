
![](img/f0f0f5d89818fdddf117bbe758ac8143_55_0.png)

图 2-4. 来自 CIFAR-10 数据集的示例图像（来源：Krizhevsky, 2009）2

默认情况下，图像数据由每个像素通道的 0 到 255 之间的整数组成。我们首先需要通过将这些值缩放至 0 到 1 之间来预处理图像，因为神经网络在每个输入的绝对值小于 1 时工作效果最佳。

我们还需要将图像的整数标签更改为独热编码向量，因为神经网络的输出将是图像属于每个类别的概率。如果图像的类别整数标签为 i，则其独热编码是一个长度为 10（类别数）的向量，其中除第 i 个元素外均为 0，而第 i 个元素为 1。这些步骤在示例 2-1 中显示。

### 示例 2-1. 预处理 CIFAR-10 数据集

```
import numpy as np
from tensorflow.keras import datasets, utils

(x_train, y_train), (x_test, y_test) = datasets.cifar10.load_data() ①

NUM_CLASSES = 10

x_train = x_train.astype('float32') / 255.0
x_test = x_test.astype('float32') / 255.0

y_train = utils.to_categorical(y_train, NUM_CLASSES)
y_test = utils.to_categorical(y_test, NUM_CLASSES)
```

- 1. 加载 CIFAR-10 数据集。x_train 和 x_test 分别是形状为 [50000, 32, 32, 3] 和 [10000, 32, 32, 3] 的 numpy 数组。y_train 和 y_test 分别是形状为 [50000, 1] 和 [10000, 1] 的 numpy 数组，包含每个图像类别的整数标签，范围为 0 到 9。
- 2. 缩放每个图像，使像素通道值位于 0 到 1 之间。
- 3. 对标签进行独热编码——y_train 和 y_test 的新形状分别为 [50000, 10] 和 [10000, 10]。

我们可以看到，训练图像数据（x_train）存储在一个形状为 [50000, 32, 32, 3] 的张量中。此数据集中没有列或行；相反，这是一个具有四个维度的张量。张量只是一个多维数组——它是矩阵向超过两个维度自然扩展。 该张量的第一个维度引用数据集中图像的索引，第二和第三个维度与图像大小相关，最后一个是通道（即红色、绿色或蓝色，因为这些是 RGB 图像）。

例如，示例 2-2 显示了如何找到图像中特定像素的通道值。

### 示例 2-2. 图像 54 中位置为 (12,13) 的像素的绿色通道 (1) 值

```
x_train[54, 12, 13, 1]
# 0.36862746
```

## 构建模型

在 Keras 中，你可以定义神经网络的结构为 Sequential 模型或使用函数式 API。

Sequential 模型对于快速定义线性层堆栈非常有用（即一个层直接跟随前一个层且没有分支）。我们可以使用 Sequential 类按示例 2-3 所示定义我们的 MLP 模型。

### 示例 2-3. 使用 Sequential 模型构建我们的 MLP

```
from tensorflow.keras import layers, models

model = models.Sequential([
    layers.Flatten(input_shape=(32, 32, 3)),
    layers.Dense(200, activation = 'relu'),
    layers.Dense(150, activation = 'relu'),
    layers.Dense(10, activation = 'softmax'),
])
```

本书中的许多模型都需要将一个层的输出传递给多个后续层，或者相反，一个层接收来自多个前序层的输入。对于这些模型，Sequential 类不适用，我们需要改用函数式 API，后者灵活得多。

![](img/f0f0f5d89818fdddf117bbe758ac8143_57_0.png)

> 我建议即使你刚开始使用 Keras 构建线性模型，也应使用函数式 API 而不是 Sequential 模型，因为随着神经网络架构变得更复杂，长期来看它会更有帮助。函数式 API 将为你的深度神经网络设计提供完全的自由。

示例 2-4 使用函数式 API 编码了相同的 MLP。在使用函数式 API 时，我们使用 Model 类来定义模型的整体输入和输出层。

### 示例 2-4. 使用函数式 API 构建我们的 MLP

```
from tensorflow.keras import layers, models

input_layer = layers.Input(shape=(32, 32, 3))
x = layers.Flatten()(input_layer)
x = layers.Dense(units=200, activation = 'relu')(x)
x = layers.Dense(units=150, activation = 'relu')(x)
output_layer = layers.Dense(units=10, activation = 'softmax')(x)
model = models.Model(input_layer, output_layer)
```

这两种方法得到的是相同的模型——架构图显示在图 2-5 中。

![](img/f0f0f5d89818fdddf117bbe758ac8143_58_0.png)

图 2-5. MLP 架构图

让我们更详细地了解 MLP 中使用的不同层和激活函数。

## 层

为了构建我们的 MLP，我们使用了三种不同类型的层：Input、Flatten 和 Dense。

Input 层是网络的入口。我们告诉网络期望每个数据元素的形状为一个元组。请注意，我们没有指定批大小；这不是必需的，因为我们可以同时将任意数量的图像传递到 Input 层。我们不需要在 Input 层定义中明确说明批大小。

接下来我们使用 Flatten 层将此输入展平为向量。这会得到长度为 3,072（= 32 × 32 × 3）的向量。我们这样做的原因是后续的 Dense 层要求其输入是扁平的，而不是多维数组。正如我们稍后会看到的，其他层类型需要多维数组作为输入，因此你需要了解每种层类型所需的输入和输出形状，以了解何时需要使用 Flatten。

Dense 层是神经网络最基本的构建块之一。它包含给定数量的单元，这些单元与前一层密集连接——也就是说，层中的每个单元都通过一条携带权重（可以为正或负）的连接与前一层中的每个单元相连。给定单元的输出是其从前一层接收到的输入的加权和，然后通过非线性激活函数处理后再发送到下一层。激活函数对于确保神经网络能够学习复杂函数而不是仅输出其输入的线性组合至关重要。

## 激活函数

有许多种激活函数，但其中最重要的三种是 ReLU、sigmoid 和 softmax。

*ReLU*（整流线性单元）激活函数定义为：如果输入为负则为 0，否则等于输入。*LeakyReLU* 激活函数与 ReLU 非常相似，只有一个关键区别：而 ReLU 激活函数对小于 0 的输入值返回 0，LeakyReLU 函数则返回与输入成比例的小负数。ReLU 单元有时会死亡，如果它们始终输出 0，因为激活前偏向负值过大。在这种情况下，梯度为 0，因此不会通过该单元向后传播误差。LeakyReLU 激活通过始终确保梯度非零来修复此问题。基于 ReLU 的函数是用于深度网络层之间以促进稳定训练的最可靠激活函数之一。

如果希望层的输出缩放至 0 到 1 之间，*sigmoid* 激活是有用的——例如，具有一个输出单元的二分类问题或多标签分类问题，其中每个观测值可以属于多个类别。图 2-6 并排比较了 ReLU、LeakyReLU 和 sigmoid 激活函数。

![](img/f0f0f5d89818fdddf117bbe758ac8143_59_0.png)

*图 2-6. ReLU、LeakyReLU 和 sigmoid 激活函数*

如果希望层的输出总和等于 1，*softmax* 激活函数是有用的；例如，对于每个观测值只属于恰好一个类别的多分类问题。它定义为：

$y_i = \frac{e^{x_i}}{\sum_{j=1}^{J} e^{x_j}}$

这里，$J$ 是层中的单元总数。在我们的神经网络中，我们在最终层使用 softmax 激活以确保输出是一组 10 个概率
