

按类别分布情况如何？下图告诉我们一些情况：

![](img/da8fb67f2acf661518076e08b6ffd9b9_128_0.png)

对数据的首个洞察：欺诈交易涉及的金额似乎更可能在100左右，而非欺诈交易则不然。

啊哈！这样我们就获得了对数据的第一个洞察！欺诈交易虽然金额较小，但异常地集中在100左右。这可能是欺诈者策略的一部分，他们不是在固定时间进行大额交易，而是将小额交易或多或少均匀地分布在时间中。

当然，发现这一点很有趣，但这绝对不是一种可扩展的方法，需要领域知识和直觉。是时候尝试更复杂的方法了。

## 自动编码器方法 – Keras

好了，是时候进入Keras了。我们应该留出一小部分数据用作验证集或测试集，并在剩余数据上开发模型。关于如何做，没有黄金标准。在本示例中，我们将使用10%的测试集和90%的训练集：

```r
# Remove the time and class column
idxs <- sample(nrow(df), size=0.1*nrow(df))
train <- df[-idxs,]
test <- df[idxs,]
y_train <- train$Class
y_test <- test$Class
X_train <- train %>% select (-one_of(c("Time", "Class")))
X_test <- test %>% select (-one_of(c("Time", "Class")))
# Coerce the data frame to matrix to perform the training
X_train <- as.matrix(X_train)
X_test <- as.matrix(X_test)
```

请注意，我们还排除了`Class`和`Time`列。我们忽略标签，将欺诈检测问题视为无监督学习问题，因此需要从训练数据中删除标签列。至于时间信息，如前所述，似乎没有明显的时间趋势。而且，在实际的欺诈检测场景中，我们更关心欺诈者的内在属性，例如使用的设备、地理位置信息或CRM系统的数据，以及账户属性（余额、平均交易量等）。

对于自动编码器的架构，与之前使用一个中间层不同，我们现在将使用**堆叠自动编码器**。堆叠自动编码器只不过是几层编码器，后跟几层解码器。在此例中，我们将使用外部编码器-解码器层包含14个全连接神经元、两个内部层各7个神经元，以及另一个内部层7个神经元的网络。您可以尝试不同的架构并将结果与我们比较，自动编码器没有普遍正确的架构，它仅依赖于经验以及通过验证图和其他指标诊断您的模型。

输入（和输出）维度在两种情况下均为29。构建自动编码器的代码如下：

```r
library(keras)
input_dim <- 29
outer_layer_dim <- 14
inner_layer_dim <- 7
input_layer <- layer_input(shape=c(input_dim))
encoder <- layer_dense(units=outer_layer_dim,
activation='relu')(input_layer)
encoder <- layer_dense(units=inner_layer_dim, activation='relu')(encoder)
decoder <- layer_dense(units=inner_layer_dim)(encoder)
decoder <- layer_dense(units=outer_layer_dim)(decoder)
decoder <- layer_dense(units=input_dim)(decoder)
autoencoder <- keras_model(inputs=input_layer, outputs = decoder)
```

我们可以查看我们的工作以检查一切是否正确：

| 层（类型） | 输出形状 | 参数数量 |
|---|---|---|
| input_5 (InputLayer) | (None, 29) | 0 |
| dense_17 (Dense) | (None, 14) | 420 |
| dense_18 (Dense) | (None, 7) | 105 |
| dense_22 (Dense) | (None, 7) | 56 |
| dense_23 (Dense) | (None, 7) | 56 |
| dense_24 (Dense) | (None, 14) | 112 |
| dense_25 (Dense) | (None, 29) | 435 |
| 总参数数：1,184 | | |
| 可训练参数数：1,184 | | |
| 不可训练参数数：0 | | |

现在我们准备开始训练。应该先编译模型，然后拟合它：

```r
autoencoder %>% compile(optimizer='adam',
                   loss='mean_squared_error',
                   metrics=('accuracy'))

history <- autoencoder %>% fit(
X_train,X_train,
epochs = 10, batch_size = 32,
validation_split=0.2
)

plot(history)
```

我们的结果如下所示。您可以看到，随着epoch数量的增加，准确率有所提高：

![](img/da8fb67f2acf661518076e08b6ffd9b9_131_0.png)

我们14-7-7-7-14架构的诊断图。

一旦自动编码器准备就绪，我们就用它来重构测试集：

```r
# Reconstruct on the test set
preds <- autoencoder %>% predict(X_test)
preds <- as.data.frame(preds)
```

我们将像之前一样，寻找异常大的重构错误，以将其标记为异常。例如，我们可以查看重构错误大于30的点，并将其声明为异常：

```r
y_preds <- ifelse(rowSums( (preds-X_test) **2 )/30<1,rowSums( (preds-X_test)**2 )/30,1)
```

同样，这个阈值不是一成不变的，在您特定的应用中使用测试集，您可以对其进行微调，并为您的问题找到最合适的阈值。

最后，让我们使用以下代码生成ROC曲线，以查看我们的模型是否正确运行：

```r
library(ROCR)
pred <- prediction(y_preds, y_test)
perf <- performance(pred, measure = "tpr", x.measure = "fpr")
plot(perf, col=rainbow(10))
```

我们看到结果令人满意。我们的曲线看起来相当笔直，原因是我们的模型输出只是二进制，原始标签也是如此。当您的模型输入类概率或其代理时，曲线会更平滑：

![](img/da8fb67f2acf661518076e08b6ffd9b9_132_0.png)

ROC曲线：由于模型输出不是类概率，而是二进制值，曲线看起来相当笔直。

## 使用H2O进行欺诈检测

让我们尝试一个略有不同的工具，它可能对实际部署有所帮助。在不断发展的数据科学领域，尝试不同的工具通常很有用，哪怕只是为了进行合理性检查。

H2O是一个用于大数据分析的开源软件。这家成立于2016年的年轻初创公司，其顾问委员会拥有数学优化和统计学习理论领域的顶尖研究人员。它在标准环境（Linux/Mac/Windows）以及大数据系统和云计算环境中运行。

您可以在R中运行H2O，但首先需要安装该包：

```r
install.packages("h2o")
```

完成后，您可以加载该库：

```r
library(h2o)
```

然后您会看到一条欢迎消息，其中包含一些警告（来自其他包的被遮蔽对象）：

```
Your next step is to start H2O:
> h2o.init()
For H2O package documentation, ask for help:
> ??h2o
After starting H2O, you can use the Web UI at http://localhost:54321
For more information visit http://docs.h2o.ai
```

那么让我们这样做，然后我们就可以开始工作了：

```r
h2o.init()
```

现在我们需要将数据读入H2O。由于计算方式略有不同，我们无法使用R中的原生数据帧结构，因此要么像往常一样读取文件然后强制转换：

```r
df <- read.csv("../data/creditcard.csv", stringsAsFactors = F)
df <- as.h2o(df)
```

或者使用h2o.uploadFile函数读取：

```r
df2 <- h2o.uploadFile("../data/creditcard.csv")
```

无论哪种方式，生成的结构类型不再是数据帧，而是一个环境。

通常，我们留出一部分数据用于训练，另一部分用于测试。在h2o中，我们可以使用h2o.splitFrame函数：

```r
splits <- h2o.splitFrame(df, ratios=c(0.8), seed=1)
train <- splits[[1]]
test <- splits[[2]]
```

现在让我们区分特征和标签，这将在片刻后很有用：

```r
label <- "Class"
features <- setdiff(colnames(train), label)
```

我们已准备好开始自动编码器的训练：

```r
autoencoder <- h2o.deeplearning(x=features,
training_frame = train,
autoencoder = TRUE,
seed = 1,
hidden=c(10,2,10),
epochs = 10,
activation = "Tanh")
```

