
# 代码实现与梯度检查

## 决策边界可视化

```matlab
vals = zeros(size(X1));

for i = 1:size(X1, 2)
    gridPoints = [X1(:, i), X2(:, i)];
    [AL, forward_caches, activation_caches] = forwardPropagationDeep(gridPoints', weights, biases, keep_prob, hiddenActivationFunc, outputActivationFunc="softmax");
    [l, m] = max(AL, [], 2);
    vals(:, i) = m;
endfor

scatter(data(:,1), data(:,2), 8, c=data(:,3), "filled");

% Plot the boundary
hold on
contour(X1, X2, vals, "linewidth", 4);
print -dpng "fig-o1.png"
```

## 辅助函数

### `cellArray_to_vector`

将权重和偏置的 cell 数组转换为向量。

```matlab
function [vec] = cellArray_to_vector(weights, biases)
    vec = [];
    for i = 1:size(weights)(2)
        w = weights{i};
        sz = size(w);
        % Take transpose before reshaping
        l = reshape(w', sz(1)*sz(2), 1);
        
        b = biases{i};
        sz1 = size(b);
        m = reshape(b', sz1(1)*sz1(2), 1);
        
        % Concatenate
        vec = [vec; l; m];
    endfor
end
```

### `gradients_to_vector`

将梯度 cell 数组转换为向量。

```matlab
function [vec] = gradients_to_vector(gradsDW, gradsDB)
    vec = [];
    for i = 1:size(gradsDW)(2)
        gW = gradsDW{i};
        sz = size(gW);
        % Take transpose before reshaping
        l = reshape(gW', sz(1)*sz(2), 1);
        
        gB = gradsDB{i};
        sz1 = size(gB);
        m = reshape(gB', sz1(1)*sz1(2), 1);
        
        % Concatenate
        vec = [vec; l; m];
    endfor
end
```

### `vector_to_cellArray`

将向量转换回权重和偏置的 cell 数组。

```matlab
function [weights1, biases1] = vector_to_cellArray(weights, biases, params)
    weights1 = {};
    biases1 = {};
    start = 1;
    
    for i = 1:size(weights)(2)
        w = weights{i};
        sz = size(w);
        % Take transpose before reshaping
        a = params(start:start+sz(1)*sz(2)-1, 1);
        b = reshape(a, sz(2), sz(1));
        weights1{i} = b';
        start = start + sz(1)*sz(2);
        
        b = biases{i};
        sz = size(b);
        c = params(start:start+sz(1)*sz(2)-1, 1);
        d = reshape(c, sz(2), sz(1));
        biases1{i} = d';
        start = start + sz(1)*sz(2);
    endfor
end
```

### `vector_to_cellArray1`

将向量转换为 cell 数组（用于梯度）。

```matlab
function [weights1, biases1] = vector_to_cellArray1(weights, biases, gradients)
    weights1 = {};
    biases1 = {};
    start = 1;
    
    for i = 1:size(weights)(2)
        w = weights{i};
        sz = size(w);
        % Take transpose before reshaping
        a = grads(start:start+sz(1)*sz(2)-1, 1);
        b = reshape(a, sz(2), sz(1));
        weights1{i} = b';
        start = start + sz(1)*sz(2);
        
        b = biases{i};
        sz = size(b);
        c = grads(start:start+sz(1)*sz(2)-1, 1);
        d = reshape(c, sz(2), sz(1));
        biases1{i} = d';
        start = start + sz(1)*sz(2);
    endfor
end
```

## 梯度检查

### `gradient_check_n`

执行梯度检查以验证反向传播实现的正确性。

```matlab
function [difference] = gradient_check_n(weights, biases, gradsDW, gradsDB, X, Y, epsilon=1e-7, outputActivationFunc="sigmoid", numClasses)
    % Convert cell array to vector
    parameters_values = cellArray_to_vector(weights, biases);
    
    % Convert gradient cell array to vector
    grad = gradients_to_vector(gradsDW, gradsDB);
    
    num_parameters = size(parameters_values)(1);
    
    % Initialize
    J_plus = zeros(num_parameters, 1);
    J_minus = zeros(num_parameters, 1);
    gradapprox = zeros(num_parameters, 1);
    
    % Compute gradapprox
    for i = 1:num_parameters
        % Compute J_plus[i]. Inputs: "parameters_values, epsilon". Output = "J_plus[i]".
        thetaplus = parameters_values;
        thetaplus(i, 1) = thetaplus(i, 1) + epsilon;
        [weights1, biases1] = vector_to_cellArray(weights, biases, thetaplus);
        [AL, forward_caches, activation_caches, droputMat] = forwardPropagationDeep(X', weights1, biases1, keep_prob=1, hiddenActivationFunc="relu", outputActivationFunc=outputActivationFunc);
        J_plus(i) = computeCost(AL, Y', outputActivationFunc=outputActivationFunc, numClasses);
        
        % Compute J_minus[i]. Inputs: "parameters_values, epsilon". Output = "J_minus[i]".
        thetaminus = parameters_values;
        thetaminus(i, 1) = thetaminus(i, 1) - epsilon;
        [weights1, biases1] = vector_to_cellArray(weights, biases, thetaminus);
        [AL, forward_caches, activation_caches, droputMat] = forwardPropagationDeep(X', weights1, biases1, keep_prob=1, hiddenActivationFunc="relu", outputActivationFunc=outputActivationFunc);
        J_minus(i) = computeCost(AL, Y', outputActivationFunc=outputActivationFunc, numClasses);
        
        % Compute gradapprox[i]
        gradapprox(i) = (J_plus(i) - J_minus(i)) / (2*epsilon);
    endfor
    
    % Compute L2Norm
    numerator = L2NormVec(grad - gradapprox);
    denominator = L2NormVec(grad) + L2NormVec(gradapprox);
    difference = numerator / denominator;
    
    if difference > 1e-04
        printf("There is a mistake in the implementation ");
        disp(difference);
    else
        printf("The implementation works perfectly");
        disp(difference);
    endif
    
    % This can be used to compare the gradients from backprop and gradapprox
    [weights1, biases1] = vector_to_cellArray(weights, biases, grad);
    printf("Gradients from back propagation");
    disp(weights1);
    disp(biases1);
    
    [weights2, biases2] = vector_to_cellArray(weights, biases, gradapprox);
    printf("Gradients from gradient check");
    disp(weights2);
    disp(biases2);
end
```

### `L2NormVec`

计算向量的 L2 范数。

```matlab
function [l2norm] = L2NormVec(x)
    l2norm = sqrt(sum(x .^ 2));
end
```

## 参考文献

1. Deep Learning Specialization - https://www.coursera.org/specializations/deep-learning
2. Neural Networks for Machine Learning - https://www.coursera.org/learn/neural-networks
3. Deep Learning by Ian Goodfellow, Yoshua Bengio and Aaron Courville - http://www.deeplearningbook.org/
4. Neural Networks: The mechanics of backpropagation - https://gigadom.wordpress.com/2017/01/21/neural-networks-the-mechanics-of-backpropagation/
5. Machine Learning - https://www.coursera.org/learn/machine-learning
6. CS231n Convolutional Neural Networks for Visual Recognition - http://cs231n.github.io/neural-networks-case-study/
7. The Softmax function and its derivative - https://eli.thegreenplace.net/2016/the-softmax-function-and-its-derivative/
8. Cross Validated - https://stats.stackexchange.com/questions/235528/backpropagation-with-softmax-cross-entropy
9. CS231n: How to calculate gradient for Softmax loss function? - https://stackoverflow.com/questions/41663874/cs231n-how-to-calculate-gradient-for-softmax-loss-function
10. Derivative of Softmax loss function - https://math.stackexchange.com/questions/945871/derivative-of-softmax-loss-function
11. The Matrix Calculus You Need For Deep Learning - https://arxiv.org/abs/1802.01528
12. A Step by Step Backpropagation Example - https://mattmazur.com/2015/03/17/a-step-by-step-backpropagation-example/
