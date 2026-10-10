
# 输出梯度

输出：`gradients["dA" + str(l + 1)]`，`gradients["dW" + str(l + 1)]`，`gradients["db" + str(l + 1)]`

```matlab
activation_cache = activation_caches{l};
forward_cache = forward_caches(l);

# dA_prev_temp, dW_temp, db_temp =
layerActivationBackward(gradients['dA'+str(l+1)], current_cache, activationFunc = "relu")

# dAl the dervative of the activation of the lth layer,is the first element dAl= gradsDA{l+1};

if (lambd == 0)
    # Get the dropout mat
    D = dropoutMat{l};
    # Multiply by the dropoutMat
    dAl = dAl .* D;
    # Divide by keep_prob to keep expected value same
    dAl = dAl ./ keep_prob;
    [dA_prev_temp, dW_temp, db_temp] = layerActivationBackward(dAl, forward_cache{1}, activation_cache, Y, activationFunc = hiddenActivationFunc, numClasses);
else
    [dA_prev_temp, dW_temp, db_temp] = layerActivationBackwardWithReg(dAl, forward_cache{1}, activation_cache, Y, lambd, activationFunc = hiddenActivationFunc, numClasses);
endif

gradsDA{l} = dA_prev_temp;
gradsDW{l} = dW_temp;
gradsDB{l} = db_temp;
endfor
end
```

# 执行梯度下降

**输入**：
- `weights` 和 `biases`
- `gradients` - `gradsW`, `gradsB`
- `learning rate`
- `outputActivationFunc`

**输出**：1 次迭代后更新的权重

```matlab
function [weights biases] = gradientDescent(weights, biases, gradsW, gradsB, learningRate, outputActivationFunc="sigmoid")
    L = size(weights)(2); # number of layers in the neural network
    # Update rule for each parameter.
    for l = 1:(L-1)
        weights{l} = weights{l} - learningRate * gradsW{l};
        biases{l} = biases{l} - learningRate * gradsB{l};
    endfor
    if (strcmp(outputActivationFunc, "sigmoid"))
        weights{L} = weights{L} - learningRate * gradsW{L};
        biases{L} = biases{L} - learningRate * gradsB{L};
    elseif (strcmp(outputActivationFunc, "softmax"))
        weights{L} = weights{L} - learningRate * gradsW{L}';
        biases{L} = biases{L} - learningRate * gradsB{L}';
    endif
end
```

# 执行 L 层深度学习模型

**输入**：
- `X` - 输入特征
- `Y` - 输出
- `layersDimensions` - 层维度
- `hiddenActivationFunc` - 隐藏层激活函数 relu / tanh
- `outputActivationFunc` - 输出层激活函数 sigmoid / softmax
- `learning rate`
- `lambd`
- `keep_prob`
- `num of iterations`

**输出**：每次迭代后更新的权重和偏置

```matlab
function [weights biases costs] = L_Layer_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learning_rate = .3, lambd=0, keep_prob=1, num_iterations = 10000, initType="default") # lr was 0.009
    rand ("seed", 1);
    costs = [];
    if (strcmp(initType, "He"))
        # He Initialization
        [weights biases] = HeInitializeDeepModel(layersDimensions);
    elseif (strcmp(initType, "Xav"))
        # Xavier Initialization
        [weights biases] = XavInitializeDeepModel(layersDimensions);
    else
        # Default initialization.
        [weights biases] = initializeDeepModel(layersDimensions);
    endif

    # Loop (gradient descent)
    for i = 0:num_iterations
        # Forward propagation: [LINEAR -> RELU]*(L-1) -> LINEAR -> SIGMOID.
        [AL forward_caches activation_caches droputMat] = forwardPropagationDeep(X, weights, biases, keep_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc);

        # Regularization parameter is 0
        if (lambd == 0)
            # Compute cost.
            cost = computeCost(AL, Y, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)(2)));
        else
            # Compute cost with regularization
            cost = computeCostWithReg(weights, AL, Y, lambd, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)(2)));
        endif

        # Backward propagation.
        [gradsDA gradsDW gradsDB] = backwardPropagationDeep(AL, Y, activation_caches, forward_caches, droputMat, lambd, keep_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)(2)));

        # Update parameters.
        [weights biases] = gradientDescent(weights, biases, gradsDW, gradsDB, learning_rate, outputActivationFunc=outputActivationFunc);

        # Print the cost every 1000 iterations
        if (mod(i, 1000) == 0)
            costs = [costs cost];
            # disp ("Cost after iteration"), L2RegularizationCost(i), disp(cost); printf("Cost after iteration i=%i cost=%d\n", i, cost);
        endif
    endfor
end
```

# 使用随机梯度下降执行 L 层深度学习模型

**输入**：
- `X` - 输入特征
- `Y` - 输出
- `layersDimensions` - 层维度
- `hiddenActivationFunc` - 隐藏层激活函数 relu / tanh
- `outputActivationFunc` - 输出层激活函数 sigmoid / softmax
- `learning rate`
- `mini_batch_size`
- `num of epochs`

**输出**：每次迭代后更新的权重和偏置

```matlab
function [weights biases costs] = L_Layer_DeepModel_SGD(X, Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learning_rate = .3, mini_batch_size = 64, num_epochs = 2500) # lr was 0.009
    rand ("seed", 1);
    costs = [];
    # Parameters initialization.
    [weights biases] = initializeDeepModel(layersDimensions);
    seed = 10;

    # Loop (gradient descent)
    for i = 0:num_epochs
        seed = seed + 1;
        [mini_batches_X mini_batches_Y] = random_mini_batches(X, Y, mini_batch_size, seed);
        minibatches = length(mini_batches_X);
        for batch = 1:minibatches
            X = mini_batches_X{batch};
            Y = mini_batches_Y{batch};
            # Forward propagation: [LINEAR -> RELU]*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.
            [AL forward_caches activation_caches] = forwardPropagationDeep(X, weights, biases, hiddenActivationFunc, outputActivationFunc=outputActivationFunc);
            # disp(batch);
            # disp(size(X));
            # disp(size(Y));

            # Compute cost.
            cost = computeCost(AL, Y, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)(2)));
            # disp(cost);

            # Backward propagation.
            [gradsDA gradsDW gradsDB] = backwardPropagationDeep(AL, Y, activation_caches, forward_caches, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)(2)));

            # Update parameters.
            [weights biases] = gradientDescent(weights, biases, gradsDW, gradsDB, learning_rate, outputActivationFunc=outputActivationFunc);
        endfor

        # Print the cost every 1000 iterations
        if (mod(i, 1000) == 0)
            costs = [costs cost];
            # disp ("Cost after iteration"), disp(i), disp(cost); printf("Cost after iteration i=%i cost=%d\n", i, cost);
        endif
    endfor
end
```

# 绘制成本与迭代次数关系图

```matlab
function plotCostVsIterations(maxIterations, costs, fig1)
    iterations = [0:1000:maxIterations];
    plot(iterations, costs);
    title ("Cost vs no of iterations ");
    xlabel("No of iterations");
    ylabel("Cost");
    print -dpng figReg2-o
end;
```

# 计算给定输入的预测值

**输入**：
- 神经网络参数
- 输入数据

```matlab
function [predictions] = predict(weights, biases, X, keep_prob=1, hiddenActivationFunc="relu")
    [AL forward_caches activation_caches] = forwardPropagationDeep(X, weights, biases, keep_prob, hiddenActivationFunc);
    predictions = (AL > 0.5);
end
```

# 绘制决策边界

```matlab
function plotDecisionBoundary(data, weights, biases, keep_prob=1, hiddenActivationFunc="relu", fig2)
    % Plot a non-linear decision boundary learned by the SVM
    colormap ("summer");
    % Make classification predictions over a grid of values
    x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';
    x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';
    [X1, X2] = meshgrid(x1plot, x2plot);
    vals = zeros(size(X1));

    # Plot the prediction for the grid
    for i = 1:size(X1, 2)
        gridPoints = [X1(:, i), X2(:, i)];
        vals(:, i) = predict(weights, biases, gridPoints', keep_prob, hiddenActivationFunc=hiddenActivationFunc);
    endfor

    scatter(data(:,1), data(:,2), 8, c=data(:,3), "filled");
    % Plot the boundary
    hold on
    # contour(X1, X2, vals, [0 0], 'LineWidth', 2);
    contour(X1, X2, vals, "linewidth", 4);
    title ({"3 layer Neural Network decision boundary"});
    hold off;
    print -dpng figReg22-o
end
```
