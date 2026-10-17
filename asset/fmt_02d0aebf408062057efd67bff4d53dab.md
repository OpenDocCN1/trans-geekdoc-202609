
```octave
############################################################################################################
#
# File : DLfunctions61.m
# Author : Tinniam V Ganesh
# Date : 16 Apr 2018
#
##########################################################################################################

1;

# 定义 sigmoid 函数
function [A, cache] = sigmoid(Z)
  A = 1 ./ (1 + exp(-Z));
  cache = Z;
end

# 定义 Relu 函数
function [A, cache] = relu(Z)
  A = max(0, Z);
  cache = Z;
end

# 定义 Relu 函数
function [A, cache] = tanhAct(Z)
  A = tanh(Z);
  cache = Z;
end

# 定义 Softmax 函数
function [A, cache] = softmax(Z)
  # 获取未归一化的概率
  exp_scores = exp(Z');
  # 对每个样本进行归一化
  A = exp_scores ./ sum(exp_scores, 2);
  cache = Z;
end

# 定义稳定 Softmax 函数
function [A, cache] = stableSoftmax(Z)
  # 按每行的最大值进行归一化
  shiftZ = Z' - max(Z', [], 2);
  exp_scores = exp(shiftZ);
  # 对每个样本进行归一化
  A = exp_scores ./ sum(exp_scores, 2);
  #disp("sm")
  #disp(A);
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

# 用 1 填充 Y=1 所在行的矩阵
# 如果 K 不是 3 或 10，可能需要修改此函数
# 此函数用于计算 softmax 导数
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

# 定义 Softmax 导数
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

# 定义稳定 Softmax 导数
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

# 为 L 层初始化模型
# 输入：每层单元数的列表
# 返回：所有层的初始权重和偏置矩阵
function [W, b] = initializeDeepModel(layerDimensions)
  rand("seed", 3);
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 遍历层维度 1..L
  # 为权重和偏置创建元胞数组
  for l = 2:size(layerDimensions)(2)
    W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * 0.01; # 乘以 .01
    b{l-1} = zeros(layerDimensions(l), 1);
  endfor
end

# L 层的 He 初始化
# 输入：每层单元数的向量
# 返回：所有层的初始权重和偏置矩阵
function [W, b] = HeInitializeDeepModel(layerDimensions)
  rand("seed", 3);
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 遍历层维度 1..L
  # 为权重和偏置创建元胞数组
  for l = 2:size(layerDimensions)(2)
    W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * sqrt(2 / layerDimensions(l-1)); # 乘以 .01
    b{l-1} = zeros(layerDimensions(l), 1);
  endfor
end

# L 层的 Xavier 初始化
# 输入：每层单元数的向量
# 返回：所有层的初始权重和偏置矩阵
function [W, b] = XavInitializeDeepModel(layerDimensions)
  rand("seed", 3);
  # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
  # 偏置是大小为 (l,1) 的向量
  # 遍历层维度 1..L
  # 为权重和偏置创建元胞数组
  for l = 2:size(layerDimensions)(2)
    W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * sqrt(1 / layerDimensions(l-1)); # 乘以 .01
    b{l-1} = zeros(layerDimensions(l), 1);
  endfor
end

# 计算深度网络中第 'l' 层的前向传播激活值
# 输入：A_prev - 上一层的激活值
# W,b - 权重和偏置矩阵及向量
# activationFunc - 激活函数 - sigmoid, tanh, relu 等
# 返回：该层的激活值
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
  elseif (strcmp(activationFunc, 'tanh')) # 计算 tanh 的激活值
    [A, activation_cache] = tanhAct(Z);
  elseif (strcmp(activationFunc, 'softmax')) # 计算 tanh 的激活值
    #[A, activation_cache] = softmax(Z);
    [A, activation_cache] = stableSoftmax(Z);
  endif
end

# 计算第 1..L 层的前向传播
# 输入：X - 输入特征
# paramaters: 权重和偏置
# keep_prob
# hiddenActivationFunc - 隐藏层激活函数 Relu/tanh/sigmoid
# outputActivationFunc- sigmoid/softmax
# 返回：AL
# caches
# 前向传播在第 1..L-1 层使用 Relu/tanh 激活函数，在第 L 层使用 sigmoid 激活函数
function [AL, forward_caches, activation_caches, dropoutMat] = forwardPropagationDeep(X, weights, biases, keep_prob = 1, hiddenActivationFunc = 'relu', outputActivationFunc = 'sigmoid')
  # 创建一个空元胞数组
  forward_caches = {};
  activation_caches = {};
  dropoutMat = {};
  # 将 A 设为 X (A0)
  A = X;
  L = length(weights); # 神经网络中的层数
  # 从第 1 层循环到第 L-1 层
  for l = 1:L-1
    A_prev = A;
    # Zi = Wi x Ai-1 + bi 和 Ai = g(Zi)
    W = weights{l};
    b = biases{l};
    [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc = hiddenActivationFunc);
    D = rand(size(A)(1), size(A)(2));
    D = (D < keep_prob);
    # 乘以 DropoutMat
    A = A .* D;
    # 除以 keep_prob 以保持期望值不变
    A = A ./ keep_prob;
    # 存储 D
    dropoutMat{l} = D;
    forward_caches{l} = forward_cache;
    activation_caches{l} = activation_cache;
  endfor
  # 由于这是二分类，在最后一层使用 sigmoid 激活函数
  W = weights{L};
  b = biases{L};
  [AL, forward_cache, activation_cache] = layerActivationForward(A, W, b, activationFunc = outputActivationFunc);

  forward_caches{L} = forward_cache;
  activation_caches{L} = activation_cache;
end
```

# 神经网络反向传播实现

## 前向传播缓存存储

```matlab
[AL, forward_cache, activation_cache] = layerActivationForward(A, W, b, activationFunc = outputActivationFunc);

forward_caches{L} = forward_cache;
activation_caches{L} = activation_cache;
```

## 列选择函数 `pickColumns`

此函数用于 `computeCost` 中。

```matlab
function [a] = pickColumns(AL, Y, numClasses)
    if (numClasses == 3)
        a = [AL(Y==0,1) ; AL(Y==1,2) ; AL(Y==2,3)];
    elseif (numClasses == 10)
        a = [AL(Y==0,1) ; AL(Y==1,2) ; AL(Y==2,3) ; AL(Y==3,4) ; AL(Y==4,5) ;
             AL(Y==5,6) ; AL(Y==6,7) ; AL(Y==7,8) ; AL(Y==8,9) ; AL(Y==9,10)];
    endif
end
```

## 成本计算函数 `computeCost`

**输入**：

- `AL`：最后一层的激活值
- `Y`：数据输出
- `outputActivationFunc`：sigmoid/softmax
- `numClasses`：类别数

**输出**：`cost`

```matlab
function [cost] = computeCost(AL, Y, outputActivationFunc="sigmoid", numClasses)
    if (strcmp(outputActivationFunc, "sigmoid"))
        numTraining = size(Y)(2);
        # Element wise multiply for logprobs
        cost = -1/numTraining * sum((Y .* log(AL)) + (1-Y) .* log(1-AL));
    elseif (strcmp(outputActivationFunc, 'softmax'))
        numTraining = size(Y)(2);
        Y = Y';
        # Select rows where Y=0,1,and 2 and concatenate to a long vector
        a = pickColumns(AL, Y, numClasses);
        # Select the correct column for log prob
        correct_probs = -log(a);
        # Compute log loss
        cost = sum(correct_probs) / numTraining;
    endif
end
```

## 带正则化的成本计算 `computeCostWithReg`

**输入**：

- `weights`：权重
- `AL`：最后一层的激活值
- `Y`：数据输出
- `lambd`：正则化参数
- `outputActivationFunc`：sigmoid/softmax
- `numClasses`：类别数

**输出**：`cost`
