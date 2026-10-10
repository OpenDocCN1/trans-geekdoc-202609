

# 执行 3 层神经网络

```python
parameters, costs = computeNN(X2, Y2, numHidden=numHid, learningRate=1.2, numIterations=10000)
print(costs)
df1 = pd.DataFrame(costs)
df = pd.concat([df, df1], axis=1)
```

# 设置迭代次数

```python
iterations = [0, 1000, 2000, 3000, 4000, 5000, 6000, 7000, 8000, 9000]
```

# 设置索引

```python
df1 = df.set_index([iterations])
```

# 为不同隐藏单元数量绘制成本与迭代次数的关系图

```python
df1.columns = [3, 5, 7]
```

# 绘图

```python
fig = df1.plot()
fig = plt.title("Cost vs No of Iterations for different no of hidden units")
plt.savefig('fig5.png', bbox_inches='tight')
```

![Image 103](index-57_1.jpg)

## 6.2a 不同学习率下的性能 (R)

```r
source("DLfunctions2_1.R")

# 读取数据
z <- as.matrix(read.csv("data.csv", header=FALSE))
x <- z[, 1:2]
y <- z[, 3]
x1 <- t(x)
y1 <- t(y)

# 遍历学习率并计算成本
learningRate <- c(0.1, 1.2, 3.0)
df <- NULL

for (i in seq_along(learningRate)) {
  # 执行 3 层神经网络
  nn <- computeNN(x1, y1, 6, learningRate=learningRate[i], numIterations=10000)
  cost <- nn$costs
  df <- cbind(df, cost)
}

# 创建数据框
df <- data.frame(df)
iterations <- seq(0, 10000, by=1000)
df <- cbind(iterations, df)
names(df) <- c("iterations", "0.5", "1.2", "3.0")

# 重塑数据
library(reshape2)
df1 <- melt(df, id="iterations") # Melt the data

# 绘制不同学习率下的成本与迭代次数关系图
ggplot(df1) + geom_line(aes(x=iterations, y=value, colour=variable), size=1) +
  xlab("Iterations") +
  ylab('Cost') + ggtitle("Cost vs No iterations for different learning rates")
```

![Image 104](index-58_1.jpg)
![Image 105](index-59_1.jpg)

## 6.2b 不同隐藏单元数量下的性能 (R)

```r
source("DLfunctions2_1.R")

# 遍历隐藏单元数量
numHidden <- c(4, 6, 9)
df <- NULL

for (i in seq_along(numHidden)) {
  # 执行 3 层神经网络
  nn <- computeNN(x1, y1, numHidden[i], learningRate=0.1, numIterations=10000)
  cost <- nn$costs
  df <- cbind(df, cost)
}

# 创建数据框
df <- data.frame(df)
iterations <- seq(0, 10000, by=1000)
df <- cbind(iterations, df)
names(df) <- c("iterations", "4", "6", "9")

# 重塑数据框
library(reshape2)

# Melt
df1 <- melt(df, id="iterations")

# 绘制不同隐藏单元数量下的成本与迭代次数关系图
ggplot(df1) + geom_line(aes(x=iterations, y=value, colour=variable), size=1) +
  xlab("Iterations") +
  ylab('Cost') + ggtitle("Cost vs No iterations for different number of hidden units")
```

![Image 106](index-60_1.jpg)
![Image 107](index-61_1.jpg)

## 6.3a 不同学习率下神经网络的性能 (Octave)

```matlab
source("DL-function2.m")

# 绘制不同学习率下的成本与迭代次数关系图
plotLRCostVsIterations()
print -djph figa.jpg
```

![Image 108](index-63_1.jpg)

## 6.3b 不同隐藏单元数量下神经网络的性能 (Octave)

```matlab
source("DL-function2.m")

# 绘制不同隐藏单元数量下的成本与迭代次数关系图
plotHiddenCostVsIterations()
print -djph figa.jpg
```

![Image 109](index-64_1.jpg)

## 7. 给神经网络“施加压力”

在第二部分中，我创建了一个正样本的中心区域和一个负样本的外部区域。这些点是使用圆的方程 $(x - a)^2 + (y - b)^2 = R^2$ 生成的。3 层神经网络在此数据上的表现如何？让我们一探究竟！**注意**：R 和 Octave 的神经网络构建也使用相同的数据集。

## 8. 手动创建圆形中心区域

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.colors
import sklearn.linear_model
from sklearn.model_selection import train_test_split
from sklearn.datasets import make_classification, make_blobs
from matplotlib.colors import ListedColormap
import sklearn
import sklearn.datasets

colors = ['black', 'gold']
cmap = matplotlib.colors.ListedColormap(colors)

x1 = np.random.uniform(0, 10, 800).reshape(800, 1)
x2 = np.random.uniform(0, 10, 800).reshape(800, 1)
X = np.append(x1, x2, axis=1)
X.shape

# 使用 (x-a)^2 + (y-b)^2 = R^2 创建数据集
# 创建一个平方值 < 0.4 的值子集。执行 ravel() 以展平此向量
a = (np.power(X[:, 0] - 5, 2) + np.power(X[:, 1] - 5, 2) <= 6).ravel()
Y = a.reshape(800, 1)

cmap = matplotlib.colors.ListedColormap(colors)

# 绘制数据集
plt.figure()
plt.title('Non-linearly separable classes')
plt.scatter(X[:, 0], X[:, 1], c=Y, marker='o', s=15, cmap=cmap)
plt.savefig('fig6.png', bbox_inches='tight')
```

![Image 110](index-68_1.jpg)

### 8.1a 隐藏单元=4 且学习率 = 2.2 时的决策边界 (Python)

使用上述超参数，决策边界呈三角形。

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.colors
import sklearn.linear_model
execfile("./DLfunctions.py")

x1 = np.random.uniform(0, 10, 800).reshape(800, 1)
x2 = np.random.uniform(0, 10, 800).reshape(800, 1)
X = np.append(x1, x2, axis=1)
X.shape

# 创建一个平方值 < 0.4 的值子集。执行 ravel() 以展平此向量
a = (np.power(X[:, 0] - 5, 2) + np.power(X[:, 1] - 5, 2) <= 6).ravel()
Y = a.reshape(800, 1)

X2 = X.T
Y2 = Y.T

# 执行 3 层神经网络
parameters, costs = computeNN(X2, Y2, numHidden=4, learningRate=2.2, numIterations=10000)

# 绘制决策边界
plot_decision_boundary(lambda x: predict(parameters, x.T), X2, Y2, str(4), str(2.2), "fig7.png")
```

```
## Cost after iteration 0: 0.692836
## Cost after iteration 1000: 0.331052
## Cost after iteration 2000: 0.326428
## Cost after iteration 3000: 0.474887
## Cost after iteration 4000: 0.247989
## Cost after iteration 5000: 0.218009
## Cost after iteration 6000: 0.201034
## Cost after iteration 7000: 0.197030
## Cost after iteration 8000: 0.193507
## Cost after iteration 9000: 0.191949
```

![Image 111](index-70_1.jpg)

### 8.1b 隐藏单元=12 且学习率 = 2.2 时的决策边界 (Python)

增加隐藏单元数量使决策边界更加圆润。

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.colors
import sklearn.linear_model
execfile("./DLfunctions.py")

x1 = np.random.uniform(0, 10, 800).reshape(800, 1)
x2 = np.random.uniform(0, 10, 800).reshape(800, 1)
X = np.append(x1, x2, axis=1)
X.shape

# 创建一个平方值 < 0.4 的值子集。执行 ravel() 以展平此向量
a = (np.power(X[:, 0] - 5, 2) + np.power(X[:, 1] - 5, 2) <= 6).ravel()
Y = a.reshape(800, 1)

X2 = X.T
Y2 = Y.T

# 执行 3 层神经网络
parameters, costs = computeNN(X2, Y2, numHidden=12, learningRate=2.2, numIterations=10000)

# 绘制决策边界
plot_decision_boundary(lambda x: predict(parameters, x.T), X2, Y2, str(12), str(2.2), "fig8.png")
```

```
## Cost after iteration 0: 0.693291
## Cost after iteration 1000: 0.383318
## Cost after iteration 2000: 0.298807
## Cost after iteration 3000: 0.251735
## Cost after iteration 4000: 0.177843
## Cost after iteration 5000: 0.130414
## Cost after iteration 6000: 0.152400
## Cost after iteration 7000: 0.065359
## Cost after iteration 8000: 0.050921
## Cost after iteration 9000: 0.039719
```

![Image 112](index-72_1.jpg)

### 8.2a 隐藏单元=9 且学习率 = 0.5 时的决策边界 (R)

当隐藏单元数量为 6 且学习率为 0.5 时，在 R 中也是三角形状。

```r
source("DLfunctions2_1.R")

z <- as.matrix(read.csv("data1.csv", header=FALSE)) # N
x <- z[, 1:2]
y <- z[, 3]
x1 <- t(x)
y1 <- t(y)

# 执行 3 层神经网络
nn <- computeNN(x1, y1, 9, learningRate=0.5, numIterations=10000) # Triangular
```

![Image 113](index-73_1.jpg)

```
## [1] 0.8398838
## [1] 0.3303621
## [1] 0.3127731
## [1] 0.3012791
## [1] 0.3305543
## [1] 0.3303964
## [1] 0.2334615
## [1] 0.1920771
## [1] 0.2341225
## [1] 0.2188118
## [1] 0.2082687
```

# 绘制决策边界

```r
plotDecisionBoundary(z, nn, 6, 0.1)
```

![Image 114](index-74_1.jpg)

### 8.2b 隐藏单元=8 且

