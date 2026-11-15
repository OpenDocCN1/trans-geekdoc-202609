
此处有一些说明。自动编码器参数已设置为 true，正如您所料。这次我们将使用略有不同的架构，仅供说明之用。您可以在 hidden 参数中看到各层的结构。我们还将使用不同的激活函数。在实践中，有时使用有界激活函数很有用，例如使用 tanh 而非 ReLu，因为 ReLu 在数值上可能不稳定。

我们可以以与使用 keras 时类似的方式生成重构：

```
# Use the predict function as before
preds <- h2o.predict(autoencoder, test)
```

我们得到如下内容：

```
> head(preds)
reconstr_Time reconstr_V1 reconstr_V2 reconstr_V3 reconstr_V4 reconstr_V5
reconstr_V6 reconstr_V7
1 380.1466 -0.3041237 0.2373746 1.617792 0.1876353 -0.7355559 0.3570959
-0.1331038
2 1446.0211 -0.2568674 0.2218221 1.581772 0.2254702 -0.6452812 0.4204379
-0.1337738
3 1912.0357 -0.2589679 0.2212748 1.578886 0.2171786 -0.6604871 0.4070894
-0.1352975
4 1134.1723 -0.3319681 0.2431342 1.626862 0.1473913 -0.8192215 0.2911475
-0.1369512
5 1123.6757 -0.3194054 0.2397288 1.619868 0.1612631 -0.7887480 0.3140728
-0.1362253
6 1004.4545 -0.3589335 0.2508191 1.643208 0.1196120 -0.8811920 0.2451117
-0.1380364
```

从这一点开始，我们可以按之前的方式继续。但是，h2o 内置了 h2o.anomaly 函数，可简化我们工作的部分内容。

我们可以做的另一种简化是，不再分别导入 ggplot2 和 dplyr，而是导入 tidyverse 包，它将这些（以及其他）有助于数据处理的包带入我们的环境：

```
library(tidyverse)
anomaly <- h2o.anomaly(autoencoder, test) %>%
as.data.frame() %>%
tibble::rownames_to_column() %>%
mutate(Class = as.vector(test[, 31]))
```

### 让我们计算平均均方误差：

```
# Type coercion useful for plotting later
anomaly$Class <- as.factor(anomaly$Class)
mean_mse <- anomaly %>%
  group_by(Class) %>%
  summarise(mean = mean(Reconstruction.MSE))
```

### 最后，根据重构错误可视化我们的测试数据：

```
anomaly$Class <- as.factor(anomaly$Class)
mean_mse <- anomaly %>%
  group_by(Class) %>%
  summarise(mean = mean(Reconstruction.MSE))
```

我们可以看到，自动编码器的工作还算不错。相当比例的欺诈案例具有相对较高的重构错误，尽管远非完美。你如何改进它：

![](img/da8fb67f2acf661518076e08b6ffd9b9_135_0.png)

使用 H2O 的我们的架构的结果表明，自动编码器在标记欺诈案例方面做得不错，但仍可改进。

## 练习

- 在我们的信用卡欺诈示例中，我们使用了欺诈和非欺诈案例的混合。在这种情况下，我们很幸运地拥有每个案例的正确标签。因此，在这种情况下，只对正常交易进行重构可能更有意义。如果仅使用非欺诈案例，检测率是否会提高？运行相同的实验，但仅使用非欺诈案例作为训练集。

- 使用信用卡数据集，将自动编码器的重构作为分类模型的输入，方式与使用 PCA 类似。这是否提高了分类的准确性？请注意，您可以在这个特定数据集上这样做，因为您拥有交易类别（欺诈/非欺诈）的信息，而其他数据中可能没有此信息。

## 变分自编码器

**变分自编码器**（VAE）是对自动编码问题的一种较新方法。与学习数据压缩表示的自动编码器不同，变分自编码器学习生成此类数据的随机过程，而不是像我们之前使用神经网络所做的那样，学习一个基本上是任意的函数。

VAE 也具有编码器和解码器部分。编码器学习假设生成数据的正态分布的均值和标准差。均值和标准差称为**潜在变量**，因为它们不是被显式观察到的，而是从数据中推断出来的。

VAE 的解码器部分将这些潜在空间点映射回数据。与之前一样，我们需要一个损失函数来衡量原始输入及其重构之间的差异。有时会添加一个额外项，称为**Kullback-Leibler 散度**，或简称为 KL 散度。KL 散度大致计算一个概率分布与另一个分布的差异。添加 KL 散度，强制后验分布与先验分布相似。这反过来又有助于既学习数据的更好表示，又减少过拟合。

与自动编码器不同，VAE 具有坚实的概率基础，因此您得到的分数确实是观测值为异常值的概率。在自动编码器中，我们得到的分数没有这种解释，因此截止值或阈值的选择完全依赖于人类专家的输入，并且严格取决于特定数据。

### 使用 VAE 进行图像重构

我们的第一个示例将使用 MNIST 数据来说明变分自编码器的使用。

开发策略如下：

- 首先，编码器网络将输入样本 x 转换为潜在空间中的两个参数，将其表示为 z_mean 和 z_log_sigma
- 然后，我们从假设用于生成数据的潜在正态分布中随机采样类似点 z，其中 z ~ z_mean + exp(z_log_sigma)*epsilon，epsilon 是一个随机正态张量
- 完成此操作后，解码器网络将这些潜在空间点 z 映射回原始输入数据

我们像往常一样，获取并预处理数据：

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
# reshape
dim(X_train) <- c(nrow(X_train), 784)
dim(X_test) <- c(nrow(X_test), 784)
# rescale
X_train <- X_train / 255
X_test <- X_test / 255
```

请注意附加行：

```
K <- keras::backend()
```

这使我们获得对张量后端的引用，Keras 将在其中执行张量操作。

现在我们来构建 VAE。它将包含大小为 2 的潜在维度和一个含 256 个神经元的隐藏层：

```
orig_dim <- 784
latent_dim <- 2
inner_dim <- 256
X <- layer_input(shape = c(original_dim))
hidden_state <- layer_dense(X, intermediate_dim, activation = "relu")
z_mean <- layer_dense(hidden_state, latent_dim)
z_log_sigma <- layer_dense(hidden_state, latent_dim)
```

接下来，借助 Keras 后端，我们定义将从潜在变量生成数据的采样函数：

```
sample_z<- function(params) {
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

我们现在定义采样点：

```
z <- layer_concatenate(list(z_mean, z_log_sigma)) %>%>
layer_lambda(sample_z)
```

是时候定义解码器了。我们创建这些层的独立实例，以便以后重复使用：

```
decoder_hidden_state <- layer_dense(units = intermediate_dim, activation =
"relu")
decoder_mean <- layer_dense(units = original_dim, activation = "sigmoid")
hidden_state_decoded <- decoder_hidden_state(z)
X_decoded_mean <- decoder_mean(hidden_state_decoded)
```

准备就绪！我们的 VAE 由以下编码器和解码器组件指定：

```
# end-to-end autoencoder
variational_autoencoder <- keras_model(X, X_decoded_mean)
encoder <- keras_model(X, z_mean)
decoder_input <- layer_input(shape = latent_dim)
```

```
decoded_hidden_state_2 <- decoder_hidden_state(decoder_input)
decoded_X_mean_2 <- decoder_mean(decoded_hidden_state_2)
generator <- keras_model(decoder_input, decoded_X_mean_2)
```

剩下的就是指定自定义损失函数，因为我们正在添加 KL 散度惩罚：

```
loss_function <- function(X, decoded_X_mean) {
  cross_entropy_loss <- loss_binary_crossentropy(X, decoded_X_mean)
  kl_loss <- -0.5*K$mean(1 + z_log_sigma - K$square(z_mean) -
  K$exp(z_log_sigma), axis = -1l)
  cross_entropy_loss + kl_loss
}
```

像往常一样，我们编译并运行算法：

```
variational_autoencoder %>% compile(optimizer = "rmsprop", loss =
loss_function)
history <- variational_autoencoder %>% fit(
  X_train, X_train,
  shuffle = TRUE,
  epochs = 10,
  batch_size = 256,
  validation_data = list(X_test, X_test)
)
plot(history)
```

训练完成后，我们可以查看性能（或使用 RStudio 中的 Viewer 实时跟踪）：

![](img/da8fb67f2acf661518076e08b6ffd9b9_139_0.png)

我们的 VAE 在 MNIST 数据上的重构性能。
