

## 1. 训练集的混淆矩阵

```
[ 11 34 30 21 13 16 4 7 5703 12]
[ 10 4 1 32 135 14 1 92 134 5526]
```

## 2. 训练集的准确率、精确率、召回率

- **准确率**：0.96
- **精确率**：0.96
- **召回率**：0.96

## 3. 测试集的混淆矩阵

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| **0** | 954 | 1 | 8 | 0 | 3 | 3 | 2 | 4 | 4 | 1 |
| **1** | 0 | 1107 | 6 | 5 | 0 | 0 | 1 | 2 | 14 | 0 |
| **2** | 11 | 7 | 957 | 10 | 5 | 0 | 5 | 20 | 16 | 1 |
| **3** | 2 | 3 | 37 | 925 | 3 | 13 | 0 | 8 | 18 | 1 |
| **4** | 2 | 6 | 1 | 1 | 944 | 0 | 7 | 3 | 4 | 14 |
| **5** | 12 | 5 | 4 | 45 | 2 | 740 | 24 | 8 | 42 | 10 |
| **6** | 8 | 4 | 4 | 2 | 16 | 9 | 903 | 0 | 12 | 0 |
| **7** | 4 | 10 | 27 | 18 | 5 | 1 | 0 | 940 | 1 | 22 |
| **8** | 11 | 13 | 6 | 13 | 9 | 10 | 7 | 2 | 900 | 3 |
| **9** | 8 | 5 | 1 | 7 | 50 | 7 | 0 | 20 | 29 | 882 |

## 4. 测试集的准确率、精确率、召回率

- **准确率**：0.93
- **精确率**：0.93
- **召回率**：0.93

![Image 264](index-174_1.jpg)

### 3.2a 带 Sigmoid 激活函数的随机数据集 – R 代码

上述 Python 代码中使用的随机数据集，已保存为 csv 文件（`data.csv`）。该代码用于在 R 中测试带有 Sigmoid 激活函数的 `L-Layer` 深度学习网络。

```r
source("DLfunctions5.R")

# 读取随机数据集
z <- as.matrix(read.csv("data.csv", header=FALSE))
x <- z[,1:2]
y <- z[,3]

X <- t(x)
Y <- t(y)

# 设置各层的维度
# 2 – 输入特征数量
# 9, 9 – 2 个隐藏层，每层 9 个隐藏单元
# 1 – 输出层 1 个激活单元
layersDimensions = c(2, 9, 9, 1)

# 在数据集上执行 L-Layer 深度学习网络，隐藏层使用 relu 激活单元
# 输出层使用 sigmoid 激活单元
retvals = L_Layer_DeepModel(X, Y, layersDimensions,
                            hiddenActivationFunc='relu',
                            outputActivationFunc="sigmoid",
                            learningRate = 0.3,
                            numIterations = 5000,
                            print_cost = TRUE)

# 绘制成本与迭代次数的关系图
iterations <- seq(0, 5000, 1000)
costs = retvals$costs
df = data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
  ggtitle("Costs vs iterations") + xlab("Iterations") + ylab("Loss")
```

![Image 265](index-176_1.jpg)

### 3.2b 带 Softmax 激活函数的螺旋数据集 – R

上述 Python 代码中使用的螺旋数据集（`spiral.csv`）被复用，以测试带有 Softmax 的多分类问题。

```r
source("DLfunctions5.R")

Z <- as.matrix(read.csv("spiral.csv", header=FALSE))

# 设置数据
X <- Z[,1:2]
y <- Z[,3]

X <- t(X)
Y <- t(y)

# 初始化特征数量、隐藏层隐藏单元数量和类别数量
numFeats <- 2  # 特征数
numHidden <- 100  # 隐藏单元数
numOutput <- 3  # 类别数

# 设置层维度
layersDimensions = c(numFeats, numHidden, numOutput)

# 执行 L-Layer 深度学习网络，隐藏层使用 relu 激活单元
# 输出层使用 softmax 激活函数
retvals = L_Layer_DeepModel(X, Y, layersDimensions,
                            hiddenActivationFunc='relu',
                            outputActivationFunc="softmax",
                            learningRate = 0.5,
                            numIterations = 9000,
                            print_cost = TRUE)

# 绘制成本与迭代次数的关系图
iterations <- seq(0, 9000, 1000)
costs = retvals$costs
df = data.frame(iterations, costs)
ggplot(df, aes(x=iterations, y=costs)) + geom_point() + geom_line(color="blue") +
  ggtitle("Costs vs iterations") + xlab("Iterations") + ylab("Costs")
```

### 3.2c 带 Softmax 激活函数的 MNIST 数据集 – R

下面的代码执行一个带有 Softmax 输出激活函数的 `L-Layer` 深度学习网络，利用随机梯度下降对 MNIST 的 10 个手写数字进行分类。使用了数据集中 32768 个随机样本进行训终。

话虽如此，R 语言中的混淆矩阵输出了大量有趣的统计数据！针对每个类别都有一堆统计指标。例如，数字 ‘6’ 和 ‘9’ 的平衡准确率约为 50%。

看起来，分类器被以下事实搞糊涂了：6 是倒过来的 9，反之亦然。测试数据集上的准确率仅约 75%。我本可以尝试调整层数、隐藏单元数量、学习率、轮数等以获得更高的准确率。但由于每次测试耗时 8 小时以上，我可能改天再研究这个！

```r
source("DLfunctions5.R")
source("mnist.R")

# 加载 mnist 数据
load_mnist()
show_digit(train$x[2,])

# 设置层维度
layersDimensions = c(784, 15, 9, 10)  # 在 1500 时有效

x <- t(train$x)
X <- x[,1:60000]
y <- train$y
y1 <- y[1:60000]
y2 <- as.matrix(y1)
Y <- t(y2)

# 从 MNIST 中随机抽取 32768 个样本
permutation = c(sample(2^15))

# 随机打乱训练数据
X1 = X[, permutation]
y1 = Y[1, permutation]
y2 <- as.matrix(y1)
Y1 = t(y2)

# 在整个训练集上执行随机梯度下降
# 隐藏层使用 'relu' 激活，输出层使用 'softmax' 激活
# 学习率 = 0.05
retvalsSGD = L_Layer_DeepModel_SGD(X1, Y1, layersDimensions,
                                   hiddenActivationFunc='relu',
                                   outputActivationFunc="softmax",
                                   learningRate = 0.05,
                                   mini_batch_size = 512,
                                   num_epochs = 1,
                                   print_cost = TRUE)

# 计算混淆矩阵
library(caret)
library(e1071)

predictions = predictProba(retvalsSGD[['parameters']],
                           X, hiddenActivationFunc='relu',
                           outputActivationFunc="softmax")
confusionMatrix(predictions, Y)
```

#### 训练集上的混淆矩阵

```
> confusionMatrix(predictions, Y)
Confusion Matrix and Statistics

Reference
Prediction    0    1    2    3    4    5    6    7    8    9
0          5738    1   21    5   16   17    7   15    9   43
1             5 6632   21   24   25    3    2   33   13  392
2            12   32 5747  106   25   28    3   27   44 4779
3             0   27   12 5715    1   21    1   20    1   13
4            10    5   21   18 5677    9   17   30   15  166
5           142   21   96  136   93 5306 5884   43   60  413
6             0    0    0    0    0    0    0    0    0    0
7             6    9   13   13    3    4    0 6085    0   55
8             8   12    7   43    1   32    2    7 5703   69
9             2    3   20   71    1    1    2    5    6   19

Overall Statistics

Accuracy : 0.777
95% CI : (0.7737, 0.7804)
No Information Rate : 0.1124
P-Value [Acc > NIR] : < 2.2e-16
Kappa : 0.7524
Mcnemar's Test P-Value : NA

Statistics by Class:

                     Class: 0 Class: 1 Class: 2 Class: 3 Class: 4 Class: 5 Class: 6
Sensitivity            0.96877  0.9837  0.96459  0.93215  0.97176  0.97879  0.00000
Specificity            0.99752  0.9903  0.90644  0.99822  0.99463  0.87380  1.00000
Pos Pred Value         0.97718  0.9276  0.53198  0.98348  0.95124  0.43513       NaN
Neg Pred Value         0.99658  0.9979  0.99571  0.99232  0.99695  0.99759  0.90137
Prevalence             0.09872  0.1124  0.09930  0.10218  0.09737  0.09035  0.09863
Detection Rate         0.09563  0.1105  0.09578  0.09525  0.09462  0.08843  0.00000
Detection Prevalence   0.09787  0.1192  0.18005  0.09685  0.09947  0.20323  0.00000
Balanced Accuracy      0.98314  0.9870  0.93551  0.96518  0.98319  0.92629  0.50000

                     Class: 7 Class: 8 Class: 9
Sensitivity            0.9713  0.97471  0.0031938
Specificity            0.9981  0.99666  0.9979464
Pos Pred Value         0.9834  0.96924  0.1461538
Neg Pred Value         0.9967  0.99727  0.9009521
Prevalence             0.1044  0.09752  0.0991500
Detection Rate         0.1014  0.09505  0.0003167
Detection Prevalence   0.1031  0.09807  0.0021667
Balanced Accuracy      0.9847  0.98568  0.5005701
```

#### 测试集上的混淆矩阵

```r
# 测试集上的混淆矩阵
xtest <- t(test$x)
Xtest <- xtest[,1:10000]

ytest <- test$y
ytest1 <- ytest[1:10000]
ytest2 <- as.matrix(ytest1)
Ytest = t(ytest2)
```

```
Confusion Matrix and Statistics

Reference
Prediction    0    1    2    3    4    5    6    7    8    9
0           950    2    2    3    0    6    9    4    7    6
1             3 1110    4    2    9    0    3   12    5   74
2             2    6  965   21    9   14    5   16   12  789
3             1    2    9  908    2   16    0   21    2    6
4             0    1    9    5  938    1    8    6    8   39
5            19    5   25   35   20  835  929    8   54   67
6             0    0    0    0    0    0    0    0    0    0
7             4    4    7   10    2    4    0  952    5    6
8             1    5    8   14    2   16    2    3  876   21
9             0    0    3   12    0    0    2    6    5    1

Overall Statistics

Accuracy : 0.7535
95% CI : (0.7449, 0.7619)
No Information Rate : 0.1135
P-Value [Acc > NIR] : < 2.2e-16
Kappa : 0.7262
Mcnemar's Test P-Value : NA

Statistics by Class:

                     Class: 0 Class: 1 Class: 2 Class: 3 Class: 4 Class: 5 Class: 6
Sensitivity            0.9694  0.9780  0.9351  0.8990  0.9552  0.9361  0.0000
Specificity            0.9957  0.9874  0.9025  0.9934  0.9915  0.8724  1.0000
Pos Pred Value         0.9606  0.9083  0.5247  0.9390  0.9241  0.4181       NaN
Neg Pred Value         0.9967  0.9972  0.9918  0.9887  0.9951  0.9929  0.9042
Prevalence             0.0980  0.1135  0.1032  0.1010  0.0982  0.0892  0.0958
Detection Rate         0.0950  0.1110  0.0965  0.0908  0.0938  0.0835  0.0000
Detection Prevalence   0.0989  0.1222  0.1839  0.0967  0.1015  0.1997  0.0000
```

