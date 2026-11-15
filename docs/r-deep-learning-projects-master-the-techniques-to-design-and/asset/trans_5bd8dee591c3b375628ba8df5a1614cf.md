

要有耐心，因为读取和处理 39,209 张图片可能需要几个小时。以防出现任何意外情况，一个良好的做法是保存数据对象，以便我们随时以后恢复：

```
> # Save the data object to a file
> saveRDS(data, file = "43 classes.rds")
> # Restore the data object
> data <- readRDS(file = "43 classes.rds")
```

对可直接使用的数据进行快速检查：

```
> data.x <- data$x
> data.y <- data$y
> dim(data.x)
[1] 39209 1024
```

## 维度正确！

> summary (as.factor (data.y))

| 类别 | 数量 |
|-------|-------|
| 0 | 210 |
| 1 | 2220 |
| 2 | 2250 |
| 3 | 1410 |
| 4 | 1980 |
| 5 | 1860 |
| 6 | 420 |
| 7 | 1440 |
| 8 | 1410 |
| 9 | 1470 |
| 10 | 2010 |
| 11 | 1320 |
| 12 | 2100 |
| 13 | 2160 |
| 14 | 780 |
| 15 | 630 |
| 16 | 420 |
| 17 | 1110 |
| 18 | 1200 |
| 19 | 210 |
| 20 | 360 |
| 21 | 330 |
| 22 | 390 |
| 23 | 510 |
| 24 | 270 |
| 25 | 1500 |
| 26 | 600 |
| 27 | 240 |
| 28 | 540 |
| 29 | 270 |
| 30 | 450 |
| 31 | 780 |
| 32 | 240 |
| 33 | 689 |
| 34 | 420 |
| 35 | 1200 |
| 36 | 390 |
| 37 | 210 |
| 38 | 2070 |
| 39 | 300 |
| 40 | 360 |
| 41 | 240 |
| 42 | 240 |

## 类别大小正确，而且它们再次相当不平衡！

> 绝对不要跳过对分类中类别平衡的检查。

在确保数据已正确加载和处理后，我们对特征（即像素）的分布进行更多探索性分析。例如，我们从类别 1（限速=30km/h）、14（停止）、20（右侧危险弯道）和 27（行人）的每张图片中提取中央 4*4 块（第 222 至 225、254 至 257、286 至 289 以及 318 至 321 个像素）中的 16 个像素。我们显示它们的直方图：

```
> central_block <- c (222:225, 254:257, 286:289, 318:321)
> par (mfrow=c(2, 2))
> for (i in c(1, 14, 20, 27)) {
+   hist(c(as.matrix(data.x[data.y==i, central_block])),
+   main=sprintf("Histogram for class %d", i),
+   xlab="Pixel brightness")
+   }
```

生成的像素亮度直方图显示如下：

![](img/da8fb67f2acf661518076e08b6ffd9b9_78_0.png)

这些类别中中央像素的亮度分布各不相同。例如，类别 20 中大部分中央像素较暗，因为该标志（右侧危险弯道）中心穿过一条粗黑色笔画；而在类别 14 中，停止标志在中央区域附近有一条白色笔画（O 的左侧部分）。从其他位置提取的像素在不同类别中也可以呈现明显的分布。

我们刚刚进行的探索性分析有助于我们继续构建基于像素的分类模型。

## 第一个解决方案 – 使用 MXNet 的卷积神经网络

我们从一个与前一章末尾开发的方案相似的方案入手，即使用 MXNet 的 CNN。

同样，我们首先使用 caret 包将数据集分为两个子集，用于训练（75%）和测试（25%）：

```
> if (!require("caret"))
+ install.packages("caret")
> library(caret)
> set.seed(42)
> train_perc = 0.75
> train_index <- createDataPartition(data.y, p=train_perc, list=FALSE)
> train_index <- train_index[sample(nrow(train_index)), ]
> data_train.x <- data.x[train_index, ]
> data_train.y <- data.y[train_index]
> data_test.x <- data.x[-train_index, ]
> data_test.y <- data.y[-train_index]
```

不要忘记指定特定的随机种子以便可重复工作。我们通常在应用 CNN 之前进行数据标准化。在我们的情况中，加载的原始像素已经在 0 到 1 的范围内；在 Y' 亮度转换后，生成的像素仍然在 0 到 1 的范围内。

> 一般来说，在将数据输入 CNN 或实际上任何神经网络或基于梯度下降的模型之前，对数据进行标准化是必要的。至于图像输入，我们通常将像素缩放到 0 到 1 的范围内。

在准备好训练集和测试集后，我们按如下方式构建 CNN 模型：

![](img/da8fb67f2acf661518076e08b6ffd9b9_80_0.png)

网络以第一组卷积层、ReLU 非线性层和池化层开始。在这里，我们使用 32 个 5*5 卷积滤波器和一个 2*2 最大池化滤波器：

```
> require(mxnet)
> data <- mx.symbol.Variable("data")
> # first convolution
> conv1 <- mx.symbol.Convolution(data=data, kernel=c(5, 5),
                                  num_filter=32)
> act1 <- mx.symbol.Activation(data=conv1, act_type="relu")
> pool1 <- mx.symbol.Pooling(data=act1, pool_type="max",
                             +         kernel=c(2, 2), stride=c(2, 2))
```

接着是第二组卷积、ReLU 非线性和池化层，其中使用了 64 个 5*5 卷积滤波器和 2*2 最大池化滤波器：

```
> # second convolution
> conv2 <- mx.symbol.Convolution(data=pool1, kernel=c(5, 5),
                                  num_filter=64)
> act2 <- mx.symbol.Activation(data=conv2, act_type="relu")
> pool2 <- mx.symbol.Pooling(data=act2, pool_type="max",
                             +         kernel=c(2, 2), stride=c(2, 2))
```

现在，通过检测边缘、曲线和形状，我们已经提取了输入图像的丰富表征，接下来进入全连接层。但在此之前，我们需要将之前卷积层生成的特征图展平：

```
> flatten <- mx.symbol.Flatten(data=pool2)
```

在全连接部分，我们应用一个带有 1,000 个单元的 ReLU 隐藏层和一个带有 43 个单元的 softmax 层：

```
> # first fully connected layer
> fc1 <- mx.symbol.FullyConnected(data=flatten, num_hidden=1000)
> act3 <- mx.symbol.Activation(data=fc1, act_type="relu")
> # second fully connected layer
> fc2 <- mx.symbol.FullyConnected(data=act3, num_hidden=43)
```

最后，softmax 层为每个 43 个类别生成输出：

```
> # softmax output
> softmax <- mx.symbol.SoftmaxOutput(data=fc2, name="sm")
```

网络的所有部分现在都已组装完成。在开始训练模型之前，我们指定随机种子和训练设备，并将矩阵 data_train.x 转换为 MXNet 卷积层所需的数组：

```
> devices <- mx.cpu()
> train.array <- t(data_train.x)
> dim(train.array) <- c(32, 32, 1, nrow(data_train.x))
> mx.set.seed(42)
```

### 模型训练时间：

```
[1] Train-accuracy=0.184965986394558
[2] Train-accuracy=0.824610169491525
[3] Train-accuracy=0.949389830508475
[4] Train-accuracy=0.968305084745763
[5] Train-accuracy=0.983050847457628
[6] Train-accuracy=0.988372881355934
[7] Train-accuracy=0.990745762711866
[8] Train-accuracy=0.993152542372882
[9] Train-accuracy=0.992576271186442
[10] Train-accuracy=0.994372881355933
[11] Train-accuracy=0.99542372881356
[12] Train-accuracy=0.995118644067798
[13] Train-accuracy=0.99671186440678
[14] Train-accuracy=0.999830508474576
[15] Train-accuracy=0.999932203389831
[16] Train-accuracy=1
[17] Train-accuracy=1
[18] Train-accuracy=1
[19] Train-accuracy=1
[20] Train-accuracy=1
[21] Train-accuracy=1
[22] Train-accuracy=1
[23] Train-accuracy=1
[24] Train-accuracy=1
[25] Train-accuracy=1
[26] Train-accuracy=1
[27] Train-accuracy=1
[28] Train-accuracy=1
[29] Train-accuracy=1
[30] Train-accuracy=1
```

我们使用以下超参数拟合模型：

- num.round = 30：最大迭代次数
- array.batch.size = 100：小批量梯度下降的批量大小
- learning.rate = 0.05：学习率
- momentum=0.9：动量因子，决定将多少之前的速度纳入当前速度
- eval.metric=mx.metric.accuracy：使用分类准确率作为评估指标
- initializer=mx.init.uniform(0.1)：初始权重从 -0.1 到 0.1 之间的均匀分布中随机生成，以降低深度网络中权重爆炸和消失的几率
- wd = 0.00001：L2 正则化的权重衰减，通过对大权重施加惩罚来避免过拟合

我们可以通过以下方式查看模型结构：

```
> graph.viz(model_cnn$symbol)
```

然后将训练好的模型应用于测试集：

```
> test.array <- t(data_test.x)
> dim(test.array) <- c(32, 32, 1, nrow(data_test.x))
> prob_cnn <- predict(model_cnn, test.array)
> prediction_cnn <- max.col(t(prob_cnn)) - 1
```

