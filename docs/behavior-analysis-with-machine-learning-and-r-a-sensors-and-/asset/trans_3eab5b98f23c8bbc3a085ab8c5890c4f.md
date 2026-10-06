

![](img/91c149cc24c3e5af2971580c9dda9d8b_349_0.png)

(一个标签或数字)。在训练自动编码器时，输入和输出是相同的，即 $(x, x)$。

现在你可能在想，训练一个输出与输入完全相同的模型有什么意义呢？如果你仔细观察图 10.11，你会发现隐藏层的单元数量（仅为 2 个）比输入层和输出层少。当数据从输入层传递到隐藏层时，它被“还原”（压缩）。然后，压缩后的数据在传递到后续层时会被重构，直到到达输出层。因此，神经网络将学习同时压缩和重构数据。一旦网络训练完成，我们就可以去掉中间隐藏层之后的层，并使用网络的“左侧”来压缩我们的数据。这就是**编码器（encoder）**。然后，我们可以使用右侧来解压缩数据。部分被称为**解码器（decoder）**。在这个例子中，编码器和解码器只包含 1 层，但它们可以有更多（我们将在下一节中看到）。在实践中，你不会使用自动编码器来压缩计算机中的文件，因为有更高效的方法。此外，这种压缩是*有损的*，这意味着不能重构的文件与原始文件完全相同。然而，自动编码器有很多应用，包括：

- 用于可视化的降维。
- 数据去噪。
- 数据生成（变分自动编码器）。
- 异常检测（这正是我们感兴趣的！）。

回想起训练神经网络时，我们需要定义一个损失函数。该函数捕捉了网络的学习程度。它衡量了预测值与真实预期输出之间的差异。在自动编码器的语境下，这种差异被称为重构误差，可以使用均方误差进行衡量（类似于回归）。

> 在这一节中，我介绍了最简单的自动编码器类型，但还有许多变体，如去噪自动编码器、变分自动编码器（VAEs）等。Wikipedia 页面提供了不同类型自动编码器的良好概述：https://en.wikipedia.org/wiki/Autoencoder

## 第 10 章检测异常行为

### 10.3.1 用于异常检测的自动编码器

```
keras_autoencoder_fish.R
```

自动编码器可以作为异常检测器，我们将使用它来检测异常鱼类轨迹。其实现方法是训练自动编码器来压缩和重构正常实例。一旦自动编码器学会了编码正常实例，我们可以预期重构误差会很小。当面对非常的实例时，自动编码器尝试重构它们将很困难，因此重构误差会更高。类似于孤立森林（Isolation Forests）中树的长度提供了实例稀有性的衡量标准，自动编码器中的重构误差可以作为异常评分。

要判断一个实例是否异常，我们可以将其通过自动编码器并计算其重构误差 $\epsilon$。如果 $\epsilon > threshold$，则该标签可以被视为异常。

与我们在孤立森林中所做的操作类似，我们将使用 `fishFeatures.csv` 文件，该文件包含了编码为特征的鱼类轨迹。每条轨迹由基于加速度和速度的 8 个数值特征组成。我们将使用 80% 的正常实例来训练自动编码器。所有异常实例将用于测试集。

在拆分数据后（代码在 `keras_autoencoder_fish.R` 中），我们将对其进行标准化（standardize）。`normalize.standard()` 函数将归一化数据使其均值为 0，标准差为 1。

```
$z = \frac{x - \mu}{\sigma} \quad (10.3)$
```

这与我们之前使用的 0-1 归一化略有不同。原因是当缩放到 0-1 时，需要学习训练集中的最小值和最大值。如果测试集中存在超出最小值和最大值的数据点，它们将被截断。但由于我们预期异常具有稀有值，因此它们可能位于训练范围之外并被截断。被截断后，异常实例看起来与正常实例更相似，更难以识别。通过对数据进行标准化，我们确保异常点的极值被保留。在这种情况下，从训练集中学习的参数是 $\mu$ 和 $\sigma$。
一旦数据被归一化，我们就可以定义自动编码器。

```
autoencoder <- keras_model_sequential()

autoencoder <- %%
layer_dense(units = 32, activation = 'relu',
    input_shape = ncol(train.normal)-2) %%
layer_dense(units = 16, activation = 'relu') %%
layer_dense(units = 8, activation = 'relu') %%
layer_dense(units = 16, activation = 'relu') %%
layer_dense(units = 32, activation = 'relu') %%
layer_dense(units = ncol(train.normal)-2, activation = 'linear')
```

这是一个普通的神经网络，其输入层的单元数与特征数量（8）相同。该网络有 5 个隐藏层，大小分别为 32, 16, 8, 16 和 32。输出层有 8 个单元（与输入相同）。所有激活函数都是 RELU，最后一个是线性，因为网络应该能够产生任何输出。现在我们可以编译并拟合模型。

```
autoencoder %% compile(
loss = 'mse',
optimizer = optimizer(lr = 0.01),
metrics = c('mse')
```

```
history <- autoencoder %%
fit(as.matrix(train.normal[,-c(1:2)]),
epochs = 100,
batch_size = 32,
validation_split = 0.10,
verbose = 2
```

均方误差（MSE）作为损失函数。我们使用正常实例作为输入和预期输出。验证集划分设置为 10%，以便我们可以绘制重构误差（损失）。随着训练的进行，损失会下降。我们可以计算正常和异常测试集上的 MSE。

![](/91c149cc24c3e5af2971580c9dda9d8b_352_0.png)

图 10.12: Loss。

```
# 计算正常测试集的 MSE。
autoencoder %>% evaluate(as.matrix(test.normal[,-c(1:2)]),
                              as.matrix(test.normal[,-c(1:2))))
```

```
# loss mean_squared_error
# 0.06147528 0.06147528

# 计算异常测试集的 MSE。
autoencoder %>% evaluate(as.matrix(test.abnormal[,-c(1:2)]),
                              as.matrix(test.abnormal[,-c(1:2))))
```

```
# loss mean_squared_error
# 2.660597 2.660597
```

显然，正常测试集的 MSE 远低于异常测试集。这意味着自动编码器在尝试重构异常点时非常困难，因为它从未见过。

为了找到一个良好的阈值，我们可以从分析训练集上的重构误差开始。首先，我们需要获取预测值。

```
# 在正常训练集上预测。
preds.train.normal <- autoencoder %%
predict_on_batch(as.matrix(train.normal[,-c(1:2)]))
```

变量 `preds.train.normal` 包含了每个特征和每个实例的预测值。我们可以将这些预测值与真实值比较来计算重构误差。作为重构误差，我们将使用平方误差。`squared_errors()` 函数计算每个实例的重构误差。

```
# 计算训练集中的单个平方误差。
errors.train.normal <- squared_errors(preds.train.normal,
                                              as.matrix(train.normal[,-c(1:2)]))
```

```
mean(errors.train.normal)
# [1] 0.8113273
```

```
quantile(errors.train.normal)
# 0% 25% 50% 75% 100%
# 0.0158690 0.2926631 0.4978471 0.8874694 15.0958992
```
