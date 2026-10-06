
# R 语言机器学习算法演示

## 朴素贝叶斯分类器

```r
# Load the e1071 package, which contains a function for creating and using a naive Bayes classifier
library(e1071)

# Create some synthetic data for illustration purposes
# The data has two features (x and y) and two classes (A and B)
set.seed(123) # Set the random seed for reproducibility
n <- 100 # Number of instances
x <- rnorm(n) # Generate random values for x from a normal distribution
y <- rnorm(n) # Generate random values for y from a normal distribution
class <- sample(c("A", "B"), n, replace = TRUE) # Assign random class labels to each instance
data <- data.frame(x, y, class) # Create a data frame with the features and the class

# Plot the data to visualize the distribution of the classes and the features
plot(data$x, data$y, col = data$class, pch = 19, xlab = "x", ylab = "y")
legend("topleft", legend = c("A", "B"), col = c("black", "red"), pch = 19)

# Split the data into training and testing sets
train_index <- sample(1:n, 0.8 * n) # Randomly select 80% of the instances for training
train_data <- data[train_index, ] # Subset the data frame for training
test_data <- data[-train_index, ] # Subset the data frame for testing

# Create a naive Bayes classifier using the training data
model <- naiveBayes(class ~ x + y, data = train_data)

# Print the model to see the estimated prior probabilities and the conditional probabilities of each feature given each class
print(model)

# Predict the class labels for the testing data using the model
pred <- predict(model, test_data)

# Compare the predicted labels with the actual labels to evaluate the accuracy of the model
table(pred, test_data$class)

# Compute the accuracy as the proportion of correct predictions
accuracy <- sum(pred == test_data$class) / length(test_data$class)
cat("The accuracy of the model is", accuracy, "\n")

# Create a new instance with some arbitrary values for x and y
new_instance <- data.frame(x = 0.5, y = -0.5)

# Predict the class label for the new instance using the model
pred_new <- predict(model, new_instance)
cat("The predicted class for the new instance is", pred_new, "\n")

# Compute the posterior probabilities for each class given the new instance using the model
posterior <- predict(model, new_instance, type = "raw")
cat("The posterior probabilities for each class are", posterior, "\n")
```

## 13.32.9 R 程序演示 KNN 分类器

这是一个演示 KNN 分类器机器学习算法的 R 程序。`k` 参数可通过交叉验证或其他方法选择。距离度量可以是欧几里得、曼哈顿、闵可夫斯基或其他用户自定义函数。

```r
# Load the required packages
library(class)
library(ggplot2)

# Generate some sample data for two classes
set.seed(123) # Set the random seed for reproducibility
x1 <- rnorm(50, mean = 0, sd = 1) # Generate 50 random numbers from a normal distribution with mean 0 and sd 1
y1 <- rnorm(50, mean = 0, sd = 1) # Generate 50 random numbers from a normal distribution with mean 0 and sd 1
x2 <- rnorm(50, mean = 3, sd = 1) # Generate 50 random numbers from a normal distribution with mean 3 and sd 1
y2 <- rnorm(50, mean = 3, sd = 1) # Generate 50 random numbers from a normal distribution with mean 3 and sd 1
class <- c(rep("A", 50), rep("B", 50)) # Assign the class labels A and B to the data points
data <- data.frame(x = c(x1, x2), y = c(y1, y2), class = class) # Combine the data into a data frame

# Plot the data using ggplot2
ggplot(data, aes(x = x, y = y, color = class)) + geom_point() + ggtitle("Sample data")

# Split the data into training and testing sets
train_index <- sample(1:100, size = 80) # Randomly select 80 indices for the training set
train_data <- data[train_index, ] # Subset the data frame by the training indices
test_data <- data[-train_index, ] # Subset the data frame by the testing indices

# Apply the k-NN classifier to the test data using k = 5 and Euclidean distance
pred_class <- knn(train = train_data[, c("x", "y")], test = test_data[, c("x", "y")], cl = train_data$class, k = 5)

# Compare the predicted class with the true class
table(pred_class, test_data$class)

# Calculate the accuracy of the classifier
accuracy <- sum(pred_class == test_data$class) / length(test_data$class)
accuracy

# Plot the test data with the predicted class
ggplot(test_data, aes(x = x, y = y, color = pred_class)) + geom_point() + ggtitle("Test data with predicted class")
```

## 13.32.10 ggplot2 简介

`ggplot2` 是一个基于图形语法声明式创建图形的系统。它是 R 编程语言中的一个包，使你能够使用一致且连贯的语法创建数据可视化。你可以用它创建简单的散点图、条形图和线图等数据可视化，以及更高级和复杂的数据可视化，如详细地图。

`ggplot2` 的目的是提供一个用于创建图形的框架，这些图形具有表现力、优雅且易于修改。它遵循图形语法原则，这是一组指定如何将数据映射到美学、使用哪些图形元素以及如何协调多个视图的规则。通过使用这种语法，你可以创建广泛的图形，以满足你的特定需求。

`ggplot2` 可用于机器学习中探索和理解数据，以及传达分析结果。例如，你可以使用 `ggplot2` 创建直方图、箱线图、散点图或密度图来检查变量的分布和关系。你还可以使用 `ggplot2` 创建热图、等高线图或曲面图来可视化复杂函数或模型。你还可以使用 `ggplot2` 通过 `plotly` 或 `shiny` 等包创建交互式图形。

## 13.32.11 使用 R 实现 PCA

下面是一个演示 PCA 机器学习的 R 语言程序。该程序对鸢尾花数据集执行 PCA，这是多元数据分析的常见示例。

该程序使用 `caret` 和 `ggplot2` 库执行 PCA、训练 KNN 分类器并可视化结果。该程序还使用混淆矩阵评估分类器的准确性。该程序表明 PCA 可以帮助根据花瓣和萼片的测量值分离不同类别的鸢尾花。

```r
# Load the required libraries
library(caret)
library(ggplot2)

# Load the iris data set
data(iris)

# Split the data into training and testing sets
set.seed(123)
trainIndex <- createDataPartition(iris$Species, p = 0.8, list = FALSE)
trainData <- iris[trainIndex, ]
testData <- iris[-trainIndex, ]
```

### 对数值特征执行 PCA

```r
preProc <- preProcess(trainData[, -5], method = "pca", thresh = 0.95)
trainPC <- predict(preProc, trainData[, -5])
testPC <- predict(preProc, testData[, -5])
```

### 将类别标签添加到 PCA 数据中

```r
trainPC$Species <- trainData$Species
testPC$Species <- testData$Species
```

### 在 PCA 数据上训练 k 近邻分类器

```r
knnFit <- train(Species ~., data = trainPC, method = "knn", tuneLength = 10)
```

### 在测试 PCA 数据上预测类别标签

```r
knnPred <- predict(knnFit, testPC)
```

### 评估分类器的准确率

```r
confusionMatrix(knnPred, testPC$Species)
```

### 绘制带有类别标签的 PCA 数据

```r
ggplot(trainPC, aes(PC1, PC2, color = Species)) +
  geom_point() +
  labs(title = "PCA of iris data")
```

## 13.32.12 使用 R 实现 LDA

LDA 通过找到能最大化类别间分离的特征线性组合来工作。在本示例中，我们将使用鸢尾花数据集。

### 加载所需的包

```r
library(MASS) # for lda function
library(ggplot2) # for plotting
```

### 加载鸢尾花数据集

```r
data(iris)
```

### 将数据拆分为训练集和测试集（分别为 80% 和 20%）

```r
set.seed(123) # for reproducibility
train_index <- sample(1:nrow(iris), 0.8 * nrow(iris))
train_data <- iris[train_index, ]
test_data <- iris[-train_index, ]
```

### 使用全部四个特征在训练数据上执行 LDA

```r
model <- lda(Species ~., data = train_data)
```

### 打印模型摘要

```r
print(model)
```

模型摘要显示每个类别的先验概率、每个特征的组均值以及线性判别式的系数。线性判别式的系数是用于将原始特征变换到能最大化类别分离的低维空间中的权重。在本例中，有两个线性判别式，因为我们有三个类别，而线性判别式的数量比类别数少一个。

### 绘制数据投影到前两个线性判别式上的图

```r
plot(model)
```

该图显示第一个线性判别式 `LD1` 将 setosa 与其他两个物种分开，而第二个线性判别式 `LD2` 将 versicolor 和 virginica 分开。该图还显示了每个类别的 95% 置信椭圆。

### 使用模型预测测试数据的类别标签

```r
pred <- predict(model, test_data)
```

### 打印混淆矩阵

```r
table(pred$class, test_data$Species)
```

混淆矩阵显示模型正确或错误分类的每个类别的观测数量。在本例中，模型正确分类了全部 30 个测试观测。

### 计算模型在测试数据上的准确率

```r
accuracy <- sum(diag(table(pred$class, test_data$Species))) / nrow(test_data)
print(accuracy)
```

准确率为 100%，这意味着模型完美地分类了测试数据。

## 13.32.13 R 中的 kernlab 包

`kernlab` 包是用于分类、回归、聚类、新颖性检测、分位数回归和降维的基于核的 ML 方法的综合集合。它包括 SVM、谱聚类、核 PCA、高斯过程和 QP 求解器等流行算法。

`kernlab` 包的目的是为在 R 中实现和使用核方法提供统一的框架。它利用 R 的新 S4 对象模型，并允许用户创建自定义核和算法。

该包可用于需要非线性和灵活模型来捕捉数据中复杂模式的 ML 应用。例如，可以使用 `ksvm` 函数使用不同的核函数和超参数执行分类或回归。或者，可以使用 `kpca` 函数使用核主成分分析执行降维或特征提取。`kernlab` 包还支持诸如 `onlearn` 之类的在线学习算法，可以在不重新训练的情况下用新数据更新模型。

## 13.32.14 R.matlab 包

`R.matlab` 是一个 R 包，提供读取和写入 MAT 文件的方法，MAT 文件是存储 MATLAB 数据的二进制文件。它还允许用户从 R 内部控制 MATLAB 并通过 TCP/IP 连接或文件系统在 R 和 MATLAB 之间交换数据。

`R.matlab` 的目的是促进 R 和 MATLAB 之间互操作性，这两种语言都是科学计算和数据分析的流行语言。`R.matlab` 可用于希望利用两种语言优势的用户，例如 R 丰富的统计和图形功能以及 MATLAB 的数值和工程工具。

`R.matlab` 可在 ML 中以多种方式使用：

- 读取和写入包含 ML 数据集或模型的 MAT 文件，例如神经网络、支持向量机或决策树。
- 从 R 内部运行执行 ML 任务的 MATLAB 脚本或函数，例如训练、测试或评估。
- 在 R 和 MATLAB 之间传输 ML 对象，例如矩阵、向量或列表，以便进一步处理或可视化。

要使用 `R.matlab`，用户需要从 CRAN 安装该包，并在其系统上安装 MATLAB v6 或更高版本。用户还需要在 MATLAB 端加载一个小型 Java 插件以启用 TCP/IP 通信。有关如何使用 `R.matlab` 的更多详细信息，用户可以查阅包文档或一些在线教程。

## 13.32.15 R 中 LPP 的实现

此 R 程序演示了 LPP ML 方法。LPP 可以通过使用核函数应用于具有非线性结构复杂数据。

### 加载所需的包
