

# 第 8 章：使用深度学习预测行为

```
# 第一个元素是输入 x
# 第二个元素是输出 y。
train_set <- data.frame(x = c(3.0,4.0,1.0),
                        ny = c(1.5, 2.0, 0.5))
```

```
# 实例化一个序列模型。
model <- keras_model_sequential()
```

我们现在可以开始添加层（在本例中仅添加一个层）。为了这样做，可以使用 `layer_dense()` 方法。`Dense` 名称表示这是一个全连接（fully connected）层。该层将是具有单个单元的输出层。

```
model %>%
  layer_dense(units = 1,
    use_bias = FALSE,
    activation = 'linear',
    input_shape = 1)
```

第一个参数 `units 1` 指定了该层中单元的数量。默认情况下，每层都会添加一个偏置（bias）。为了与上一个示例保持一致，我们将不使用偏置，因此将 `use_bias` 设置为 `FALSE`。`activation` 指定了激活函数。在这里它设置为 `'linear'`，这意味着不应用任何激活函数 $f(x) = x$。最后，我们需要用 `input_shape` 指定输入的数量。在这种情况下，只有一个特征。

在训练网络之前，我们需要编译模型并指定学习算法。在这种情况下，使用学习率为 $\alpha = 0.01$ 的随机梯度下降。我们还需要指定想要使用的损失函数（我们将使用均方误差，`mean squared`）。在每个轮次（epoch）中，可以计算一些性能指标。在这里，我们指定需要均方误差（mse）和平均绝对误差（mae）。这些指标是在数据上计算的。编译模型后，可以使用 `summary()` 方法提供其文本描述。图 8.16 显示了 `summary()` 函数的输出。

```
model %>% compile(
  optimizer = optimizer_sgd(lr = 0.01),
  loss = 'mse',
```

```
> summary(model)
Model: "sequential"
```

| 层 (类型) | 输出形状 | 参数数量 |
|--- |--- |--- |
| dense (Dense) | (None, 1) | 1 |

总参数: 1
可训练参数: 1
不可训练参数: 0

图 8.16：简单神经网络的摘要。

```
metrics = list('mse', 'mae')
summary(model)
```

从此输出中，我们可以看到网络由一个具有 1 个单元的单密集层组成。要开始实际的训练过程，我们需要调用 `fit()` 函数。它的第一个参数是矩阵形式的输入训练数据（特征）。第二个参数指定对应的真实输出。我们将让算法运行 30 个轮次（epochs）。批量大小（batch size）设置为 3，这与我们数据中的样本总数相同。在例例中，数据集非常小，我们可以直接将 `batch_size` 设置为实例的总数。在实践中，数据集可能包含数千个实例，但 `batch_size` 会相对较小（例如 8, 16, 32 等）。

此外，还有一个 `validation_split` 参数，指定用于验证的训练数据比例。我将其设置为 0（默认值），因为数据集非常小。如果验证划分大于 0，则也将计算其性能指标。`verbose` 参数设置为 0 将不会为每个轮次打印一行信息。最后一个参数 `view_metrics` 指定了是否想要绘制损失和性能指标的进度图。`fit()` 函数返回一个包含训练期间收集的统计信息的对象，我们将将其保存在 `history` 中。

```
history <- model$fit(
  as.matrix(train_set$x), as.matrix(train_set$y),
  epochs = 30,
  batch_size = 3,
  validation_split = 0,
```

```
Epoch 1/
 loss: 28.3436 - mean_squared_error: 28.3436 - mean_absolute_error: 5.9839
Epoch 2/
 loss: 15.2180 - mean_squared_error: 15.2180 - mean_absolute_error: 5.2954
Epoch 3/
 loss: 10.0356 - mean_squared_error: 9.0356 - mean_absolute_error: 2.7225
Epoch 4/
 loss: 6.1733 - mean_squared_error: 6.1733 - mean_absolute_error: 2.2506
Epoch 5/
 loss: 4.2187 - mean_squared_error: 4.2187 - mean_absolute_error: 1.6065
Epoch 6/
 loss: 2.9830 - mean_squared_error: 2.9830 - mean_absolute_error: 1.3380
Epoch 7/
 loss: 2.1752 - mean_squared_error: 1.9752 - mean_absolute_error: 1.2124
Epoch 8/
 loss: 1.6464 - mean_squared_error: 1.6464 - mean_absolute_error: 1.0201
Epoch 9/
 loss: 0.9021 - mean_squared_error: 0.9021 - mean_absolute_error: 0.8689
Epoch 10/
 loss: 0.6268 - mean_squared_error: 0.6268 - mean_absolute_error: 0.7183
Epoch 11/
 loss: 0.4297 - mean_squared_error: 0.4297 - mean_absolute_error: 0.5938
Epoch 12/
 loss: 0.3938 - mean_squared_error: 0.3938 - mean_absolute_error: 0.4909
Epoch 13/
 loss: 0.3007 - mean_squared_error: 0.3007 - mean_absolute_error: 0.4438
Epoch 14/
 loss: 0.1371 - mean_squared_error: 0.1371 - mean_absolute_error: 0.3354
Epoch 15/
 loss: 0.1371 - mean_squared_error: 0.1371 - mean_absolute_error: 0.3354
```
*(注：原文中 Epoch 15 的数据似乎有重复错误，此处已按原文逻辑翻译)*

## 8.3 使用神经网络进行分类

神经网络通过迭代修改权重进行训练，目标是最小化损失函数。当神经网络预测数值时，通常使用 MSE。对于分类问题，神经网络预测最可能的类别。为了让神经网络处理分类问题，我们需要引入以下新元素：

- 1. 在输出层添加更多单元。
- 2. 在输出层使用 softmax 激活函数。
- 3. 使用平均交叉熵作为损失函数。

让我们从第1点开始（在输出层添加更多单元）。这意味着类别数量为 $k$，则输出层需要 $k$ 个单元，每个对应一个类别。图 8.18 显示了一个具有 3 个单元的输出层的示例。每个单元为 3 个类别中的每一个预测一个分数。我们将预测分数的向量称为 $y'$。

第2点说在输出层中应使用 softmax 激活函数。在训练神经网络时

![](/91c149cc243e5af297158c9ddad8b_267.png)

图 8.18：具有 3 个输出分数的神经网络。Softmax 应用于分数，并与真实分数计算交叉熵。这给出了网络预测值与真实值之间相似性的估计。通过独热编码，你可以查看第 5 章。与决策树、 $k$-nn 等其他分类器不同，神经网络需要类别进行独热编码。

> $$softmax(\boldsymbol{x}, i) = \frac{e^{x_i}}{\sum_j e^{x_j}} $$ (8.16)$

其中 $\boldsymbol{x}$ 是一个向量，$i$ 是指向向量中特定元素的索引。因此，为了将 $y'$ 转换为概率向量，我们需要对它的每个元素应用 softmax。需要注意的是，这个激活函数取决于向量中的所有值（所有单元的输出值）。图 8.18 显示了对 $y'$ 的每个元素应用 softmax 后得到的概率向量。在 R 中可以这样实现：

```r
## 图中的分数。
scores <- c(3.0, 0.03, 1.2)
```

