

# 516 附录

我们还计算了 F1 分数，它是精确率（precision）和召回率（recall）的调和平均数。F1 分数的计算公式如下：F1-Score=$2\times \frac{Precision \times Recall}{Precision + Recall}$

```python
from sklearn.metrics import f1_score
f1_score(y_train_5, y_train_pred)
```

现在我们得到了模型的精确率和召回率，并将探索这两个指标之间的权衡。随着精确率的提高，召回率会降低，反之亦然。根据应用的不同，你可能更需要获得更高的召回率或更高的精确率。这被称为“精确率/召回率权衡”。我们定义了一个函数——`plot_precision_recall_vs_threshold()`，允许我们绘制不同阈值的精确率与召回率的关系图。我们还定义了一个函数——`plot_precision_vs_recall()`，允许我们绘制给定阈值的精确率与召回率的权衡图。

最后，我们生成 ROC ，它是真正例率（TPR）和假正例率（FPR）的视觉表示。该曲线通过计算不同阈值下的 FPR 和 TPR 绘制而成。

```python
from sklearn.metrics import roc_curve
fpr, tpr, thresholds = roc_curve(y_train_5, y_train_pred)
```

ROC 最终允许我们计算分类器的 AUC，它是保持不变的。理想情况下，我们希望 AUC 尽可能接近 1（1 代表能够完美地区分正类和负类）。AUC 越接近 1，模型的性能就越好。

恭喜你！到此，我们已经完成了动手练习。你已经成功完成了以下所有内容：

- 训练了一个分类器
- 使用交叉验证评估了分类器
- 调整了不同的超参数
- 计算了精确率、召回率和 F1 分数等关键指标
- 生成了 ROC 和 AUC 以识别具有高召回率和低 FPR 的最佳模型

在后续附录中，我们将实现一个多层感知器（MLP）。

## 多层感知器

在本附录中，我们将通过 Jupyter notebook 进行一个上手练习，使用 MNIST 数据集实现一个 MLP。

### MNIST 数据集与 MLP 回顾

本练习使用的 MNIST 数据集包含 70,000 张图像。每张图像都是 28×28 的灰度图像，与以下类别之一的标签相关：

- 0: T 恤/上衣
- 1: 裤子
- 2: 毛衣
- 3: 连衣裙
- 4: 外套
- 5: 凉鞋
- 6: 衫
- 7: 运动鞋
- 8: 包
- 9: 踝靴

每张图像表示为一个从 0（白色）到 255（黑色）的 784 维特征向量，并用其代表的数字标记。MLP 是一种全连接前馈神经网络（ANN）。它由三层组成：输入层、隐藏层和输出层。输入层接收待处理的信号。处理在隐藏层进行，隐藏层是网络的计算引擎。最终的分类在输出层生成。

我们首先回顾本节中的一些有用定义。如果你想对其中一些概念进行深层次理解，我们也鼓励你参考第 4 章：

- **超参数（Hyperparameter）**：设计者可以调节的“旋钮”。这包括层数、节点数、激活函数类型、学习率、训练次数（epochs）和批量大小（batch size）。这些值不是由算法学习的（与参数不同），因此由设计者定义。
- **学习率（Learning rate）**：梯度下降寻找全局最小值的速率。
- **Epoch（时期）**：对训练/验证数据的完整正向和反向遍历。
- **批量大小（Batch size）**：在一次迭代中通过网络的训练/验证集的子集。批量大小越大，GPU 并行处理的内容就越多。
- **迭代（Iteration）**：完成一个 epoch 需要的批次数。

如第 4 章 4.4 节所述，反向传播（backpropagation）是每个神经网络训练的引擎。通过反向传播过程，定义神经元之间连接的权重和偏置会进行调整，以最小化损失函数，损失函数捕捉了训练期间神经网络输出与预期目标值之间的差异。

在练习中，我们将完成以下任务：

- 使用 MLP 架构实现神经网络以利用 MNIST Fashion 数据集。
- 调整几个神经网络超参数以获得最佳模型性能。
- 使用交叉熵指标衡量损失，并使用准确率衡量模型性能。
- 使用反向传播训练模型学习 266,610 个参数并达到接近 90% 的性能。

## 实现 MLP 分类器

我们将开始启动此练习的 Jupyter notebook。在 notebook 的第一部分，我们开始导入几个常用模块（sklearn, keras, numpy, tensorflow, matplotlib），并确保我们运行的是最新版本的 Python。

接下来，我们为各种类型的激活函数及其导数定义实用函数，我们在稍后设计神经网络时会引用它们。然后我们获取 MNIST Fashion 数据集，该数据集已划分为训练集（60,000 张）和测试集（10,000 张图像）。

```python
fashion_mnist = keras.datasets.fashion_mnist
(X_train, y_train_full), (X_test, y_test) = fashion_mnist.load_data()
```

我们进一步划分了训练集以获得包含 5,000 个样本的验证集。我们还将像素强度从 0–255 缩小到 0–1 范围，并通过除以 255 将其转换为浮点数：

```python
X_valid, y_train = X_train_full[:5000] / 255, y_train_full[5000:] / 255
X_test = y_test / 255
```

我们使用 Sequential API 构建模型：

```python
model = keras.models.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),
    keras.layers.Dense(368, activation="relu"),
    keras.layers.Dropout(0.2),
    keras.layers.Dense(10, activation="softmax"),
])
```

在训练之前，我们需要用优化器和损失函数编译模型：

```python
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
```

现在开始训练模型。需要注意的是，我们的训练（最多 25 个 epochs）可能需要几分钟完成：

```python
history = model.fit(X_train, y_train, epochs=25, validation_data=(X_valid, y_valid))
```

输出中的每一行显示了 1 个 epoch 的结果。交叉熵训练损失和准确率以及验证损失和准确率会被记录。最后一个 epoch（25/25）中的指标表示最终模型的交叉熵损失和准确率。我们可以绘制训练和验证（损失和准确率）随 epoch 变化的图：

```python
import matplotlib.pyplot as plt

loss = history.history['loss']
val_loss = history.history['val_loss']
acc = history.history['accuracy']
val_acc = history.history['val_accuracy']
epochs = range(1, len(loss) + 1)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.plot(epochs, loss, 'r=loss')
plt.plot(epochs, val_loss, 'b=val_loss')
plt.title('Model Loss')
plt.xlabel('Epoch')
plt.ylabel('Loss')
plt.legend()

plt.subplot(1, 2, 2)
plt.plot(epochs, acc, 'r=acc')
plt.plot(epochs, val_acc, 'b=val_acc')
plt.title('Model Accuracy')
plt.xlabel('Epoch')
plt.ylabel('Accuracy')
plt.legend()
plt.show()
```

最后，我们现在评估测试集上的性能：

```python
model.evaluate(X_test, y_test)
```

我们现在可以使用 MLP 预测测试数据前三个实例的性能，并与样本的图形显示进行比较：

```python
import numpy as np

predictions = model.predict(X_test[:3])
predicted_classes = np.argmax(predictions, axis=1)
actual_classes = y_test[:3]

print(predicted_classes)
print(actual_classes)
```

## 520 附录

交叉熵损失函数是分类任务的常用选择。它使用概率公式为 $H(p, q) = -\sum p(x)\log(q(x))$，$p(x)$ 是真实类别概率，$q(x)$ 是预测概率。由于我们对小于 1 的数字取对数，因此需要负号使交叉熵损失变为正数。我们使用 Sequential API 构建模型：

```python
model = keras.models.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),
    keras.layers.Dense(368, activation="relu"),
    keras.layers.Dropout(0.2),
    keras.layers.Dense(10, activation="softmax"),
])
```

在训练之前，我们需要用优化器和损失函数编译模型：

```python
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
```

现在开始训练模型。需要注意的是，我们的训练（最多 25 个 epochs）可能需要几分钟完成：

```python
history = model.fit(X_train, y_train, epochs=25, validation_data=(X_valid, y_valid))
```

输出中的每一行显示了 1 个 epoch 的结果。交叉熵训练损失和准确率以及验证损失和准确率会被记录。最后一个 epoch（25/25）中的指标表示最终模型的交叉熵损失和准确率。我们可以绘制训练和验证（损失和准确率）随 epoch 变化的图：

```python
import matplotlib.pyplot as plt

loss = history.history['loss']
val_loss = history.history['val_loss']
acc = history.history['accuracy']
val_acc = history.history['val_accuracy']
epochs = range(1, len(loss) + 1)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.plot(epochs, loss, 'r=loss')
plt.plot(epochs, val_loss, 'b=val_loss')
plt.title('Model Loss')
plt.xlabel('Epoch')
plt.ylabel('Loss')
plt.legend()

plt.subplot(1, 2, 2)
plt.plot(epochs, acc, 'r=acc')
plt.plot(epochs, val_acc, 'b=val_acc')
plt.title('Model Accuracy')
plt.xlabel('Epoch')
plt.ylabel('Accuracy')
plt.legend()
plt.show()
```

