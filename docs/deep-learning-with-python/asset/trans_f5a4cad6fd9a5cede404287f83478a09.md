

对于编译步骤，我们照常使用 RMSprop 优化器。由于模型以单个 sigmoid 单元结束，我们将使用二元交叉熵作为损失（提醒一下，请查看第 6 章中的表 6.1，了解在各种情况下应使用哪种损失函数的速查表）。

列表 8.8 配置模型以进行训练

```python
model.compile(loss="binary_crossentropy",
              optimizer="rmsprop",
              metrics=["accuracy"])
```

### 8.2.4 数据预处理

如你现在所知，在将数据馈送到模型之前，应将其格式化为适当预处理的浮点张量。目前，数据作为 JPEG 文件存储在驱动器上，因此将其放入模型的步骤大致如下：

- 1. 读取图片文件。
- 2. 将 JPEG 内容解码为 RGB 像素网格。
- 3. 将这些转换为浮点张量。
- 4. 将它们调整为共享大小（我们将使用 180 × 180）。
- 5. 将它们打包成批次（我们将使用 32 张图片的批次）。

这看起来可能有点令人望而生畏，但幸运的是，Keras 提供了实用工具来自动处理这些步骤。特别是，Keras 提供了实用函数 image_dataset_from_directory()，它可以让你快速设置一个数据管道，自动将磁盘上的图像文件转换为预处理张量的批次。我们将在此处使用它。

调用 image_dataset_from_directory(directory) 将首先列出 directory 的子目录，并假设每个子目录包含我们其中一个类别的图像。然后它将索引每个子目录中的图像文件。最后，它将创建并返回一个配置为读取这些文件、打乱它们、将它们解码为张量、将它们调整为共享大小并将它们打包成批次的 tf.data.Dataset 对象。

列表 8.9 使用 image_dataset_from_directory 读取图像

```python
from tensorflow.keras.utils import image_dataset_from_directory

train_dataset = image_dataset_from_directory(
    new_base_dir / "train",
    image_size=(180, 180),
    batch_size=32)

validation_dataset = image_dataset_from_directory(
    new_base_dir / "validation",
    image_size=(180, 180),
    batch_size=32)

test_dataset = image_dataset_from_directory(
    new_base_dir / "test",
    image_size=(180, 180),
    batch_size=32)
```

## 了解 TensorFlow Dataset 对象

TensorFlow 提供了 tf.data API 来为机器学习模型创建高效的输入管道。其核心类是 tf.data.Dataset。

Dataset 对象是一个迭代器：你可以在 for 循环中使用它。它通常会返回输入数据和标签的批次。你可以将 Dataset 对象直接传递给 Keras 模型的 fit() 方法。

Dataset 类处理了许多否则你自己实现起来会很麻烦的关键功能——特别是异步数据预取（在模型处理前一批数据的同时预处理下一批数据，从而保持执行流程不间断）。

Dataset 类还公开了用于修改数据集的函数式 API。下面是一个快速示例：让我们从随机数的 NumPy 数组中创建一个 Dataset 实例。我们将考虑 1,000 个样本，每个样本是大小为 16 的向量：

```python
import numpy as np
import tensorflow as tf
random_numbers = np.random.normal(size=(1000, 16))
dataset = tf.data.Dataset.from_tensor_slices(random_numbers)
```

> from_tensor_slices() 类方法可用于从 NumPy 数组、或 NumPy 数组的元组或字典中创建 Dataset。

起初，我们的数据集仅产生单个样本：

```
>>> for i, element in enumerate(dataset):
...     print(element.shape)
...     if i >= 2:
...         break
(16,)
(16,)
(16,)
```

我们可以使用 .batch() 方法对数据进行批处理：

```
>>> batched_dataset = dataset.batch(32)
>>> for i, element in enumerate(batched_dataset):
...     print(element.shape)
...     if i >= 2:
...         break
(32, 16)
(32, 16)
(32, 16)
```

更广泛地说，我们可以使用一系列有用的数据集方法，例如

- `.shuffle(buffer_size)`—在缓冲区内打乱元素
- `.prefetch(buffer_size)`—在 GPU 内存中预取一组元素，以实现更好的设备利用率。
- `.map(callable)`—对数据集的每个元素应用任意转换（callable 函数，它预期将数据集产生的单个元素作为输入）。

尤其是 `.map()` 方法，是你会经常使用的方法。下面是一个示例。我们将使用它将玩具数据集中元素的形状从 (16,) 调整为 (4, 4)：

```
>>> reshaped_dataset = dataset.map(lambda x: tf.reshape(x, (4, 4)))
>>> for i, element in enumerate(reshaped_dataset):
...     print(element.shape)
...     if i >= 2:
...         break
>>>
(4, 4)
(4, 4)
(4, 4)
```

在本章中，你即将看到更多 map() 的用法。

让我们来看看其中一个 Dataset 对象的输出：它生成 180 x 180 RGB 图像的批次（形状 (32, 180, 180, 3)）和整数标签（形状 (32,)）。每个批次包含 32 个样本（批次大小）。

列表 8.10 显示 Dataset 生成的数据和标签的形状

```
>>> for data_batch, labels_batch in train_dataset:
...     print("data batch shape:", data_batch.shape)
...     print("labels batch shape:", labels_batch.shape)
...     break
data batch shape: (32, 180, 180, 3)
labels batch shape: (32,)
```

让我们在我们的数据集上拟合模型。我们将使用 `fit()` 中的 `validation_data` 参数来监控单独 Dataset 对象上的验证指标。

请注意，我们还将使用 `ModelCheckpoint` 回调在每个 epoch 后保存模型。我们将用指定保存文件位置的路径对其进行配置，以及参数 `save_best_only=True` 和 `monitor="val_loss"`：它们告诉回调仅在当前 `val_loss` 指标值低于训练期间任何先前值时才保存新文件（覆盖之前的任何文件）。这保证了保存的文件将始终包含模型在验证数据上表现最佳的训练 epoch 对应的状态。因此，如果我们开始过拟合，就不必为较少的 epoch 重新训练新模型：我们只需重新加载保存的文件即可。

列表 8.11 使用 Dataset 拟合模型

```python
callbacks = [
    keras.callbacks.ModelCheckpoint(
        filepath="convnet_from_scratch.keras",
        save_best_only=True,
        monitor="val_loss")
]

history = model.fit(
    train_dataset,
    epochs=30,
    validation_data=validation_dataset,
    callbacks=callbacks)
```

让我们在训练期间绘制模型在训练数据和验证数据上的损失和准确率（参见图 8.9）。

列表 8.12 显示训练期间的损失和准确率曲线

```python
import matplotlib.pyplot as plt
accuracy = history.history["accuracy"]
val_accuracy = history.history["val_accuracy"]
loss = history.history["loss"]
val_loss = history.history["val_loss"]
epochs = range(1, len(accuracy) + 1)
plt.plot(epochs, accuracy, "bo", label="Training accuracy")
plt.plot(epochs, val_accuracy, "b", label="Validation accuracy")
plt.title("Training and validation accuracy")
plt.legend()
plt.figure()
plt.plot(epochs, loss, "bo", label="Training loss")
plt.plot(epochs, val_loss, "b", label="Validation loss")
plt.title("Training and validation loss")
plt.legend()
plt.show()
```

![](img/ab452ecf572a1f1372915be13bd8088f_244_0.png)

![](img/ab452ecf572a1f1372915be13bd8088f_244_1.png)

图 8.9 简单卷积网络的训练和验证指标

这些图表是过拟合的典型特征。训练准确率随时间线性增加，直到达到近乎 100%，而验证准确率在 75% 时达到峰值。验证损失在仅十个 epoch 后达到最小值，然后停滞不前，而训练损失随着训练继续线性下降。

让我们检查测试准确率。我们将从保存的文件中重新加载模型，以评估其在开始过拟合之前的状态。

