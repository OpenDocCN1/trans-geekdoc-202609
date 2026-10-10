

# Adam 优化器实现

```r
gradientDescent <- function(parameters, gradients, learningRate=0.1, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # 神经网络中的层数
  v_corrected <- list()
  s_corrected <- list()

  # 每个参数的更新规则。使用 for 循环。
  for(l in 1:(L-1)) {
    # v[['dWk']] = beta * v[['dWk']] + (1-beta) * dWk
    v[[paste("dW", l, sep="")]] = beta1 * v[[paste("dW", l, sep="")]] +
      (1 - beta1) * gradients[[paste('dW', l, sep="")]]
    v[[paste("db", l, sep="")]] = beta1 * v[[paste("db", l, sep="")]] +
      (1 - beta1) * gradients[[paste('db', l, sep="")]]

    # 计算一阶矩的偏差修正估计。
    v_corrected[[paste("dW", l, sep="")]] = v[[paste("dW", l, sep="")]] / (1 - beta1^t)
    v_corrected[[paste("db", l, sep="")]] = v[[paste("db", l, sep="")]] / (1 - beta1^t)

    # 梯度的逐元素相乘
    s[[paste("dW", l, sep="")]] = beta2 * s[[paste("dW", l, sep="")]] +
      (1 - beta2) * gradients[[paste('dW', l, sep="")]] *
      gradients[[paste('dW', l, sep="")]]
    s[[paste("db", l, sep="")]] = beta2 * s[[paste("db", l, sep="")]] +
      (1 - beta2) * gradients[[paste('db', l, sep="")]] *
      gradients[[paste('db', l, sep="")]]

    # 计算二阶矩的偏差修正估计。
    s_corrected[[paste("dW", l, sep="")]] = s[[paste("dW", l, sep="")]] / (1 - beta2^t)
    s_corrected[[paste("db", l, sep="")]] = s[[paste("db", l, sep="")]] / (1 - beta2^t)

    # 更新参数。
    d1 = sqrt(s_corrected[[paste("dW", l, sep="")]] + epsilon)
    d2 = sqrt(s_corrected[[paste("db", l, sep="")]] + epsilon)
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] -
      learningRate * v_corrected[[paste("dW", l, sep="")]] / d1
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] -
      learningRate * v_corrected[[paste("db", l, sep="")]] / d2
  }

  # 计算第 L 层
  if(outputActivationFunc == "sigmoid") {
    v[[paste("dW", L, sep="")]] = beta1 * v[[paste("dW", L, sep="")]] +
      (1 - beta1) * gradients[[paste('dW', L, sep="")]]
    v[[paste("db", L, sep="")]] = beta1 * v[[paste("db", L, sep="")]] +
      (1 - beta1) * gradients[[paste('db', L, sep="")]]

    # 计算一阶矩的偏差修正估计。
    v_corrected[[paste("dW", L, sep="")]] = v[[paste("dW", L, sep="")]] / (1 - beta1^t)
    v_corrected[[paste("db", L, sep="")]] = v[[paste("db", L, sep="")]] / (1 - beta1^t)

    # 梯度的逐元素相乘
    s[[paste("dW", L, sep="")]] = beta2 * s[[paste("dW", L, sep="")]] +
      (1 - beta2) * gradients[[paste('dW', L, sep="")]] *
      gradients[[paste('dW', L, sep="")]]
    s[[paste("db", L, sep="")]] = beta2 * s[[paste("db", L, sep="")]] +
      (1 - beta2) * gradients[[paste('db', L, sep="")]] *
      gradients[[paste('db', L, sep="")]]

    # 计算二阶矩的偏差修正估计。
    s_corrected[[paste("dW", L, sep="")]] = s[[paste("dW", L, sep="")]] / (1 - beta2^t)
    s_corrected[[paste("db", L, sep="")]] = s[[paste("db", L, sep="")]] / (1 - beta2^t)

    # 更新参数。
    d1 = sqrt(s_corrected[[paste("dW", L, sep="")]] + epsilon)
    d2 = sqrt(s_corrected[[paste("db", L, sep="")]] + epsilon)
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] -
      learningRate * v_corrected[[paste("dW", L, sep="")]] / d1
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] -
      learningRate * v_corrected[[paste("db", L, sep="")]] / d2
  } else if (outputActivationFunc == "softmax") {
    v[[paste("dW", L, sep="")]] = beta1 * v[[paste("dW", L, sep="")]] +
      (1 - beta1) * t(gradients[[paste('dW', L, sep="")]])
    v[[paste("db", L, sep="")]] = beta1 * v[[paste("db", L, sep="")]] +
      (1 - beta1) * t(gradients[[paste('db', L, sep="")]])

    # 计算一阶矩的偏差修正估计。
    v_corrected[[paste("dW", L, sep="")]] = v[[paste("dW", L, sep="")]] / (1 - beta1^t)
    v_corrected[[paste("db", L, sep="")]] = v[[paste("db", L, sep="")]] / (1 - beta1^t)

    # 梯度的逐元素相乘
    s[[paste("dW", L, sep="")]] = beta2 * s[[paste("dW", L, sep="")]] +
      (1 - beta2) * t(gradients[[paste('dW', L, sep="")]]) *
      t(gradients[[paste('dW', L, sep="")]])
    s[[paste("db", L, sep="")]] = beta2 * s[[paste("db", L, sep="")]] +
      (1 - beta2) * t(gradients[[paste('db', L, sep="")]]) *
      t(gradients[[paste('db', L, sep="")]])

    # 计算二阶矩的偏差修正估计。
    s_corrected[[paste("dW", L, sep="")]] = s[[paste("dW", L, sep="")]] / (1 - beta2^t)
    s_corrected[[paste("db", L, sep="")]] = s[[paste("db", L, sep="")]] / (1 - beta2^t)

    # 更新参数。
    d1 = sqrt(s_corrected[[paste("dW", L, sep="")]] + epsilon)
    d2 = sqrt(s_corrected[[paste("db", L, sep="")]] + epsilon)
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] -
      learningRate * v_corrected[[paste("dW", L, sep="")]] / d1
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] -
      learningRate * v_corrected[[paste("db", L, sep="")]] / d2
  }

  return(parameters)
}
```

# L 层深度学习模型执行

## 函数：`L_Layer_DeepModel`

执行一个 L 层深度学习模型。

### 输入参数
- `X`：输入特征
- `Y`：输出标签
- `layersDimensions`：各层维度
- `hiddenActivationFunc`：隐藏层激活函数，`relu` / `tanh`
- `outputActivationFunc`：输出层激活函数，`sigmoid` / `softmax`
- `learningRate`：学习率
- `lambd`：正则化参数
- `keep_prob`：Dropout 保留概率
- `numIterations`：迭代次数
- `initType`：初始化类型

### 输出
- 更新后的权重参数

```r
L_Layer_DeepModel <- function(X, Y, layersDimensions,
                              hiddenActivationFunc='relu',
                              outputActivationFunc= 'sigmoid',
                              learningRate = 0.5,
                              lambd=0,
                              keep_prob=1,
                              numIterations = 10000,
                              initType="default",
                              print_cost=FALSE) {
  # 将成本向量初始化为 NULL
  costs <- NULL

  # 参数初始化。
  if (initType == "He") {
    parameters = HeInitializeDeepModel(layersDimensions)
  } else if (initType == "Xav") {
    parameters = XavInitializeDeepModel(layersDimensions)
  } else {
    parameters = initializeDeepModel(layersDimensions)
  }

  # 循环（梯度下降）
  for(i in 0:numIterations) {
    # 前向传播：[LINEAR -> RELU]*(L-1) -> LINEAR -> SIGMOID/SOFTMAX。
    retvals = forwardPropagationDeep(X, parameters, keep_prob,
                                     hiddenActivationFunc,
                                     outputActivationFunc=outputActivationFunc)
    AL <- retvals[['AL']]
    caches <- retvals[['caches']]
    dropoutMat <- retvals[['dropoutMat']]

    # 计算成本。
    if(lambd == 0) {
      cost <- computeCost(AL,
                          Y, outputActivationFunc=outputActivationFunc,
                          numClasses=layersDimensions[length(layersDimensions)])
    } else {
      cost <- computeCostWithReg(parameters, AL, Y, lambd,
                                 outputActivationFunc=outputActivationFunc,
                                 numClasses=layersDimensions[length(layersDimensions)])
    }

    # 反向传播。
    gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd, keep_prob, hiddenActivationFunc,
                                        outputActivationFunc=outputActivationFunc,
                                        numClasses=layersDimensions[length(layersDimensions)])

    # 更新参数。
    parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

    if(i %% 1000 == 0) {
      costs = c(costs, cost)
      print(cost)
    }
  }

  retvals <- list("parameters"=parameters, "costs"=costs)
  return(retvals)
}
```

# L 层深度学习模型执行（随机梯度下降）

## 函数：`L_Layer_DeepModel_SGD`

执行一个带有随机梯度下降的 L 层深度学习模型。

### 输入参数
- `X`：输入特征
- `Y`：输出标签
- `layersDimensions`：各层维度
- `hiddenActivationFunc`：隐藏层激活函数，`relu` / `tanh`
- `outputActivationFunc`：输出层激活函数，`sigmoid` / `softmax`
- `learningRate`：学习率
- `lrDecay`：是否启用学习率衰减
- `decayRate`：衰减率
- `lambd`：正则化参数
- `keep_prob`：Dropout 保留概率
- `optimizer`：优化器类型
- `beta`：动量参数
- `beta1`：一阶矩估计指数衰减率
- `beta2`：二阶矩估计指数衰减率
- `epsilon`：数值稳定性常数
- `mini_batch_size`：小批量大小
- `num_epochs`：训练轮数

### 输出
- 每次迭代后更新的权重

```r
L_Layer_DeepModel_SGD <- function(X, Y, layersDimensions,
                                  hiddenActivationFunc='relu',
                                  outputActivationFunc= 'sigmoid',
                                  learningRate = .3,
                                  lrDecay=FALSE,
                                  decayRate=1,
                                  lambd=0,
                                  keep_prob=1,
                                  optimizer="gd",
                                  beta=0.9,
                                  beta1=0.9,
                                  beta2=0.999,
                                  epsilon=10^-8,
                                  mini_batch_size = 64,
                                  num_epochs = 2500) {
  # 函数体未在输入文本中完全给出
}
```

