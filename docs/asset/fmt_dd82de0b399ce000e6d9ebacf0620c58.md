
## 参数列表

- `outputActivationFunc`：输出层激活函数（`sigmoid` / `softmax`）
- `learningRate`：学习率
- `lrDecay`：是否启用学习率衰减
- `decayRate`：衰减率
- `lambd`：正则化参数
- `keep_prob`：Dropout 保留概率
- `optimizer`：优化器类型（`gd`、`momentum`、`rmsprop`、`adam`）
- `beta`：Momentum/RMSprop 的动量参数
- `beta1`：Adam 的一阶矩估计指数衰减率
- `beta2`：Adam 的二阶矩估计指数衰减率
- `epsilon`：数值稳定性常数
- `mini_batch_size`：小批量大小
- `num_epochs`：训练轮数
- `print_cost`：是否打印成本

## 输出

- 每次迭代后更新的权重

## 实现代码

### R 语言实现

```r
L_Layer_DeepModel_SGD <- function(X, Y, layersDimensions,
                                  hiddenActivationFunc = 'relu',
                                  outputActivationFunc = 'sigmoid',
                                  learningRate = .3,
                                  lrDecay = FALSE,
                                  decayRate = 1,
                                  lambd = 0,
                                  keep_prob = 1,
                                  optimizer = "gd",
                                  beta = 0.9,
                                  beta1 = 0.9,
                                  beta2 = 0.999,
                                  epsilon = 10^-8,
                                  mini_batch_size = 64,
                                  num_epochs = 2500,
                                  print_cost = FALSE) {

  # 检查数值
  cat("learningRate= ", learningRate)
  cat("\n")
  cat("lambd=", lambd)
  cat("\n")
  cat("keep_prob=", keep_prob)
  cat("\n")
  cat("optimizer=", optimizer)
  cat("\n")
  cat("lrDecay=", lrDecay)
  cat("\n")
  cat("decayRate=", decayRate)
  cat("\n")
  cat("beta=", beta)
  cat("\n")
  cat("beta1=", beta1)
  cat("\n")
  cat("beta2=", beta2)
  cat("\n")
  cat("epsilon=", epsilon)
  cat("\n")
  cat("mini_batch_size=", mini_batch_size)
  cat("\n")
  cat("num_epochs=", num_epochs)
  cat("\n")

  set.seed(1)

  # 初始化成本向量为 NULL
  costs <- NULL
  t <- 0

  # 参数初始化
  parameters = initializeDeepModel(layersDimensions)

  # 初始化优化器
  if (optimizer == "momentum") {
    v <- initializeVelocity(parameters)
  } else if (optimizer == "rmsprop") {
    s <- initializeRMSProp(parameters)
  } else if (optimizer == "adam") {
    adamVals <- initializeAdam(parameters)
  }

  seed = 10

  # 循环训练轮数
  for (i in 0:num_epochs) {
    seed = seed + 1
    minibatches = random_mini_batches(X, Y, mini_batch_size, seed)

    for (batch in 1:length(minibatches)) {
      mini_batch_X = minibatches[[batch]][['mini_batch_X']]
      mini_batch_Y = minibatches[[batch]][['mini_batch_Y']]

      # 前向传播
      retvals = forwardPropagationDeep(mini_batch_X, parameters, keep_prob, hiddenActivationFunc,
                                       outputActivationFunc = outputActivationFunc)

      AL <- retvals[['AL']]
      caches <- retvals[['caches']]
      dropoutMat <- retvals[['dropoutMat']]

      # 计算成本
      if (lambd == 0) {
        cost <- computeCost(AL,
                            mini_batch_Y, outputActivationFunc = outputActivationFunc,
                            numClasses = layersDimensions[length(layersDimensions)])
      } else {
        cost <- computeCostWithReg(parameters, AL, Y, lambd,
                                   outputActivationFunc = outputActivationFunc,
                                   numClasses = layersDimensions[length(layersDimensions)])
      }

      # 反向传播
      gradients = backwardPropagationDeep(AL, mini_batch_Y, caches, dropoutMat, lambd, keep_prob, hiddenActivationFunc,
                                          outputActivationFunc = outputActivationFunc,
                                          numClasses = layersDimensions[length(layersDimensions)])

      if (optimizer == "gd") {
        # 更新参数
```

### Octave/Matlab 实现

#### 文件信息
```matlab
############################################################################################################
#
# File : DLfunctions7.R
# Author : Tinniam V Ganesh
# Date : 16 Apr 2018
#
##########################################################################################################
1;
```

#### 激活函数定义

**Sigmoid 函数**
```matlab
function [A,cache] = sigmoid(Z)
    A = 1 ./ (1 + exp(-Z));
    cache = Z;
end
```

**ReLU 函数**
```matlab
function [A,cache] = relu(Z)
    A = max(0, Z);
    cache = Z;
end
```

**Tanh 函数**
```matlab
function [A,cache] = tanhAct(Z)
    A = tanh(Z);
    cache = Z;
end
```

**Softmax 函数**
```matlab
function [A,cache] = softmax(Z)
    # 获取未归一化的概率
    exp_scores = exp(Z');
    # 对每个样本进行归一化
    A = exp_scores ./ sum(exp_scores, 2);
    cache = Z;
end
```

**稳定 Softmax 函数**
```matlab
function [A,cache] = stableSoftmax(Z)
    # 按每行的最大值进行归一化
    shiftZ = Z' - max(Z', [], 2);
    exp_scores = exp(shiftZ);
    # 对每个样本进行归一化
    A = exp_scores ./ sum(exp_scores, 2);
    # disp("sm")
    # disp(A);
    cache = Z;
end
```

#### 导数函数定义

**ReLU 导数**
```matlab
function [dZ] = reluDerivative(dA, cache)
    Z = cache;
    dZ = dA;
    # 获取大于 0 的元素
    a = (Z > 0);
    # 仅选择 Z > 0 的那些元素
    dZ = dZ .* a;
end
```

**Sigmoid 导数**
```matlab
function [dZ] = sigmoidDerivative(dA, cache)
    Z = cache;
    s = 1 ./ (1 + exp(-Z));
    dZ = dA .* s .* (1 - s);
end
```

**Tanh 导数**
```matlab
function [dZ] = tanhDerivative(dA, cache)
    Z = cache;
    a = tanh(Z);
    dZ = dA .* (1 - a .^ 2);
end
```

**辅助函数：构造独热编码矩阵**
```matlab
# 用 1 填充 Y=1 所在行的矩阵
# 如果 K 不是 3 或 10，此函数可能需要修改
# 此函数用于计算 Softmax 导数
function [Y1] = popMatrix(Y, numClasses)
    Y1 = zeros(length(Y), numClasses);
    if (numClasses == 3) # 针对 3 个输出类别
        Y1(Y == 0, 1) = 1;
        Y1(Y == 1, 2) = 1;
        Y1(Y == 2, 3) = 1;
    elseif (numClasses == 10) # 针对 10 个输出类别
        Y1(Y == 0, 1) = 1;
        Y1(Y == 1, 2) = 1;
        Y1(Y == 2, 3) = 1;
        Y1(Y == 3, 4) = 1;
        Y1(Y == 4, 5) = 1;
        Y1(Y == 5, 6) = 1;
        Y1(Y == 6, 7) = 1;
        Y1(Y == 7, 8) = 1;
        Y1(Y == 8, 9) = 1;
        Y1(Y == 9, 10) = 1;
    endif
end
```

**Softmax 导数**
```matlab
function [dZ] = softmaxDerivative(dA, cache, Y, numClasses)
    Z = cache;
    # 获取未归一化的概率
    shiftZ = Z' - max(Z', [], 2);
    exp_scores = exp(shiftZ);
    # 对每个样本进行归一化
    probs = exp_scores ./ sum(exp_scores, 2);
    # dZ = pi - yi
    yi = popMatrix(Y, numClasses);
    dZ = probs - yi;
end
```

**稳定 Softmax 导数**
```matlab
function [dZ] = stableSoftmaxDerivative(dA, cache, Y, numClasses)
    Z = cache;
    # 获取未归一化的概率
    exp_scores = exp(Z');
    # 对每个样本进行归一化
    probs = exp_scores ./ sum(exp_scores, 2);
    # dZ = pi - yi
    yi = popMatrix(Y, numClasses);
    dZ = probs - yi;
end
```

#### 矩阵操作与初始化

```matlab
yi = popMatrix(Y, numClasses);
dZ = probs - yi;
```

#### 初始化深度模型 (L 层)

**输入**：每层单元数的向量  
**返回**：所有层的初始权重和偏置矩阵

```matlab
function [W, b] = initializeDeepModel(layerDimensions)
    rand("seed", 3);
    % note the Weight matrix at layer 'l' is a matrix of size (l,l-1)
    % The Bias is a vectors of size (l,1)
    % Loop through the layer dimension from 1.. L
    % Create cell arrays for Weights and biases
    for l = 2:size(layerDimensions)(2)
        W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * 0.01; % Multiply by .01
        b{l-1} = zeros(layerDimensions(l), 1);
    endfor
end
```

#### He 初始化 (L 层)

**输入**：每层单元数的向量  
**返回**：所有层的初始权重和偏置矩阵

```matlab
function [W, b] = HeInitializeDeepModel(layerDimensions)
    rand("seed", 3);
    % note the Weight matrix at layer 'l' is a matrix of size (l,l-1)
    % The Bias is a vectors of size (l,1)
    % Loop through the layer dimension from 1.. L
    % Create cell arrays for Weights and biases
    for l = 2:size(layerDimensions)(2)
        W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * sqrt(2 / layerDimensions(l-1)); % Multiply by .01
        b{l-1} = zeros(layerDimensions(l), 1);
    endfor
end
```

#### Xavier 初始化 (L 层)

**输入**：每层单元数的向量  
**返回**：所有层的初始权重和偏置矩阵
