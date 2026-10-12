
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
