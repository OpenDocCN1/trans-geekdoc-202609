

# 输出

`gradients["dA" + str(l + 1)]`, `gradients["dW" + str(l + 1)]`, `gradients["db" + str(l + 1)]`

```r
current_cache = caches[[l]]$cache

if (lambd == 0) {
  cat("l=", l)
  # 获取 dropout 矩阵
  D <- dropoutMat[[paste("D", l, sep="")]]
  # 将梯度与 dropout 矩阵相乘
  gradients[[paste('dA', l+1, sep="")]] = gradients[[paste('dA', l+1, sep="")]] * D
  # 除以 keep_prob 以保持期望值不变
  gradients[[paste('dA', l+1, sep="")]] = gradients[[paste('dA', l+1, sep="")]] / keep_prob
  retvals = layerActivationBackward(gradients[[paste('dA', l+1, sep="")]], current_cache, Y,
                                    activationFunc = hiddenActivationFunc)
} else {
  retvals = layerActivationBackwardWithReg(gradients[[paste('dA', l+1, sep="")]], current_cache, Y, lambd,
                                           activationFunc = hiddenActivationFunc)
}

gradients[[paste("dA", l, sep="")]] <- retvals[['dA_prev']]
gradients[[paste("dW", l, sep="")]] <- retvals[['dW']]
gradients[[paste("db", l, sep="")]] <- retvals[['db']]
}

return(gradients)
}
```

# 执行梯度下降

**输入**：权重和偏置、梯度、学习率、`outputActivationFunc` - 隐藏层的激活函数 sigmoid/softmax

**输出**：1 次迭代后更新的权重

```r
gradientDescent <- function(parameters, gradients, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # 神经网络中的层数
  # 每个参数的更新规则。使用 for 循环。
  for(l in 1:(L-1)) {
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] - learningRate * gradients[[paste("dW", l, sep="")]]
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] - learningRate * gradients[[paste("db", l, sep="")]]
  }
  if(outputActivationFunc == "sigmoid") {
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * gradients[[paste("dW", L, sep="")]]
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * gradients[[paste("db", L, sep="")]]
  } else if (outputActivationFunc == "softmax") {
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * t(gradients[[paste("dW", L, sep="")]])
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * t(gradients[[paste("db", L, sep="")]])
  }
  return(parameters)
}
```

# 执行带动量的梯度下降

**输入**：权重和偏置、`beta`、梯度、学习率、`outputActivationFunc` - 隐藏层的激活函数 sigmoid/softmax

**输出**：1 次迭代后更新的权重

```r
gradientDescentWithMomentum <- function(parameters, gradients, v, beta, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # 神经网络中的层数
  # 每个参数的更新规则。使用 for 循环。
  for(l in 1:(L-1)) {
    # 计算速度
    # v[['dWk']] = beta * v[['dWk']] + (1-beta) * dWk
    v[[paste("dW", l, sep="")]] = beta * v[[paste("dW", l, sep="")]] + (1-beta) * gradients[[paste('dW', l, sep="")]]
    v[[paste("db", l, sep="")]] = beta * v[[paste("db", l, sep="")]] + (1-beta) * gradients[[paste('db', l, sep="")]]
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] - learningRate * v[[paste("dW", l, sep="")]]
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] - learningRate * v[[paste("db", l, sep="")]]
  }
  # 计算第 L 层
  if(outputActivationFunc == "sigmoid") {
    v[[paste("dW", L, sep="")]] = beta * v[[paste("dW", L, sep="")]] + (1-beta) * gradients[[paste('dW', L, sep="")]]
    v[[paste("db", L, sep="")]] = beta * v[[paste("db", L, sep="")]] + (1-beta) * gradients[[paste('db', L, sep="")]]
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * v[[paste("dW", l, sep="")]]
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * v[[paste("db", l, sep="")]]
  } else if (outputActivationFunc == "softmax") {
    v[[paste("dW", L, sep="")]] = beta * v[[paste("dW", L, sep="")]] + (1-beta) * t(gradients[[paste('dW', L, sep="")]])
    v[[paste("db", L, sep="")]] = beta * v[[paste("db", L, sep="")]] + (1-beta) * t(gradients[[paste('db', L, sep="")]])
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * t(gradients[[paste("dW", L, sep="")]])
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * t(gradients[[paste("db", L, sep="")]])
  }
  return(parameters)
}
```

# 执行带 RMSProp 的梯度下降

**输入**：`parameters`、`gradients`、`s`、`beta1`、`epsilon`、学习率、`outputActivationFunc` - 隐藏层的激活函数 sigmoid/softmax

**输出**：1 次迭代后更新的权重

```r
gradientDescentWithRMSProp <- function(parameters, gradients, s, beta1, epsilon, learningRate, outputActivationFunc="sigmoid") {
  L = length(parameters)/2 # 神经网络中的层数
  # 每个参数的更新规则。使用 for 循环。
  for(l in 1:(L-1)) {
    # 计算 RMSProp
    # s[['dWk']] = beta1 * s[['dWk']] + (1-beta1) * dWk**2 / sqrt(s[['dWk']])
    # 梯度的逐元素相乘
    s[[paste("dW", l, sep="")]] = beta1 * s[[paste("dW", l, sep="")]] + (1-beta1) * gradients[[paste('dW', l, sep="")]] * gradients[[paste('dW', l, sep="")]]
    s[[paste("db", l, sep="")]] = beta1 * s[[paste("db", l, sep="")]] + (1-beta1) * gradients[[paste('db', l, sep="")]] * gradients[[paste('db', l, sep="")]]
    parameters[[paste("W", l, sep="")]] = parameters[[paste("W", l, sep="")]] - learningRate * gradients[[paste('dW', l, sep="")]] / sqrt(s[[paste("dW", l, sep="")]] + epsilon)
    parameters[[paste("b", l, sep="")]] = parameters[[paste("b", l, sep="")]] - learningRate * gradients[[paste('db', l, sep="")]] / sqrt(s[[paste("db", l, sep="")]] + epsilon)
  }
  # 计算第 L 层
  if(outputActivationFunc == "sigmoid") {
    s[[paste("dW", L, sep="")]] = beta1 * s[[paste("dW", L, sep="")]] + (1-beta1) * gradients[[paste('dW', L, sep="")]] * gradients[[paste('dW', L, sep="")]]
    s[[paste("db", L, sep="")]] = beta1 * s[[paste("db", L, sep="")]] + (1-beta1) * gradients[[paste('db', L, sep="")]] * gradients[[paste('db', L, sep="")]]
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * gradients[[paste('dW', l, sep="")]] / sqrt(s[[paste("dW", L, sep="")]] + epsilon)
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * gradients[[paste('db', l, sep="")]] / sqrt(s[[paste("db", L, sep="")]] + epsilon)
  } else if (outputActivationFunc == "softmax") {
    s[[paste("dW", L, sep="")]] = beta1 * s[[paste("dW", L, sep="")]] + (1-beta1) * t(gradients[[paste('dW', L, sep="")]]) * t(gradients[[paste('dW', L, sep="")]])
    s[[paste("db", L, sep="")]] = beta1 * s[[paste("db", L, sep="")]] + (1-beta1) * t(gradients[[paste('db', L, sep="")]]) * t(gradients[[paste('db', L, sep="")]])
    parameters[[paste("W", L, sep="")]] = parameters[[paste("W", L, sep="")]] - learningRate * t(gradients[[paste("dW", L, sep="")]]) / sqrt(s[[paste("dW", L, sep="")]] + epsilon)
    parameters[[paste("b", L, sep="")]] = parameters[[paste("b", L, sep="")]] - learningRate * t(gradients[[paste("db", L, sep="")]]) / sqrt(s[[paste("db", L, sep="")]] + epsilon)
  }
  return(parameters)
}
```

# 执行带 Adam 的梯度下降

**输入**：`parameters`、`gradients`、`v`、`s`、`t`、`beta1`、`beta2`、`epsilon`、学习率、`outputActivationFunc` - 隐藏层的激活函数 sigmoid/softmax

**输出**：1 次迭代后更新的权重

```r
gradientDescentWithAdam <- function(parameters, gradients, v, s, t, beta1=0.9, beta2=0.999, epsilon=10^-8,
```

