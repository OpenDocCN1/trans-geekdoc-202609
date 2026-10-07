
这确实显示这是一张沙拉的图片：

![](img/5720be5c3cca252e12448e68d25607b5_328_0.png)

## 模型分类器部分已经工作了

事实上，如果你执行 `classifier_model.predict(x)`，即使用上一章中那个没有添加边界框层（bounding layers）的模型，那么你应该得到完全相同的概率分布。（试一试！）

当然，你也可以使用生成器来做预测：

```python
preds = model.predict_generator(train_generator)
```

这将为 `train_annotations` dataframe 中的所有行创建预测结果：一个大小为 (7040, 20) 的数组用于分类输出，以及一个大小为 (7040, 4) 的数组用于边界框输出。但正如你所看到的，边界框的预测目前还没有意义……除非你训练了该模型。

## 训练它！

现在所有组件已就绪，训练模型就像之前一样。该模型再次在带有带有快速 GPU 的机器上进行训练。（如果你的电脑很慢，那么真的不值得自己训练这个模型。）

首先，为验证集创建一个生成器，并将 `shuffle` 设置为 `False`：

```python
val_generator = BoundingBoxGenerator(val_annotations, val_dir, image_height, image_width, batch_size, shuffle=False)
```

现在部分代码位于 `helpers.py` 中，因此导入这些函数：

```python
from helpers import combine_histories, plot_loss, plot_bbox_histories = []

## 机器学习

## 第9章：超越分类

然后训练若干轮（epochs）：

```python
histories.append(model.fit_generator(train_generator,
    steps_per_epoch=len(train_generator),
    epochs=5,
    validation_data=val_generator,
    validation_steps=len(val_generator),
    workers=8))
```

由于模型中涉及的操作更多，Keras 在训练期间会打印更多信息：

```
Epoch 5
220/220 [============================] - 14s 64ms/step - loss: 1.8093 - class_prediction_loss: 0.4749 - bbox_prediction_loss: 0.1187 - class_prediction_acc: 0.8709 - val_loss: 1.2640 - val_class_prediction_loss: 0.5931 - val_bbox_prediction_loss: 0.0522 - val_class_prediction_acc: 0.8168
```

这里有 `class_prediction_loss`，它是分类输出的交叉熵损失。还有 `bbox_prediction_loss`，它是用于边界框预测的均方误差（Mean Squared Error）损失。这些名称取自输出层，这也是为什么给你的层赋予有意义的标识符的另一个原因。

注意边界框损失比分类损失小得多，仅为 0.1187。你无法真正比较这些值，因为它们是使用完全不同的公式计算的。重要的是它们随时间推移的变化趋势。

总损失值是这两个损失之和，并根据你为 `model.compile()` 提供的 `loss_weights` 进行加权，以及分类器层的 L2 惩罚。总体总损失只是模型运行状态的一个指示——这个数字本身是没有意义的。

Keras 打印了一个 `class_prediction_acc` 指标，用于衡量训练集上分类的准确率，但边界框预测没有这样的指标。这是因为你告诉 `model.compile()` 你只想要 `metrics={"class_prediction": "accuracy"}`。毕竟，边界框预测的“准确”意味着什么呢？我们很快会回到这个话题，因为有一个非常有用的指标可以使用，但它不是准确率。

raywenderlich.com

330

在前在前五个轮次中，总损失似乎正在下降，但很难说这归因于分类损失还是边界框损失。所以，我们只绘制边界框损失看看效果如何：

```python
history = combine_histories(histories)
plot_bbox_loss(history)
```

![](img/5720be5c3cca252e12448e68d25607b5_330_0.png)

前 5 个轮次中边界框预测的损失

训练损失确实显著下降了，但验证损失看起来并不特别令人深刻。那么模型是否真的在学习某些有用的东西呢？很难说，因为损失本身并不能告诉你模型运行得如何。你唯一能说的是损失较低时模型损失较高时运行更好——这没什么启发性。

至少对于分类输出，你可以计算准确率，它比损失更具解释性。如果损失下降了 10%，意味着什么？谁知道呢……但准确率提高 10% 就非常有意义。

幸运的是，对于边界框预测，还有一个让我们对模型质量产生直观感受的指标：IOU。

## IOU

抱歉，这并不意味着我欠了什么钱。这个缩写代表交并比（Intersection-over-Union），尽管有些人称之为 Jaccard 指数。

为了衡量预测的边界框与训练数据中真实值框的匹配程度，你可以计算它们的重叠程度或它们的交集。但仅有重叠是不够的，重要的是它们不重叠的部分有多少。

IOU 取两个边界框的交集，并将其除以它们的总面积（并集），得到一个 0 到 1 之间的数字。两个框越相似，数值越高。完美匹配为 1，而 0 表示两个框完全不重叠。

## 交集

## 并集

![](img/5720be5c3cca252e12448e68d25607b5_331_0.png)

IOU 是两个框的交集除以并集。`helpers.py` 模块有一个简单的 `iou` 函数用于计算交并比。你可以这样使用它：

```python
from helpers import iou
bbox1 = [0.2, 0.7, 0.3, 0.6]
bbox2 = [0.4, 0.6, 0.7, 0.5]
print(iou(bbox1, bbox2))
```

这输出 0.35，意味着这两个框有四分之一的共同部分。你可以通过以下方式查看：

![](img/5720be5c3cca252e12448e68d25607b5_332_0.png)

## 机器学习

## 第9章：超越分类

这看起来是正确的：

![](img/5720be5c3cca252e12448e68d25607b5_331_0.png)

IOU 是两个框的交集除以并集。`helpers.py` 模块有一个简单的 `iou` 函数用于计算交并比。对于边界框的预测比只看损失更有启发性。要使用这个指标，你需要编译模型：

```python
from helpers import iou, MeanIOU
model.compile(loss=["sparse_categorical_crossentropy", "mse"],
              optimizer=Adam(lr=1e-3),
              metrics=["class_prediction": "accuracy", "bbox_prediction": MeanIOU()])
```

区别在于增加了 `MeanIOU`。现在 Keras 计算来自模型预测的平均 IOU。`MeanIOU` 对象是一个简单的包装器，让 Keras 使用 `iou()` 函数。这输出验证集的 IOU。

如果你再次训练模型，Keras 现在还会打印 `bbox_prediction_mean_iou` 指标，训练集从 0.25 逐渐增加到 0.43，但验证集仅达到 0.34。

你可以通过 `plot_iou(history)` 查看 IOU 随时间的变化。这是训练 15 轮的图，期间每五轮将学习率手动缩小 10 倍。

raybenderlich.com

333

机器学习

第9章：超越分类

![](img/5720be5c3cca252e12448e68d25607b5_333_0.png)

## 平均 IOU 的图

这显示平均 IOU 随时间确实有所提高，至少对于训练集是这样。每隔几轮，当学习率降低时，都有一个提升。

然而，验证集的曲线并不那么令人深刻（也不那么平滑）。无疑这里存在过拟合的情况，另一个 `Conv2D` 层添加的参数比模型其他部分的总和还要多……

顺便说，这张图略有误导性。它似乎验证 IOU 并没有提高多少，但请记住，验证分数是在每个轮次后测量的，因此此时模型已经看过了了一轮训练。在未训练的模型上，平均验证 IOU 实际上接近 0。（提示：你可以在训练前通过 `model.evaluate_generator(val_generator, steps=len(val_generator))` 这一点。）

所以，这个简单的定位模型到底如何？嗯，让我们看看测试集中的一些图片并亲眼观察一下。

> 注意：你也可以使用一种基于 IOU 值的损失函数，称为 DICE 损失。目前你使用的是 MSE 损失，它试图让边界框的每个单独角坐标都尽可能接近真实值。但模型并不真正知道这四个数字之间是有联系的。
