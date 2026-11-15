
这是根据自编码器对点的重构。我们将把重构与原始图像之间（欧几里得）距离大于三的点标记为红色，其余点保持蓝色。为什么是这些点？我们的自编码器了解到我们的数据集具有某些内在属性（它学习了平均点的分布），因此在重构错误异常大的那些点上，可能存在值得探究的内容：

```
# Coerce back the matrix to data frame to use ggplot later
df <- as.data.frame(df)
# Euclidean distance larger than 3 = sum of squares larger than 9
df$color <- ifelse((df$V1-preds$V1)**2+(df$V2-preds$V2)**2>9,"red","blue")
```

最后，我们可以使用 ggplot 查看结果：

```
library(ggplot2)
df %>% ggplot(aes(V1,V2),col=df$color)+geom_point(color = df$color,
position="jitter")
```

以下截图展示了我们识别异常点的效果：

![](img/da8fb67f2acf661518076e08b6ffd9b9_115_0.png)

自编码器的输出。蓝色表示由我们的自编码器重构的点，红色表示数据集中的原始点。我们可以看到，有一簇红点，得益于我们的自编码器，我们可以将其识别为异常点。

在上述截图中，蓝色点是自编码器重构的图像。我们可以看到，它正确地学习到大部分点来自以 (0,0) 为中心的正态分布，这与预期一致。然而，仍然有一些点在原始数据集上是 *正常* 的，却被标记为异常。不必这么快就对学习自编码器感到气馁，原因在于我们使用的自编码器相当简单。我们将探讨使用自编码器解决异常值检测问题的更复杂方法。

## 自编码器与 MNIST

无论是在研究论文、博客文章还是书籍中，许多深度学习算法的示例都涉及 MNIST 数据集。我们也不例外，将使用 MNIST 介绍一个自编码器的小型用例。

动机如下：假设你想自动检测假币。那么你需要教会计算机什么是 *平均钞票* 的表征，以便能够检测出有显著差异的钞票。鉴于全球每天发生的现金交易量巨大，且欺诈者的手段日益复杂，手动完成此过程是不可想象的。一种方法是使用复杂的成像软件，这正是 D40 或 D50 等假币检测器的工作原理。

使用 MNIST 的另一个原因显然是出于实践考虑。在撰写本文时，我未能找到一个包含假币的良好训练数据集，而 MNIST 已预装在 `keras` 中。

我们从加载数据集开始：

```
library(keras)
mnist <- dataset_mnist()
X_train <- mnist$train$x
y_train <- mnist$train$y
X_test <- mnist$test$x
y_test <- mnist$test$y
```

让我们更仔细地查看数据集：

```
image(X_train[1,, ], col=gray.colors(3))
y_train[1]
```

如果一切正常，你应该能看到数字五的图像。

在训练自编码器之前，我们需要进行一些预处理。x_train 数据是一个三维数组（图像、宽度、高度），包含灰度值。我们需要首先将这些数组转换为矩阵，通过将高度和宽度重塑为单个向量，这样我们不再处理 28 x 28 的方阵，而是得到一个 28*28=784 的向量。然后，我们将灰度值从 0 到 255 之间的整数转换为 0 到 1 之间的浮点值：

```
# reshape
dim(X_train) <- c(nrow(X_train), 784)
dim(X_test) <- c(nrow(X_test), 784)
# rescale
X_train <- X_train / 255
X_test <- X_test / 255
```

初始预处理完成后，我们定义自编码器的拓扑结构。让我们使用一个包含 32 个神经元的编码层，以达到 784/32 = 24.5 的压缩比：

```
input_dim <- 28*28 #784
inner_layer_dim <- 32
input_layer <- layer_input (shape=c(input_dim))
encoder <- layer_dense(units=inner_layer_dim,
activation='relu') (input_layer)
decoder <- layer_dense(units=784) (encoder)
autoencoder <- keras_model(inputs=input_layer, outputs = decoder)
```

我们现在可以编译和训练模型了：

```
autoencoder %>% compile(optimizer='adam',
loss='mean_squared_error',
metrics=c('accuracy'))
history <- autoencoder %>% fit(
X_train, X_train,
epochs = 50, batch_size = 256,
validation_split=0.2
)
```

使用 plot 命令，我们可以查看模型在训练和验证过程中的性能，如下所示：

```
plot(history)
```

更好的是，如果你使用 RStudio 作为 IDE，Viewer 面板中有一个实时视图。使用此命令，你应该能看到两个图，显示准确率和损失作为 epoch 数量的函数：

![](img/da8fb67f2acf661518076e08b6ffd9b9_118_0.png)

使用 Viewer 面板实时查看训练。点击 "在新窗口中打开" 按钮：

![](img/da8fb67f2acf661518076e08b6ffd9b9_118_1.png)

实时训练。横轴是 epoch 数量，纵轴显示损失和准确率。

使用 `predict` 方法，我们重构数字并计算重构错误：

```
# Reconstruct on the test set
preds <- autoencoder %>% predict(X_test)
error <- rowSums((preds-X_test)**2)
error
```

直觉上，有些类别可能更难预测，因为有些人书写数字的方式略有不同。哪些类别的重构错误更高？

```
# Which were more problematic to reconstruct?
eval <- data.frame(error=error, class=as.factor(y_test))
library(dplyr)
eval %>% group_by(class) %>% summarise(avg_error=mean(error))
```

| 类别 | 平均错误 |
|-------|-----------|
| 0 | 14.091963 |
| 1 | 6.126858 |
| 2 | 17.245944 |
| 3 | 14.138960 |
| 4 | 13.189842 |
| 5 | 15.170581 |
| 6 | 14.570642 |
| 7 | 11.778826 |
| 8 | 16.120203 |
| 9 | 11.645038 |

请注意，预计会出现一些小幅度的差异，例如，数据洗牌中涉及随机因素。不过，总体趋势应该相似。

一图胜千言，因此与其使用 `dplyr` 总结数据，不如使用 `ggplot2` 来可视化这些信息：

```
library(ggplot2)
eval %>%
 group_by(class) %>%
 summarise(avg_error=mean(error)) %>%
 ggplot(aes(x=class, fill=class, y=avg_error)) + geom_col()
```

如下所示，我们可以看到每个类别的重构错误情况。这一点很重要，因为它可以让我们知道我们的分类器是否在某种程度上存在偏见，或者是否觉得某些类别比其他类别更难训练：

![](img/da8fb67f2acf661518076e08b6ffd9b9_120_0.png)

MNIST 数据集中的重构错误。2 和 8 似乎是最有问题的类别，而 1 似乎是最容易识别的。

嗯，这当然很有用，也很有趣，我们可以看到 2 重构起来有些困难，这可能是因为它有时看起来像 7。直觉上，8 很容易与 9 或 0 混淆，所以结果在某种程度上是合理的。

查看我们重构自编码器性能的更好方法是直接查看重构示例。为此，我们需要首先将原始数据和重构结果重塑回原始形状：

```
# Reshape original and reconstructed
dim(X_test) <- c(nrow(X_test),28,28)
dim(preds) <- c(nrow(preds),28,28)
```

现在让我们看看重构后的图像：

```
image(255*preds[1,,], col=gray.colors(3))
```

让我们看看测试集中典型元素的重构图像：

![](img/da8fb67f2acf661518076e08b6ffd9b9_121_0.png)

我们的自编码器重构的图像。

它与重构前的原始图像相比如何？让我们看看：

```
y_test[1]
image(255*X_test[1,,], col=gray.colors(3) )
```

![](img/da8fb67f2acf661518076e08b6ffd9b9_121_1.png)

原始图像。

总体而言，24.5 的压缩比表现不差！显然还有很多可以改进的地方，但我们已经可以看到自编码器学习数据内在特征的潜力。

## MNIST 中的异常值检测

好吧，诚然，我们之前的应用程序至今与欺诈或异常值检测无关。我们可以对之前的设置进行一些小修改，以展示类似的框架是如何工作的。为此，让我们假设数字 7 是一个异常类，并尝试从我们的正常数字（0、1、2、3、4、5、6、8、9）的结果中识别它。

我们将在正常数据集上训练自编码器，然后将其应用于测试集。目标是尽可能抽象正常情况下的尽可能多的特征。这需要了解正常情况，这意味着需要有标记数据可用，因此，对于许多实际应用（例如信用卡欺诈或入侵检测）来说，这是一个理想场景，我们有时（或者更确切地说，是经常）缺乏此类标记数据。
