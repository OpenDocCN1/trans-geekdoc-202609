
# Adam 优化器参数更新实现

## 核心更新逻辑（第 l+1 层）

```python
v["dW" + str(l+1)] = beta1 * v["dW" + str(l+1)] + (1 - beta1) * gradients['dW' + str(l+1)]
v["db" + str(l+1)] = beta1 * v["db" + str(l+1)] + (1 - beta1) * gradients['db' + str(l+1)]

# Compute bias-corrected first moment estimate.
v_corrected["dW" + str(l+1)] = v["dW" + str(l+1)] / (1 - np.power(beta1, t))
v_corrected["db" + str(l+1)] = v["db" + str(l+1)] / (1 - np.power(beta1, t))

# Moving average of the squared gradients like RMSProp
s["dW" + str(l+1)] = beta2 * s["dW" + str(l+1)] + (1 - beta2) * np.multiply(gradients['dW' + str(l+1)], gradients['dW' + str(l+1)])
s["db" + str(l+1)] = beta2 * s["db" + str(l+1)] + (1 - beta2) * np.multiply(gradients['db' + str(l+1)], gradients['db' + str(l+1)])

# Compute bias-corrected second raw moment estimate.
s_corrected["dW" + str(l+1)] = s["dW" + str(l+1)] / (1 - np.power(beta2, t))
s_corrected["db" + str(l+1)] = s["db" + str(l+1)] / (1 - np.power(beta2, t))

# Update parameters.
d1 = np.sqrt(s_corrected["dW" + str(l+1)] + epsilon)
d2 = np.sqrt(s_corrected["db" + str(l+1)] + epsilon)

parameters["W" + str(l+1)] = parameters['W' + str(l+1)] - (learningRate * v_corrected["dW" + str(l+1)] / d1)
parameters["b" + str(l+1)] = parameters['b' + str(l+1)] - (learningRate * v_corrected["db" + str(l+1)] / d2)
```

## 输出层特殊处理

### Sigmoid 激活函数

```python
if outputActivationFunc == "sigmoid":
    # Compute 1st moment for L
    v["dW" + str(L)] = beta1 * v["dW" + str(L)] + (1 - beta1) * gradients['dW' + str(L)]
    v["db" + str(L)] = beta1 * v["db" + str(L)] + (1 - beta1) * gradients['db' + str(L)]

    # Compute bias-corrected first moment estimate.
    v_corrected["dW" + str(L)] = v["dW" + str(L)] / (1 - np.power(beta1, t))
    v_corrected["db" + str(L)] = v["db" + str(L)] / (1 - np.power(beta1, t))

    # Compute 2nd moment for L
    s["dW" + str(L)] = beta2 * s["dW" + str(L)] + (1 - beta2) * np.multiply(gradients['dW' + str(L)], gradients['dW' + str(L)])
    s["db" + str(L)] = beta2 * s["db" + str(L)] + (1 - beta2) * np.multiply(gradients['db' + str(L)], gradients['db' + str(L)])

    # Compute bias-corrected second raw moment estimate.
    s_corrected["dW" + str(L)] = s["dW" + str(L)] / (1 - np.power(beta2, t))
    s_corrected["db" + str(L)] = s["db" + str(L)] / (1 - np.power(beta2, t))

    # Update parameters.
    d1 = np.sqrt(s_corrected["dW" + str(L)] + epsilon)
    d2 = np.sqrt(s_corrected["db" + str(L)] + epsilon)

    parameters["W" + str(L)] = parameters['W' + str(L)] - (learningRate * v_corrected["dW" + str(L)] / d1)
    parameters["b" + str(L)] = parameters['b' + str(L)] - (learningRate * v_corrected["db" + str(L)] / d2)
```

### Softmax 激活函数

```python
elif outputActivationFunc == "softmax":
    # Compute 1st moment
    v["dW" + str(L)] = beta1 * v["dW" + str(L)] + (1 - beta1) * gradients['dW' + str(L)].T
    v["db" + str(L)] = beta1 * v["db" + str(L)] + (1 - beta1) * gradients['db' + str(L)].T

    # Compute bias-corrected first moment estimate.
    v_corrected["dW" + str(L)] = v["dW" + str(L)] / (1 - np.power(beta1, t))
    v_corrected["db" + str(L)] = v["db" + str(L)] / (1 - np.power(beta1, t))

    # Compute 2nd moment
    s["dW" + str(L)] = beta2 * s["dW" + str(L)] + (1 - beta2) * np.multiply(gradients['dW' + str(L)].T, gradients['dW' + str(L)].T)
    s["db" + str(L)] = beta2 * s["db" + str(L)] + (1 - beta2) * np.multiply(gradients['db' + str(L)].T, gradients['db' + str(L)].T)

    # Compute bias-corrected second raw moment estimate.
    s_corrected["dW" + str(L)] = s["dW" + str(L)] / (1 - np.power(beta2, t))
    s_corrected["db" + str(L)] = s["db" + str(L)] / (1 - np.power(beta2, t))

    # Update parameters.
    d1 = np.sqrt(s_corrected["dW" + str(L)] + epsilon)
    d2 = np.sqrt(s_corrected["db" + str(L)] + epsilon)

    parameters["W" + str(L)] = parameters['W' + str(L)] - (learningRate * v_corrected["dW" + str(L)] / d1)
    parameters["b" + str(L)] = parameters['b' + str(L)] - (learningRate * v_corrected["db" + str(L)] / d2)

return parameters, v, s
```

# L 层深度学习模型执行

## `L_Layer_DeepModel` 函数

**功能**：执行 L 层深度学习模型（批量梯度下降）

**参数**：
- `X1`：输入特征
- `Y1`：输出标签
- `layersDimensions`：各层维度
- `hiddenActivationFunc`：隐藏层激活函数（`relu`/`tanh`/`sigmoid`）
- `outputActivationFunc`：输出层激活函数（`sigmoid`/`softmax`）
- `learningRate`：学习率
- `lambd`：正则化参数
- `keep_prob`：Dropout 保留概率
- `num_iterations`：迭代次数
- `initType`：初始化类型（`He`/`Xavier`/`default`）
- `print_cost`：是否打印成本
- `figure`：成本曲线保存路径

**返回**：训练后的参数

```python
def L_Layer_DeepModel(X1, Y1, layersDimensions,
                      hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate=.3, lambd=0, keep_prob=1, num_iterations=10000, initType="default", print_cost=False, figure="figa.png"):
    np.random.seed(1)
    costs = []

    # Parameters initialization.
    if initType == "He":
        parameters = HeInitializeDeepModel(layersDimensions)
    elif initType == "Xavier":
        parameters = XavInitializeDeepModel(layersDimensions)
    else:  # Default
        parameters = initializeDeepModel(layersDimensions)

    # Loop (gradient descent)
    for i in range(0, num_iterations):
        AL, caches, dropoutMat = forwardPropagationDeep(X1, parameters, keep_prob,
                                                        hiddenActivationFunc="relu", outputActivationFunc=outputActivationFunc)

        # Regularization parameter is 0
        if lambd == 0:
            # Compute cost
            cost = computeCost(parameters, AL, Y1, outputActivationFunc=outputActivationFunc)
        # Include L2 regularization
        else:
            # Compute cost
            cost = computeCostWithReg(parameters, AL, Y1, lambd, outputActivationFunc=outputActivationFunc)

        # Backward propagation.
        gradients = backwardPropagationDeep(AL, Y1, caches, dropoutMat, lambd, keep_prob,
                                            hiddenActivationFunc="relu", outputActivationFunc=outputActivationFunc)

        # Update parameters.
        parameters = gradientDescent(parameters, gradients, learningRate=learningRate, outputActivationFunc=outputActivationFunc)

        # Print the cost every 1000 training example
        if print_cost and i % 1000 == 0:
            print("Cost after iteration %i: %f" % (i, cost))

        if print_cost and i % 1000 == 0:
            costs.append(cost)

    # plot the cost
    plt.plot(np.squeeze(costs))
    plt.ylabel('Cost')
    plt.xlabel('No of iterations (x1000)')
    plt.title("Learning rate =" + str(learningRate))
    plt.savefig(figure, bbox_inches='tight')
    # plt.show()
    plt.clf()
    plt.close()

    return parameters
```

## `L_Layer_DeepModel_SGD` 函数

**功能**：执行 L 层深度学习模型（随机梯度下降及变体）

**参数**：
- `X1`：输入特征
- `Y1`：输出标签
- `layersDimensions`：各层维度
- `hiddenActivationFunc`：隐藏层激活函数（`relu`/`tanh`/`sigmoid`）
- `outputActivationFunc`：输出层激活函数（`sigmoid`/`softmax`）
- `learningRate`：学习率
- `lrDecay`：是否启用学习率衰减
- `decayRate`：衰减率
- `lambd`：正则化参数
- `keep_prob`：Dropout 保留概率
- `optimizer`：优化器（`gd`/`momentum`/`rmsprop`/`adam`）
- `beta`：Momentum/RMSProp 参数
- `beta1`：Adam 一阶矩参数
- `beta2`：Adam 二阶矩参数
- `epsilon`：数值稳定性常数
- `mini_batch_size`：小批量大小
- `num_epochs`：训练轮数
- `print_cost`：是否打印成本
- `figure`：成本曲线保存路径

**返回**：更新后的权重和偏置

```python
def L_Layer_DeepModel_SGD(X1, Y1, layersDimensions,
                          hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate=.3, lrDecay=False, decayRate=1,
                          lambd=0, keep_prob=1, optimizer="gd", beta=0.9, beta1=0.9, beta2=0.999,
                          epsilon=1e-8, mini_batch_size=64, num_epochs=2500,
                          print_cost=False, figure="figa.png"):

    print("lr=", learningRate)
    print("lrDecay=", lrDecay)
    print("decayRate=", decayRate)
    print("lambd=", lambd)
    print("keep_prob=", keep_prob)
    print("optimizer=", optimizer)
    print("beta=", beta)
    print("beta1=", beta1)
    print("beta2=", beta2)
    print("epsilon=", epsilon)
    print("mini_batch_size=", mini_batch_size)
    print("num_epochs=", num_epochs)
    print("epsilon=", epsilon)

    t = 0  # Adam counter
    np.random.seed(1)
    costs = []

    # Parameters initialization.
    parameters = initializeDeepModel(layersDimensions)

    # Initialize the optimizer
    if optimizer == "gd":
        pass  # no initialization required for gradient descent
    elif optimizer == "momentum":
        v = initializeVelocity(parameters)
    elif optimizer == "rmsprop":
        s = initializeRMSProp(parameters)
    elif optimizer == "adam":
        v, s = initializeAdam(parameters)

    seed = 10

    # Loop for number of epochs
    for i in range(num_epochs):
        # ... (后续训练循环逻辑)
```
