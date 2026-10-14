
图 2-8 显示了此方法输出。

```
10000/10000 [====================] - 1s 55us/step

[1.4358007415771485, 0.4896]
```

## 图 2-8. evaluate 方法的输出

输出是我们正在监控的指标列表：分类交叉熵和准确率。我们可以看到，即使在模型从未见过的图像上，模型准确率仍为 49.0%。请注意，如果模型随机猜测，它将达到大约 10% 的准确率（因为有 10 个类别），因此 49.0% 是一个不错的结果，考虑到我们使用的是非常基础的神经网络。

我们可以使用 predict 方法查看测试集上的部分预测，如示例 2-10 所示。

## 示例 2-10. 使用 predict 方法查看测试集上的预测

```
CLASSES = np.array(['airplane', 'automobile', 'bird', 'cat', 'deer', 'dog'
    , 'frog', 'horse', 'ship', 'truck'])

preds = model.predict(x_test) ①
preds_single = CLASSES[np.argmax(preds, axis = -1)] ②
actual_single = CLASSES[np.argmax(y_test, axis = -1)]
```

① preds 是一个形状为 [10000, 10] 的数组——即每个观测值的 10 个类别概率向量。

② 我们使用 numpy 的 argmax 函数将此概率数组转换回单个预测。这里，axis = -1 告诉函数将数组在最后一个维度（类别维度）上坍缩，使得 preds_single 的形状变为 [10000, 1]。

我们可以使用示例 2-11 中的代码同时查看部分图像及其标签和预测。如预期，约有一半是正确的。

## 示例 2-11. 显示 MLP 的预测与实际标签

```
import matplotlib.pyplot as plt

n_to_show = 10
indices = np.random.choice(range(len(x_test)), n_to_show)

fig = plt.figure(figsize=(15, 3))
fig.subplots_adjust(hspace=0.4, wspace=0.4)
```

```
for i, idx in enumerate(indices):
    img = x_test[idx]
    ax = fig.add_subplot(1, n_to_show, i+1)
    ax.axis('off')
    ax.text(0.5, -0.35, 'pred = ' + str(preds_single[idx]), fontsize=10
        , ha='center', transform=ax.transAxes)
    ax.text(0.5, -0.7, 'act = ' + str(actual_single[idx]), fontsize=10
        , ha='center', transform=ax.transAxes)
    ax.imshow(img)
```

图 2-9 显示了模型做出的随机选择的预测，以及真实标签。

![](img/f0f0f5d89818fdddf117bbe758ac8143_66_0.png)

图 2-9. 模型做出的一些预测，以及实际标签

恭喜！你刚刚使用 Keras 构建了一个多层感知器，并用它对新数据进行预测。尽管这是一个监督学习问题，但在未来章节构建生成模型时，本章的许多核心思想（如损失函数、激活函数以及理解层形状）仍然极其重要。接下来我们将通过引入几种新的层类型来探讨改进此模型的方法。

## 卷积神经网络 (CNN)

网络表现尚未达到最佳的一个原因是因为网络中没有任何东西考虑到输入图像的空间结构。事实上，我们的第一步是将图像展平成一个单一向量，以便将其传递给第一个 Dense 层！

为此我们需要使用卷积层。

## 卷积层

首先，我们需要理解在深度学习的上下文中 *卷积* 是指什么。

图 2-10 显示了灰度图像的两个不同的 3 × 3 × 1 部分与 3 × 3 × 1 *滤波器*（或 *核*）进行卷积。卷积是通过将滤波器逐像素与图像部分相乘并求和结果来执行的。当图像部分与滤波器非常匹配时输出更正，当图像部分是滤波器的反转时输出更负。上例与滤波器强烈共振，因此产生较大的正值。下例与滤波器共振不大，因此产生接近零的值。

![](img/f0f0f5d89818fdddf117bbe758ac8143_67_0.png)

*图 2-10. 将 3 × 3 卷积滤波器应用于灰度图像的两个部分*

如果我们将滤波器在整个图像上从左到右、从上到下移动，同时记录卷积输出，我们将获得一个新数组，该数组根据滤波器中的值挑选出输入的特定特征。例如，图 2-11 显示了两个不同的滤波器，它们突出显示水平和垂直边缘。

![](img/f0f0f5d89818fdddf117bbe758ac8143_67_1.png)

## 运行此示例的代码

你可以在书籍仓库中位于 *notebooks/02_deeplearning/02_cnn/convolutions.ipynb* 的 Jupyter notebook 中手动查看此卷积过程。

![](img/f0f0f5d89818fdddf117bbe758ac8143_68_0.png)

## 图 2-11. 将两个卷积滤波器应用于灰度图像

卷积层只是一组滤波器，其中存储在滤波器中的值是神经网络通过训练学习到的权重。最初这些是随机的，但逐渐滤波器会调整其权重以开始挑选出有趣的特征，例如边缘或特定的颜色组合。

在 Keras 中，Conv2D 层对具有两个空间维度（例如图像）的输入张量应用卷积。例如，示例 2-12 中显示的代码构建了一个具有两个滤波器的卷积层，以匹配图 2-11 中的示例。

## 示例 2-12. 将 Conv2D 层应用于灰度输入图像

```
from tensorflow.keras import layers

input_layer = layers.Input(shape=(64,64,1))
conv_layer_1 = layers.Conv2D(
    filters = 2
  , kernel_size = (3,3)
  , strides = 1
  , padding = "same"
)(input_layer)
```

接下来，让我们更详细地查看 Conv2D 层的两个参数——strides 和 padding。

## 步幅

strides 参数是层在输入上移动滤波器时使用的步长。因此，增加步幅会减小输出张量的大小。例如，当 strides = 2 时，输出张量的高度和宽度将是输入张量的一半。这对于在张量通过网络时减小其空间大小，同时增加通道数非常有用。

## 填充

padding = "same" 输入参数用零填充输入数据，以便当 strides = 1 时，层输出大小与输入大小完全相同。

图 2-12 显示了 3 × 3 核在 5 × 5 输入图像上移动，padding = "same" 且 strides = 1。此卷积层的输出大小也将为 5 × 5，因为填充允许核延伸到图像边缘，使其在两个方向上都能拟合五次。如果没有填充，核在每个方向上只能拟合三次，输出大小为 3 × 3。

![](img/f0f0f5d89818fdddf117bbe758ac8143_69_0.png)

图 2-12. 3 × 3 × 1 核（灰色）在 5 × 5 × 1 输入图像（蓝色）上移动，padding = "same" 且 strides = 1，以生成 5 × 5 × 1 输出（绿色）（来源：Dumoulin and Visin, 2018）⁵

设置 padding = "same" 是确保你能够轻松跟踪张量在经过多个卷积层时的大小的好方法。具有 padding = "same" 的卷积层的输出形状为：

(input height / stride, input width / stride, filters)

## 堆叠卷积层

Conv2D 层的输出是另一个四维张量，现在形状为 (batch_size, height, width, filters)，因此我们可以将 Conv2D 层堆叠在彼此之上，以增加神经网络的深度并使其更强大。为了演示这一点，让我们想象我们将 Conv2D 层应用于 CIFAR-10 数据集，并希望预测给定图像的标签。请注意，这次我们不是有一个输入通道（灰度），而是有三个（红、绿和蓝）。

示例 2-13 显示了如何构建一个简单的卷积神经网络，我们可以训练它来完成此任务。

## 示例 2-13. 使用 Keras 构建卷积神经网络模型的代码

```
from tensorflow.keras import layers, models

input_layer = layers.Input(shape=(32,32,3))
conv_layer_1 = layers.Conv2D(
    filters = 10
  , kernel_size = (4,4)
  , strides = 2
  , padding = 'same'
)(input_layer)
conv_layer_2 = layers.Conv2D(
    filters = 20
  , kernel_size = (3,3)
  , strides = 2
  , padding = 'same'
)(conv_layer_1)
flatten_layer = layers.Flatten()(conv_layer_2)
output_layer = layers.Dense(units=10, activation = 'softmax')(flatten_layer)
model = models.Model(input_layer, output_layer)
```

此代码对应于图 2-13 中显示的图表。

![](img/f0f0f5d89818fdddf117bbe758ac8143_70_0.png)

图 2-13. 卷积神经网络的图表

请注意，现在我们正在处理彩色图像，第一卷积层中的每个滤波器的深度为 3 而非 1（即，每个滤波器的形状为 4 × 4 × 3，而非 4 × 4 × 1）。这是为了匹配输入的三个通道（红、绿、蓝）

