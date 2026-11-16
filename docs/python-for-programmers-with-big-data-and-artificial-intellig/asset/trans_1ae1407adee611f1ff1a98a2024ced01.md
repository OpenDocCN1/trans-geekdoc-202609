
和尖锐极小值。CoRR abs/1609.04836 (2016)。
https://arxiv.org/abs/1609.04836.

- 总体来说，应使用一些样本来 *验证* 模型。如果指定了验证数据，则在每个 epoch 之后，模型将使用它进行预测并显示 *验证损失和准确率*。您可以研究这些值来调整您的层和 *拟合* 方法的超参数，或者可能更改模型的层组成。在此，我们使用了 *验证分割* 参数来指示模型应保留 *最后 10%* (0.1) 的训练样本用于验证 4——在此情况下，6000 个样本将用于验证。如果您有单独的验证数据，可以使用 *验证数据* 参数（如您将在第 15.9 节中看到）来指定包含样本数组和目标标签的元组。总体而言，最好获得 *随机选择* 的 *验证数据*。您可以为此目的使用 scikit-learn 的 *训练测试分割* 函数（如我们将在本章稍后所做），然后使用 *验证数据* 参数传递随机选择的数据。

4 https://keras.io/getting-started/faq/#how-is-the-validation-split-computed.

在以下输出中，我们将训练准确率 (acc) 和验证准确率 (val_acc) 加粗显示：

点击此处查看代码图像

```
[37]: cnn.fit(X_train, y_train, epochs=5, batch_size=64,
    validation_split=0.1)
Train on 54000 samples, validate on 6000 samples
Epoch 1/5
54000/54000 [==============================] - 68s 1ms/step - loss: 0.1407 -
Epoch 2/5
54000/54000 [==============================] - 64s 1ms/step - loss: 0.0426 -
Epoch 3/5
54000/54000 [==============================] - 69s 1ms/step - loss: 0.0299 -
Epoch 4/5
54000/54000 [==============================] - 70s 1ms/step - loss: 0.0197 -
Epoch 5/5
54000/54000 [==============================] - 63s 1ms/step - loss: 0.0155 -
[37]: <tensorflow.python.keras.callbacks.History at 0x7f105ba0ada0>
```

在第 15.7 节中，我们将介绍 *TensorBoard*——一个用于可视化深度学习模型数据的 TensorFlow 工具。具体来说，我们将查看图表，显示训练和验证准确率及损失值如何随 epoch 变化。在第 15.8 节中，我们将演示 Andrej Karpathy 的 ConvnetJS 工具，该工具在网页浏览器中训练卷积网络，并动态可视化层的输出，包括每个卷积层在学习时“看到”的内容。还将运行他的 MNIST 和 CIFAR10 模型。这些将帮助您更好地理解神经网络的复杂操作。

随着训练的进行，*拟合* 方法会输出信息，显示每个 epoch 的进度、每个 epoch 执行所需时间（在此例中，每个耗时 63–70 秒）以及该轮次的评估指标。在该模型的最后一个 epoch 中，训练样本的准确率达到 99.48% (`acc`)，验证样本的准确率达到 99.27% (`val_acc`)。这些数字很令人印象深刻，考虑到我们尚未尝试调整超参数或修改层的数量和类型，而这些可能会导致更好（或更差）的结果。就像机器学习一样，深度学习是一门受益于大量实验的经验科学。

## 评估模型

现在我们可以检查模型在未见过的数据上的准确率。为此，我们调用模型的 `evaluate` 方法，其输出显示处理测试样本所需的时间（在此例中为四秒零 366 微秒）：

点击此处查看代码图像

```
[38]: loss, accuracy = cnn.evaluate(X_test, y_test)
10000/10000 [===================================] - 4s 366us/step

[39]: loss
[39]: 0.026809450998473768

[40]: accuracy
[40]: 0.9917
```

根据前面的输出，我们的卷积网络模型在预测未见数据的标签时准确率为 99.17%——而且此时我们尚未尝试调整模型。通过稍微在线搜索，您可以找到能够以接近 100% 的准确率预测 MNIST 的模型。尝试使用不同数量的层、不同类型的层和层参数进行实验，并观察这些变化如何影响您的结果。

## 进行预测

模型的 `predict method` 预测其参数数组 (`X_test`) 中数字图像的类别：

点击此处查看代码图像

```
[41]: predictions = cnn.predict(X_test)
```

我们可以通过查看 `y_test[0]` 来检查第一个样本数字应该是什么：

点击此处查看代码图像

```
[42]: y_test[0]
[42]: array([0., 0., 0., 0., 0., 0., 0., 1., 0., 0.], dtype=float32)
```

根据此输出，第一个样本是数字 7，因为测试样本标签的类别表示在索引 7 处指定了 1.0——请回顾，我们是通过 `one-hot encoding` 创建此表示的。

让我们检查 `predict` 方法对第一个测试样本返回的概率：

点击此处查看代码图像

```
[43]: for index, probability in enumerate(predictions[0]):
  print(f'{index}: {probability:.10%}')
0: 0.00000000201%
1: 0.000001355%
2: 0.0000186951%
3: 0.0000015494%
4: 0.0000000003%
5: 0.0000000012%
6: 0.0000000000%
7: 99.9999761581%
8: 0.0000005577%
9: 0.0000011416%
```

根据输出，`predictions[0]` 表明我们的模型几乎可以肯定这个数字是 7。并非所有预测都有这种确定性。

## 定位错误预测

接下来，我们希望查看一些 *错误* 预测的图像，以了解模型难以处理的图像。例如，如果它总是将 8 错误预测，那么也许我们需要在训练数据中包含更多 8。

在查看错误预测之前，我们需要先定位它们。考虑上面的 `predictions[0]`。要确定预测是否正确，我们必须比较 `predictions[0]` 中最大概率的索引与 `y_test[0]` 中包含 `1.0` 的元素的索引。如果这些索引值相同，则预测正确；否则，预测错误。NumPy 的 `argmax` 函数确定其数组参数中最高值元素的索引。让我们使用它来定位错误预测。在以下代码片段中，`p` 是预测值数组，`e` 是预期值数组（预期值是数据集测试图像的标签）：

点击此处查看代码图像

```
[44]: images = X_test.reshape((10000, 28, 28))
incorrect_predictions = []
for i, (p, e) in enumerate(zip(predictions, y_test)):
  predicted, expected = np.argmax(p), np.argmax(e)
  if predicted != expected:
    incorrect_predictions.append(
      (i, images[i], predicted, expected))
```

在此代码片段中，我们首先将 Keras 学习所需的形状 `(28, 28, 1)` 的样本重新 reshape 回 Matplotlib 显示图像所需的 `(28, 28)`。接下来，我们使用 `for` 语句填充列表 `incorrect_predictions`。我们将数组 `predictions` 和 `y_test` 中代表每个样本的行进行 zip 操作，然后对其进行 enumerate，以便捕获它们的索引。如果 `p` 和 `e` 的 `argmax` 结果不同，则预测错误，我们会向 `incorrect_predictions` 追加一个元组，包含该样本的索引、图像、`predicted` 值和 `expected` 值。我们可以使用以下代码确认错误预测的总数（测试集中的 10,000 张图像）：

```
[45]: len(incorrect_predictions)
[45]: 83
```

## 可视化错误预测

以下代码片段显示了 24 张错误图像，每张图像都标记了其索引、预测值 (p) 和预期值 (e)：

点击此处查看代码图像

```
[46]: figure, axes = plt.subplots(nrows=4, ncols=6, figsize=(16, 12))
for axes, item in zip(axes.ravel(), incorrect_predictions):
    index, image, predicted, expected = item
    axes.imshow(image, cmap=plt.cm.gray_r)
    axes.set_xticks([]) # remove x-axis tick marks
    axes.set_yticks([]) # remove y-axis tick marks
    axes.set_title(
    f'index: {index}\np: {predicted}; e: {expected}')
plt.tight_layout()
```

在读取预期值之前，查看每个数字并写下您认为它是什么数字。这是了解数据的重要部分：

![](img/34b7fc2f1ee27beb73bca14927d42340_705_0.png)

## 显示多个错误预测的概率

让我们来看看一些错误预测的概率。以下函数显示指定预测数组的概率：
