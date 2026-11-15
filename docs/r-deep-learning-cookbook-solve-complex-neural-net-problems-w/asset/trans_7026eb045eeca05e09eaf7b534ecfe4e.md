
- 用于初始化权重和偏置的选项，连同权重分布和缩放。
- 基于分类中的误差分数和回归中均方误差的停止条件（classification_stop 和 regression_stop）。还可选择执行早期停止。
- 用于通过弹性平均法提高分布式模型收敛性的选项，参数包括移动率和正则化强度。

## 工作原理...

模型性能可以使用许多指标来评估，例如准确率、AUC、误分类率（%）、误分类计数、F1 分数、精确率、召回率、特异度等。但是，在本章中，模型性能的评估基于 AUC。

以下是已训练模型的训练准确率和交叉验证准确率。训练和交叉验证 AUC 分别为 0.984 和 0.982：

```
# Get the training accuracy (AUC)
> train_performance <- h2o.performance(occupancy.deepmodel,train = T)
> train_performance@metrics$AUC
[1] 0.9848667
```

```
# Get the cross-validation accuracy (AUC)
> xval_performance <- h2o.performance(occupancy.deepmodel,xval = T)
> xval_performance@metrics$AUC
[1] 0.9821723
```

由于我们已在模型中提供测试数据（作为验证数据集），以下是其性能。测试数据上的 AUC 为 0.991。

```
# Get the testing accuracy (AUC)
> test_performance <- h2o.performance(occupancy.deepmodel,valid = T)
> test_performance@metrics$AUC
[1] 0.9905056
```

## 在 H2O 中使用网格搜索调整超参数

H2O 包还允许您使用网格搜索（h2o.grid）进行超参数调整。

### 准备工作

我们首先使用以下代码加载并初始化 H2O 包：

```
# Load the required packages
require(h2o)

# Initialize H2O instance (single node)
localH2O = h2o.init(ip = "localhost", port = 54321, startH2O = TRUE, min_mem_size = "20G", nthreads = 8)
```

占用率数据集已加载，转换为十六进制格式，并命名为 occupancy_train.hex。

### 操作方法...

本节将重点介绍如何在 H2O 中使用网格搜索优化超参数。

- 1. 在我们的案例中，我们将优化激活函数、隐藏层数量（连同每层的神经元数量）、时代（epochs）以及正则化 lambda（l1 和 l2）：

```
# Perform hyper parameter tuning
activation_opt <- c("Rectifier","RectifierWithDropout",
"Maxout","MaxoutWithDropout")
hidden_opt <- list(5, c(5,5))
epoch_opt <- c(10,50,100)
l1_opt <- c(0,1e-3,1e-4)
l2_opt <- c(0,1e-3,1e-4)

hyper_params <- list(activation = activation_opt,
    hidden = hidden_opt,
    epochs = epoch_opt,
    l1 = l1_opt,
    l2 = l2_opt)
```

- 2. 以下搜索条件已设置以执行网格搜索。在上述列表之外，还可以指定停止指标的类型、停止的最小容差以及停止的最大轮数：

```
#set search criteria
search_criteria <- list(strategy = "RandomDiscrete", max_models=300)
```

- 3. 现在，让我们按以下方式对训练数据执行网格搜索：

```
# Perform grid search on training data
dl_grid <- h2o.grid(x = x,
 y = y,
 algorithm = "deeplearning",
 grid_id = "deep_learn",
 hyper_params = hyper_params,
 search_criteria = search_criteria,
 training_frame = occupancy_train.hex,
 nfolds = 5)
```

- 4. 网格搜索完成后（此处共有 216 个不同模型），可以根据多个指标（如 logloss、残差偏差、均方误差、AUC、准确率、精确率、召回率、f1 等）选择最佳模型。在我们的场景中，让我们选择 AUC 最高的最佳模型：

```
#Select best model based on auc
d_grid <- h2o.getGrid("deep_learn", sort_by = "auc", decreasing = T)
best_dl_model <- h2o.getModel(d_grid@model_ids[[1]])
```

## 工作原理...

以下是网格搜索模型在训练数据集和交叉验证数据集上的性能。我们可以观察到，在执行网格搜索后，训练和交叉验证场景中的 AUC 均提高了一个单位。网格搜索后的训练和交叉验证 AUC 分别为 0.996 和 0.997。

```
# Performance on Training data after grid search
> train_performance.grid <- h2o.performance(best_dl_model, train = T)
> train_performance.grid@metrics$AUC
[1] 0.9965881
```

```
# Performance on Cross validation data after grid search
> xval_performance.grid <- h2o.performance(best_dl_model, xval = T)
> xval_performance.grid@metrics$AUC
[1] 0.9979131
```

现在，让我们评估最佳网格搜索模型在测试数据集上的性能。我们可以观察到，执行网格搜索后，AUC 提高了 0.25 个单位。测试数据上的 AUC 为 0.993。

```
# Predict the outcome on test dataset
yhat <- h2o.predict(best_dl_model, occupancy_test.hex)
```

```
# Performance of the best grid-searched model on the Test dataset
> yhat$pmax <- pmax(yhat$p0, yhat$p1, na.rm = TRUE)
> roc_obj <- pROC::roc(c(as.matrix(occupancy_test.hex$Occupancy)),
c(as.matrix(yhat$pmax)))
> pROC::auc(roc_obj)
Area under the curve: 0.9932
```

## 使用 MXNet 搭建神经网络

上一章详细介绍了在 R 中安装 MXNet 以及使用其 Web 界面的工作示例。要开始建模，请在 R 环境中加载 MXNet 包。

### 准备工作

加载所需的包：

```
# Load the required packages
require(mxnet)
```

### 操作方法...

- 1. 在 R 中加载占用率训练数据集和测试数据集：

```
# Load the occupancy data
occupancy_train <-
read.csv("C:/occupation_detection/datatraining.txt", stringsAsFactors = T)
occupancy_test <-
read.csv("C:/occupation_detection/datatest.txt", stringsAsFactors = T)
```

- 2. 将使用以下自变量（x）和因变量（y）来建模 GLM：

```
# Define input (x) and output (y) variables
x = c("Temperature", "Humidity", "Light", "CO2", "HumidityRatio")
y = "Occupancy"
```

- 3. 根据 MXNet 的要求，将训练数据集和测试数据集转换为矩阵，并确保结果变量的类为数值型（而不是 H2O 中的因子型）：

```
# convert the train data into matrix
occupancy_train.x <- data.matrix(occupancy_train[, x])
occupancy_train.y <- occupancy_train$Occupancy

# convert the test data into matrix
occupancy_test.x <- data.matrix(occupancy_test[, x])
occupancy_test.y <- occupancy_test$Occupancy
```

- 4. 现在，让我们手动配置神经网络。首先，配置一个带特定名称的符号变量。然后，配置一个符号全连接网络，包含单个隐藏层中的五个神经元，随后接带 logit 损失（或交叉熵损失）的 softmax 激活函数。还可以创建带不同激活函数的其他（全连接）隐藏层。

```
# Configure Neural Network structure
smb.data <- mx.symbol.Variable("data")
smb.fc <- mx.symbol.FullyConnected(smb.data, num_hidden=5)
smb.soft <- mx.symbol.SoftmaxOutput(smb.fc)
```

- 5. 神经网络配置完成后，让我们使用 mx.model.FeedForward.create 函数创建（或训练）（前馈）神经网络模型。该模型针对迭代次数或时代数（100）、评估指标（分类准确率）、每次迭代或时代的大小（100 个观测值）以及学习率（0.01）等参数进行了精细调整：

```
# Train the network
model.nn <- mx.model.FeedForward.create(symbol = smb.soft,
                                   X = occupancy_train.x,
                                   y = occupancy_train.y,
                                   ctx = mx.cpu(),
                                   num.round = 100,
                                   eval.metric = mx.metric.accuracy,
                                   array.batch.size = 100,
                                   learning.rate = 0.01)
```

## 工作原理...

现在，让我们评估模型在训练数据集和测试数据集上的性能。训练数据上的 AUC 为 0.978，测试数据上的 AUC 为 0.982：

```
# Train accuracy (AUC)
> train_pred <- predict(model.nn, occupancy_train.x)
> train_yhat <- max.col(t(train_pred))-1
> roc_obj <- pROC::roc(c(occupancy_train.y), c(train_yhat))
> pROC::auc(roc_obj)
Area under the curve: 0.9786
```

```
# Test accuracy (AUC)
> test_pred <- predict(model.nn, occupancy_test.x)
> test_yhat <- max.col(t(test_pred))-1
> roc_obj <- pROC::roc(c(occupancy_test.y), c(test_yhat))
> pROC::auc(roc_obj)
Area under the curve: 0.9824
```

## 使用 TensorFlow 搭建神经网络

本节将介绍在搭建两层神经网络模型中 TensorFlow 的应用。

### 准备工作

要开始建模，请在环境中加载 tensorflow 包。R 会加载默认的 tf 环境变量，还会在 np 变量中加载 Python 的 NumPy 库：

```
library("tensorflow") # Load Tensorflow
np <- import("numpy") # Load numpy library
```
