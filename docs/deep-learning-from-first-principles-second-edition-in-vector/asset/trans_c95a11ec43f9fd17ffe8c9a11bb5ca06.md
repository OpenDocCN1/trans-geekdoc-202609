

# Python 代码片段

```python
proba = np.argmax(A2, axis=0).reshape(-1, 1)

print("A2=", A2.shape)

return proba
```

# 绘制决策边界

```python
# Plot a decision boundary
# Input : Input Model,
# X
# Y
# sz - Num of hidden units
# lr - Learning rate
# Fig to be saved as
# Returns Null

def plot_decision_boundary1(X, y, W1, b1, W2, b2, figure2="figc.png"):
    # plot_decision_boundary(lambda x: predict(parameters, x.T),
    # x1, y1.T, str(0.3), "fig2.png")
    h = 0.02
    x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
    y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
    xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                         np.arange(y_min, y_max, h))
    Z = np.dot(np.maximum(0, np.dot(np.c_[xx.ravel(), yy.ravel()], W1.T) +
                          b1.T), W2.T) + b2.T
    Z = np.argmax(Z, axis=1)
    Z = Z.reshape(xx.shape)
    fig = plt.figure()
    plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)
    print(X.shape)
    y1 = y.reshape(300,)
    plt.scatter(X[:, 0], X[:, 1], c=y1, s=40, cmap=plt.cm.Spectral)
    plt.xlim(xx.min(), xx.max())
    plt.ylim(yy.min(), yy.max())
    plt.savefig(figure2, bbox_inches='tight')
```

# 加载数据集

```python
# Load the data set
def load_dataset():
    np.random.seed(1)
    train_X, train_Y = sklearn.datasets.make_circles(n_samples=300, noise=.05)
    np.random.seed(2)
    test_X, test_Y = sklearn.datasets.make_circles(n_samples=100, noise=.05)

    # Visualize the data
    print(train_X.shape)
    print(train_Y.shape)
    print("load")

    # plt.scatter(train_X[:, 0], train_X[:, 1], c=train_Y, s=40,
    # cmap=plt.cm.Spectral);
    train_X = train_X.T
    train_Y = train_Y.reshape((1, train_Y.shape[0]))
    test_X = test_X.T
    test_Y = test_Y.reshape((1, test_Y.shape[0]))
    return train_X, train_Y, test_X, test_Y
```

# R 语言实现 (7.2 R)

```r
############################################################################################################
#
# File : DLfunctions7.R
# Author : Tinniam V Ganesh
# Date : 16 Apr 2018
#
##########################################################################################################

library(ggplot2)
library(PRROC)
library(dplyr)

# 计算向量的 Sigmoid 函数值
sigmoid <- function(Z) {
  A <- 1 / (1 + exp(-Z))
  cache <- Z
  retvals <- list("A" = A, "Z" = Z)
  return(retvals)
}

# 这是旧版本。性能开销很大
# 计算 ReLU
reluOld <- function(Z) {
  A <- apply(Z, 1:2, function(x) max(0, x))
  cache <- Z
  retvals <- list("A" = A, "Z" = Z)
  return(retvals)
}

# 计算向量的 ReLU 函数值 (当前版本)
relu <- function(Z) {
  # 执行 ReLU。将小于等于 0 的值设为 0
  Z[Z < 0] = 0
  A = Z
  cache <- Z
  retvals <- list("A" = A, "Z" = Z)
  return(retvals)
}

# 计算向量的 Tanh 激活函数值
tanhActivation <- function(Z) {
  A <- tanh(Z)
  cache <- Z
  retvals <- list("A" = A, "Z" = Z)
  return(retvals)
}

# 计算向量的 Softmax 函数值
softmax <- function(Z) {
  # 获取未归一化的概率
  exp_scores = exp(t(Z))
  # 对每个样本进行归一化
  A = exp_scores / rowSums(exp_scores)
  retvals <- list("A" = A, "Z" = Z)
  return(retvals)
}

# 计算 ReLU 的导数
# g'(z) = 1 if z > 0 and 0 otherwise
reluDerivative <- function(dA, cache) {
  Z <- cache
  dZ <- dA
  # 创建一个值 > 0 的逻辑矩阵
  a <- Z > 0
  # 当 z <= 0 时，也应将 dz 设为 0。执行逐元素乘法
  dZ <- dZ * a
  return(dZ)
}

# 计算 Sigmoid 的导数
# 导数 g'(z) = a * (1-a)
sigmoidDerivative <- function(dA, cache) {
  Z <- cache
  s <- 1 / (1 + exp(-Z))
  dZ <- dA * s * (1 - s)
  return(dZ)
}

# 计算 Tanh 的导数
# 导数 g'(z) = 1 - a^2
tanhDerivative <- function(dA, cache) {
  Z = cache
  a = tanh(Z)
  dZ = dA * (1 - a^2)
  return(dZ)
}

# 此函数用于计算 Softmax 导数
# 在 Y==1 的行中填充 1 矩阵
# 可能需要扩展以支持 K 个类别。目前
# 支持 K=3 和 K=10
popMatrix <- function(Y, numClasses) {
  a = rep(0, times = length(Y))
  Y1 = matrix(a, nrow = length(Y), ncol = numClasses)
  # 将 Y 为类别值的行和列设为 1
  if (numClasses == 3) {
    Y1[Y == 0, 1] = 1
    Y1[Y == 1, 2] = 1
    Y1[Y == 2, 3] = 1
  } else if (numClasses == 10) {
    Y1[Y == 0, 1] = 1
    Y1[Y == 1, 2] = 1
    Y1[Y == 2, 3] = 1
    Y1[Y == 3, 4] = 1
    Y1[Y == 4, 5] = 1
    Y1[Y == 5, 6] = 1
    Y1[Y == 6, 7] = 1
    Y1[Y == 7, 8] = 1
    Y1[Y == 8, 9] = 1
    Y1[Y == 9, 10] = 1  # 修正：原代码 Y1[Y==9,0] 索引为0不合法，推测应为10
  }
  return(Y1)
}

# 计算 Softmax 导数
softmaxDerivative <- function(dA, cache, y, numTraining, numClasses) {
  # 注意：dA 未使用。dL/dZ = dL/dA * dA/dZ = pi-yi
  Z <- cache
  # 计算 Softmax
  exp_scores = exp(t(Z))
  # 对每个样本进行归一化
  probs = exp_scores / rowSums(exp_scores)
  # 创建一个零矩阵
  Y1 = popMatrix(y, numClasses)
  # a=rep(0,times=length(Y))
  # Y1=matrix(a,nrow=length(Y),ncol=numClasses)
  # 将 Y 为类别值的行和列设为 1
  dZ = probs - Y1
  return(dZ)
}

# 初始化 L 层模型
# 输入：每层单元数的向量
# 返回：所有层的初始权重和偏置矩阵
initializeDeepModel <- function(layerDimensions) {
  set.seed(2)
  # 初始化空列表
  layerParams <- list()
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 从 1 循环到 L
  # R 语言索引从 1 开始
  for (l in 2:length(layerDimensions)) {
    # 初始化一个大小为 l x l-1 的小随机数矩阵
    # 创建大小为 l x l-1 的随机数
    w = rnorm(layerDimensions[l] * layerDimensions[l-1]) * 0.01
    # 用这些初始权重创建一个大小为 l x l-1 的权重矩阵
    # 并添加到列表 W1,W2... WL 中
    layerParams[[paste('W', l-1, sep="")]] = matrix(w, nrow = layerDimensions[l], ncol = layerDimensions[l-1])
    layerParams[[paste('b', l-1, sep="")]] = matrix(rep(0, layerDimensions[l]), nrow = layerDimensions[l], ncol = 1)
  }
  return(layerParams)
}

# L 层模型的 He 初始化
# 输入：每层单元数的向量
# 返回：所有层的初始权重和偏置矩阵
# He 初始化将随机数乘以 sqrt(2/layerDimensions[previouslayer])
HeInitializeDeepModel <- function(layerDimensions) {
  set.seed(2)
  # 初始化空列表
  layerParams <- list()
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 从 1 循环到 L
  # R 语言索引从 1 开始
  for (l in 2:length(layerDimensions)) {
    # 初始化一个大小为 l x l-1 的小随机数矩阵
    # 创建大小为 l x l-1 的随机数
    w = rnorm(layerDimensions[l] * layerDimensions[l-1])
    # 用这些初始权重创建一个大小为 l x l-1 的权重矩阵
    # 并添加到列表 W1,W2... WL 中
    # He 初始化 - 除以 sqrt(2/layerDimensions[previous layer])
    layerParams[[paste('W', l-1, sep="")]] = matrix(w, nrow = layerDimensions[l], ncol = layerDimensions[l-1]) * sqrt(2 / layerDimensions[l-1])
    layerParams[[paste('b', l-1, sep="")]] = matrix(rep(0, layerDimensions[l]), nrow = layerDimensions[l], ncol = 1)
  }
  return(layerParams)
}

# L 层模型的 Xavier 初始化
# 输入：每层单元数的向量
# 返回：所有层的初始权重和偏置矩阵
# Xavier 初始化将随机数乘以 sqrt(1/layerDimensions[previouslayer])
XavInitializeDeepModel <- function(layerDimensions) {
  set.seed(2)
  # 初始化空列表
  layerParams <- list()
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 从 1 循环到 L
  # R 语言索引从 1 开始
  for (l in 2:length(layerDimensions)) {
    # 初始化一个大小为 l x l-1 的小随机数矩阵
    # 创建大小为 l x l-1 的随机数
    w = rnorm(layerDimensions[l] * layerDimensions[l-1])
    # 用这些初始权重创建一个大小为 l x l-1 的权重矩阵
    # 并添加到列表 W1,W2... WL 中
    # Xavier 初始化 - 除以 sqrt(1/layerDimensions[previous layer])
    layerParams[[paste('W', l-1, sep="")]] = matrix(w, nrow = layerDimensions[l], ncol = layerDimensions[l-1]) * sqrt(1 / layerDimensions[l-1])
    layerParams[[paste('b', l-1, sep="")]] = matrix(rep(0, layerDimensions[l]), nrow = layerDimensions[l], ncol = 1)
  }
  return(layerParams)
}
```

