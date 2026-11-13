

```
optimizer.apply_gradients(zip(gradients, model.trainable_weights))
self.compiled_metrics.update_state(targets, predictions)
return {m.name: m.result() for m in self.metrics}
```

让我们试试：

```
inputs = keras.Input(shape=(28 * 28,))
features = layers.Dense(512, activation="relu")(inputs)
features = layers.Dropout(0.5)(features)
outputs = layers.Dense(10, activation="softmax")(features)
model = CustomModel(inputs, outputs)

model.compile(optimizer=keras.optimizers.RMSProp(),
              loss=keras.losses.SparseCategoricalCrossentropy(),
              metrics=[keras.metrics.SparseCategoricalAccuracy()])
model.fit(train_images, train_labels, epochs=3)
```

这包含了大量信息，但你现在已经掌握了足够使用 Keras 几乎做任何事情的知识。

## 总结

- Keras 提供了基于 *渐进式揭示复杂性* 原则的一系列不同工作流。它们之间都能顺畅协同工作。
- 你可以通过 `Sequential` 类、函数式 API 或通过继承 `Model` 类来构建模型。大多数情况下，你将使用函数式 API。
- 训练和评估模型最简单的方式是使用默认的 `fit()` 和 `evaluate()` 方法。
- Keras 回调提供了一种在调用 `fit()` 期间监控模型的简单方法，并根据模型状态自动采取行动。
- 你也可以通过重写 `train_step()` 方法，完全控制 `fit()` 的行为。
- 除了 `fit()`，你还可以从头开始编写自己的训练循环。这对于实现全新训练算法的研究人员非常有用。

## 计算机视觉深度学习简介

### 本章内容

- 理解卷积神经网络（convnets）
- 使用数据增量来缓解过拟合
- 使用预训练的 convnet 进行特征提取
- 微调预训练的 convnet

计算机视觉是深度学习最早期也是最大的成功案例。每天，你都在与深度视觉模型交互——通过 Google 照片、Google 图片搜索、YouTube、相机应用中的视频滤镜、OCR 软件以及更多其他方式。这些模型也是自动驾驶、机器人技术、AI 辅助医疗诊断、自动零售结账系统甚至自动化农业等前沿研究的核心。

计算机视觉是推动深度学习在 2011 年至 2015 年间初步兴起的问题领域。一种被称为卷积神经网络的深度学习模型在当时开始在图像分类竞赛中取得非常出色的成绩，首先是 Dan Ciresan 赢得两个小众竞赛（ICDAR 2011 中文字符识别竞赛和 IJCNN 2011 德国交通标志识别竞赛），随后更引人注目的是，2012 年秋季，Hinton 小组赢得了高调的 ImageNet 大规模视觉识别挑战赛。许多其他有前景的结果很快也开始在其他计算机视觉任务中涌现。

有趣的是，这些早期的成功当时还不足以让深度学习成为主流——花了好几年时间。计算机视觉研究社区多年来一直投资于神经网络以外的方法，并且并不完全准备好仅仅因为出现了新事物就放弃它们。在 2013 年和 2014 年，深度学习仍然面临着许多资深计算机视觉研究者的强烈怀疑。直到 2016 年，它才最终成为主流。我记得 2014 年 2 月，我曾劝说我的一位前教授转向深度学习。“它是下一个大事！”我会说。“嗯，也许这只是个时髦，”他回答。到 2016 年，他整个实验室都在做深度学习。时机成熟的想法是无法阻挡的。

本章介绍卷积神经网络，也称为 _卷积神经网络（convnets)_，这是一种深度学习模型，如今几乎在所有计算机视觉应用中都被通用使用。你将学习将 convnets 应用于图像分类问题——特别是涉及小型训练数据集的问题，如果你不是大型科技公司，这就是最常见的用例。

### 8.1 卷积神经网络简介

我们即将深入探讨 convnets 是什么，以及它们为何在计算机视觉任务中如此成功。但首先，让我们来看一个简单的 convnet 示例，该示例对 MNIST 数字进行分类，这是我们在第 2 章中使用全连接网络完成的任务（当时的测试准确率为 97.8%）。尽管这个 convnet 很基础，但其准确率将远超我们在第 2 章中的全连接模型。

下面的清单展示了一个基本 convnet 的样子。它是 `Conv2D` 和 `MaxPooling2D` 层的堆叠。你马上就会看到它们各自的作用。我们将使用函数式 API 构建模型，该 API 在上一章中介绍过。

### 清单 8.1 实例化一个小型 convnet

```python
from tensorflow import keras
from tensorflow.keras import layers
inputs = keras.Input(shape=(28, 28, 1))
x = layers.Conv2D(filters=32, kernel_size=3, activation="relu")(inputs)
x = layers.MaxPooling2D(pool_size=2)(x)
x = layers.Conv2D(filters=64, kernel_size=3, activation="relu")(x)
x = layers.MaxPooling2D(pool_size=2)(x)
x = layers.Conv2D(filters=128, kernel_size=3, activation="relu")(x)
x = layers.Flatten()(x)
outputs = layers.Dense(10, activation="softmax")(x)
model = keras.Model(inputs=inputs, outputs=outputs)
```

重要的是，convnet 的输入张量形状为 (image_height, image_width, image_channels)，不包括批次维度。在这里，我们将配置 convnet 来处理大小为 (28, 28, 1) 的输入，这是 MNIST 图像的格式。

让我们显示我们的 convnet 的架构。

### 清单 8.2 显示模型摘要

```
>>> model.summary()
Model: "model"
Layer (type)                 Output Shape              Param #
================================================================
input_1 (InputLayer)         [(None, 28, 28, 1)]       0
================================================================
conv2d (Conv2D)              (None, 26, 26, 32)        320
================================================================
max_pooling2d (MaxPooling2D) (None, 13, 13, 32)        0
================================================================
conv2d_1 (Conv2D)            (None, 11, 11, 64)        18496
================================================================
max_pooling2d_1 (MaxPooling2 (None, 5, 5, 64)          0
================================================================
conv2d_2 (Conv2D)            (None, 3, 3, 128)         73856
================================================================
flatten (Flatten)            (None, 1152)              0
================================================================
dense (Dense)                (None, 10)                11530
================================================================
Total params: 104,202
Trainable params: 104,202
Non-trainable params: 0
```

你可以看到，每个 Conv2D 和 MaxPooling2D 层的输出都是形状为 (height, width, channels) 的秩-3 张量。随着模型深度增加，宽度和高度维度往往会缩小。通道数由传递给 Conv2D 层的第一个参数控制（32、64 或 128）。

在最后一个 Conv2D 层之后，我们得到形状为 (3, 3, 128) 的输出——一个具有 128 个通道的 3 x 3 特征图。下一步是将此输出馈送到全连接分类器中，即你已经熟悉的那种：一堆 Dense 层。这些分类器处理向量（即 1D），而当前输出是一个秩-3 张量。为了弥补这一差距，我们在添加 Dense 层之前，先使用 Flatten 层将 3D 输出展平为 1D。

最后，我们进行 10 类分类，因此最后一层有 10 个输出和一个 softmax 激活函数。

现在，让我们在 MNIST 数字上训练 convnet。我们将重用第 2 章 MNIST 示例中的大量代码。因为我们使用 softmax 输出进行 10 类分类，所以将使用类别交叉熵损失；由于标签是整数，我们将使用其稀疏版本，即 sparse_categorical_crossentropy。

