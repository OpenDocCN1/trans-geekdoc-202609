

# Octave/Matlab 神经网络实现代码

## 核心计算函数

```octave
dZ = dA .* (1 - a .^ 2);
```

## 辅助函数

### popMatrix
填充矩阵，在 Y=1 的行放置 1。

```octave
function [Y1] = popMatrix(Y, numClasses)
    Y1 = zeros(length(Y), numClasses);
    if (numClasses == 3)  # For 3 output classes
        Y1(Y == 0, 1) = 1;
        Y1(Y == 1, 2) = 1;
        Y1(Y == 2, 3) = 1;
    elseif (numClasses == 10)  # For 10 output classes
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

### softmaxDerivative
定义 Softmax 导数。

```octave
function [dZ] = softmaxDerivative(dA, cache, Y, numClasses)
    Z = cache;
    # get unnormalized probabilities
    shiftZ = Z' - max(Z', [], 2);
    exp_scores = exp(shiftZ);
    # normalize them for each example
    probs = exp_scores ./ sum(exp_scores, 2);
    # dZ = pi - yi
    yi = popMatrix(Y, numClasses);
    dZ = probs - yi;
end
```

### stableSoftmaxDerivative
定义稳定 Softmax 导数。

```octave
function [dZ] = stableSoftmaxDerivative(dA, cache, Y, numClasses)
    Z = cache;
    # get unnormalized probabilities
    exp_scores = exp(Z');
    # normalize them for each example
    probs = exp_scores ./ sum(exp_scores, 2);
    # dZ = pi - yi
    yi = popMatrix(Y, numClasses);
    dZ = probs - yi;
end
```

## 模型初始化

### initializeDeepModel
为 L 层初始化模型。

```octave
function [W, b] = initializeDeepModel(layerDimensions)
    rand("seed", 3);
    # note the Weight matrix at layer 'l' is a matrix of size (l,l-1)
    # The Bias is a vectors of size (l,1)
    # Loop through the layer dimension from 1.. L
    # Create cell arrays for Weights and biases
    for l = 2:size(layerDimensions)(2)
        W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * 0.01; # Multiply by .01
        b{l-1} = zeros(layerDimensions(l), 1);
    endfor
end
```

## 前向传播

### layerActivationForward
计算深度网络中第 `l` 层的激活值。

```octave
function [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc)
    # Compute Z
    Z = W * A_prev + b;
    # Create a cell array
    forward_cache = {A_prev, W, b};
    # Compute the activation for sigmoid
    if (strcmp(activationFunc, "sigmoid"))
        [A, activation_cache] = sigmoid(Z);
    elseif (strcmp(activationFunc, "relu"))  # Compute the activation for Relu
        [A, activation_cache] = relu(Z);
    elseif (strcmp(activationFunc, 'tanh'))  # Compute the activation for tanh
        [A, activation_cache] = tanhAct(Z);
    elseif (strcmp(activationFunc, 'softmax'))  # Compute the activation for softmax
        # [A, activation_cache] = softmax(Z);
        [A, activation_cache] = stableSoftmax(Z);
    endif
end
```

### forwardPropagationDeep
计算第 1 到 L 层的前向传播。

```octave
function [AL, forward_caches, activation_caches] = forwardPropagationDeep(X, weights, biases, hiddenActivationFunc='relu', outputActivationFunc='sigmoid')
    # Create an empty cell array
    forward_caches = {};
    activation_caches = {};
    # Set A to X (A0)
    A = X;
    L = length(weights);  # number of layers in the neural network
    # Loop through from layer 1 to upto layer L
    for l = 1:L-1
        A_prev = A;
        # Zi = Wi x Ai-1 + bi and Ai = g(Zi)
        W = weights{l};
        b = biases{l};
        [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc=hiddenActivationFunc);
        forward_caches{l} = forward_cache;
        activation_caches{l} = activation_cache;
    endfor
    # Since this is a binary classification use the sigmoid activation function in last layer
    W = weights{L};
    b = biases{L};
    [AL, forward_cache, activation_cache] = layerActivationForward(A, W, b, activationFunc=outputActivationFunc);
    forward_caches{L} = forward_cache;
    activation_caches{L} = activation_cache;
end
```

## 成本计算

### pickColumns
选取 Y==1 的列，用于 `computeCost`。

```octave
function [a] = pickColumns(AL, Y, numClasses)
    if (numClasses == 3)
        a = [AL(Y == 0, 1); AL(Y == 1, 2); AL(Y == 2, 3)];
    elseif (numClasses == 10)
        a = [AL(Y == 0, 1); AL(Y == 1, 2); AL(Y == 2, 3); AL(Y == 3, 4); AL(Y == 4, 5);
             AL(Y == 5, 6); AL(Y == 6, 7); AL(Y == 7, 8); AL(Y == 8, 9); AL(Y == 9, 10)];
    endif
end
```

### computeCost
计算成本。

```octave
function [cost] = computeCost(AL, Y, outputActivationFunc="sigmoid", numClasses)
    if (strcmp(outputActivationFunc, "sigmoid"))
        numTraining = size(Y)(2);
        # Element wise multiply for logprobs
        cost = -1/numTraining * sum((Y .* log(AL)) + (1 - Y) .* log(1 - AL));
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

## 反向传播

### layerActivationBackward
计算单层的反向传播。

```octave
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
    # Check if softmax
    if (strcmp(activationFunc, "softmax"))
        W = forward_cache{2};
        b = forward_cache{3};
        dW = 1/numTraining * A_prev * dZ;
        db = 1/numTraining * sum(dZ, 1);
        dA_prev = dZ * W;
    else
        W = forward_cache{2};
        b = forward_cache{3};
        dW = 1/numTraining * dZ * A_prev';
        db = 1/numTraining * sum(dZ, 2);
        dA_prev = W' * dZ;
    endif
end
```

### backwardPropagationDeep
计算深度网络的反向传播。

```octave
function [gradsDA, gradsDW, gradsDB] = backwardPropagationDeep(AL, Y, activation_caches, forward_caches, hiddenActivationFunc='relu', outputActivationFunc="sigmoid", numClasses)
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
    # ... (代码截断，原文未提供完整实现)
end
```

