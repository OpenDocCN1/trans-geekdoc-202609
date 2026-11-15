
我们可以使用以下代码片段来检查算法的性能：

```r
library(ggplot2)
preds <- variational_autoencoder %>% predict(X_test)
error <- rowSums((preds-X_test)**2)
eval <- data.frame(error=error, class=as.factor(y_test))
eval %>%
  group_by(class) %>%
  summarise(avg_error=mean(error)) %>%
  ggplot(aes(x=class, fill=class, y=avg_error))+geom_col()
```

结果如下所示：

![](img/da8fb67f2acf661518076e08b6ffd9b9_140_0.png)

重构错误看起来相当令人沮丧，因为使用自动编码器显然效果更好。我们如何改进这一点？一种方法是提高隐空间的维度。在当前设置中，我们的隐空间仅为二维。然而，请注意，在质量方面并没有太大损失：

![](img/da8fb67f2acf661518076e08b6ffd9b9_140_1.png)

![](img/da8fb67f2acf661518076e08b6ffd9b9_141_0.png)

左侧为我们的 VAE 重构的图像，右侧为原始图像（屏幕上）。

此外，我们现在拥有一个生成过程！这意味着我们可以自己生成数字。让我们遍历隐空间并使用概率分布来生成自己的数字：

```
# Reshape original and reconstructed
dim(X_test) <- c(nrow(X_test),28,28)
dim(preds) <- c(nrow(preds),28,28)
image(255*preds[1,,], col=gray.colors(3))
y_test[1]
image(255*X_test[1,,], col=gray.colors(3))

grid_x <- seq(-4, 4, length.out = 3)
grid_y <- seq(-4, 4, length.out = 3)

rows <- NULL
for(i in 1:length(grid_x)){
  column <- NULL
  for(j in 1:length(grid_y)){
    z_sample <- matrix(c(grid_x[i], grid_y[j]), ncol = 2)
    column <- rbind(column, predict(generator, z_sample) %>% matrix(ncol = 28))
  }
  rows <- cbind(rows, column)
}
rows %>% as.raster() %>% plot()
```

让我们看看我们的 VAE 生成的一些数字：

![](img/da8fb67f2acf661518076e08b6ffd9b9_141_1.png)

由 VAE 生成的数字。

## MNIST 中的异常值检测

让我们再次探讨 MNIST 中的异常值检测问题。与之前一样，假设这次数字 0 是我们的异常值，并且我们希望能够检测它。

与之前一样，我们读取并预处理数据：

```
library(keras)
# Switch to the 1-based indexing from R
options(tensorflow.one_based_extract = FALSE)
K <- keras::backend()
mnist <- dataset_mnist()
X_train <- mnist$train$x
y_train <- mnist$train$y
X_test <- mnist$test$x
y_test <- mnist$test$y
# Exclude "0" from the training set. "0" will be the outlier
outlier_idxs <- which(y_train!=0, arr.ind = T)
X_train <- X_train[outlier_idxs,,]
y_test <- sapply(y_test, function(x) { ifelse(x==0,"outlier","normal") })
# reshape
dim(X_train) <- c(nrow(X_train), 784)
dim(X_test) <- c(nrow(X_test), 784)
# rescale
X_train <- X_train / 255
X_test <- X_test / 255
```

然后我们定义编码器结构。请注意，我们将使用一个不同的结构：128 维隐空间和中间层中 256 个神经元：

```
original_dim <- 784
latent_dim <- 2
intermediate_dim <- 256
X <- layer_input(shape = c(original_dim))
hidden_state <- layer_dense(X, intermediate_dim, activation = "relu")
z_mean <- layer_dense(hidden_state, latent_dim)
z_log_sigma <- layer_dense(hidden_state, latent_dim)
```

并重写我们的 sample_z 函数以使其更易于自定义：

```
sample_z <- function(params) {
z_mean <- params[, 0:1]
z_log_sigma <- params[, 2:3]
epsilon <- K$random_normal(
shape = c(K$shape(z_mean)[[1]]),
mean=0.,
stddev=1
)
z_mean + K$exp(z_log_sigma/2)*epsilon
}
```

### 然后是解码器部分：

```
z <- layer_concatenate(list(z_mean, z_log_sigma)) %>%
layer_lambda(sample_z)
decoder_hidden_state <- layer_dense(units = intermediate_dim, activation = "relu")
decoder_mean <- layer_dense(units = original_dim, activation = "sigmoid")
hidden_state_decoded <- decoder_hidden_state(z)
X_decoded_mean <- decoder_mean(hidden_state_decoded)
```

### 最后，完整的自动编码器：

```
variational_autoencoder <- keras_model(X, X_decoded_mean)
encoder <- keras_model(X, z_mean)
decoder_input <- layer_input(shape = latent_dim)
decoded_hidden_state_2 <- decoder_hidden_state(decoder_input)
decoded_X_mean_2 <- decoder_mean(decoded_hidden_state_2)
generator <- keras_model(decoder_input, decoded_X_mean_2)
```

### 我们使用以下定义损失函数：

```
loss_function <- function(X, decoded_X_mean) {
cross_entropy_loss <- loss_binary_crossentropy(X, decoded_X_mean)
kl_loss <- -0.5*K$mean(1 + z_log_sigma - K$square(z_mean) -
K$exp(z_log_sigma), axis = -1L)
cross_entropy_loss + kl_loss
}
```

### 我们使用与之前相同的函数来训练模型：

```
variational_autoencoder %>% compile(optimizer = "rmsprop", loss = loss_function)
history <- variational_autoencoder %>% fit(
X_train, X_train,
shuffle = TRUE,
epochs = 10,
batch_size = 256,
validation_data = list(X_test, X_test)
)
plot(history)
```

训练完成后，我们来看看性能：

```
preds <- variational_autoencoder %>% predict(X_test)
error <- rowSums( (preds-X_test)**2 )
eval <- data.frame(error=error, class=as.factor( y_test ) )
library(dplyr)
library(ggplot2)
eval %>%
ggplot( aes(x=class, fill=class, y=error) )+geom_boxplot()
```

让我们看看每个类的重构错误：

![](img/da8fb67f2acf661518076e08b6ffd9b9_144_0.png)

使用 VAE 的重构错误。

该图表明将重构错误阈值设为 5：

```
threshold <- 5
y_preds <- sapply(error,
function(x) (ifelse(x>threshold, "outlier","normal") ))
```

现在我们来看混淆矩阵：

| y_preds | normal | outlier |
|---|---|---|
| outlier | 9020 | 980 |

这表明我们走在正确的道路上！但在庆祝之前，我们还应该查看其他分类指标，即 ROC 曲线以及该曲线下的面积 (AUC)：

```
library(ROCR)
pred <- prediction(error, y_test)
perf <- performance(pred, measure = "tpr", x.measure = "fpr")
auc <- unlist(performance(pred, measure = "auc")@y.values)
plot(perf, col=rainbow(10))
```

我们得到的 AUC 为 0.8473375，下面显示了一个合理的 ROC 曲线，这表明我们的 VAE 在区分异常值 0 方面做得很好。

请注意，这比数字 7 为异常值时的效果好得多。这告诉我们，当异常观测与常规观测过于相似时，我们需要付出额外的努力：

![](img/da8fb67f2acf661518076e08b6ffd9b9_145_0.png)

## 文本欺诈检测

欺诈已成为超越传统交易欺诈的问题。例如，许多网站依赖于用户对餐馆、酒店或旅游景点等服务的评论，这些评论以不同方式变现。如果用户对这些评论失去信任，例如，商家故意操纵自己业务的好评，那么该网站将难以重获信任并保持盈利。因此，检测此类潜在问题非常重要。

自动编码器如何帮助我们解决这个问题？与之前一样，其思路是学习网站上*正常*评论的表示，然后找出不符合*正常*评论的那些评论。文本数据的问题在于在之前需要进行一些处理。我们将通过一个示例来说明这一点，这也将作为下一章中将讨论的不同文本建模方式的动机。

## 从非结构化文本数据到矩阵

文本数据的一个问题是单词和句子很混乱，数据挖掘算法通常不能开箱即用，因为它们旨在对数据的抽象（通常以矩阵形式）进行操作。因此，我们需要找到一种方法将混乱的文本数据表示为矩阵。

在实践中，最常用的矩阵表示之一是*词袋*模型。这是一种从文本中提取信息的非常简单直观的方法。它有一些注意事项，将在后面讨论。

文本的词袋表示包括：

- 已知单词的词汇表
- 与这些单词出现相关的数值度量

例如，假设我们有一个由三个句子组成的*语料库*（文档集合）：

- "我的句子"
- "你的句子"
- "我的句子，你的句子，我们的句子"

词汇表（忽略逗号）是以下单词的集合
(`"My"`, `"sentence"`, `"sentences"`, `"Your"`, `"your"`, `"our"`)。至于数值度量，一个自然的选择是*计数*函数。因此，矩阵表示如下：

| My | Your | sentence | sentences | your | our |
|---|---|---|---|---|---|
| 1 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 |
| 1 | 0 | 2 | 1 | 1 | 1 |
