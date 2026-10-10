
# 矩阵操作与初始化

```matlab
yi = popMatrix(Y, numClasses);
dZ = probs - yi;
```

# 初始化深度模型 (L层)

**输入**: 每层单元数的向量  
**返回**: 所有层的初始权重和偏置矩阵

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

# He 初始化 (L层)

**输入**: 每层单元数的向量  
**返回**: 所有层的初始权重和偏置矩阵

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

# Xavier 初始化 (L层)

**输入**: 每层单元数的向量  
**返回**: 所有层的初始权重和偏置矩阵

```matlab
function [W, b] = XavInitializeDeepModel(layerDimensions)
    rand("seed", 3);
    % note the Weight matrix at layer 'l' is a matrix of size (l,l-1)
    % The Bias is a vectors of size (l,1)
    % Loop through the layer dimension from 1.. L
    % Create cell arrays for Weights and biases
    for l = 2:size(layerDimensions)(2)
        W{l-1} = rand(layerDimensions(l), layerDimensions(l-1)) * sqrt(1 / layerDimensions(l-1)); % Multiply by .01
        b{l-1} = zeros(layerDimensions(l), 1);
    endfor
end
```

# 初始化速度

**输入**: `weights`, `biases`  
**返回**: `vdW`, `vdB` - 初始速度

```matlab
function [vdW, vdB] = initializeVelocity(weights, biases)
    L = size(weights)(2); % Create an integer
    % Initialize a cell array
    v = {};
    % Initialize velocity with the same dimensions as W
    for l = 1:L
        sz = size(weights{l});
        vdW{l} = zeros(sz(1), sz(2));
        sz = size(biases{l});
        vdB{l} = zeros(sz(1), sz(2));
    endfor;
end
```

# 初始化 RMSProp

**输入**: `weights`, `biases`  
**返回**: `sdW`, `sdB` - 初始 RMSProp

```matlab
function [sdW, sdB] = initializeRMSProp(weights, biases)
    L = size(weights)(2); % Create an integer
    % Initialize a cell array
    s = {};
    % Initialize velocity with the same dimensions as W
    for l = 1:L
        sz = size(weights{l});
        sdW{l} = zeros(sz(1), sz(2));
        sz = size(biases{l});
        sdB{l} = zeros(sz(1), sz(2));
    endfor;
end
```

# 初始化 Adam

**输入**: `parameters`  
**返回**: `vdW`, `vdB`, `sdW`, `sdB` - 初始 Adam

```matlab
function [vdW, vdB, sdW, sdB] = initializeAdam(weights, biases)
    L = size(weights)(2); % Create an integer
    % Initialize a cell array
    s = {};
    % Initialize velocity with the same dimensions as W
    for l = 1:L
        sz = size(weights{l});
        vdW{l} = zeros(sz(1), sz(2));
        sdW{l} = zeros(sz(1), sz(2));
        sz = size(biases{l});
        sdB{l} = zeros(sz(1), sz(2));
        vdB{l} = zeros(sz(1), sz(2));
    endfor;
end
```

# 计算深度网络前向传播中第 `l` 层的激活值

**输入**: 
- `A_prev` - 上一层的激活值
- `W`, `b` - 权重和偏置矩阵及向量
- `activationFunc` - 激活函数 (sigmoid, tanh, relu 等)

**返回**: 该层的激活值

**公式**:
- `Z = W * X + b`
- `A = sigmoid(Z)`, `A = Relu(Z)`, `A = tanh(Z)`

```matlab
function [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc)
    % Compute Z
    Z = W * A_prev + b;
    % Create a cell array
    forward_cache = {A_prev, W, b};
    % Compute the activation for sigmoid
    if (strcmp(activationFunc, "sigmoid"))
        [A, activation_cache] = sigmoid(Z);
    elseif (strcmp(activationFunc, "relu")) % Compute the activation for Relu
        [A, activation_cache] = relu(Z);
    elseif (strcmp(activationFunc, 'tanh')) % Compute the activation for tanh
        [A, activation_cache] = tanhAct(Z);
    elseif (strcmp(activationFunc, 'softmax')) % Compute the activation for tanh
        % [A, activation_cache] = softmax(Z);
        [A, activation_cache] = stableSoftmax(Z);
    endif
end
```

# 计算第 1..L 层的前向传播

**输入**: 
- `X` - 输入特征
- `parameters`: 权重和偏置
- `keep_prob`
- `hiddenActivationFunc` - 隐藏层激活函数 (Relu/tanh/sigmoid)
- `outputActivationFunc` - 输出层激活函数 (sigmoid/softmax)

**返回**: `AL`, `forward_caches`, `activation_caches`, `dropoutMat`

前向传播在第 1..L-1 层使用 Relu/tanh 激活函数，第 L 层使用 sigmoid 激活函数。

```matlab
function [AL, forward_caches, activation_caches, dropoutMat] = forwardPropagationDeep(X, weights, biases, keep_prob=1, hiddenActivationFunc='relu', outputActivationFunc='sigmoid')
    % Create an empty cell array
    forward_caches = {};
    activation_caches = {};
    dropoutMat = {};
    % Set A to X (A0)
    A = X;
    L = length(weights); % number of layers in the neural network
    % Loop through from layer 1 to upto layer L
    for l = 1:L-1
        A_prev = A;
        % Zi = Wi x Ai-1 + bi and Ai = g(Zi)
        W = weights{l};
        b = biases{l};
        [A, forward_cache, activation_cache] = layerActivationForward(A_prev, W, b, activationFunc=hiddenActivationFunc);
        D = rand(size(A)(1), size(A)(2));
        D = (D < keep_prob);
        % Multiply by DropoutMat
        A = A .* D;
        % Divide by keep_prob to keep expected value same
        A = A ./ keep_prob;
        % Store D
        dropoutMat{l} = D;
        forward_caches{l} = forward_cache;
        activation_caches{l} = activation_cache;
    endfor
    % Since this is binary classification use the sigmoid activation function in last layer
    W = weights{L};
    b = biases{L};
    [AL, forward_cache, activation_cache] = layerActivationForward(A, W, b, activationFunc = outputActivationFunc);
    forward_caches{L} = forward_cache;
    activation_caches{L} = activation_cache;
end
```

# 选取 Y==1 的列

此函数用于 `computeCost`。

```matlab
function [a] = pickColumns(AL, Y, numClasses)
    if (numClasses == 3)
        a = [AL(Y==0,1) ; AL(Y==1,2) ; AL(Y==2,3)];
    elseif (numClasses == 10)
        a = [AL(Y==0,1) ; AL(Y==1,2) ; AL(Y==2,3); AL(Y==3,4); AL(Y==4,5);
             AL(Y==5,6); AL(Y==6,7); AL(Y==7,8); AL(Y==8,9); AL(Y==9,10)];
    endif
end
```

# 计算代价

**输入**: 
- `AL` - 最后一层的激活值
- `Y` - 数据输出
- `outputActivationFunc` - sigmoid/softmax
- `numClasses`

**输出**: `cost`

```matlab
function [cost] = computeCost(AL, Y, outputActivationFunc="sigmoid", numClasses)
    if (strcmp(outputActivationFunc, "sigmoid"))
        numTraining = size(Y)(2);
        % Element wise multiply for logprobs
        cost = -1/numTraining * sum((Y .* log(AL)) + (1-Y) .* log(1-AL));
    elseif (strcmp(outputActivationFunc, 'softmax'))
        numTraining = size(Y)(2);
        Y = Y';
        % Select rows where Y=0,1,and 2 and concatenate to a long vector
        % a = [AL(Y==0,1) ; AL(Y==1,2) ; AL(Y==2,3)];
        a = pickColumns(AL, Y, numClasses);
        % Select the correct column for log prob
        correct_probs = -log(a);
        % Compute log loss
        cost = sum(correct_probs) / numTraining;
    endif
end
```

# 带正则化的代价计算

**输入**: 
- `weights`
- `AL` - 最后一层的激活值
- `Y` - 数据输出
- `lambd`
- `outputActivationFunc` - sigmoid/softmax
- `numClasses`

**输出**: `cost`

```matlab
function [cost] = computeCostWithReg(weights, AL, Y, lambd, outputActivationFunc="sigmoid", numClasses)
    if (strcmp(outputActivationFunc, "sigmoid"))
        numTraining = size(Y)(2);
        % Element wise multiply for logprobs
        cost = -1/numTraining * sum((Y .* log(AL)) + (1-Y) .* log(1-AL));
        % Regularization cost
        L = size(weights)(2);
        L2RegularizationCost = 0;
        for l = 1:L
            wtSqr = weights{l} .* weights{l};
            % disp(sum(sum(wtSqr,1)));
            L2RegularizationCost += sum(sum(wtSqr, 1));
        endfor
        L2RegularizationCost = (lambd / (2 * numTraining)) * L2RegularizationCost;
        cost = cost + L2RegularizationCost;
    elseif (strcmp(outputActivationFunc, 'softmax'))
        numTraining = size(Y)(2);
        Y = Y';
        % Select rows where Y=0,1,and 2 and concatenate to a long vector
```
