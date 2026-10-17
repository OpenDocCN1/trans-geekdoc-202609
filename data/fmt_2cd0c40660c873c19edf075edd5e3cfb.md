
```matlab
plot(iterations, costs, color=col(i), "linewidth", 3);
hold off;
title("Cost vs no of iterations for different number of hidden units");
xlabel("No of iterations");
ylabel("Cost");
legend('4', '9', '12');
endfor
end
```

# 每个参数的更新规则

```python
for l in range(L):
    parameters["W" + str(l+1)] = parameters['W'+str(l+1)] - learningRate * gradients['dW' + str(l+1)]
    parameters["b" + str(l+1)] = parameters['b'+str(l+1)] - learningRate * gradients['db' + str(l+1)]
return parameters
```

# 执行 L 层深度学习模型

**输入**：

- `X` - 输入特征
- `Y` - 输出
- `layersDimensions` - 层维度
- `hiddenActivationFunc` - 隐藏层激活函数 relu /tanh
- `learning_rate` - 学习率
- `num_iterations` - 迭代次数

**输出**：更新后的权重和偏置

```python
def L_Layer_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu', learning_rate=.3, num_iterations=10000, fig="figx.png"): # lr was 0.009
    np.random.seed(1)
    costs = []

    # 初始化参数
    parameters = initializeDeepModel(layersDimensions)

    # 执行梯度下降
    for i in range(0, num_iterations):
        # 执行一轮前向传播
        AL, caches = forwardPropagationDeep(X, parameters, hiddenActivationFunc)

        # 计算成本
        cost = computeCost(AL, Y)

        # 通过 1 轮反向传播计算梯度
        gradients = backwardPropagationDeep(AL, Y, caches, hiddenActivationFunc)

        # 更新参数
        parameters = gradientDescent(parameters, gradients, learning_rate)

        # 存储成本
        if i % 100 == 0:
            print("Cost after iteration %i: %f" % (i, cost))

        if i % 100 == 0:
            costs.append(cost)

    # 绘制成本图
    fig1 = plt.plot(np.squeeze(costs))
    fig1 = plt.ylabel('cost')
    fig1 = plt.xlabel('No of iterations(per 100)')
    fig1 = plt.title("Learning rate =" + str(learning_rate))
    # plt.show()
    fig1.figure.savefig(fig, bbox_inches='tight')
    plt.clf()

    return parameters
```

# 绘制决策边界

**输入**：

- 输入模型
- `X`
- `Y`
- `sz` - 隐藏单元数量
- `lr` - 学习率
- 保存为的图片文件

**返回**：空

```python
def plot_decision_boundary(model, X, y, lr, fig):
    # 设置最小和最大值并给予一些填充
    x_min, x_max = X[0, :].min() - 1, X[0, :].max() + 1
    y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1
    colors = ['black', 'yellow']
    cmap = matplotlib.colors.ListedColormap(colors)
    h = 0.01

    # 生成一个点网格，点之间距离为 h
    xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))

    # 预测整个网格的函数值
    Z = model(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)

    # 绘制等高线和训练示例
    fig2 = plt.contourf(xx, yy, Z, cmap="coolwarm")
    fig2 = plt.ylabel('x2')
    fig2 = plt.xlabel('x1')
    fig2 = plt.scatter(X[0, :], X[1, :], c=y, s=7, cmap=cmap)
    fig2 = plt.title("Decision Boundary for learning rate:" + lr)
    fig2.figure.savefig(fig, bbox_inches='tight')
    plt.clf()
```

# 预测给定输入的输出

**输入**：

- `parameters`
- `X`

**输出**：预测结果

```python
def predict(parameters, X):
    A2, cache = forwardPropagationDeep(X, parameters)
    predictions = (A2 > 0.5)
    return predictions
```

# 预测给定数据的概率分数

**输入**：

- `parameters`
- `X`

**输出**：输出的概率

```python
def predict_proba(parameters, X):
    A2, cache = forwardPropagationDeep(X, parameters)
    proba = A2
    return proba
```

# 绘制决策边界

**输入**：

- 输入模型
- `X`
- `Y`
- `sz` - 隐藏单元数量
- `lr` - 学习率
- 保存为的图片文件

**返回**：空

```python
def plot_decision_surface(model, X, y, sz, lr, fig):
    # 设置最小和最大值并给予一些填充
    x_min, x_max = X[0, :].min() - 1, X[0, :].max() + 1
    y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1
    z_min, z_max = X[2, :].min() - 1, X[2, :].max() + 1
    colors = ['black', 'gold']
    cmap = matplotlib.colors.ListedColormap(colors)
    h = 3

    # 生成一个点网格，点之间距离为 h
    xx, yy, zz = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h), np.arange(z_min, z_max, h))

    # 预测整个网格的函数值
    a = np.c_[xx.ravel(), yy.ravel(), zz.ravel()]
    Z = predict(parameters, a.T)
    Z = Z.reshape(xx.shape)

    # 绘制等高线和训练示例
    # plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)
    ax = plt.axes(projection='3d')
    ax.contour3D(xx, yy, Z, 50, cmap='binary')
    # plt.ylabel('x2')
    # plt.xlabel('x1')
    plt.scatter(X[0, :], X[1, :], c=y, cmap=cmap)
    plt.title("Decision Boundary for hidden layer size:" + sz + " and learning rate:" + lr)
    plt.show()
```

```python
def plotSurface(X, parameters):
    # xx, yy, zz = np.meshgrid(np.arange(10), np.arange(10), np.arange(10))
    x_min, x_max = X[0, :].min() - 1, X[0, :].max() + 1
    y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1
    z_min, z_max = X[2, :].min() - 1, X[2, :].max() + 1
    colors = ['red']
    cmap = matplotlib.colors.ListedColormap(colors)
    h = 1
    xx, yy, zz = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h), np.arange(z_min, z_max, h))

    # 对网格值预测模型
    a = np.c_[xx.ravel(), yy.ravel(), zz.ravel()]
    Z = predict(parameters, a.T)
    r = Z.T
    r1 = r.reshape(xx.shape)

    # 找出预测值为 1 的值
    xx1 = xx[r1]
    yy1 = yy[r1]
    zz1 = zz[r1]

    # 绘制这些值
    ax = plt.axes(projection='3d')
    # ax.plot_trisurf(xx1, yy1, zz1, cmap='bone', edgecolor='none')
    # ax.scatter3D(xx1, yy1, zz1, c=zz1, s=10, cmap=cmap)
    # ax.plot_surface(xx1, yy1, zz1, 'gray')
```

### 3.2 R

```r
############################################################################################################
#
# File : DLfunctions33.R
# Author : Tinniam V Ganesh
# Date : 30 Jan 2018
#
##########################################################################################################

library(ggplot2)
library(PRROC)
library(dplyr)

# 计算向量的 Sigmoid
sigmoid <- function(Z) {
    A <- 1 / (1 + exp(-Z))
    cache <- Z
    retvals <- list("A" = A, "Z" = Z)
    return(retvals)
}

# 计算向量的 Relu
relu <- function(Z) {
    A <- apply(Z, 1:2, function(x) max(0, x))
    cache <- Z
    retvals <- list("A" = A, "Z" = Z)
    return(retvals)
}

# 计算向量的 tanh 激活
tanhActivation <- function(Z) {
    A <- tanh(Z)
    cache <- Z
    retvals <- list("A" = A, "Z" = Z)
    return(retvals)
}

# 计算 Relu 的导数
# g'(z) = 1 if z >0 and 0 otherwise
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

# 计算 tanh 的导数
# 导数 g'(z) = 1 - a²
tanhDerivative <- function(dA, cache) {
    Z = cache
    a = tanh(Z)
    dZ = dA * (1 - a^2)
    return(dZ)
}

# 初始化 L 层模型
# 输入：每层单元数列表
# 返回：所有层的初始权重和偏置矩阵
initializeDeepModel <- function(layerDimensions) {
    set.seed(2)
    # 初始化空列表
    layerParams <- list()
    # 注意第 'l' 层的权重矩阵是大小为 (l,l-1) 的矩阵
    # 偏置是大小为 (l,1) 的向量
    # 从 1 循环到 L
    # R 中索引从 1 开始
    for(l in 2:length(layersDimensions)) {
        # 初始化一个大小为 l x l-1 的小随机数矩阵
        # 创建大小为 l x l-1 的随机数
        w = rnorm(layersDimensions[l] * layersDimensions[l-1]) * 0.01
        # 用这些初始权重创建一个大小为 l x l-1 的权重矩阵并
        # 添加到列表 W1,W2... WL
        layerParams[[paste('W', l-1, sep="")]] = matrix(w, nrow=layersDimensions[l], ncol=layersDimensions[l-1])
        layerParams[[paste('b', l-1, sep="")]] = matrix(rep(0, layersDimensions[l]), nrow=layersDimensions[l], ncol=1)
    }
    return(layerParams)
}

# 计算深度网络前向传播中第 'l' 层的激活值
# 输入：A_prec - 上一层的激活值
# W,b - 权重和偏置矩阵及向量
# activationFunc - 激活函数 - sigmoid、tanh、relu 等
# 返回值(list) ：该层的激活值
# Z = W * X + b
# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)
layerActivationForward <- function(A_prev, W, b, activationFunc) {
    # 计算 Z
    z = W %*% A_prev

    # 按列广播偏置 'b'
    Z <- sweep(z, 1, b, '+')

    forward_cache <- list("A_prev"=A_prev, "W"=W, "b"=b)

    # 计算 sigmoid 的激活值
    if(activationFunc == "sigmoid") {
        vals = sigmoid(Z)
    } else if (activationFunc == "relu") { # 计算 relu 的激活值
        vals = relu(Z)
    } else if(activationFunc == 'tanh') { # 计算 tanh 的激活值
        vals = tanhActivation(Z)
    }

    # 创建前向缓存和激活缓存的列表
    cache <- list("forward_cache"=forward_cache, "activation_cache"=vals[['Z']])
    retvals <- list("A"=vals[['A']], "cache"=cache)
    return(retvals)
}
```
