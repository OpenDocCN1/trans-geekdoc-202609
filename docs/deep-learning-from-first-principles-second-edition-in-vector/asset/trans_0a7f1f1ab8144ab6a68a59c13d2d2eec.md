

# 实现简单神经网络

## 简介

在第一章中，我用向量化的 Python、R 和 Octave 实现了逻辑回归，这是一个想成为神经网络的网络（没有隐藏层的神经网络）。在第二章中，我实现了一个常规但略显原始的神经网络（仅有 1 个隐藏层的神经网络）。本章实现了手动创建数据集的分类，其中两个类的不同簇是线性不可分的。

神经网络在学习各种类别之间的非线性边界方面表现良好。最初使用逻辑回归进行分类。然后在同一数据集上使用一个简单的 3 层神经网络并绘制决策边界。普通逻辑回归表现相当差。使用带有径向基核的 SVM 在创建非线性边界方面会表现好得多。本章调用的函数实现见附录 2 - 实现简单神经网络。您可以从 GitHub 克隆和分叉 3 层神经网络的向量化实现（Python、R 和 Octave）：

[DeepLearningFromFirstPrinciples](https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap2-SimpleNeuralNetwork)

## 3 层神经网络

下图展示了一个带有 1 个隐藏层的 3 层神经网络（NN）的简单表示。

在上述神经网络中，输入层有两个输入特征，隐藏层有三个隐藏单元，输出层有一个输出单元，因为它处理二分类问题。隐藏层的激活单元可以是 `tanh`、`sigmoid`、`relu` 等。输出层的激活函数是 `sigmoid`，用于处理二分类。

### 重要结果（记忆复习！）

**前向传播**

```math
# Superscript indicates layer '1'
Z^{[1]} = W^{[1]} X + b^{[1]}
A^{[1]} = \tanh(Z^{[1]})
```

```math
# Superscript indicates layer '2'
Z^{[2]} = W^{[2]} A^{[1]} + b^{[2]}
A^{[2]} = \sigma(Z^{[2]})
```

因此：

```math
A^{[1]} = \tanh(Z^{[1]})
A^{[2]} = \sigma(Z^{[2]})
```

同理：

```math
\frac{\partial A^{[1]}}{\partial Z^{[1]}} = 1 - (A^{[1]})^2
\frac{\partial A^{[2]}}{\partial Z^{[2]}} = A^{[2]}(1 - A^{[2]})
```

这些方程可以写为：

**I) 一些重要结果（记忆复习！）**

```math
\frac{d}{dx}\tanh(x) = 1 - \tanh^2(x) \quad \text{(a)}
```

```math
\frac{d}{dx}\sigma(x) = \sigma(x)(1 - \sigma(x)) \quad \text{(b)}
```

使用 (a) 我们可以得到：

```math
\frac{\partial A^{[1]}}{\partial Z^{[1]}} = 1 - (A^{[1]})^2
```

以及：

```math
\frac{\partial A^{[2]}}{\partial Z^{[2]}} = A^{[2]}(1 - A^{[2]})
```

(b)

现在：

```math
\frac{\partial L}{\partial Z^{[2]}} = A^{[2]} - Y
```

```math
\frac{\partial L}{\partial W^{[2]}} = \frac{\partial L}{\partial Z^{[2]}} (A^{[1]})^T
```

```math
\frac{\partial L}{\partial b^{[2]}} = \frac{\partial L}{\partial Z^{[2]}}
```

```math
\frac{\partial L}{\partial Z^{[1]}} = (W^{[2]})^T \frac{\partial L}{\partial Z^{[2]}} \odot (1 - (A^{[1]})^2)
```

```math
\frac{\partial L}{\partial W^{[1]}} = \frac{\partial L}{\partial Z^{[1]}} X^T
```

```math
\frac{\partial L}{\partial b^{[1]}} = \frac{\partial L}{\partial Z^{[1]}}
```

(c)

因为：

```math
\frac{\partial \tanh(x)}{\partial x} = 1 - \tanh^2(x)
```

并且使用 (c) 我们得到：

```math
\frac{\partial L}{\partial Z^{[1]}} = (W^{[2]})^T \frac{\partial L}{\partial Z^{[2]}} \odot (1 - (A^{[1]})^2)
```

使用 (b) 中 `sinhx` 和 `coshx` 导数的值我们得到：

因为：

```math
\frac{d}{dx}\sinh(x) = \cosh(x), \quad \frac{d}{dx}\cosh(x) = \sinh(x)
```

(d)

**II) 导数**

对数损失如下所示：

```math
L = -[Y \log(A^{[2]}) + (1-Y)\log(1-A^{[2]})]
```

因为：

```math
\frac{\partial L}{\partial A^{[2]}} = -\frac{Y}{A^{[2]}} + \frac{1-Y}{1-A^{[2]}}
```

因此：

```math
\frac{\partial L}{\partial Z^{[2]}} = A^{[2]} - Y
```

见第一章 equation (2)

因此：

```math
\frac{\partial L}{\partial W^{[2]}} = \frac{\partial L}{\partial Z^{[2]}} (A^{[1]})^T \quad \text{(e)}
```

```math
\frac{\partial L}{\partial b^{[2]}} = \frac{\partial L}{\partial Z^{[2]}} \quad \text{(f)}
```

以及：

```math
\frac{\partial L}{\partial Z^{[1]}} = (W^{[2]})^T \frac{\partial L}{\partial Z^{[2]}} \odot (1 - (A^{[1]})^2)
```

以及：

```math
\frac{\partial L}{\partial W^{[1]}} = \frac{\partial L}{\partial Z^{[1]}} X^T \quad \text{(g)}
```

```math
\frac{\partial L}{\partial b^{[1]}} = \frac{\partial L}{\partial Z^{[1]}} \quad \text{(h)}
```

**III) 反向传播**

使用 II) 中的导数，我们可以使用链式法则推导出以下结果：

(i)

```math
\frac{\partial L}{\partial Z^{[2]}} = A^{[2]} - Y
```

```math
\frac{\partial L}{\partial W^{[2]}} = \frac{1}{m} \frac{\partial L}{\partial Z^{[2]}} (A^{[1]})^T
```

```math
\frac{\partial L}{\partial b^{[2]}} = \frac{1}{m} \sum \frac{\partial L}{\partial Z^{[2]}}
```

```math
\frac{\partial L}{\partial Z^{[1]}} = (W^{[2]})^T \frac{\partial L}{\partial Z^{[2]}} \odot (1 - (A^{[1]})^2)
```

```math
\frac{\partial L}{\partial W^{[1]}} = \frac{1}{m} \frac{\partial L}{\partial Z^{[1]}} X^T
```

```math
\frac{\partial L}{\partial b^{[1]}} = \frac{1}{m} \sum \frac{\partial L}{\partial Z^{[1]}}
```

使用 (i) 和 (e) 的结果我们得到：

(j)

(k)

以及：

化简得到：

(l) 和

(m)

**IV) 梯度下降**

## Octave 代码实现

```octave
b = b - learningRate * db;

if (mod(i, 100) == 0)
    # Append index and loss
    index = [index i];
    losses = [losses loss];
endif
end
end

# Determine the predicted value for dataset
function yPredicted = predict(w, b, X)
    m = size(X)(1, 2);
    yPredicted = zeros(1, m);
    # Compute Z
    Z = w' * X + b;
    # Compute sigmoid
    A = sigmoid(Z);
    for i = 1:size(X)(1, 2),
        # Set predicted as 1 if A > 0.5
        if (A(1, i) >= 0.5)
            yPredicted(1, i) = 1;
        else
            yPredicted(1, i) = 0;
        endif
    end
end

# Normalize by dividing each value by the sum of squares
function normalized = normalize(x)
    # Compute Frobenius norm. Square the elements, sum rows and then find square root
    a = sqrt(sum(x .^ 2, 2));
    # Perform element wise division
    normalized = x ./ a;
end

# Split into train and test sets
function [X_train, y_train, X_test, y_test] = trainTestSplit(dataset, trainPercent)
    # Create a random index
    ix = randperm(length(dataset));
    # Split into training
    trainSize = floor(trainPercent / 100 * length(dataset));
    train = dataset(ix(1:trainSize), :);
    # And test
    test = dataset(ix(trainSize + 1:length(dataset)), :);
    X_train = train(:, 1:30);
    y_train = train(:, 31);
    X_test = test(:, 1:30);
    y_test = test(:, 31);
end

# Read the data
cancer = csvread("cancer.csv");

# Split as train and test
[X_train, y_train, X_test, y_test] = trainTestSplit(cancer, 75);

# Initialize w and b
w = zeros(size(X_train)(1, 2), 1);
b = 0;

# Normalize training
X_train1 = normalize(X_train);
X_train2 = X_train1';
y_train1 = y_train';

# Perform gradient descent
[w1, b1, dw, db, losses, idx] = gradientDescent(w, b, X_train2, y_train1, numIterations=3000, learningRate=0.75);

# Normalize X_test
X_test1 = normalize(X_test);
# Transpose X_train so that we have a matrix as (features, numSamples)
X_test2 = X_test1';
y_test1 = y_test';

# Use the values of the weights generated from Gradient Descent
yPredictionTest = predict(w1, b1, X_test2);
yPredictionTrain = predict(w1, b1, X_train2);

# Compute Accuracy
trainAccuracy = 100 - mean(abs(yPredictionTrain - y_train1)) * 100
testAccuracy = 100 - mean(abs(yPredictionTest - y_test1)) * 100

trainAccuracy = 90.845
testAccuracy = 89.510

graphics_toolkit('gnuplot')
plot(idx, losses);
title('Gradient descent- Cost vs No of iterations');
xlabel('No of iterations');
ylabel('Cost');
```

## 结论

本章从一个简单的 2 层神经网络实现逻辑回归开始。显然，这个简单神经网络的性能与高度优化的 sklearn 逻辑回归相比相对较差。这是因为上述神经网络没有任何隐藏层。深度学习和神经网络之所以能取得非凡的性能，是因为存在深层隐藏层。

---

> “What does the world outside your head really ‘look’ like? Not only is there no color, there’s also no sound: the compression and expansion of air is picked up by the ears and turned into electrical signals. The brain then presents these signals to us as mellifluous tones and swishes and clatters and jangles. Reality is also odorless: there’s no such thing as smell outside our brains. Molecules floating through the air bind to receptors in our nose and are interpreted as different smells by our brain. The real world is not full of rich sensory events; instead, our brains light up the world with their own sensuality.”
> 
> — *The Brain: The Story of You* by David Eagleman

> “The world is Maya, illusory. The ultimate reality, the Brahman, is all-pervading and all-permeating, which is colourless, odourless, tasteless, nameless and formless”
> 
> — *Bhagavad Gita*

