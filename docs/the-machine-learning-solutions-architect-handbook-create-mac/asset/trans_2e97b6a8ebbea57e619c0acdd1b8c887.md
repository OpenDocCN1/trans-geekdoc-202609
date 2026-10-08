

- **定义损失函数：** TensorFlow 2.x 提供了一系列内置的损失函数，例如用于回归任务的均方误差（MSE）和平均绝对误差（MAE），以及用于分类任务的交叉熵损失。你可以在 https://en.wikipedia.org/wiki/Mean_squared_error 和 https://en.wikipedia.org/wiki/Mean_absolute_error 找到更多关于 MSE 和 MAE 的信息。你可以在 `tf.keras.losses` 中找到支持的损失函数列表。你可以在 https://keras.io/api/losses/ 找到更多关于不同损失的信息。如果内置损失函数不能满足需求，你可以自定义损失函数。

- **选择优化器：** TensorFlow 2.x 为模型训练提供了一系列内置的优化器，例如用于参数优化的 Adam 优化器和随机梯度下降（SGD）优化器，它们位于 `tf.keras.optimizers` 中。你可以在 https://keras.io/api/optimizers/ 找到更多关于不同支持的优化器的详细信息。Adam 和 SGD 是最常用的两种优化器。

- **选择评估指标：** TensorFlow 2.x 通过其 `tf.keras.metrics` 类提供了一系列内置的评估指标（例如准确率和交叉熵），用于模型训练评估。你也可以在训练期间为模型评估定义自定义指标。

- **将网络编译为模型：** 这一步将定义的网络同定义的损失函数、优化器和评估指标编译成计算图，为模型训练做好准备。

- **拟合模型：** 这一步通过分批次（batches）和多个轮次（epochs）将数据馈给计算图来启动训练过程，以优化模型参数。

- **评估模型：** 模型训练完成后，你可以使用 `evaluate` 函数针对测试数据对模型进行评估。

- **保存模型：** 模型可以 SavedModel 格式或 HDF5 格式保存。

- **模型服务：** TensorFlow 自带了模型服务框架，我们将详细介绍它。该库设计用于在服务器集群上进行大规模生产级的数据处理和模型训练。

## 动手操练 – 训练 TensorFlow 模型

在本次练习中，你将学习如何在本地环境中安装 TensorFlow，并构建和训练你之前安装的简单神经网络。如果你不记得如何操作，请访问第 3 章《机器学习》中的动手操练部分。现在让我们开始吧：

1. 在第一个单元格中，运行以下代码安装 TensorFlow：
```bash
!pip install --upgrade tensorflow
```

2. 现在导入库并加载示例数据。我们将使用 TensorFlow 库自带的内置 `fashion_mnist` 数据集进行加载。接下来，我们将数据加载到 `tf.data.Dataset` 类中，然后调用它的 `batch()` 函数来设置批次大小。
```python
import numpy as np
import tensorflow as tf
tf.enable_eager_execution()

train, test = tf.keras.datasets.fashion_mnist.load_data()
images, labels = train
labels = labels.astype(np.int32)
images = images/255
train_ds = tf.data.Dataset.from_tensor_slices((images, labels))
train_ds = train_ds.batch(32)
```

3. 让我们看看数据长什么样。在新单元格中运行以下代码以查看示例数据：
```python
from matplotlib import pyplot as plt

print("label: " + str(labels[0]))
pixels = images[0]
plt.imshow(pixels, cmap='gray')
plt.show()
```

接下来，我们必须构建一个具有两个隐藏层（一个包含 100 个节点，另一个包含 50 个节点）和一个具有 10 个节点的输出层（每个节点代表一个类别标签）的 MLP 网络。然后我们将使用 Adam 优化器编译网络，使用交叉熵损失作为优化目标，并将准确率作为衡量指标。Adam 优化器是梯度下降（GD）的一种变体，它主要在通过自适应学习更新学习率以提高收敛性方面改进了 GD，而 GD 使用恒定的学习率进行参数更新。交叉熵衡量分类模型的性能，其中输出是不同类别的概率分布。当预测分布偏离实际类别标签时，交叉熵误差会增加。为了启动训练过程，我们将运行 10 个轮次（epochs）。一个轮次是指整个数据集的一次完整遍历：

```python
model = tf.keras.Sequential([
    tf.keras.layers.Flatten(),
    tf.keras.layers.Dense(100, activation="relu"),
    tf.keras.layers.Dense(50, activation="relu"),
    tf.keras.layers.Dense(10),
    tf.keras.layers.Softmax()
])

model.compile(optimizer='adam',
    loss=tf.keras.losses.SparseCategoricalCrossentropy(),
    metrics=[tf.keras.metrics.SparseCategoricalAccuracy()])

model.fit(train_ds, epochs=10)
```

当模型训练时，你将看到每个轮次报告的损失指标和准确率指标。

现在模型已经训练完成，我们需要使用测试数据集来验证其性能。在以下代码中，我们正在为测试数据创建一个 `test_ds`：

```python
images_test, labels_test = test
labels_test = labels_test.astype(np.int32)
images_test = images_test/255

test_ds = tf.data.Dataset.from_tensor_slices((images_test, labels_test))
test_ds = test_ds.batch(32)
test_ds = test_ds.shuffle(1000)

results = model.evaluate(test_ds)
print("test loss, test acc:", results)
```

6. 你也可以使用独立的 `keras.metrics` 来评估模型。在这里，我们获取预测结果并使用 `tf.keras.metrics.Accuracy` 计算测试中预测值与真实值之间的准确率：

```python
predictions = model.predict(images_test[0])
predicted_labels = np.argmax(predictions, axis=1)
m = tf.keras.metrics.Accuracy()
m.update_state(labels_test[0], predicted_labels)
print(m.result().numpy())
```

7. 要保存模型，在新单元格中运行以下代码。它将以 SavedModel 格式保存模型：
```python
model.save('my_model')
```

恭喜！你已经成功安装了 TensorFlow 并训练了一个深度学习模型。

