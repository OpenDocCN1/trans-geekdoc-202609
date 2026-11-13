

四个副本中的每一个都在自己的设备上独立地处理一个本地批次：它们先运行前向传递，再运行反向传递。每个副本都会输出一个“权重增量”，用于描述根据模型在本地批次上的损失相对于之前权重的梯度，应将模型中的每个权重变量更新多少。

源自本地梯度的权重增量会在四个副本之间高效合并，以获得全局增量，并应用于所有副本。由于此操作在每个步骤结束时执行，副本始终保持同步：它们的权重始终相等。

![](img/ab452ecf572a1f1372915be13bd8088f_451_0.png)

> Figure 13.2 MirroredStrategy 训练的一个步骤：每个模型副本计算本地权重更新，然后将其合并并用于更新所有副本的状态。

## tf.data 性能提示

进行分布式训练时，请始终将数据作为 `tf.data.Dataset` 对象提供，以保证获得最佳性能。（将数据作为 NumPy 数组传递也可行，因为这些数组会被 `fit()` 转换为 `Dataset` 对象。）你还应确保利用数据预取：在将数据集传递给 `fit()` 之前，调用 `dataset.prefetch(buffer_size)`。如果不确定选择哪个缓冲区大小，可尝试 `dataset.prefetch(tf.data.AUTOTUNE)` 选项，它会为你选择缓冲区大小。

在理想情况下，在 _N_ 个 GPU 上训练将带来 _N_ 倍的加速比。但在实际中，分布式训练会引入一些开销——特别是，合并来自不同设备的权重增量需要一定时间。你获得的实际加速比是所用 GPU 数量的函数：

- 使用两个 GPU 时，加速比接近 2x。
- 使用四个 GPU 时，加速比约为 3.8x。
- 使用八个 GPU 时，加速比约为 7.3x。

这假设你使用了足够大的全局批次大小，以使每个 GPU 都能充分利用。如果你的批次大小太小，本地批次大小将不足以让 GPU 保持忙碌。

## 13.2.3 TPU 训练

除了 GPU 之外，深度学习领域还有一种趋势，即将工作流迁移到专门为深度学习工作流设计的越来越专业化的硬件上（这种特定用途芯片被称为 ASIC，即专用集成电路）。各种大小公司都在开发新芯片，但当今最突出的这类努力是 Google 的 Tensor Processing Unit (TPU)，它在 Google Cloud 和 Google Colab 上可用。

在 TPU 上训练确实需要经过一些繁琐步骤，但额外的工作是值得的：TPU 速度非常快。在 TPU V2 上训练通常比在 NVIDIA P100 GPU 上训练快 15 倍。对大多数模型而言，TPU 训练平均比 GPU 训练高出 3 倍的成本效益。

## 通过 Google Colab 使用 TPU

你实际上可以在 Colab 中免费使用 8 核 TPU。在 Colab 菜单中，在 Runtime 标签页下，在 Change Runtime Type 选项中，你会发现除了 GPU 运行时之外，还可以使用 TPU 运行时。

当使用 GPU 运行时时，你的模型可以直接访问 GPU，无需做任何特殊操作。但 TPU 运行时并非如此；在开始构建模型之前，你需要采取一个额外步骤：你需要连接到 TPU 集群。

它的工作原理如下：

```
import tensorflow as tf
tpu = tf.distribute.cluster_resolver.TPUClusterResolver.connect()
print("Device:", tpu.master())
```

你不必过分担心这段代码的作用——它只是一个小小的咒语，用于将你的笔记本运行时连接到设备。芝麻开门。

与多 GPU 训练的情况类似，使用 TPU 要求你打开一个分布式策略作用域——在此例中，是 TPUStrategy 作用域。TPUStrategy 遵循与 MirroredStrategy 相同的分布式模板——模型在每个 TPU 核心上复制一次，且副本始终保持同步。

下面是一个简单示例。

```
Listing 13.4 Building a model in a TPUStrategy scope
from tensorflow import keras
from tensorflow.keras import layers

strategy = tf.distribute.TPUStrategy(tpu)
print(f"Number of replicas: {strategy.num_replicas_in_sync}")

def build_model(input_size):
    inputs = keras.Input((input_size, input_size, 3))
    x = keras.applications.resnet.preprocess_input(inputs)
    x = keras.applications.resnet.ResNet50(
        weights=None, include_top=False, pooling="max") (x)
outputs = layers.Dense(10, activation="softmax")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop",
    loss="sparse_categorical_crossentropy",
    metrics=["accuracy"])
return model

with strategy.scope():
    model = build_model(input_size=32)
```

我们几乎准备好开始训练了。但 Colab 中的 TPU 有一个有点奇怪的地方：它是双 VM 设置，这意味着托管你笔记本运行时的 VM 与 TPU 所在的 VM 不是同一个。因此，你无法从存储在本地磁盘上的文件进行训练（也就是说，无法从链接到托管笔记本的 VM 的磁盘上的文件进行训练）。TPU 运行时无法从那里读取数据。你在数据加载方面有两种选择：

- 从驻留在 VM 内存中的数据进行训练（不在磁盘上）。如果你的数据在 NumPy 数组中，那你已经在这样做了。
- 将数据存储在 Google Cloud Storage (GCS) 桶中，并创建直接从桶中读取数据的数据集，而无需在本地下载。TPU 运行时可以从 GCS 读取数据。对于太大而无法完全放入内存的数据集，这是你唯一的选择。

在我们的例子中，让我们从内存中的 NumPy 数组进行训练——CIFAR10 数据集：

```
(x_train, y_train), (x_test, y_test) = keras.datasets.cifar10.load_data()
model.fit(x_train, y_train, batch_size=1024)
```

> 请注意，与多 GPU 训练一样，TPU 训练需要大批次大小来确保设备保持高利用率。

你会注意到第一个时代开始需要一段时间——这是因为你的模型正在被编译成 TPU 可以执行的形式。一旦该步骤完成，训练本身就会快得惊人。

## 谨防 I/O 瓶颈

由于 TPU 可以极快地处理数据批次，从 GCS 读取数据的速度很容易成为瓶颈。

- 如果你的数据集足够小，应该将其保留在 VM 内存中。你可以通过在数据集上调用 `dataset.cache()` 来实现这一点。这样，数据只会从 GCS 读取一次。
- 如果你的数据集太大而无法放入内存，请务必将其存储为 TFRecord 文件——一种高效的二进制存储格式，可以非常快速地加载。在 keras.io 上，你会找到一个代码示例，演示如何将数据格式化为 TFRecord 文件（https://keras.io/examples/keras_recipes/creating_tfrecords/）。

## 利用步骤融合提高 TPU 利用率

由于 TPU 拥有大量可用的计算能力，你需要使用非常大的批次来保持 TPU 核心忙碌。对于小型模型，所需的批次大小可能会变得非常大——每个批次高达 10,000 个样本。在处理巨大批次时，你应该相应地提高优化器学习率；你将对权重进行较少的更新，但每次更新都会更准确（因为梯度是使用更多数据点计算的），因此你应该以更大的幅度移动权重。

不过，有一个简单的技巧可以让你在保持合理批次大小的同时充分利用 TPU：步骤融合。其思想是在每个 TPU 执行步骤期间运行多个训练步骤。基本上，在 VM 内存到 TPU 的两次往返之间完成更多工作。为此，只需在 `compile()` 中指定 `steps_per_execution` 参数——例如，`steps_per_execution=8` 以在每个 TPU 执行期间运行八个训练步骤。对于未充分利用 TPU 的小型模型，这可以带来显著的加速。

## 总结

- 你可以利用超参数调优和 KerasTuner 来自动化寻找最佳模型配置的繁琐工作。但要注意验证集过拟合！
- 各异模型的集成通常可以显著提升预测质量。
- 通过开启混合精度，可以加速 GPU 上的模型训练——你通常几乎不需要付出任何代价就能获得不错的速度提升。
- 为了进一步扩展工作流，你可以使用 `tf.distribute.MirroredStrategy` API 在多个 GPU 上训练模型。
- 你甚至可以通过使用 `TPUStrategy` API 在 Google 的 TPU 上训练（可在 Colab 上使用）。如果你的模型较小，请务必利用步骤融合（通过 `compile(..., steps_per_execution=N)` 参数），以充分利用 TPU 核心。

