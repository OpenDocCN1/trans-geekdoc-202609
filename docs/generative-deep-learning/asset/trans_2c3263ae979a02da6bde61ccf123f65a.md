
在 Keras 中，BatchNormalization 层实现了批归一化功能，如示例 2-14 所示。

### 示例 2-14. Keras 中的 BatchNormalization 层

```
from tensorflow.keras import layers
layers.BatchNormalization(momentum = 0.9)
```

momentum 参数是在计算移动平均值和移动标准差时赋予之前值的权重。

## Dropout

在备考时，学生使用往年试卷和样题来提高对学科内容的了解是常见做法。有些学生试图死记硬背这些问题的答案，但在考试中却遇到困难，因为他们并未真正理解学科内容。最优秀的学生利用练习材料来加深整体理解，因此即使面对从未见过的新问题，仍能正确作答。

同样的原则适用于机器学习。任何成功的机器学习算法都必须确保其能泛化到未见数据，而不仅仅是记住训练数据集。如果算法在训练数据集上表现良好，但在测试数据集上表现不佳，我们称之为过拟合。为抵消这一问题，我们使用正则化技术，确保模型在开始过拟合时受到惩罚。

有许多方法可以正则化机器学习算法，但对于深度学习，最常见的方法之一是使用 dropout 层。这一思想由 Hinton 等人在 2012 年提出，并在 Srivastava 等人 2014 年的论文中发表。

Dropout 层非常简单。在训练期间，每个 dropout 层从前一层中随机选择一组单元并将其输出设为 0，如图 2-15 所示。

令人难以置信的是，这一简单的添加通过确保网络不会过度依赖某些单元或单元组而大幅减少过拟合，这些单元或单元组实际上只是记住训练集中的观测值。如果使用 dropout 层，网络就不能过度依赖任何一个单元，因此知识会在整个网络中更均匀地分布。

![](img/f0f0f5d89818fdddf117bbe758ac8143_76_0.png)

图 2-15. 一个 dropout 层

这使得模型在泛化到未见数据方面好得多，因为网络已在不熟悉的条件下训练出准确的预测，例如随机丢弃单元所导致的情况。dropout 层内部没有需要学习的权重，因为要丢弃的单元是随机决定的。在预测时，dropout 层不会丢弃任何单元，以便使用完整的网络进行预测。

![](img/f0f0f5d89818fdddf117bbe758ac8143_76_1.png)

### Dropout 类比

回到我们的类比，这有点像数学学生做往年试卷时，其公式手册中随机缺少了一些关键公式。这样，他们通过对核心原理的理解来学习如何回答问题，而不是总是查阅书中相同位置的公式。到考试时，由于他们能够超越训练材料进行泛化，因此会发现回答从未见过的问题容易得多。

Keras 中的 Dropout 层实现了这一功能，其中 rate 参数指定从前一层丢弃的单元比例，如示例 2-15 所示。

### 示例 2-15. Keras 中的 Dropout 层

```
from tensorflow.keras import layers
layers.Dropout(rate = 0.25)
```

Dropout 层最常用于 dense 层之后，因为这些层由于权重数量更多而最容易过拟合，不过你也可以在卷积层之后使用它们。

![](img/f0f0f5d89818fdddf117bbe758ac8143_77_0.png)

批归一化也被证明可以减少过拟合，因此许多现代深度学习架构根本不使用 dropout，完全依赖批归一化进行正则化。与大多数深度学习原理一样，没有适用于每种情况的金科玉律——唯一确定什么最好的方法是测试不同的架构，看看哪一个在保留数据集合上表现最佳。

## 构建 CNN

你现在已经看到了三种新的 Keras 层类型：Conv2D、BatchNormalization 和 Dropout。让我们把这些组件组合成一个 CNN 模型，看看它在 CIFAR-10 数据集上的表现如何。

![](img/f0f0f5d89818fdddf117bbe758ac8143_77_1.png)

## 运行本示例的代码

你可以在书库中名为 notebooks/02_deeplearning/02_cnn/cnn.ipynb 的 Jupyter notebook 中运行以下示例。

我们将测试的模型架构如示例 2-16 所示。

### 示例 2-16. 使用 Keras 构建 CNN 模型的代码

```
from tensorflow.keras import layers, models

input_layer = layers.Input((32,32,3))

x = layers.Conv2D(filters = 32, kernel_size = 3
                 , strides = 1, padding = 'same')(input_layer)
x = layers.BatchNormalization()(x)
x = layers.LeakyReLU()(x)

x = layers.Conv2D(filters = 32, kernel_size = 3, strides = 2, padding = 'same')(x)
x = layers.BatchNormalization()(x)
x = layers.LeakyReLU()(x)

x = layers.Conv2D(filters = 64, kernel_size = 3, strides = 1, padding = 'same')(x)
x = layers.BatchNormalization()(x)
x = layers.LeakyReLU()(x)

x = layers.Conv2D(filters = 64, kernel_size = 3, strides = 2, padding = 'same')(x)
x = layers.BatchNormalization()(x)
x = layers.LeakyReLU()(x)

x = layers.Flatten()(x)

x = layers.Dense(128)(x)
x = layers.BatchNormalization()(x)
x = layers.LeakyReLU()(x)
x = layers.Dropout(rate = 0.5)(x)

output_layer = layers.Dense(10, activation = 'softmax')(x)

model = models.Model(input_layer, output_layer)
```

我们使用四个堆叠的 Conv2D 层，每个层后都跟着一个 BatchNormalization 层和一个 LeakyReLU 层。在展平 resulting 张量后，我们将数据通过一个大小为 128 的 Dense 层，再次后接 BatchNormalization 层和 LeakyReLU 层。紧接着是一个用于正则化的 Dropout 层，网络以一个大小为 10 的输出 Dense 层结束。

![](img/f0f0f5d89818fdddf117bbe758ac8143_78_0.png)

使用批归一化层和激活层的顺序是个人偏好问题。通常批归一化层放在激活层之前，但一些成功的架构会反过来使用这些层。如果你选择在激活之前使用批归一化，可以使用缩写 BAD（批归一化、激活，然后丢弃）来记住顺序！

模型摘要如表 2-3 所示。

### 表 2-3. CIFAR-10 的 CNN 模型摘要

| 层 (类型) | 输出形状 | 参数数 |
|---|---|---|
| InputLayer | (None, 32, 32, 3) | 0 |
| Conv2D | (None, 32, 32, 32) | 896 |
| BatchNormalization | (None, 32, 32, 32) | 128 |
| LeakyReLU | (None, 32, 32, 32) | 0 |
| Conv2D | (None, 16, 16, 32) | 9,248 |
| BatchNormalization | (None, 16, 16, 32) | 128 |
| LeakyReLU | (None, 16, 16, 32) | 0 |
| Conv2D | (None, 16, 16, 64) | 18,496 |
| BatchNormalization | (None, 16, 16, 64) | 256 |
| LeakyReLU | (None, 16, 16, 64) | 0 |
| Conv2D | (None, 8, 8, 64) | 36,928 |
| BatchNormalization | (None, 8, 8, 64) | 256 |
| LeakyReLU | (None, 8, 8, 64) | 0 |
| Flatten | (None, 4096) | 0 |
| Dense | (None, 128) | 524,416 |
| BatchNormalization | (None, 128) | 512 |
| LeakyReLU | (None, 128) | 0 |
| Dropout | (None, 128) | 0 |
| Dense | (None, 10) | 1290 |

总参数数 592,554
可训练参数 591,914
非可训练参数 640

![](img/f0f0f5d89818fdddf117bbe758ac8143_79_0.png)

继续之前，请确保你能够手工计算每个层的输出形状和参数数量。这是一个很好的练习，可以证明你完全理解了每个层的构造方式以及它如何连接到前一层！不要忘记包含作为 Conv2D 和 Dense 层一部分的偏置权重。

## 训练和评估 CNN

我们以与之前完全相同的方式编译和训练模型，并调用 evaluate 方法来确定其在保留数据集上的准确率（图 2-16）。

```
model.evaluate(x_test, y_test, batch_size=1000)

10000/10000 [==============================] - 15s 1ms/step

[0.8423407137393951, 0.7155999958515167]
```

图 2-16. CNN 性能

如你所见，该模型现在达到了 71.5% 的准确率，相比之前的 49.0% 有很大提升！图 2-17 显示了我们新的卷积模型的一些预测结果。

这一改进仅仅是通过改变模型架构以包含卷积、批归一化和 dropout 层实现的。请注意，我们新模型的參數數量實際上比之前的模型更少，即使層數遠多。這展示了在模型设计上保持实验精神的重要性，以及对不同层类型如何为你所用感到自在。当构建生成
