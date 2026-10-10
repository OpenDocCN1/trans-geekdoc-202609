
# 加载数据

```r
df = read.csv("circles.csv", header = FALSE)
z <- as.matrix(read.csv("circles.csv", header = FALSE))
x <- z[, 1:2]
y <- z[, 3]
X <- t(x)
Y <- t(y)
```

# 设置层维度

```r
# 2 – 输入特征数量
# 11 – 1 个隐藏层 11 个隐藏单元
# 1 – 输出层 1 个 sigmoid 激活单元
layersDimensions = c(2, 11, 1)
```

# 训练 L 层深度学习网络

```r
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.6
# lambd=0.1
retvals = L_Layer_DeepModel(X, Y, layersDimensions,
                            hiddenActivationFunc = 'relu',
                            outputActivationFunc = "sigmoid",
                            learningRate = 0.5,
                            lambd = 0.1,
                            numIterations = 9000,
                            initType = "default",
                            print_cost = TRUE)
```

# 绘制成本与迭代次数的关系图

```r
iterations <- seq(0, 9000, 1000)
costs = retvals$costs
df = data.frame(iterations, costs)
ggplot(df, aes(x = iterations, y = costs)) + geom_point() + geom_line(color = "blue") +
  ggtitle("Costs vs iterations") + xlab("No of iterations") + ylab("Cost")
```

![Image 295](index-231_1.jpg)

# 绘制决策边界

```r
plotDecisionBoundary(z, retvals, hiddenActivationFunc = "relu", 0.5)
```

![Image 296](index-232_1.jpg)

## 2.2b 正则化：螺旋数据 – R

# 读取螺旋数据集

# 加载数据

```r
source("DLfunctions61.R")
Z <- as.matrix(read.csv("spiral.csv", header = FALSE))
```

# 设置数据

```r
X <- Z[, 1:2]
y <- Z[, 3]
X <- t(X)
Y <- t(y)
```

# 设置层维度

```r
layersDimensions = c(2, 100, 3)
# 2 – 输入特征数量
# 100 – 1 个隐藏层 100 个隐藏单元
# 3 – 输出层 3 个 softmax 类别
```

# 训练 L 层深度学习网络

```r
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.5
# lambd=0.01
retvals = L_Layer_DeepModel(X, Y, layersDimensions,
                            hiddenActivationFunc = 'relu',
                            outputActivationFunc = "softmax",
                            learningRate = 0.5,
                            lambd = 0.01,
                            numIterations = 9000,
                            print_cost = TRUE)
parameters <- retvals$parameters
```

# 绘制决策边界

```r
plotDecisionBoundary1(Z, parameters)
```

![Image 297](index-234_1.jpg)

## 2.3a 正则化：圆环数据 – Octave

```matlab
source("DL61functions.m")
# 加载数据
data = csvread("circles.csv");
X = data(:, 1:2);
Y = data(:, 3);
```

# 设置层维度

```matlab
# 2 – 输入特征数量
# 11 – 1 个隐藏层 11 个隐藏单元
# 1 – 输出层 1 个 sigmoid 激活单元
layersDimensions = [2 11 1]; # tanh=-0.5(ok), # relu=0.1 best!
```

# 训练 L 层深度学习网络

```matlab
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.5
# lambd=0.2
[weights biases costs] = L_Layer_DeepModel(X', Y', layersDimensions,
                                           hiddenActivationFunc = 'relu',
                                           outputActivationFunc = "sigmoid",
                                           learningRate = 0.5,
                                           lambd = 0.2,
                                           keep_prob = 1,
                                           numIterations = 8000,
                                           initType = "default");
```

# 绘制成本与迭代次数的关系图

```matlab
plotCostVsIterations(8000, costs)
```

# 绘制决策边界

```matlab
plotDecisionBoundary(data, weights, biases, keep_prob = 1, hiddenActivationFunc = "relu")
```

![Image 298](index-236_1.jpg)
![Image 299](index-237_1.jpg)

## 2.3b 正则化：螺旋数据 2 – Octave

```matlab
source("DL61functions.m")
data = csvread("spiral.csv");
```

# 设置数据

```matlab
X = data(:, 1:2);
Y = data(:, 3);
```

# 设置层维度

```matlab
# 2 – 输入特征数量
# 100 – 1 个隐藏层 100 个隐藏单元
# 3 – 输出层 3 个类别，使用 softmax 激活单元
layersDimensions = [2 100 3]
```

# 训练 L 层深度学习网络

```matlab
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.6
# lambd=0.2
[weights biases costs] = L_Layer_DeepModel(X', Y', layersDimensions,
                                           hiddenActivationFunc = 'relu',
                                           outputActivationFunc = "softmax",
                                           learningRate = 0.6,
                                           lambd = 0.2,
                                           keep_prob = 1,
                                           numIterations = 10000);
```

# 绘制成本与迭代次数的关系图

```matlab
plotCostVsIterations(10000, costs)
```

# 绘制决策边界

```matlab
plotDecisionBoundary1(data, weights, biases, keep_prob = 1, hiddenActivationFunc = "relu")
```

![Image 300](index-240_1.jpg)
![Image 301](index-241_1.jpg)

## 3.1a Dropout：圆环数据 – Python

**Dropout** 正则化技术被 **Alex Krizhevsky**、**Ilya Sutskever** 和 **Geoffrey E. Hinton** 教授在 **“使用深度卷积神经网络进行 ImageNet 分类”** ([https://www.nvidia.cn/content/tesla/pdf/machine-learning/imagenet-classification-with-deep-convolutional-nn.pdf](https://www.nvidia.cn/content/tesla/pdf/machine-learning/imagenet-classification-with-deep-convolutional-nn.pdf)) 一文中极其有效地用于防止过拟合。

Dropout 技术的工作原理是在前向传播周期中，根据 `keep_prob` 标准在每个隐藏层中随机丢弃一组激活单元。以下是 Octave 代码。系统会为每一层创建一个 ‘dropoutMat’，用于指定要丢弃的单元。**注意**：在反向传播周期计算梯度时，必须使用相同的 `dropoutMat`。因此，dropout 矩阵被存储在一个元胞数组中。

```matlab
for l = 1:L-1
    ...
    D = rand(size(A)(1), size(A)(2));
    D = (D < keep_prob);
    # 将部分隐藏单元置零
    A = A .* D;
    # 除以 keep_prob 以保持 A 的期望值不变
    A = A ./ keep_prob;
    # 将 D 存储在 dropoutMat 元胞数组中
    dropoutMat{l} = D;
    ...
endfor
```

在反向传播周期中，我们有：

```matlab
for l = (L-1):-1:1
    ...
    D = dropoutMat{l};
    # 根据相同的 dropout 矩阵将 dAl 置零
    dAl = dAl .* D;
    # 除以 keep_prob 以维持期望值
    dAl = dAl ./ keep_prob;
    ...
endfor
```

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import sklearn.linear_model
import pandas as pd
import sklearn
import sklearn.datasets
exec(open("DLfunctions61.py").read())
```

# 加载数据

```python
train_X, train_Y, test_X, test_Y = load_dataset()
```

# 设置层维度

```python
# 2 – 输入特征数量
# 7 – 1 个隐藏层 7 个隐藏单元
# 1 – 输出层 1 个 sigmoid 激活单元
layersDimensions = [2, 7, 1]
```

# 训练 L 层深度学习网络

```python
# 隐藏层激活函数 – relu
# 输出层激活函数 – sigmoid
# 学习率 – 0.6
# keep_prob=0.7
parameters = L_Layer_DeepModel(train_X, train_Y, layersDimensions,
                               hiddenActivationFunc = 'relu',
                               outputActivationFunc = "sigmoid",
                               learningRate = 0.6,
                               keep_prob = 0.7,
                               num_iterations = 9000,
                               initType = "default",
                               print_cost = True,
                               figure = "fig11.png")
```

# 清除绘图

```python
plt.clf()
plt.close()
```

# 绘制决策边界

```python
plot_decision_boundary(lambda x: predict(parameters, x.T, keep_prob = 0.7), train_X, train_Y, str(0.6), figure1 = "fig12.png")
```

![Image 302](index-245_1.jpg)
![Image 303](index-246_1.jpg)

## 3.1b Dropout：螺旋数据 – Python

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import sklearn.linear_model
import pandas as pd
import sklearn
import sklearn.datasets
exec(open("DLfunctions61.py").read())
```

# 创建输入数据集 - 摘自 CS231n 卷积神经网络，http://cs231n.github.io/neural-networks-case-study/

```python
N = 100 # 每个类别的点数
D = 2 # 维度
K = 3 # 类别数量
X = np.zeros((N*K, D)) # 数据矩阵（每行 = 单个样本）
y = np.zeros(N*K, dtype='uint8') # 类别标签

for j in range(K):
    ix = range(N*j, N*(j+1))
    r = np.linspace(0.0, 1, N) # 半径
    t = np.linspace(j*4, (j+1)*4, N) + np.random.randn(N)*0.2 # theta
    X[ix] = np.c_[r*np.sin(t), r*np.cos(t)]
    y[ix] = j
```

# 绘制数据

```python
plt.scatter(X[:, 0], X[:, 1], c=y, s=40, cmap=plt.cm.Spectral)
plt.clf()
plt.close()
```

# 设置层维度

```python
# 2 – 输入特征数量
# 100 – 1 个隐藏层 100 个隐藏单元
# 3 – 输出层 3 个类别，使用 softmax 激活单元
layersDimensions = [2, 100, 3]
```

![Image 304](index-248_1.jpg)

```python
y1 = y.reshape(-1, 1).T
```

# 训练 L 层深度学习网络

```python
# 隐藏层激活函数 – relu
# 输出层激活函数 – softmax
# 学习率 – 1
# keep_prob=0.9
parameters = L_Layer_DeepModel(X.T, y1, layersDimensions,
                               hiddenActivationFunc = 'relu',
                               outputActivationFunc = "softmax",
                               learningRate = 1,
                               keep_prob = 0.9,
                               num_iterations = 9000,
                               initType = "default",
                               print_cost = True,
                               figure = "fig13.png")
```
