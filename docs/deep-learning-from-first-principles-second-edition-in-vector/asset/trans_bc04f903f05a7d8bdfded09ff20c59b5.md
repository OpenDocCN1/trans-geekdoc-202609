

# Input: X - 输入特征

# Parameters: 权重和偏置

# keep_prob

# hiddenActivationFunc - 隐藏层的激活函数 Relu/tanh

# outputActivationFunc - 输出层的激活函数 - sigmoid/softmax

# Returns: AL

# caches

# dropoutMat

# 正向传播在第 1 层到 L-1 层使用 Relu/tanh 激活函数，在第 L 层使用 sigmoid 激活函数

```python
def forwardPropagationDeep(X, parameters, keep_prob=1,
                           hiddenActivationFunc='relu', outputActivationFunc='sigmoid'):
    caches = []

    # 初始化 dropout 矩阵
    dropoutMat = {}

    # 将 A 设为 X (A0)
    A = X

    L = int(len(parameters) / 2)  # 神经网络中的层数

    # 从第 1 层循环到第 L 层
    for l in range(1, L):
        A_prev = A

        # Zi = Wi x Ai-1 + bi 和 Ai = g(Zi)
        A, cache = layerActivationForward(A_prev, parameters['W' + str(l)], parameters['b' + str(l)], keep_prob, activationFunc=hiddenActivationFunc)

        # 随机丢弃一些激活单元
        # 创建一个与 A 形状相同的矩阵
        D = np.random.rand(A.shape[0], A.shape[1])
        D = (D < keep_prob)

        # 我们需要在反向传播中使用相同的 'dropout' 矩阵
        # 保存 dropout 矩阵以供反向传播使用
        dropoutMat["D" + str(l)] = D

        A = np.multiply(A, D)
        A = np.divide(A, keep_prob)

        caches.append(cache)

    # 由于这是二分类，在最后一层使用 sigmoid 激活函数
    AL, cache = layerActivationForward(A, parameters['W' + str(L)], parameters['b' + str(L)], activationFunc=outputActivationFunc)
    caches.append(cache)

    return AL, caches, dropoutMat
```

# 计算代价

# Input: parameters

# : AL

# : Y

# : outputActivationFunc - 输出层的激活函数 - sigmoid/softmax/tanh

# Output: cost

```python
def computeCost(parameters, AL, Y, outputActivationFunc="sigmoid"):
    if outputActivationFunc == "sigmoid":
        m = float(Y.shape[1])

        # 对 logprobs 进行逐元素相乘
        cost = -1 / m * np.sum(Y * np.log(AL) + (1 - Y) * (np.log(1 - AL)))
        cost = np.squeeze(cost)

    elif outputActivationFunc == "softmax":
        # 对 softmax 进行 Y 的转置
        Y = Y.T
        m = float(len(Y))

        # 计算对数概率。基于输出 y 获取正确类别的对数概率
        correct_logprobs = -np.log(AL[range(int(m)), Y.T])

        # 计算损失
        cost = np.sum(correct_logprobs) / m

    return cost
```

# 计算带正则化的代价

# Input: parameters

# : AL

# : Y

# : lambd

# : outputActivationFunc - 输出层的激活函数 - sigmoid/softmax/tanh

# Output: cost

```python
def computeCostWithReg(parameters, AL, Y, lambd,
                       outputActivationFunc="sigmoid"):
    if outputActivationFunc == "sigmoid":
        m = float(Y.shape[1])

        # 对 logprobs 进行逐元素相乘
        cost = -1 / m * np.sum(Y * np.log(AL) + (1 - Y) * (np.log(1 - AL)))
        cost = np.squeeze(cost)

        # 正则化代价
        L = int(len(parameters) / 2)
        L2RegularizationCost = 0
        for l in range(L):
            L2RegularizationCost += np.sum(np.square(parameters['W' + str(l + 1)]))
        L2RegularizationCost = (lambd / (2 * m)) * L2RegularizationCost
        cost = cost + L2RegularizationCost

    elif outputActivationFunc == "softmax":
        # 对 softmax 进行 Y 的转置
        Y = Y.T
        m = float(len(Y))

        # 计算对数概率。基于输出 y 获取正确类别的对数概率
        correct_logprobs = -np.log(AL[range(int(m)), Y.T])

        # 计算损失
        cost = np.sum(correct_logprobs) / m

        # 正则化代价
        L = int(len(parameters) / 2)
        L2RegularizationCost = 0
        for l in range(L):
            L2RegularizationCost += np.sum(np.square(parameters['W' + str(l + 1)]))
        L2RegularizationCost = (lambd / (2 * m)) * L2RegularizationCost
        cost = cost + L2RegularizationCost

    return cost
```

# 计算包含 dropout 的单周期反向传播

# Input: 神经网络参数 - dA

# # cache - forward_cache 和 activation_cache

# # 输入特征

# # keep_prob

# # 输出值 Y

# Returns: 梯度

# dL/dWi = dL/dZi * Al-1

# dl/dbl = dL/dZl

# dL/dZ_prev = dL/dZl * W

```python
def layerActivationBackward(dA, cache, Y, keep_prob=1,
                            activationFunc="relu"):
    forward_cache, activation_cache = cache
    A_prev, W, b = forward_cache
    numtraining = float(A_prev.shape[1])

    # print("n=", numtraining)
    # print("no=", numtraining)

    if activationFunc == "relu":
        dZ = reluDerivative(dA, activation_cache)
    elif activationFunc == "sigmoid":
        dZ = sigmoidDerivative(dA, activation_cache)
    elif activationFunc == "tanh":
        dZ = tanhDerivative(dA, activation_cache)
    elif activationFunc == "softmax":
        dZ = stableSoftmaxDerivative(dA, activation_cache, Y, numtraining)

    if activationFunc == 'softmax':
        dW = 1 / numtraining * np.dot(A_prev, dZ)
        db = 1 / numtraining * np.sum(dZ, axis=0, keepdims=True)
        dA_prev = np.dot(dZ, W)
    else:
        # print(numtraining)
        dW = 1 / numtraining * (np.dot(dZ, A_prev.T))
        # print("dW=", dW)
        db = 1 / numtraining * np.sum(dZ, axis=1, keepdims=True)
        # print("db=", db)
        dA_prev = np.dot(W.T, dZ)

    return dA_prev, dW, db
```

# 计算带正则化的单周期反向传播

# Input: dA - 神经网络参数

# # cache - forward_cache 和 activation_cache

# # 输出值 Y

# # lambd

# # activationFunc

# Returns dA_prev, dW, db

# Returns: 梯度

# dL/dWi = dL/dZi * Al-1

# dl/dbl = dL/dZl

# dL/dZ_prev = dL/dZl * W

```python
def layerActivationBackwardWithReg(dA, cache, Y, lambd, activationFunc):
    forward_cache, activation_cache = cache
    A_prev, W, b = forward_cache
    numtraining = float(A_prev.shape[1])

    # print("n=", numtraining)
    # print("no=", numtraining)

    if activationFunc == "relu":
        dZ = reluDerivative(dA, activation_cache)
    elif activationFunc == "sigmoid":
        dZ = sigmoidDerivative(dA, activation_cache)
    elif activationFunc == "tanh":
        dZ = tanhDerivative(dA, activation_cache)
    elif activationFunc == "softmax":
        dZ = stableSoftmaxDerivative(dA, activation_cache, Y, numtraining)

    if activationFunc == 'softmax':
        # 添加正则化因子
        dW = 1 / numtraining * np.dot(A_prev, dZ) + (lambd / numtraining) * W.T
        db = 1 / numtraining * np.sum(dZ, axis=0, keepdims=True)
        dA_prev = np.dot(dZ, W)
    else:
        # 添加正则化因子
        dW = 1 / numtraining * (np.dot(dZ, A_prev.T)) + (lambd / numtraining) * W
        # print("dW=", dW)
        db = 1 / numtraining * np.sum(dZ, axis=1, keepdims=True)
        # print("db=", db)
        dA_prev = np.dot(W.T, dZ)

    return dA_prev, dW, db
```

# 计算单周期反向传播

# Input: AL: L 层网络的输出 - 权重

# # Y 真实输出

# # caches -- 包含以下内容的缓存列表：

# # dropoutMat

# # lambd

# # keep_prob

# # 每个 layerActivationForward() 的缓存，激活函数为 "relu"/"tanh"
# # (即 caches[l]，l 的范围为 range(L-1)，即 l = 0...L-2)

# # layerActivationForward() 的缓存，激活函数为 "sigmoid" (即 caches[L-1])

# # hiddenActivationFunc - 隐藏层的激活函数 - relu/sigmoid/tanh

# # outputActivationFunc - 输出层的激活函数 - sigmoid/softmax

# Returns:

# gradients -- 一个包含梯度的字典

# gradients["dA" + str(l)] = ...

# gradients["dW" + str(l)] = ...

```python
def backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep_prob=1,
                            hiddenActivationFunc='relu', outputActivationFunc="sigmoid"):
    # 初始化梯度
    gradients = {}

    # 设置层数
    L = len(caches)
    m = float(AL.shape[1])

    if outputActivationFunc == "sigmoid":
        Y = Y.reshape(AL.shape)  # 执行此行后，Y 的形状与 AL 相同

        # 初始化反向传播
        # dl/dAL = -(y/a + (1-y)/(1-a)) - 在输出层
        dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))
    else:
        dAL = 0
        Y = Y.T

    # 由于这是二分类，输出层的激活函数是 sigmoid
    # 获取最后一层的梯度
    # Inputs: "AL, Y, caches"。
    # Outputs: "gradients["dAL"], gradients["dWL"], gradients["dbL"]"
    current_cache = caches[L - 1]

    if lambd == 0:
        gradients["dA" + str(L)], gradients["dW" + str(L)], gradients["db" + str(L)] \
            = layerActivationBackward(dAL, current_cache,
                                      Y, activationFunc=outputActivationFunc)
    else:  # 正则化
```

