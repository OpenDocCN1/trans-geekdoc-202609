

## 3.2a Dropout：圆环数据 – Python

```python
keep_prob=0.9, num_iterations = 5000, print_cost = True, figure="fig13.png")
plt.clf()
plt.close()

W1 = parameters['W1']
b1 = parameters['b1']
W2 = parameters['W2']
b2 = parameters['b2']

# 绘制决策边界
plot_decision_boundary1(X, y1, W1, b1, W2, b2, figure2="fig14.png")
```

![图片 305](index-249_1.jpg)

## 3.2a Dropout：圆环数据 – R

```r
source("DLfunctions61.R")

# 加载数据
df = read.csv("circles.csv", header=FALSE)
z <- as.matrix(read.csv("circles.csv", header=FALSE))
x <- z[, 1:2]
y <- z[, 3]

X <- t(x)
Y <- t(y)

# 设置层维度
# 2 – 输入特征数量
# 11 – 1 个隐藏层，11 个隐藏单元
# 1 – 输出层 1 个 sigmoid 激活单元
layersDimensions = c(2, 11, 1)

# 训练 L 层深度学习网络
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.5
# keep_prob=0.8
retvals = L_Layer_DeepModel(X, Y, layersDimensions,
                            hiddenActivationFunc='relu',
                            outputActivationFunc="sigmoid",
                            learningRate = 0.5,
                            keep_prob=0.8,
                            numIterations = 9000,
                            initType="default",
                            print_cost = TRUE)

# 绘制决策边界
plotDecisionBoundary(z, retvals, keep_prob=0.6,
                     hiddenActivationFunc="relu", 0.5)
```

![图片 306](index-251_1.jpg)

## 3.2b Dropout：螺旋数据 – R

```r
# 读取螺旋数据集
source("DLfunctions61.R")

# 加载数据
Z <- as.matrix(read.csv("spiral.csv", header=FALSE))

# 设置数据
X <- Z[, 1:2]
y <- Z[, 3]

X <- t(X)
Y <- t(y)

# 训练 L 层深度学习网络
# 隐藏层激活函数 – relu
# 输出层激活函数 – softmax
# 学习率 – 0.1
# keep_prob=0.9
retvals = L_Layer_DeepModel(X, Y, layersDimensions,
                            hiddenActivationFunc='relu',
                            outputActivationFunc="softmax",
                            learningRate = 0.1,
                            keep_prob=0.90,
                            numIterations = 9000,
                            print_cost = TRUE)

parameters <- retvals$parameters

# 绘制决策边界
plotDecisionBoundary1(Z, parameters)
```

![图片 307](index-253_1.jpg)

## 3.3a Dropout：圆环数据 – Octave

```octave
data = csvread("circles.csv");
X = data(:, 1:2);
Y = data(:, 3);

# 设置层维度
# 2 – 输入特征数量
# 11 – 1 个隐藏层，11 个隐藏单元
# 1 – 输出层 1 个 sigmoid 激活单元
layersDimensions = [2 11 1];

# 训练 L 层深度学习网络
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.5
# keep_prob=0.8
[weights, biases, costs] = L_Layer_DeepModel(X', Y', layersDimensions,
                                             hiddenActivationFunc='relu',
                                             outputActivationFunc="sigmoid",
                                             learningRate = 0.5,
                                             lambd=0,
                                             keep_prob=0.8,
                                             numIterations = 10000,
                                             initType="default");

# 绘制代价与迭代次数关系图
plotCostVsIterations(10000, costs)

# 绘制决策边界
plotDecisionBoundary1(data, weights, biases, keep_prob=1,
                      hiddenActivationFunc="relu")
```

![图片 308](index-256_1.jpg)
![图片 309](index-257_1.jpg)

## 3.3b Dropout 螺旋数据 – Octave

```octave
source("DL61functions.m")
data = csvread("spiral.csv");

# 设置数据
X = data(:, 1:2);
Y = data(:, 3);

# 设置层维度
layersDimensions = [numFeats numHidden numOutput];

# 训练 L 层深度学习网络
# 隐藏层激活函数 – relu
# 输出层激活函数 – softmax
# 学习率 – 0.1
# keep_prob=0.8
[weights, biases, costs] = L_Layer_DeepModel(X', Y', layersDimensions,
                                             hiddenActivationFunc='relu',
                                             outputActivationFunc="softmax",
                                             learningRate = 0.1,
                                             lambd=0,
                                             keep_prob=0.8,
                                             numIterations = 10000);

# 绘制代价与迭代次数关系图
plotCostVsIterations(10000, costs)

# 绘制决策边界
plotDecisionBoundary1(data, weights, biases, keep_prob=1,
                      hiddenActivationFunc="relu")
```

![图片 310](index-259_1.jpg)
![图片 311](index-260_1.jpg)

## 4. 结论

本文进一步增强了我早期的 L 层通用深度学习网络实现，增加了初始化技术、L2 正则化或 Dropout 正则化的选项。

## 7. 梯度下降优化技术

> **人工智能是新电力。–** 安德鲁·吴教授
>
> **人类和动物的大部分学习都是无监督学习。如果智力是一块蛋糕，无监督学习就是蛋糕本身，监督学习是蛋糕上的糖霜，强化学习则是糖霜上的樱桃。我们知道如何制作糖霜和樱桃，却不知道如何制作蛋糕。我们需要先解决无监督学习问题，才能考虑实现真正的 AI。–** Yann LeCun，2016 年 3 月 14 日 (Facebook)

### 1. 简介

在《从原理到深度学习》第 7 章中，我实现了随机梯度下降 (SGD) 中用于加速收敛的优化方法。具体而言，我讨论并实现了以下梯度下降优化技术：

a. 原始随机梯度下降
b. 学习率衰减
c. 动量法
d. RMSProp
e. 自适应矩估计

本章进一步增强了我用向量化 Python、R 和 Octave 实现的通用 L 层深度学习网络，使其也包含随机梯度下降优化技术。

这些向量化实现位于附录 7 - 梯度下降优化技术中。

您可以从 Github 克隆/下载代码：`DeepLearningFromFirstPrinciples` (https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap7-DLGradientDescentOptimization)。

顺便提一下，关于随机梯度优化技术中使用的各种优化方法，可以在 Sebastian Ruder 的博客 (http://ruder.io/optimizing-gradient-descent/) 上看到很好的讨论。

**注意**：本章中的向量化 Python、R 和 Octave 实现仅使用了 1024 个随机训练样本。这是为了减少计算时间。您可以自由使用完整数据集（60000 个训练数据）进行计算。

本章主要基于安德鲁·吴教授的深度学习专项课程 (https://www.coursera.org/specializations/deep-learning)。此处讨论的所有优化技术均使用随机梯度下降，并基于指数加权平均法。因此，例如如果我们有一些时间序列数据，则可以将时间 't' 处的指数平均值表示为前一个值的序列，如下所示。

此处  表示数据集在  上的平均值。通过选择不同的  值，我们可以对更多或更少的数据点进行平均。

我们可以写出如下方程：

和

通过代入，我们得到：

因此可以看出，  是前值  的加权和，这是一个指数衰减函数。

### 1.1a. 随机梯度下降 (原始版) – Python

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import sklearn.linear_model
import pandas as pd
import sklearn
import sklearn.datasets

exec(open("DLfunctions7.py").read())
exec(open("load_mnist.py").read())

# 读取 MNIST 训练数据和标签
training = list(read(dataset='training', path=".\\mnist"))
test = list(read(dataset='testing', path=".\\mnist"))

lbls = []
pxls = []

# 循环
for i in range(60000):
    l, p = training[i]
    lbls.append(l)
    pxls.append(p)

labels = np.array(lbls)
pixels = np.array(pxls)
y = labels.reshape(-1, 1)
```

