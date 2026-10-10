

# 逻辑回归作为两层神经网络

本章探讨将逻辑回归实现为两层神经网络，即仅包含输入层和输出层、没有隐藏层的神经网络。该两层网络分别用 Python、R 和 Octave 语言实现。之所以加入 Octave，是因为它是 Matlab 的近亲。

这些 Python、R 和 Octave 实现是等价的向量化实现。因此，如果你熟悉其中任一语言，就能看懂另外两种语言对应的代码。本章调用的函数实现见附录 1 —— 作为神经网络的逻辑回归。

你也可以从 Github 的 `DeepLearningFromFirstPrinciples` 仓库克隆/下载 Python、R 和 Octave 的向量化代码 (https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap1-LogisticRegressionAsNeuralNetwork)。首先，使用 `sklearn` 的逻辑回归包对 `sklearn` 的癌症数据集执行逻辑回归。如下所示。

## 1. 逻辑回归

```python
import numpy as np
import pandas as pd
import os
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import make_classification, make_blobs
from sklearn.metrics import confusion_matrix
from matplotlib.colors import ListedColormap
from sklearn.datasets import load_breast_cancer

# Load the cancer data
(X_cancer, y_cancer) = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X_cancer, y_cancer, random_state=0)

# Call the Logistic Regression function
clf = LogisticRegression().fit(X_train, y_train)

# Print accuracy of training and test set
print('Accuracy of Logistic regression classifier on training set: {:.2f}'.format(clf.score(X_train, y_train)))
print('Accuracy of Logistic regression classifier on test set: {:.2f}'.format(clf.score(X_test, y_test)))
```

## 逻辑回归分类器在训练集上的准确率: 0.96
## 逻辑回归分类器在测试集上的准确率: 0.96

![Image 2](index-15_1.jpg)
![Image 3](index-15_2.jpg)

## 2. 逻辑回归作为两层神经网络

在下一节中，逻辑回归将在 Python、R 和 Octave 中实现为两层神经网络。来自 `sklearn` 的相同癌症数据集被用于在 Python、R 和 Octave 中训练和测试神经网络。这可以用下图表示。

癌症数据集有 30 个输入特征，目标变量“output”为 0 或 1。因此，输出层将使用 Sigmoid 激活函数进行分类。

这个简单的两层神经网络如下所示。

在输入层，有 30 个特征及其对应的权重，这些权重被初始化为较小的随机值。

其中“b”为偏置项。

![Image 4](index-16_1.jpg)
![Image 5](index-16_2.jpg)

激活函数是 Sigmoid 函数，公式为：

当输出层使用 Sigmoid 函数时，损失函数由下式给出：

(1)

![Image 6](index-17_1.jpg)
![Image 7](index-17_2.jpg)
![Image 8](index-17_3.jpg)

## 3. 梯度下降

### 3.1 前向传播

神经网络的前向传播周期计算输出 `Z` 和 Sigmoid 激活函数的激活值。然后利用给定特征的输出 'y'，根据上述公式 (1) 计算“损失”。

### 3.2 反向传播

反向传播周期确定“损失”受前几层直到输入层的微小变化影响程度。换句话说，反向传播计算输入层权重的变化，以最小化输出层的损失。在最陡下降路径上执行多次梯度下降循环以寻找局部极小值。换言之，梯度下降计算输入层的一组权重和偏置，使其产生最低损失。输入层的权重按称为“学习率”的参数减小。过大的“学习率”可能越过局部极小值，过小的“学习率”可能导致收敛时间过长。

梯度下降迭代前向传播和反向传播循环，直到损失最小化。此过程针对 'm' 个训练样本执行。

### 3.3 微分链式法则

设 `y = f(u)` 且 `u = g(x)`，则根据链式法则：

### 3.4 Sigmoid 的导数

设 ...

则 ...

![Image 9](index-18_1.jpg)
![Image 10](index-18_2.jpg)
![Image 11](index-18_3.jpg)
![Image 12](index-18_4.jpg)
![Image 13](index-18_5.jpg)
![Image 14](index-18_6.jpg)
![Image 15](index-18_7.jpg)
![Image 16](index-18_8.jpg)
![Image 17](index-18_9.jpg)
![Image 18](index-18_10.jpg)
![Image 19](index-18_11.jpg)
![Image 20](index-18_12.jpg)
![Image 21](index-18_13.jpg)
![Image 22](index-18_14.jpg)
![Image 23](index-18_15.jpg)
![Image 24](index-18_16.jpg)
![Image 25](index-18_17.jpg)

以及 ...

利用微分链式法则可得：

因此 ...

-(2)

两层神经网络表示逻辑回归的 3 个方程为：

-(a)
-(b)
-(c)

其中 `L` 为 Sigmoid 输出激活函数的损失。反向传播步骤需要计算 ... 和 ... 。若为回归问题，则为 ... 和 ... ，其中 `dE` 为均方误差函数。

损失函数的导数计算如下：

-(d)

因为 ...

同样由方程 (2) 可写为：

– (e)

根据链式法则 ...

因此将 (d) 和 (e) 的结果代入上式：

![Image 26](index-19_1.jpg)
![Image 27](index-19_2.jpg)
![Image 28](index-19_3.jpg)
![Image 29](index-19_4.jpg)
![Image 30](index-19_5.jpg)
![Image 31](index-19_6.jpg)
![Image 32](index-19_7.jpg)
![Image 33](index-19_8.jpg)
![Image 34](index-19_9.jpg)
![Image 35](index-19_10.jpg)
![Image 36](index-19_11.jpg)
![Image 37](index-19_12.jpg)

可得：

(f)

最终：

-(g)
– (h)

由 (f) 得 ...

因此 (g) 简化为：

-(i)

同样：

-(j)

由于 ... 并在 (j) 中使用 (f) 可得 ...

梯度利用 ... 和 ... 的值计算输入层的权重及对应偏置。

书籍 *Deep Learning* (http://www.deeplearningbook.org/) 中的计算图表示 —— 作者 Ian Goodfellow, Yoshua Bengio, Aaron Courville —— 对可视化和计算反向传播非常有用。逻辑回归两层神经网络的计算图如下所示。

![Image 38](index-20_1.jpg)

## 4. 逻辑回归神经网络 - Python 代码

```python
import numpy as np
import pandas as pd
import os
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split

# Define the sigmoid function
def sigmoid(z):
    a = 1 / (1 + np.exp(-z))
    return a

# Initialize weights and biases
def initialize(dim):
    w = np.zeros(dim).reshape(dim, 1)
    b = 0
    return w

# Compute the loss
def computeLoss(numTraining, Y, A):
    loss = -1 / numTraining * np.sum(Y * np.log(A) + (1 - Y) * (np.log(1 - A)))
    return loss

# Execute the forward propagation
def forwardPropagation(w, b, X, Y):
    # Compute Z
    Z = np.dot(w.T, X) + b

    # Determine the number of training samples
    numTraining = float(len(X))

    # Compute the output of the sigmoid activation function
    A = sigmoid(Z)

    # Compute the loss
    loss = computeLoss(numTraining, Y, A)

    # Compute the gradients dZ, dw and db
    dZ = A - Y
    dw = 1 / numTraining * np.dot(X, dZ.T)
    db = 1 / numTraining * np.sum(dZ)

    # Return the results as a dictionary
    gradients = {"dw": dw, "db": db}
    loss = np.squeeze(loss)
    return gradients, loss

# Compute Gradient Descent
def gradientDescent(w, b, X, Y, numIterations, learningRate):
    losses = []
    idx = []

    # Iterate
    for i in range(numIterations):
        gradients, loss = forwardPropagation(w, b, X, Y)
```

