
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

```matlab
function [cost] = computeCostWithReg(weights, AL, Y, lambd, outputActivationFunc="sigmoid", numClasses)
    if (strcmp(outputActivationFunc, "sigmoid"))
        numTraining = size(Y)(2);
        # Element wise multiply for logprobs
        cost = -1/numTraining * sum((Y .* log(AL)) + (1-Y) .* log(1-AL));
        
        # Regularization cost
        L = size(weights)(2);
        L2RegularizationCost = 0;
        for l = 1:L
            wtSqr = weights{l} .* weights{l};
            # disp(sum(sum(wtSqr,1)));
            L2RegularizationCost += sum(sum(wtSqr,1));
        endfor
        L2RegularizationCost = (lambd / (2 * numTraining)) * L2RegularizationCost;
        cost = cost + L2RegularizationCost;
        
    elseif (strcmp(outputActivationFunc, 'softmax'))
        numTraining = size(Y)(2);
        Y = Y';
        # Select rows where Y=0,1,and 2 and concatenate to a long vector
        a = pickColumns(AL, Y, numClasses);
        # Select the correct column for log prob
        correct_probs = -log(a);
        # Compute log loss
        cost = sum(correct_probs) / numTraining;
        
        # Regularization cost
        L = size(weights)(2);
        L2RegularizationCost = 0;
        for l = 1:L
            # Compute L2 Norm
            wtSqr = weights{l} .* weights{l};
            # disp(sum(sum(wtSqr,1)));
            L2RegularizationCost += sum(sum(wtSqr,1));
        endfor
        L2RegularizationCost = (lambd / (2 * numTraining)) * L2RegularizationCost;
        cost = cost + L2RegularizationCost;
    endif
end
```

## 单层反向传播 `layerActivationBackward`

**输入**：
- `dA`：神经网络参数梯度
- `forward_cache` & `activation_cache`：缓存
- `Y`：输出值
- `activationFunc`：sigmoid/softmax
- `numClasses`：类别数

**返回**：梯度 `dA_prev`, `dW`, `db`

```matlab
function [dA_prev, dW, db] = layerActivationBackward(dA, forward_cache, activation_cache, Y, activationFunc, numClasses)
    A_prev = forward_cache{1};
    W = forward_cache{2};
    b = forward_cache{3};
    numTraining = size(A_prev)(2);
    
    if (strcmp(activationFunc, "relu"))
        dZ = reluDerivative(dA, activation_cache);
    elseif (strcmp(activationFunc, "sigmoid"))
        dZ = sigmoidDerivative(dA, activation_cache);
    elseif (strcmp(activationFunc, "tanh"))
        dZ = tanhDerivative(dA, activation_cache);
    elseif (strcmp(activationFunc, "softmax"))
        # dZ = softmaxDerivative(dA, activation_cache, Y, numClasses);
        dZ = stableSoftmaxDerivative(dA, activation_cache, Y, numClasses);
    endif
    
    if (strcmp(activationFunc, "softmax"))
        W = forward_cache{2};
        b = forward_cache{3};
        # Add the regularization factor
        dW = 1/numTraining * A_prev * dZ;
        db = 1/numTraining * sum(dZ, 1);
        dA_prev = dZ * W;
    else
        W = forward_cache{2};
        b = forward_cache{3};
        # Add the regularization factor
        dW = 1/numTraining * dZ * A_prev';
        db = 1/numTraining * sum(dZ, 2);
        dA_prev = W' * dZ;
    endif
end
```

## 带正则化的单层反向传播 `layerActivationBackwardWithReg`

**输入**：
- `dA`：神经网络参数梯度
- `forward_cache` & `activation_cache`：缓存
- `Y`：输出值
- `lambd`：正则化参数
- `activationFunc`：激活函数
- `numClasses`：类别数

**返回**：梯度 `dA_prev`, `dW`, `db`

```matlab
function [dA_prev, dW, db] = layerActivationBackwardWithReg(dA, forward_cache, activation_cache, Y, lambd=0, activationFunc, numClasses)
    A_prev = forward_cache{1};
    W = forward_cache{2};
    b = forward_cache{3};
    numTraining = size(A_prev)(2);
    
    if (strcmp(activationFunc, "relu"))
        dZ = reluDerivative(dA, activation_cache);
    elseif (strcmp(activationFunc, "sigmoid"))
        dZ = sigmoidDerivative(dA, activation_cache);
    elseif (strcmp(activationFunc, "tanh"))
        dZ = tanhDerivative(dA, activation_cache);
    elseif (strcmp(activationFunc, "softmax"))
        # dZ = softmaxDerivative(dA, activation_cache, Y, numClasses);
        dZ = stableSoftmaxDerivative(dA, activation_cache, Y, numClasses);
    endif
    
    if (strcmp(activationFunc, "softmax"))
        W = forward_cache{2};
        b = forward_cache{3};
        # Add the regularization factor
        dW = 1/numTraining * A_prev * dZ + (lambd/numTraining) * W';
        db = 1/numTraining * sum(dZ, 1);
        dA_prev = dZ * W;
    else
        W = forward_cache{2};
        b = forward_cache{3};
        # Add the regularization factor
        dW = 1/numTraining * dZ * A_prev' + (lambd/numTraining) * W;
        db = 1/numTraining * sum(dZ, 2);
        dA_prev = W' * dZ;
    endif
end
```

## 深层网络反向传播 `backwardPropagationDeep`

**输入**：
- `AL`：L 层网络的输出
- `Y`：真实输出
- `activation_caches`：激活缓存列表
- `forward_caches`：前向缓存列表
- `dropoutMat`：Dropout 矩阵
- `lambd`：正则化参数
- `keep_prob`：保留概率
- `hiddenActivationFunc`：隐藏层激活函数
- `outputActivationFunc`：输出层激活函数
- `numClasses`：类别数

**返回**：
- `gradsDA`, `gradsDW`, `gradsDB`：梯度字典

```matlab
function [gradsDA, gradsDW, gradsDB] = backwardPropagationDeep(AL, Y, activation_caches, forward_caches, dropoutMat, lambd=0, keep_prob=1, hiddenActivationFunc='relu', outputActivationFunc="sigmoid", numClasses)
    # Set the number of layers
    L = length(activation_caches);
    m = size(AL)(2);
    
    if (strcmp(outputActivationFunc, "sigmoid"))
        # Initializing the backpropagation
        # dl/dAL = -(y/a + (1-y)/(1-a)) - At the output layer
        dAL = -((Y ./ AL) - (1 - Y) ./ (1 - AL));
    elseif (strcmp(outputActivationFunc, "softmax"))
        dAL = 0;
        Y = Y';
    endif
    
    # Since this is a binary classification the activation at output is sigmoid
    # Get the gradients at the last layer
    # Inputs: "AL, Y, caches".
    # Outputs: "gradients["dAL"], gradients["dWL"], gradients["dbL"]"
    activation_cache = activation_caches{L};
    forward_cache = forward_caches(L);
    
    # Note the cell array includes an array of forward caches. To get to this we need to include the index {1}
    if (lambd == 0)
        [dA, dW, db] = layerActivationBackward(dAL, forward_cache{1}, activation_cache, Y, activationFunc = outputActivationFunc, numClasses);
    else
        [dA, dW, db] = layerActivationBackwardWithReg(dAL, forward_cache{1}, activation_cache, Y, lambd, activationFunc = outputActivationFunc, numClasses);
    endif
    
    if (strcmp(outputActivationFunc, "sigmoid"))
        gradsDA{L} = dA;
    elseif (strcmp(outputActivationFunc, "softmax"))
        gradsDA{L} = dA'; # Note the transpose
    endif
    
    gradsDW{L} = dW;
    gradsDB{L} = db;
    
    # Traverse in the reverse direction
    for l = (L-1):-1:1
        # Compute the gradients for L-1 to 1 for Relu/tanh
        # Inputs: "gradients["dA" + str(l + 2)], caches".
```
