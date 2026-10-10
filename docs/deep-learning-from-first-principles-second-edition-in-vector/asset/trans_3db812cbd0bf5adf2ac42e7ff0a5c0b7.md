
# 给定输入预测输出

## 输入 : parameters

## : X

## 输出: predictions

```r
predict <- function(parameters, X, hiddenActivationFunc='relu'){
  fwdProp <- forwardPropagationDeep(X, parameters, hiddenActivationFunc)
  predictions <- fwdProp$AL > 0.5
  return (predictions)
}
```

# 绘制决策边界

## 此函数使用 ggplot2

```r
plotDecisionBoundary <- function(z, retvals, hiddenActivationFunc, lr){
  # 找到数据的最小值和最大值
  xmin <- min(z[,1])
  xmax <- max(z[,1])
  ymin <- min(z[,2])
  ymax <- max(z[,2])
  
  # 创建一个值的网格
  a = seq(xmin, xmax, length=100)
  b = seq(ymin, ymax, length=100)
  grid <- expand.grid(x=a, y=b)
  colnames(grid) <- c('x1', 'x2')
  grid1 <- t(grid)
  
  # 预测该网格的输出
  q <- predict(retvals$parameters, grid1, hiddenActivationFunc)
  q1 <- t(data.frame(q))
  q2 <- as.numeric(q1)
  grid2 <- cbind(grid, q2)
  colnames(grid2) <- c('x1', 'x2', 'q2')
  
  z1 <- data.frame(z)
  names(z1) <- c("x1", "x2", "y")
  atitle = paste("Decision boundary for learning rate:", lr)
  
  # 绘制边界的等高线
  ggplot(z1) +
    geom_point(data = z1, aes(x = x1, y = x2, color = y)) +
    stat_contour(data = grid2, aes(x = x1, y = x2, z = q2, color=q2), alpha = 0.9) +
    ggtitle(atitle)
}
```

# 给定数据集预测概率得分

## 输入 : parameters

## : X

## 输出: 输出的概率

```r
computeScores <- function(parameters, X, hiddenActivationFunc='relu'){
  fwdProp <- forwardPropagationDeep(X, parameters, hiddenActivationFunc)
  scores <- fwdProp$AL
  return (scores)
}
```

# 3.3 Octave

```matlab
############################################################################################################
#
# File: DLfunctions3.m
# Developer: Tinniam V Ganesh
# Date : 30 Jan 2018
#
##########################################################################################################

1;

# 定义 Sigmoid 函数
function [A, cache] = sigmoid(Z)
  A = 1 ./ (1 + exp(-Z));
  cache = Z;
end

# 定义 Relu 函数
function [A, cache] = relu(Z)
  A = max(0, Z);
  cache = Z;
end

# 定义 Tanh 函数
function [A, cache] = tanhAct(Z)
  A = tanh(Z);
  cache = Z;
end

# 定义 Relu 导数
function [dZ] = reluDerivative(dA, cache)
  Z = cache;
  dZ = dA;
  # 获取大于 0 的元素
  a = (Z > 0);
  # 仅选择 Z > 0 的那些元素
  dZ = dZ .* a;
end

# 定义 Sigmoid 导数
function [dZ] = sigmoidDerivative(dA, cache)
  Z = cache;
  s = 1 ./ (1 + exp(-Z));
  dZ = dA .* s .* (1 - s);
end

# 定义 Tanh 导数
function [dZ] = tanhDerivative(dA, cache)
  Z = cache;
  a = tanh(Z);
  dZ = dA .* (1 - a .^ 2);
end

# 初始化模型
# 输入 : 特征数量
# 隐藏单元数量
# 输出层单元数量
# 返回: 权重和偏置矩阵及向量
# 为 L 层初始化模型
# 输入 : 每层单元数量的向量
# 返回: 所有层的初始权重和偏置矩阵作为元胞数组
function [W, b] = initializeDeepModel(layerDimensions)
  rand("seed", 3);
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 从 1 循环到 L
  # 为权重和偏置创建元胞数组
  for l = 2:size(layerDimensions)(2)
    W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * 0.01; # 乘以 .01
    b{l-1} = zeros(layerDimensions(l), 1);
  endfor
end

# 计算深度网络前向传播中第 'l' 层的激活值
# 输入 : A_prev - 上一层的激活值
# W,b - 权重和偏置矩阵及向量
# activationFunc - 激活函数 - sigmoid, tanh, relu 等
# 返回 : A, forward_cache, activation_cache
# :
# Z = W * X + b
# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)
function [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc)
  # 计算 Z
  Z = W * A_prev + b;
  # 创建一个元胞数组
  forward_cache = {A_prev, W, b};
  # 计算 sigmoid 的激活值
  if (strcmp(activationFunc, "sigmoid"))
    [A, activation_cache] = sigmoid(Z);
  elseif (strcmp(activationFunc, "relu")) # 计算 Relu 的激活值
    [A, activation_cache] = relu(Z);
  elseif(strcmp(activationFunc, 'tanh')) # 计算 tanh 的激活值
    [A, activation_cache] = tanhAct(Z);
  endif
end

# 计算第 1..L 层的前向传播
# 输入 : X - 输入特征
# paramaters: 权重和偏置
# hiddenActivationFunc - 隐藏层的激活函数 Relu/tanh
# 返回 : AL, forward_caches, activation_caches 作为元胞数组
# 前向传播在第 1..L-1 层使用 Relu/tanh 激活函数，在第 L 层使用 sigmoid 激活函数
function [AL, forward_caches, activation_caches] = forwardPropagationDeep(X, weights, biases, hiddenActivationFunc='relu')
  # 创建一个空元胞数组
  forward_caches = {};
  activation_caches = {};
  # 将 A 设为 X (A0)
  A = X;
  L = length(weights); # 神经网络中的层数
  # 从第 1 层循环到第 L 层
  for l = 1:L-1
    A_prev = A;
    # Zi = Wi x Ai-1 + bi 和 Ai = g(Zi)
    W = weights{l};
    b = biases{l};
    [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc=hiddenActivationFunc);
    forward_caches{l} = forward_cache;
    activation_caches{l} = activation_cache;
  endfor
  # 因为这是二分类，所以在最后一层使用 sigmoid 激活函数
  W = weights{L};
  b = biases{L};
  [AL, forward_cache, activation_cache] = layerActivationForward(A, W, b, activationFunc = "sigmoid");
  forward_caches{L} = forward_cache;
  activation_caches{L} = activation_cache;
end

# 计算代价
# 输入 : 最后一层的激活值
# : 数据的输出
# 输出: 代价
function [cost] = computeCost(AL, Y)
  numTraining = size(Y)(2);
  # 逐元素相乘计算 logprobs
  cost = -1/numTraining * sum((Y .* log(AL)) + (1-Y) .* log(1-AL));
end

# 计算 layerActivationBackward
# 输入 : 神经网络参数 - dA
# # cache - forward_cache & activation_cache
# 返回: dA_prev, dW, db
# dL/dWi= dL/dZi*Al-1
# dl/dbl = dL/dZl
# dL/dZ_prev=dL/dZl*W
function [dA_prev, dW, db] = layerActivationBackward(dA, forward_cache, activation_cache, activationFunc)
  if (strcmp(activationFunc, "relu"))
    dZ = reluDerivative(dA, activation_cache);
  elseif (strcmp(activationFunc, "sigmoid"))
    dZ = sigmoidDerivative(dA, activation_cache);
  elseif(strcmp(activationFunc, "tanh"))
    dZ = tanhDerivative(dA, activation_cache);
  endif
  
  A_prev = forward_cache{1};
  W = forward_cache{2};
  b = forward_cache{3};
  numTraining = size(A_prev)(2);
  dW = 1/numTraining * dZ * A_prev';
  db = 1/numTraining * sum(dZ, 2);
  dA_prev = W' * dZ;
end

# 计算 1 个周期的反向传播
# 输入 : AL: L 层网络的输出 - weights
# # Y 真实输出
# # activation_caches
# # forward_caches
# layerActivationForward() 的每个缓存，带有 "relu"/"tanh"
# #(即 caches[l], 对于 l in range(L-1) 即 l = 0...L-2)
# #layerActivationForward() 的缓存，带有 "sigmoid" (即 caches[L-1])
# hiddenActivationFunc - 隐藏层的激活函数
#
# 返回 (元胞数组): gradsDA, gradsDW, gradsDB
function [gradsDA, gradsDW, gradsDB] = backwardPropagationDeep(AL, Y, activation_caches, forward_caches, hiddenActivationFunc='relu')
  # 设置层数
  L = length(activation_caches);
  m = size(AL)(2);
  # 初始化反向传播
  # dl/dAL= -(y/a + (1-y)/(1-a)) - 在输出层
  dAL = -((Y ./ AL) - (1 - Y) ./ (1 - AL));
  # 因为这是二分类，输出层的激活函数是 sigmoid
  # 获取最后一层的梯度
  # 输入: "AL, Y, caches"。
  # 输出: "gradients["dAL"]", gradients["dWL"]", gradients["dbL"]"
  activation_cache = activation_caches{L};
  forward_cache = forward_caches{L};
  # 注意元胞数组包含一个前向缓存数组。要访问它，我们需要包含索引 {1}
```
